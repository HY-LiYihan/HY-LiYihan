# Proposed Research Plan and Past Research Experience - Bilingual Copy Draft

> Usage: copy the text inside each `text` block into the corresponding field. The English version is written for direct submission. The Chinese version is a faithful reference version for your own checking or later reuse.
> Tone: specific, research-oriented, and deliberately not overstated.

---

## English Version

### Mandatory Field 1 - Research Experience or Participation in Research Projects

```text
My research experience has developed across embodied robotics, autonomous systems, and AI-assisted annotation systems. Although my undergraduate major is English Language and Literature, I have pursued minors in Intelligent Unmanned Systems and Computer Science and Technology, and I have focused my research training on robotics, perception, and embodied AI.

At HCL Lab, HKUST(GZ), I have worked as a research assistant on dexterous manipulation and visuo-tactile robot learning. My current work includes building a Real2Sim pipeline for dexterous manipulation using Gaussian Splatting, semantic segmentation, and agent-based scene construction. The goal is to reproduce real manipulation scenes as interactive simulation assets that can support policy learning and evaluation. I have also studied visuo-tactile WAM for multimodal decision-making, focusing on how visual and tactile observations can be synchronized, represented, and evaluated under realistic sensing constraints. In addition, I have been developing a UMI-style teleoperation device adapted to flexible grasping tasks, with the aim of collecting general manipulation demonstrations in a more scalable and reproducible way.

At RAPID Lab, Sun Yat-sen University, I participated in several embodied intelligence projects under Prof. Hui Cheng. In the RAPID Hand project, I worked around the structure and hardware of a perception-integrated dexterous hand, including low-latency control and visuo-tactile synchronization for contact-rich whole-hand manipulation. In visual navigation research, I contributed to studies on building and optimizing topological navigation maps from unordered images, which relates to robust navigation in open and weakly structured environments. I also contributed to vision-based traversability research, including end-to-end RGB-to-traversability modeling and evaluation. This experience helped me understand the full research loop from hardware constraints and sensing pipelines to benchmark design and policy evaluation.

As a UAV development intern at Guangzhou Yunzong Technology Co., Ltd., I worked on practical autonomous systems. I developed ESP32-based multi-agent star networking and Mesh communication components and helped build data/video transmission links for multi-UAV coordination and ground-station feedback. I also participated in UAV autonomy development, including propulsion selection, formation flight, navigation and localization, flight-test workflow design, and analysis of reinforcement-learning-based disturbance-resilient control. This industry-side experience made me more aware of the gap between algorithms that work in controlled experiments and systems that must operate under communication, latency, power, and safety constraints.

I have also conducted research on AI-assisted annotation and language systems. As first author of Goldsmith, I designed a gold-loss-guided prompt training method for agentic annotation. The system treats an operational definition as a trainable textual object, uses a small expert gold set to evaluate candidate definitions, and accepts revisions only when structured gold loss improves. I evaluated the pipeline on NER, relation extraction, and event extraction tasks. This work trained me to think carefully about evaluation design, error analysis, and human-in-the-loop workflows. In related projects, I built GenreShift and Rosetta, systems for linguistic analysis and agentic annotation, including feature extraction, retrieval, LLM judge routing, review feedback, and Prodigy-compatible JSONL export.

Across these projects, my role has not been limited to isolated implementation. I have participated in problem formulation, system integration, data collection, experiment design, baseline construction, and writing. I am still developing as a researcher, but these experiences have given me a practical foundation for studying embodied robot learning: I have worked with physical hardware, teleoperation, simulation, perception models, dataset construction, and evaluation pipelines. They also shaped my proposed research direction: building more scalable, physically grounded, and evaluable Real2Sim-to-Real pipelines for visuo-tactile dexterous manipulation.
```

### Mandatory Field 2 - Proposed Research Topic

```text
My proposed research topic is Real2Sim-to-Real visuo-tactile learning for contact-rich dexterous manipulation. The general field is embodied AI and robot learning. The specific research questions are: how can real manipulation scenes, human teleoperation demonstrations, and tactile feedback be converted into realistic simulation and training data; and how can robot policies trained with these assets transfer reliably back to physical dexterous manipulation tasks?
```

### Mandatory Field 3 - Proposed Research Plan

