# Yihan Li

- Phone: +86 18615276438
- Email: liyihan.xyz@gmail.com
- Website: [liyihan.xyz](https://liyihan.xyz)

## Education

**Sun Yat-sen University**  
B.A. in English, School of Foreign Languages  
Sep 2023 - Jun 2027 (Expected)  
GPA: 3.71/4.0

Minor in Computer Science and Technology, School of Computer Science and Engineering  
GPA: 3.85/4.0

Relevant Coursework:
- Mathematics: Linear Algebra, Calculus, Discrete Mathematics, Mathematical Modeling
- Computer Science: Data Structures and Algorithms, Natural Language Processing, Programming Design

## Publications

**OmniTrav: A Dataset and Benchmark for 360° Vision-based Traversability via Foundation Models**  
**Yihan Li**, Hao Ren, Zhenglan Jiang, Junzhe Zhu, Hui Cheng*  
IROS 2026 (Submission)

**Unordered Landmark Visual Navigation**  
Hao Ren, Junzhe Zhu, **Yihan Li**, Zetong Bi, Le Zheng, Zhi Li, Yiqing Yuan, Zhaoliang Wan, Lu Qi, Hui Cheng  
ECCV 2026 (Submission)

**RAPID Hand: A Robust, Affordable, Perception-Integrated, Dexterous Manipulation Platform for Generalist Robot Autonomy**  
Zhaoliang Wan, Zetong Bi, Zida Zhou, Hao Ren, Yiming Zeng, **Yihan Li**, Lu Qi, Xu Yang, Ming-Hsuan Yang, Hui Cheng  
NeurIPS 2025

## Research Experience

### OmniTrav: Dataset and Benchmark for 360° Vision-based Traversability
First Author, Prof. Hui Cheng  
Jun 2025 - Mar 2026

- Proposed the Camera-to-Traversability (C2T) pipeline, directly mapping RGB inputs from pinhole, fisheye, and panoramic cameras to 360° radial clearance vectors, eliminating reliance on depth sensors.
- Built the OmniTrav dataset (4.7k scenes / 250k frames / 577 GB) with an automated annotation pipeline based on foundation models (DINOv3 + FPN + cross-attention angle projector), requiring no manual labeling.
- Outperformed ResNet-FC and DINOv3-MLP baselines across all three camera types; panoramic obstacle detection F1 = 1.0, pinhole median error 0.27 m — the first traversability benchmark covering heterogeneous camera geometries.

### Perception-Integrated Dexterous Manipulation (RAPID Hand)
Research Assistant, Prof. Hui Cheng  
Nov 2024 - Jun 2025

- Developed real-time low-level drivers for a custom 20-DoF anthropomorphic hand, establishing a stable 1 kHz control loop for precise torque and position control during manipulation.
- Designed the whole-hand perception integration module, synchronizing wrist-mounted vision, fingertip tactile sensors, and joint proprioception with hardware-level temporal synchronization under 7 ms latency.
- Built a high-fidelity MuJoCo simulation environment for Sim2Real validation; trained a whole-hand visuotactile Diffusion Policy achieving 50/50 success on rolling and translation tasks, substantially outperforming concurrent work on multi-finger non-prehensile retrieval.

### Unordered Landmark Visual Navigation (ULVN)
Research Assistant, Prof. Hui Cheng  
Jun 2025 - Mar 2026

- Contributed to the ULVN framework, which achieves image-goal navigation from unordered landmark collections using RGB only — no temporal priors or auxiliary sensors — through co-designed topological mapping, global localization, and closed-loop planning.
- RAVEL mapping module achieves F1 = 0.7365, outperforming PlaceNav (0.6043) and ViNT (0.5815); BPL localization achieves 95.49% overall accuracy and 93.99% on difficult paths, surpassing MegaLoc and JIST.
- Navigation success rate (ULVN+NoMaD) reaches 71.9% with 0.42 average collisions, significantly outperforming end-to-end SOTA UniGoal (61.6%).

### LLM-based Automated Annotation for Academic Discourse
(Guangdong Provincial Philosophy and Social Science Planning Project 2025)  
Research Assistant, Assoc. Prof. Man Guo  
Jan 2025 - Oct 2025

- Engineered an automated annotation system using LLMs and prompt engineering to extract linguistic projection relations from unstructured text.
- Achieved 85% annotation accuracy through iterative fine-tuning, converting complex academic discourse into hierarchical structured data for large-scale quantitative analysis.

## Work Experience

### Sun Yat-sen University RoboTech Association
President; Competition Team Captain  
Nov 2023 - Present

- Led daily operations and training programs for the university's largest robotics association, managing a multidisciplinary team of 160+ members.
- Organized the university-level Smart Space Unmanned Vehicle Technology Challenge, coordinating logistics, rules, and technical support for 47 participating teams.
- Directed preparation for major national competitions (RoboMaster, Diansai), overseeing timelines, budget allocation, and cross-team collaboration, resulting in multiple national awards.

### Yun Drone
R&D Intern  
Jun 2025 - Mar 2026

- Conducted hardware selection and system integration for research UAVs, finalizing flight controller, ESC, and sensor configurations for payload optimization.
- Performed flight testing for stability and maneuverability, analyzed logs to identify control anomalies, and provided data-driven PID tuning recommendations.
- Collaborated with the mechanical team to optimize structural layout, ensuring electromagnetic compatibility (EMC) and vibration isolation for sensitive sensors.

## Project Experience

### RoboMaster Visual System Development (RMUL)
Vice Captain (Season 25); Team Advisor (Season 26); Algorithm Group Leader (Navigation & Vision)  
Mar 2025 - Jul 2025

- Led navigation and vision algorithm planning and implementation on NVIDIA Jetson and Intel NUC platforms.
- Designed an auto-aiming system using Extended Kalman Filter (EKF) to predict high-speed erratic target trajectories, achieving a 90%+ hit rate.
- Deployed a YOLO-based armor classification model optimized with TensorRT and OpenVINO, reducing inference latency to 10 ms for real-time closed-loop control.
- Implemented robust communication between the vision PC and STM32 MCU, ensuring precise gimbal synchronization under high-latency wireless conditions.

### Autonomous Navigation and Robotic Arm Pick-and-Place for Off-road Vehicles
Project Leader  
Mar 2025 - Jul 2025

- Optimized FAST_LIO2 for 4WD differential and Ackermann chassis to address mapping and loop-closure in degenerate environments; combined high-frequency odometry with ICP for accurate relocalization.
- Optimized a TEB-based local planner for high-speed precise navigation; integrated binocular point clouds, YOLOv11, and PnP for 6-DoF robotic arm pick-and-place.

### UAV Swarm Flight Based on Mesh Networking and GNSS RTK
Core Member  
Jul 2025 - Oct 2025

- Debugged and deployed a mesh self-organizing network module to establish real-time inter-UAV data links.
- Collected and validated GNSS RTK positioning data; completed high-precision calibration and analyzed error sources by comparing static and dynamic results with base-station data.
- Co-designed swarm flight test plans supporting multi-UAV coordination tasks including swarm takeoff/landing, trajectory tracking, and dynamic formation changes.

### GenreShift: Intelligent Genre Conversion System Based on Quantitative Linguistics and LLMs
Project Leader  
Oct 2024 - Nov 2025

- Led corpus construction, data crawling and cleaning, stylometric feature extraction, LoRA fine-tuning, and Mixture-of-Experts (MoE) system development.
- Directed overall project planning; filed an invention patent: "A Genre Conversion Method and System Based on Quantitative Linguistics and LLMs" (Application No. 2025105553019).

## Honors and Awards

- National First Prize (Team Leader), China Robot and Artificial Intelligence Competition, 2025
- Champion (Team Leader), National Intelligent Unmanned Systems Application Challenge, 2025
- National Second Prize (Team Leader), National Undergraduate Electronics Design Contest, 2025
- National Second Prize (Visual Group Leader), RoboMaster University League, 2025
- Honorable Mention (Team Leader), Mathematical Contest in Modeling (MCM), 2024

## Professional Skills

- Programming: ROS1/2, Python, C/C++, MATLAB, STM32/Arduino embedded development
- Engineering Tools: Fusion 360, SolidWorks, EDA design
- Licenses: AOPA Multi-rotor VLOS Pilot, C1 Driver's License
- Languages: Mandarin (Native), English (TEM-4), French
- Interests: Badminton, Soccer, Cycling, FPV drones

