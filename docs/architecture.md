---
title: 系统架构
desc: 了解系统的整体设计、模块划分与数据流。
breadcrumb: "[首页](/) › 核心模块 › 系统架构"
layout: default
---

## 架构概览

系统采用经典的 **感知-规划-控制** 三层架构，各模块通过 ROS2 话题（Topic）和服务（Service）进行通信，实现松耦合设计。

```
┌─────────────────────────────────────────────────┐
│                    传感器层                       │
│  相机 · 激光雷达 · IMU · 编码器 · 压感传感器     │
└──────────────────┬──────────────────────────────┘
                   │ sensor_msgs
┌──────────────────▼──────────────────────────────┐
│                  感知模块                         │
│  3D检测 · 语义分割 · 深度估计 · 目标跟踪        │
└──────────────────┬──────────────────────────────┘
                   │ perception_msgs
┌──────────────────▼──────────────────────────────┐
│                  导航模块                         │
│  建图(SLAM) · 全局规划 · 局部规划 · 重定位       │
└──────────────────┬──────────────────────────────┘
                   │ nav_msgs
┌──────────────────▼──────────────────────────────┐
│                  控制模块                         │
│  底盘控制 · 机械臂控制 · 云台同步 · 力控        │
└──────────────────┬──────────────────────────────┘
                   │ cmd_msgs
┌──────────────────▼──────────────────────────────┐
│                  执行器层                         │
│  电机 · 舵机 · 电调 · 底盘 · 机械臂             │
└─────────────────────────────────────────────────┘
```

## 核心模块

### 感知模块

感知模块负责从传感器原始数据中提取环境语义信息，输出结构化的感知结果供下游模块使用。

| 节点 | 输入 | 输出 | 频率 |
|------|------|------|------|
| `armor_detector` | Image | ArmorArray | 100 Hz |
| `depth_estimator` | Image | DepthMap | 30 Hz |
| `semantic_seg` | Image | SegMap | 30 Hz |
| `target_tracker` | Detection + Depth | TrackArray | 100 Hz |

### 导航模块

导航模块融合建图、定位与规划，输出速度指令给控制模块。

- **SLAM：** 基于 FAST_LIO2 的激光-惯性里程计，支持退化环境检测与回环闭合
- **全局规划：** 基于 A\* / Dijkstra 的拓扑路径搜索
- **局部规划：** 基于 TEB 的时空优化，支持动态避障
- **重定位：** ICP + 语义匹配，实现全局重定位

### 控制模块

控制模块接收规划的速度指令，输出底层执行器的控制信号。

- **底盘控制：** 差速/阿克曼运动学模型，PID 速度跟踪
- **机械臂控制：** 6-DoF 逆运动学求解，MoveIt2 集成
- **云台同步：** EKF 预测 + 前馈补偿，延迟补偿至 <5ms

## 数据流

所有模块间通过 ROS2 DDS 通信，关键数据流如下：

```bash
# 传感器 → 感知
/camera/image_raw       → armor_detector  → /detection/armor
/camera/image_raw       → depth_estimator → /perception/depth
/lidar/points           → slam_node       → /slam/odom

# 感知 → 导航
/perception/obstacles   → local_planner   → /nav/cmd_vel
/slam/odom              → global_planner  → /nav/path

# 导航 → 控制
/nav/cmd_vel            → chassis_ctrl    → /cmd/chassis
/nav/arm_goal           → arm_ctrl        → /cmd/arm
```

> 💡 **设计原则：** 每个模块都是独立的 ROS2 节点，可以单独启动、调试和替换。你可以只运行感知模块来验证检测效果，而不需要启动整个导航栈。

## 项目结构

```
your-project/
├── docs/                    ← 项目文档（本站）
├── src/
│   ├── perception/          ← 感知模块
│   │   ├── armor_detector/
│   │   ├── depth_estimator/
│   │   └── semantic_seg/
│   ├── navigation/          ← 导航模块
│   │   ├── slam/
│   │   ├── global_planner/
│   │   └── local_planner/
│   ├── control/             ← 控制模块
│   │   ├── chassis_ctrl/
│   │   ├── arm_ctrl/
│   │   └── gimbal_ctrl/
│   └── common/              ← 公共工具与消息定义
├── config/                  ← 参数配置文件
├── launch/                  ← 启动文件
├── docker/                  ← Docker 构建文件
└── README.md
```