```text
Proposed title: Grounded Real2Sim-to-Real Visuo-Tactile Learning for Dexterous Manipulation

Research motivation. Robots are becoming increasingly capable in perception and planning, but contact-rich manipulation remains difficult to scale. A dexterous robot must understand not only what an object looks like, but also how contact evolves during grasping, sliding, squeezing, regrasping, and recovery from small failures. Current robot learning pipelines often face two practical bottlenecks. First, collecting high-quality real robot data is expensive and slow. Second, simulation is useful but often fails to capture the geometry, contact, compliance, and visual appearance of real scenes. I propose to study a Real2Sim-to-Real approach that uses real scene reconstruction, semantic grounding, teleoperation, tactile sensing, and policy learning as one connected pipeline.

Aim 1: Build a realistic and editable Real2Sim scene-construction pipeline. I will investigate how to reconstruct manipulation scenes from RGB/RGB-D observations and human demonstrations using 3D Gaussian Splatting and semantic segmentation. The reconstructed scene should not only be visually realistic but also usable for robot learning. Therefore, I will study how to convert visual reconstructions into interactive simulation assets with object masks, approximate collision geometry, task-relevant affordance regions, and contact-relevant annotations. Agent-based tools may be used to assist scene parsing, asset organization, and consistency checking, but the system should remain auditable rather than relying on unverified automatic outputs.

Aim 2: Develop a scalable demonstration and sensing interface. I plan to use a UMI-style teleoperation setup adapted to flexible grasping and dexterous manipulation. The interface will record synchronized RGB, proprioception, action, and tactile signals when available. A key technical question is how to align demonstrations with reconstructed simulation scenes so that the same task can be replayed, perturbed, and evaluated in simulation before deployment. I will also examine latency, calibration, and synchronization, because small timing errors can have large effects in contact-rich manipulation.

Aim 3: Learn visuo-tactile manipulation policies with simulation and real feedback. Starting from imitation learning baselines, I will study policies conditioned on RGB, tactile observations, and task descriptions. Diffusion-style visuomotor policies are a natural baseline because they can model action sequences for continuous control, while vision-language-action models provide a useful reference for instruction-conditioned generalization. I do not assume that a large VLA model alone will solve dexterous manipulation. Instead, I want to study when foundation-model priors are useful and when local physical feedback, tactile signals, and task-specific adaptation are necessary. If feasible, I will explore safe online adaptation in constrained settings, where the robot can improve from real execution while respecting safety and hardware limits.

Aim 4: Evaluate transfer, data efficiency, and robustness. I will design experiments around flexible grasping and representative contact-rich manipulation tasks such as grasping deformable or irregular objects, regrasping after partial failure, and manipulating objects with limited visual observability. Evaluation will include task success rate, contact stability, recovery behavior, sim-to-real performance gap, demonstration efficiency, control latency, and sensitivity to lighting, object pose, and tactile noise. I will compare policies trained with real-only data, simulation-only data, and the proposed Real2Sim-to-Real pipeline. The aim is not only to improve performance, but also to identify which parts of the pipeline actually reduce the sim-to-real gap.

Preliminary foundation and feasibility. My previous work directly supports this plan. At HCL Lab, I have worked on Gaussian Splatting, semantic segmentation, agent-based Real2Sim scene construction, visuo-tactile WAM, and UMI-style teleoperation for flexible grasping. At RAPID Lab, I worked on RAPID Hand hardware and low-latency visuo-tactile synchronization, topological visual navigation from unordered images, and RGB-to-traversability modeling. These experiences give me a starting point in physical system integration, multimodal sensing, simulation, dataset construction, and evaluation. My work on Goldsmith also supports the methodology of this proposal because it trained me to design careful evaluation loops, structured error analysis, and human-in-the-loop refinement rather than relying only on qualitative demonstrations.

Originality and expected contribution. The originality of this plan lies in treating Real2Sim-to-Real not as a single conversion step, but as a full research pipeline connecting real scene capture, semantic grounding, teleoperation, tactile sensing, simulation asset generation, policy learning, and real-world evaluation. If successful, the work could contribute: (1) a reproducible pipeline for turning real manipulation scenes into training and evaluation environments; (2) a visuo-tactile dataset for flexible and dexterous manipulation; (3) empirical evidence on when tactile feedback and scene reconstruction improve transfer; and (4) open benchmarks or tools that can help other researchers compare Real2Sim-to-Real manipulation methods.

Significance and impact. This research is relevant to manufacturing, logistics, service robotics, and assistive robotics, especially in regions where robotics hardware, supply chains, and application scenarios are close to each other. In the Guangdong-Hong Kong-Macau Greater Bay Area, there is a strong opportunity to connect university research with hardware manufacturing, testing sites, and real deployment needs. I hope this work can contribute a small but concrete step toward robots that can learn manipulation skills with less manual engineering, better evaluation, and more reliable transfer from research prototypes to practical systems.

Selected references:
[1] Kerbl, B., Kopanas, G., Leimkuehler, T., and Drettakis, G. 3D Gaussian Splatting for Real-Time Radiance Field Rendering. SIGGRAPH, 2023.
[2] Chi, C., Feng, S., Du, Y., Xu, Z., Cousineau, E., Burchfiel, B., Tedrake, R., and Song, S. Diffusion Policy: Visuomotor Policy Learning via Action Diffusion. RSS, 2023.
[3] Chi, C., Xu, Z., Pan, C., Cousineau, E., Burchfiel, B., Feng, S., Tedrake, R., and Song, S. Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots. RSS, 2024.
[4] Zitkovich, B. et al. RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control. CoRL, 2023.
```

