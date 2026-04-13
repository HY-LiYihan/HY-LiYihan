---
title: 常见问题
desc: 使用过程中遇到的问题和解决方案。
breadcrumb: "[首页](/) › 参考 › 常见问题"
layout: default
---

## 安装相关

### Q: `rosdep install` 失败怎么办？

检查网络连接，或使用国内镜像源：

```bash
export ROSDISTRO_INDEX_URL=https://mirrors.tuna.tsinghua.edu.cn/rosdistro/index-v4.yaml
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```

### Q: Docker 容器里没有 GPU 怎么办？

确保已安装 NVIDIA Container Toolkit：

```bash
# 安装
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
sudo apt-get install -y nvidia-container-toolkit

# 重启 Docker
sudo systemctl restart docker

# 验证
docker run --rm --gpus all nvidia/cuda:12.2.0-base-ubuntu22.04 nvidia-smi
```

## 运行相关

### Q: RViz2 在 Docker 里打不开？

需要配置 X11 转发：

```bash
# 主机端允许 X 转发
xhost +local:docker

# 启动容器时挂载 X11 socket
docker compose run --rm dev
```

确保 `docker-compose.yml` 中已配置：

```yaml
environment:
  - DISPLAY=${DISPLAY}
volumes:
  - /tmp/.X11-unix:/tmp/.X11-unix:rw
```

### Q: SLAM 建图出现漂移？

可能的原因和排查顺序：

1. **IMU 数据质量** → 检查 `ros2 topic hz /imu/data` 是否稳定
2. **激光雷达时间同步** → 检查 `message_filters` 是否正常
3. **运动过快** → 降低底盘速度，或启用回环检测
4. **退化环境** → 长走廊等场景，启用退化检测

## 性能相关

### Q: 推理延迟太高怎么办？

| 优化手段 | 预期提升 | 难度 |
|---------|---------|------|
| TensorRT FP16 | 2-3x | 低 |
| 模型剪枝 | 1.5-2x | 中 |
| 输入分辨率降低 | 1.5x | 低 |
| 多线程流水线 | 1.3x | 中 |

### Q: 系统整体 CPU 占用过高？

- 检查是否有节点以过高频率运行：`ros2 topic hz <topic>`
- 降低非关键节点的运行频率
- 检查是否有死循环或频繁的内存分配
