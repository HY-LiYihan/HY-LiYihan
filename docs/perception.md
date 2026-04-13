---
title: 感知模块
desc: 3D 目标检测、语义分割、深度估计与目标跟踪。
breadcrumb: "[首页](/) › 核心模块 › 感知模块"
layout: default
---

## 概述

感知模块负责从传感器原始数据中提取环境语义信息，输出结构化的感知结果供下游模块使用。

主要包含以下子模块：

- **装甲板检测**：基于 YOLOv11 的实时目标检测
- **深度估计**：单目/双目深度推理
- **语义分割**：场景级语义理解
- **目标跟踪**：基于 EKF 的多目标跟踪

## 装甲板检测

### 模型选型

我们使用 YOLOv11 作为基线模型，并通过 TensorRT / OpenVINO 加速推理。

| 模型 | 输入分辨率 | 推理延迟 (Jetson Orin) | mAP@0.5 |
|------|-----------|----------------------|---------|
| YOLOv11n | 640×640 | 8 ms | 92.1% |
| YOLOv11s | 640×640 | 12 ms | 95.3% |
| YOLOv11m | 640×640 | 22 ms | 96.8% |

> **💡 选择建议：** 在 RMUL 场景下推荐 `YOLOv11s`，在延迟和精度之间取得了最佳平衡。

### TensorRT 部署

```bash
# 导出 ONNX
python export.py --weights best.pt --format onnx --simplify

# 转换 TensorRT Engine
trtexec --onnx=best.onnx \
        --saveEngine=best.engine \
        --fp16 \
        --batch=1

# 验证推理
python trt_infer.py --engine best.engine --test images/
```

## 目标跟踪

### EKF 预测

使用扩展卡尔曼滤波预测高速机动目标轨迹，核心状态向量：

$$
\mathbf{x} = [x, y, z, v_x, v_y, v_z, \theta, \omega]^T
$$

预测步骤：

1. 观测：装甲板中心 3D 坐标（相机坐标系）
2. 预测：基于运动模型外推下一时刻状态
3. 更新：融合观测与预测，输出最优估计

### 命中率

在 RMUL 2025 赛季实测数据：

| 场景 | 命中率 | 平均延迟 |
|------|--------|---------|
| 静止目标 | 98% | 5 ms |
| 横向移动 | 93% | 8 ms |
| 高速机动 | 85% | 12 ms |

## 通信协议

感知节点与 STM32 控制器之间的通信协议：

```cpp
// 感知输出消息定义
struct PerceptionMsg {
    uint8_t target_id;      // 目标 ID
    float   px, py, pz;     // 目标位置 (相机系)
    float   vx, vy, vz;     // 目标速度
    float   confidence;      // 置信度
    uint8_t armor_type;     // 装甲板类型
} __attribute__((packed));
```

> ⚠️ **注意：** 在高延迟无线环境下（>50ms），需要启用预测补偿模式，否则云台跟踪会滞后。

## 常见问题

### Q: TensorRT 推理结果和 ONNX 不一致？

检查是否开启了 FP16 模式。某些小目标检测对精度敏感，可以尝试：

```bash
# 使用 FP32 模式
trtexec --onnx=best.onnx --saveEngine=best_fp32.engine
```

### Q: 检测在暗光环境下掉点严重？

- 训练时加入暗光数据增强（random brightness / gamma）
- 考虑使用红外相机作为补充输入
- 参考 `config/perception_lowlight.yaml` 中的调参建议
