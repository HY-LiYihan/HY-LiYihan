# 李溢涵

- 电话：+86 18615276438
- 邮箱：liyihan.xyz@gmail.com
- 个人网站：[liyihan.xyz](https://liyihan.xyz)

## 教育背景

**中山大学**  
外国语学院 英语专业  
2023年9月 - 2027年6月（预计）  
GPA：3.71/4.0

计算机学院 计算机科学与技术辅修  
GPA：3.85/4.0

相关课程：
- 数学：线性代数、微积分、离散数学、数学建模
- 计算机：数据结构与算法、自然语言处理（NLP）、程序设计

## 学术成果

**OmniTrav: A Dataset and Benchmark for 360° Vision-based Traversability via Foundation Models**  
**Yihan Li**, Hao Ren, Zhenglan Jiang, Junzhe Zhu, Hui Cheng*  
IROS 2026 submitted

**Unordered Landmark Visual Navigation**  
Hao Ren, Junzhe Zhu, **Yihan Li**, Zetong Bi, Le Zheng, Zhi Li, Yiqing Yuan, Zhaoliang Wan, Lu Qi, Hui Cheng  
ECCV 2026 submitted

**RAPID Hand: A Robust, Affordable, Perception-Integrated, Dexterous Manipulation Platform for Generalist Robot Autonomy**  
Zhaoliang Wan, Zetong Bi, Zida Zhou, Hao Ren, Yiming Zeng, **Yihan Li**, Lu Qi, Xu Yang, Ming-Hsuan Yang, Hui Cheng  
NeurIPS 2025

## 科研经历

### OmniTrav：面向 360° 视觉可通行性的数据集与基准
第一作者，合作导师：成慧 教授  
2025年6月 - 2026年3月

- 提出 Camera-to-Traversability（C2T）流水线，将针孔、鱼眼、全景等多类相机的 RGB 输入直接映射为 360° 径向通行距离向量，消除对深度传感器的依赖。
- 构建 OmniTrav 数据集（4.7k 场景 / 25 万帧 / 577 GB），设计基于基础模型（DINOv3 + FPN + 跨注意力角度投影器）的自动标注流水线，无需人工标注。
- 在三类相机上均优于 ResNet-FC 与 DINOv3-MLP 基线；全景障碍检测 F1 达 1.0，针孔中位误差 0.27 m，为首个覆盖多相机几何的可通行性基准。

### 感知融合灵巧手运动控制与抓取实验（RAPID Hand）
科研助理，合作导师：成慧 教授  
2024年11月 - 2025年6月

- 面向自研 20 自由度仿人灵巧手，开发实时底层运动控制驱动，建立稳定的 1 kHz 控制回路，保障抓取过程中的控制精度与输出力矩表现。
- 负责视触觉融合模块，完成腕部视觉、指尖触觉传感器与关节本体感知的同步与融合，通过硬件级时序同步将感知链路延迟稳定在 7 ms 以内。
- 搭建高保真 MuJoCo 仿真环境开展 Sim2Real 验证，基于 Diffusion Policy 训练全手视触觉策略；在滚动与平移任务上达到 50/50 成功率，多指非抓取取物任务显著优于对比工作。

### Unordered Landmark Visual Navigation（ULVN）
科研助理，合作导师：成慧 教授  
2025年6月 - 2026年3月

- 参与 ULVN 框架开发，该框架在无时序先验、仅 RGB 输入条件下实现无序地标视觉导航，联合设计拓扑建图、全局定位与闭环规划三个模块。
- 框架中 RAVEL 建图模块 F1 达 0.7365，优于 PlaceNav（0.6043）、ViNT（0.5815）等基线；BPL 定位模块全局准确率 95.49%，困难路径准确率 93.99%，均超越 MegaLoc 与 JIST。
- 导航成功率（ULVN+NoMaD）达 71.9%，平均碰撞次数 0.42，显著优于端到端 SOTA 方法 UniGoal（61.6%）。


### 面向学术语篇的 LLM 自动标注研究
（广东省哲学社会科学规划项目 2025）  
科研助理，合作导师：郭曼 副教授  
2025年1月 - 2025年10月

- 基于大语言模型（LLM）与 Prompt Engineering 构建自动标注系统，从非结构化文本中抽取语言投射关系。
- 通过迭代微调实现 85% 标注准确率，将复杂学术语篇转换为层级化结构数据，支撑大规模量化分析。

## 工作经历

### 中山大学 RoboTech 机器人协会
会长；竞赛队队长  
2023年11月 - 至今

- 负责协会日常运营与训练体系建设，管理 160+ 人跨学科团队。
- 组织校级“智行空间”无人车技术挑战赛，统筹赛务、规则制定与技术支持，共服务 47 支参赛队伍。
- 统筹 RoboMaster、电赛等国家级赛事备赛，管理项目进度、经费与跨组协作，获得多项国家级奖项。

### Yun Drone
研发实习生  
2025年6月 - 2026年3月

- 完成科研无人机硬件选型与系统集成，确定飞控、电调及传感器配置方案，优化载荷能力。
- 执行飞行稳定性与机动性测试，基于飞行日志定位控制异常并提出 PID 调参建议。
- 协同结构团队优化机体布局，确保敏感传感器的电磁兼容（EMC）与减振性能。

## 项目经历

### RoboMaster 视觉系统开发（RMUL）
25 赛季副队长；26 赛季战队指导；算法组负责人（导航与视觉）  
2025年3月 - 2025年7月

- 负责战队导航与视觉算法方向规划与技术落地，在 NVIDIA Jetson 与 Intel NUC 平台开发高性能感知与控制模块。
- 设计并实现自瞄系统，使用扩展卡尔曼滤波（EKF）预测高速机动目标轨迹，命中率达到 90%+。
- 部署 YOLO 装甲板分类模型，并通过 TensorRT 与 OpenVINO 优化，将推理延迟降至 10 ms，满足实时闭环控制。
- 实现视觉主机与 STM32 控制器的稳健通信协议，在高延迟无线环境下保证云台精确同步。

### 复杂场景越野车自主导航与机械臂精准抓取系统
项目负责人  
2025年3月 - 2025年7月

- 面向四驱差速与阿克曼底盘，优化 FAST_LIO2 解决退化环境建图与回环问题；结合高频里程计与 ICP 实现高效高精重定位。
- 优化基于 TEB 的局部规划器，实现高速高精导航；融合双目点云、YOLOv11 与 PnP 求解，完成 6 自由度机械臂精准抓取。

### 基于 Mesh 组网与 GNSS RTK 的无人机集群飞行
核心成员  
2025年7月 - 2025年10月

- 调试并部署 Mesh 自组网通信模块，建立机间实时数据链路。
- 采集并验证 GNSS RTK 定位数据，完成高精度位置标定，并通过静态/动态飞行结果与基站数据对比分析误差来源。
- 共同制定集群飞行测试方案，支撑多机协同任务（集群起降、轨迹跟踪、动态编队变换）。

### GenreShift：基于计量语言学与 LLM 的智能体裁转换系统
项目负责人  
2024年10月 - 2025年11月

- 负责准平行语料构建、数据爬取与清洗、文体特征提取、LoRA 微调及 Mixture-of-Experts（MoE）系统搭建。
- 统筹项目整体规划，已申请发明专利：一种基于计量语言学与 LLM 的智能体裁转换方法及系统（申请号：2025105553019）。

## 荣誉奖项

- 国家一等奖（队长），中国机器人及人工智能大赛，2025
- 全国总冠军（队长），全国智能无人系统应用挑战赛，2025
- 国家二等奖（队长），全国大学生电子设计竞赛，2025
- 国家二等奖（视觉组组长），RoboMaster 高校联盟赛，2025
- Honorable Mention（队长），美国大学生数学建模竞赛（MCM），2024

## 专业技能

- 编程与开发：ROS1/2、Python、C/C++、MATLAB、STM32/Arduino 嵌入式开发
- 工程工具：Fusion 360、SolidWorks、EDA 设计
- 证书：AOPA 多旋翼视距内驾驶员执照、C1 驾照
- 语言：中文（母语）、英语（TEM-4）、法语
- 兴趣：羽毛球、足球、骑行、FPV 无人机