### Mandatory Field 4 - Research Proposal Upload

```text
[Upload file here]

Suggested filename: Yihan_Li_Research_Proposal_Real2Sim_VisuoTactile_Manipulation.pdf
Suggested title: Grounded Real2Sim-to-Real Visuo-Tactile Learning for Dexterous Manipulation
```

### Vision Statement 1 - Reasons for Wishing to Pursue PhD / MPhil Studies in the GBA

```text
I wish to pursue PhD / MPhil studies in the Guangdong-Hong Kong-Macau Greater Bay Area because the region is one of the few places where robotics research, hardware manufacturing, AI innovation, and real application scenarios are tightly connected. My proposed research requires this kind of environment. It is not enough to study robot learning only through offline datasets or simulation; I need access to physical platforms, sensing hardware, teleoperation devices, manufacturing resources, and realistic testing scenarios.

The GBA is especially attractive to me because it combines strong universities, active robotics laboratories, advanced manufacturing in Shenzhen and Dongguan, and international academic links through Hong Kong and Macau. Having studied at Sun Yat-sen University and visited HKUST(GZ), I have already experienced how the region supports cross-institutional and cross-disciplinary work. For a student working between embodied AI, robot hardware, perception, and practical deployment, this ecosystem is highly valuable.

I also hope to grow in an environment where research can remain academically rigorous while staying close to real-world constraints. My past experiences in university laboratories and UAV industry work showed me that good robotics research should be tested against latency, calibration, communication, hardware reliability, and safety. The GBA provides a rare setting where these constraints can be studied seriously rather than treated as afterthoughts.
```

### Vision Statement 2 - Long-Term Career Plan, Aims and Interests After Graduation

```text
My long-term goal is to become a researcher and engineer working on embodied intelligence systems that can operate reliably in real environments. After graduation, I hope to continue working at the intersection of robot learning, multimodal perception, and hardware-aware system design. I am open to both academic and industry research paths, but in either case I want my work to remain connected to physical robots and measurable deployment challenges.

In the medium term, I would like to build expertise in visuo-tactile robot learning, Real2Sim-to-Real transfer, dexterous manipulation, and evaluation methodology. I hope to publish rigorous research, release useful tools or datasets when appropriate, and collaborate with laboratories and companies that work on manufacturing, logistics, service robotics, or assistive systems.

In the longer term, I hope to lead or contribute to a research group that develops practical embodied AI systems with responsible evaluation standards. I am particularly interested in robots that can learn from human demonstrations, improve through safe real-world feedback, and adapt to objects and environments that were not fully specified during training. I also hope to mentor younger students, especially those crossing from nontraditional backgrounds into robotics and AI, as I have done from language studies into intelligent unmanned systems and computer science.
```

### Vision Statement 3 - Contribution to Research Development in the GBA and Society

```text
I would like to contribute to the GBA by developing robotics research that is both technically solid and useful for real application contexts. The region has strong needs and opportunities in advanced manufacturing, logistics, urban services, inspection, healthcare support, and education. My proposed work on Real2Sim-to-Real visuo-tactile manipulation could contribute to these areas by making robot skill learning more data-efficient, easier to evaluate, and more transferable from laboratory settings to practical environments.

At the research level, I hope to contribute open datasets, reproducible benchmarks, and system components when possible. Robotics research often suffers when results depend on private hardware, undocumented calibration, or qualitative demonstrations. I would like my work to emphasize clear evaluation, transparent failure analysis, and reusable tools so that other researchers can build on it.

At the educational and community level, I hope to continue organizing robotics training and competitions, as I have done in RoboTech Association at Sun Yat-sen University. Student robotics communities are important because they help more young people enter engineering through hands-on systems rather than only coursework. In the long run, I hope my work can help connect university research, student innovation, and industrial needs in the GBA.

For society, I am most interested in robots that extend human capability rather than replace human judgment. Reliable manipulation systems could reduce repetitive labor, assist in hazardous environments, and support services where human workers face physical constraints. I believe such systems should be developed with careful attention to safety, transparency, and realistic evaluation.
```

### Vision Statement 4 - Intellectual Vision and Aspirations Demonstrated Through the Proposed Research Plan

```text
The intellectual vision behind my proposed research is that embodied intelligence should be physically grounded. A robot should not only recognize objects or follow language commands; it should understand how perception, contact, action, and environment interact over time. For dexterous manipulation, this means learning from vision, touch, geometry, demonstrations, and real execution feedback together.

My aspiration is to study the bridge between rich AI models and physical robot systems. Foundation models can provide useful semantic priors, but contact-rich manipulation also depends on timing, force, uncertainty, and hardware constraints. I want to investigate how these two sides can be combined: using large models and reconstruction methods to organize perception and task context, while using tactile feedback, teleoperation data, simulation, and real experiments to keep policies grounded in physical reality.

I also want my research to demonstrate a careful attitude toward evaluation. In robotics, a visually impressive demo is not enough. A meaningful system should specify what data it uses, how scenes are reconstructed, what assumptions are made in simulation, what failure cases remain, and how much transfer actually occurs on real hardware. Through this proposed research, I hope to show that I can pursue ambitious questions while keeping the methodology honest, testable, and useful to others.
```

---

## 中文版本

### 必填项 1 - 科研经历或科研项目参与情况

```text
我的科研经历主要围绕具身机器人、自主系统和 AI 辅助标注系统展开。虽然我的本科主修专业是英语专业文学学士，但我同时修读智能无人系统辅修和计算机科学与技术辅修，并将主要科研训练集中在机器人感知、具身智能和多模态系统上。

在香港科技大学（广州）HCL Lab，我作为科研助理参与灵巧操作与视触觉机器人学习相关研究。目前的工作包括基于 Gaussian Splatting、语义分割和 agent 构建面向灵巧操作的 Real2Sim pipeline，将真实操作场景复现为可交互的仿真资产，用于策略学习与评估。我也参与视触觉 WAM 相关研究，关注视觉与触觉信息如何在真实传感约束下进行同步、表示和评估。此外，我正在自主研发适配柔性夹取任务的 UMI 风格遥操作设备，希望以更可扩展、可复现的方式采集通用操作演示数据。

在中山大学 RAPID Lab，我在成慧教授指导下参与多个具身智能项目。在 RAPID Hand 项目中，我围绕感知集成灵巧手的结构和硬件开发开展工作，包括低延迟控制和视触觉同步，以支撑接触丰富的全手灵巧操作实验。在视觉导航方向，我参与基于无序图像建立拓扑导航地图并进行优化的研究，这与开放、弱结构化环境中的鲁棒导航密切相关。我也参与视觉可通行性研究，包括端到端 RGB 到可通行性的模型开发与评估。这些经历帮助我理解从硬件约束、传感链路、数据集构建到模型评估的完整研究流程。

在广州云纵科技有限公司担任无人机研发实习生期间，我参与更接近工程部署的自主系统开发。我基于 ESP32 研发多机星型组网与 Mesh 通信组件，并搭建数图传链路，用于支持多机协同和地面站数据回传。我还参与无人机自主系统研发，内容包括动力系统选型、编队飞行、导航定位、飞行测试流程设计，以及基于强化学习的抗扰控制方法和飞行日志分析。这段产业侧经历让我更加清楚地认识到，算法从受控实验走向真实系统时，会受到通信、延迟、功耗、安全性和硬件可靠性等因素的影响。

我也开展过 AI 辅助标注和语言系统相关研究。作为 Goldsmith 的第一作者，我设计了 Gold-Loss 引导的智能体标注提示训练方法。该系统将操作性定义视为可训练文本对象，用小规模专家 gold set 评估候选定义，并仅在结构化 gold loss 下降时接受修改。我在 NER、关系抽取和事件抽取任务上对该流水线进行了实验验证。这项工作训练了我在评估设计、错误分析和 human-in-the-loop 流程方面的能力。在相关项目中，我还构建了 GenreShift 和 Rosetta，用于语言学分析与智能体标注，涉及计量语言学特征抽取、检索、LLM judge 路由、审阅反馈和 Prodigy 兼容 JSONL 导出。

总体而言，我的科研参与并不只是单一模块实现，而是覆盖问题定义、系统集成、数据采集、实验设计、baseline 构建和论文写作等环节。我仍处于科研训练阶段，但这些经历已经为我研究具身机器人学习打下了较实际的基础：我接触过真实硬件、遥操作、仿真、多模态感知、数据集构建和评估流程。这些经历也塑造了我后续希望深入研究的方向，即构建更可扩展、更具物理 grounding、也更容易评估的 Real2Sim-to-Real 视触觉灵巧操作学习 pipeline。
```

### 必填项 2 - 拟研究课题

```text
我的拟研究课题是面向接触丰富灵巧操作的 Real2Sim-to-Real 视触觉机器人学习。该方向属于具身智能与机器人学习领域。具体研究问题包括：如何将真实操作场景、人类遥操作演示和触觉反馈转化为可用于仿真和训练的数据资产；以及如何使基于这些资产训练的机器人策略可靠迁移回真实灵巧操作任务。
```

### 必填项 3 - 拟研究计划

```text
拟题：Grounded Real2Sim-to-Real Visuo-Tactile Learning for Dexterous Manipulation

研究动机。机器人在感知和规划方面已经取得了较大进展，但接触丰富的灵巧操作仍然很难规模化。一个灵巧机器人不仅需要理解物体“看起来是什么”，还需要理解抓取、滑动、挤压、重抓和小失败恢复过程中接触状态如何变化。当前机器人学习 pipeline 面临两个实际瓶颈：第一，高质量真实机器人数据采集成本高、速度慢；第二，仿真虽然有用，但常常无法准确表达真实场景中的几何、接触、柔顺性和视觉外观。因此，我希望研究一种 Real2Sim-to-Real 方法，将真实场景重建、语义 grounding、遥操作、触觉传感和策略学习连接成一个完整 pipeline。

目标一：构建真实且可编辑的 Real2Sim 场景生成 pipeline。我将研究如何利用 RGB/RGB-D 观测和人类演示，通过 3D Gaussian Splatting 与语义分割重建操作场景。该重建结果不仅需要视觉上真实，还应能服务于机器人学习。因此，我会研究如何将视觉重建转化为可交互仿真资产，包括物体 mask、近似碰撞几何、任务相关 affordance 区域和接触相关标注。agent 工具可以辅助场景解析、资产组织和一致性检查，但系统应保持可审计，而不是依赖不可验证的自动输出。

目标二：开发可扩展的演示采集与传感接口。我计划使用适配柔性夹取和灵巧操作的 UMI 风格遥操作设备，记录同步的 RGB、本体感知、动作和可用的触觉信号。一个关键技术问题是如何将演示数据与重建后的仿真场景对齐，使同一任务能够在仿真中回放、扰动和评估，再部署到真实系统中。我也会关注延迟、标定和同步问题，因为在接触丰富操作中，微小的时间误差也可能显著影响策略表现。

目标三：利用仿真和真实反馈学习视触觉操作策略。我会从模仿学习 baseline 开始，研究以 RGB、触觉观测和任务描述为条件的策略。Diffusion-style visuomotor policy 是自然的 baseline，因为它适合连续控制中的动作序列建模；vision-language-action model 则可作为指令条件泛化的参考。我不会预设大规模 VLA 模型本身能够解决灵巧操作，而是希望研究 foundation model prior 在哪些情况下有帮助，以及何时必须依赖本地物理反馈、触觉信号和任务特定适配。如果条件允许，我也会探索安全约束下的 online adaptation，使机器人能从真实执行中改进，同时遵守安全和硬件限制。

目标四：评估迁移能力、数据效率和鲁棒性。我会围绕柔性夹取和代表性的接触丰富操作任务设计实验，例如抓取柔性或不规则物体、部分失败后的重抓，以及在视觉观测受限情况下进行操作。评估指标包括任务成功率、接触稳定性、失败恢复能力、sim-to-real performance gap、演示数据效率、控制延迟，以及对光照、物体位姿和触觉噪声的敏感性。我将比较 real-only data、simulation-only data 和所提出 Real2Sim-to-Real pipeline 训练出的策略。研究目的不仅是提升性能，也包括识别 pipeline 中哪些环节真正缩小了 sim-to-real gap。

前期基础与可行性。我的已有经历能直接支持这一计划。在 HCL Lab，我已经参与 Gaussian Splatting、语义分割、agent-based Real2Sim 场景构建、视触觉 WAM 和面向柔性夹取的 UMI 风格遥操作。在 RAPID Lab，我参与 RAPID Hand 硬件与低延迟视触觉同步、基于无序图像的拓扑视觉导航，以及 RGB 到可通行性的模型研究。这些经历使我具备一定的物理系统集成、多模态传感、仿真、数据集构建和评估基础。Goldsmith 项目也支持该研究方法，因为它训练了我设计严谨评估循环、结构化错误分析和 human-in-the-loop refinement 的能力，而不是仅依赖定性展示。

原创性与预期贡献。该计划的原创性在于把 Real2Sim-to-Real 视为一个完整研究 pipeline，而不仅是单次场景转换步骤。它连接真实场景采集、语义 grounding、遥操作、触觉传感、仿真资产生成、策略学习和真实世界评估。如果研究顺利，预期贡献包括：（1）一个将真实操作场景转化为训练和评估环境的可复现 pipeline；（2）一个面向柔性和灵巧操作的视触觉数据集；（3）关于触觉反馈和场景重建在何种条件下改善迁移效果的实验证据；（4）可供其他研究者比较 Real2Sim-to-Real 操作方法的开放 benchmark 或工具。

意义与影响。该研究与制造、物流、服务机器人和辅助机器人等场景相关，尤其适合硬件供应链、机器人实验平台和应用场景紧密相连的地区。在粤港澳大湾区，大学研究、硬件制造、测试场景和实际部署需求之间有较强连接。我希望这项工作能为机器人以更少人工工程、更清晰评估和更可靠迁移能力学习操作技能提供一个小而具体的贡献。

参考文献：
[1] Kerbl, B., Kopanas, G., Leimkuehler, T., and Drettakis, G. 3D Gaussian Splatting for Real-Time Radiance Field Rendering. SIGGRAPH, 2023.
[2] Chi, C., Feng, S., Du, Y., Xu, Z., Cousineau, E., Burchfiel, B., Tedrake, R., and Song, S. Diffusion Policy: Visuomotor Policy Learning via Action Diffusion. RSS, 2023.
[3] Chi, C., Xu, Z., Pan, C., Cousineau, E., Burchfiel, B., Feng, S., Tedrake, R., and Song, S. Universal Manipulation Interface: In-The-Wild Robot Teaching Without In-The-Wild Robots. RSS, 2024.
[4] Zitkovich, B. et al. RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control. CoRL, 2023.
```

### 必填项 4 - 上传研究计划

```text
[在此处上传文件]

建议文件名：Yihan_Li_Research_Proposal_Real2Sim_VisuoTactile_Manipulation.pdf
建议题目：Grounded Real2Sim-to-Real Visuo-Tactile Learning for Dexterous Manipulation
```

### Vision Statement 1 - 希望在粤港澳大湾区攻读 PhD / MPhil 的原因

```text
我希望在粤港澳大湾区攻读 PhD / MPhil，是因为这里是少数将机器人科研、硬件制造、AI 创新和真实应用场景紧密连接的地区。我的拟研究方向需要这样的环境。仅仅依靠离线数据集或仿真研究机器人学习是不够的，我需要接触真实机器人平台、传感硬件、遥操作设备、制造资源和实际测试场景。

大湾区对我尤其有吸引力，因为这里同时拥有高水平大学、活跃的机器人实验室、深圳和东莞等地的先进制造能力，以及香港、澳门带来的国际学术连接。我在中山大学学习，并曾在香港科技大学（广州）访问和参与科研，已经感受到这一地区对跨机构、跨学科合作的支持。对于一个工作在具身 AI、机器人硬件、感知和实际部署之间的学生来说，这样的生态非常宝贵。

我也希望在一个既重视学术严谨性，又接近真实约束的环境中成长。过去在高校实验室和无人机企业的经历让我认识到，好的机器人研究需要面对延迟、标定、通信、硬件可靠性和安全性等问题。大湾区提供了少有的条件，让这些真实约束能够被认真研究，而不是被当作附带问题处理。
```

### Vision Statement 2 - 毕业后的长期职业规划、目标与兴趣

```text
我的长期目标是成为一名研究者和工程师，专注于能够在真实环境中可靠运行的具身智能系统。毕业后，我希望继续在机器人学习、多模态感知和硬件感知系统设计的交叉方向工作。我对学术研究和产业研究路径都持开放态度，但无论在哪种路径中，我都希望自己的工作始终与真实机器人和可衡量的部署挑战保持连接。

中期来看，我希望在视触觉机器人学习、Real2Sim-to-Real 迁移、灵巧操作和评估方法方面建立系统能力。我希望发表严谨的研究成果，在合适情况下发布有用的工具或数据集，并与制造、物流、服务机器人或辅助系统方向的实验室和企业合作。

长期来看，我希望能够领导或深度参与一个研究团队，开发具有负责任评估标准的实用具身 AI 系统。我尤其关注能够从人类演示中学习、通过安全真实反馈改进，并适应训练阶段未被完全指定的物体和环境的机器人。我也希望继续指导更年轻的学生，特别是那些像我一样从非传统背景进入机器人和 AI 领域的人。
```

### Vision Statement 3 - 希望对大湾区科研发展和社会作出的贡献

```text
我希望为大湾区贡献既具有技术扎实性、又贴近真实应用场景的机器人研究。大湾区在先进制造、物流、城市服务、巡检、医疗支持和教育等方面都有强烈需求和机会。我拟研究的 Real2Sim-to-Real 视触觉操作学习，可以通过提升机器人技能学习的数据效率、评估清晰度和从实验室到实际环境的迁移能力，为这些方向提供支持。

在科研层面，我希望在条件允许时贡献开放数据集、可复现 benchmark 和系统组件。机器人研究有时会因为私有硬件、未充分记录的标定流程或定性展示而难以复现。我希望自己的工作强调清晰评估、透明失败分析和可复用工具，使其他研究者能够在此基础上继续推进。

在教育和社区层面，我希望延续在中山大学 RoboTech 机器人协会中的组织经验，继续参与机器人训练和竞赛活动。学生机器人社区很重要，因为它能让更多年轻人通过动手系统进入工程领域，而不只是停留在课程学习中。长期来看，我希望自己的工作能促进大湾区高校科研、学生创新和产业需求之间的连接。

对社会而言，我最关注的是能够扩展人类能力、而不是简单替代人类判断的机器人。可靠的操作系统可以减少重复劳动，辅助危险环境中的任务，也可以支持一些受到体力限制的服务场景。我认为这类系统应该在安全性、透明性和真实评估方面被谨慎开发。
```

### Vision Statement 4 - 希望通过拟研究计划展示的学术视野和抱负

```text
我的学术视野是：具身智能应该具有物理 grounding。机器人不应只是识别物体或执行语言指令，而应该理解感知、接触、动作和环境如何随时间相互作用。对于灵巧操作而言，这意味着需要同时从视觉、触觉、几何、人类演示和真实执行反馈中学习。

我的抱负是研究丰富 AI 模型与真实机器人系统之间的桥梁。Foundation model 可以提供有价值的语义先验，但接触丰富操作同样依赖时序、力、 uncertainty 和硬件约束。我希望研究如何结合这两方面：利用大模型和重建方法组织感知与任务语境，同时利用触觉反馈、遥操作数据、仿真和真实实验，让策略保持在物理现实中 grounding。

我也希望通过该研究展示一种谨慎的评估态度。在机器人研究中，视觉上精彩的 demo 并不足够。一个有意义的系统应该说明它使用了什么数据、如何重建场景、仿真中有哪些假设、还存在哪些失败案例，以及在真实硬件上到底发生了多少迁移。通过这个拟研究计划，我希望证明自己能够追求有野心的问题，同时保持方法诚实、可测试，并且对其他研究者有用。
```
