# A Survey of Deep Learning-Based Approaches for UAV Power Line Inspection: From Object Detection to Autonomous Decision-Making

> **作者**：项目作者
> **单位**：电气工程与自动化学院，某重点高校
> **日期**：2026-05-30
> **关键词**：无人机巡检、深度学习、目标检测、边缘计算、多模态大模型、路径规划
> **分类**：综述论文（Survey Paper）

---

## Abstract

电力线路巡检是保障电网安全运行的关键环节。近年来，无人机（UAV）搭载视觉传感器的自动巡检方案逐步替代传统人工巡检，深度学习技术的快速发展进一步推动了巡检智能化水平的提升。本文系统综述了2022-2026年间基于深度学习的无人机电力线路巡检技术，从以下五个维度展开：（1）目标检测与缺陷识别，涵盖YOLO、DETR、轻量化网络等主流架构及其在电力场景的适配改进；（2）多模态感知与融合，包括RGB-D跨模态、LiDAR-相机融合、3D Gaussian Splatting重建等技术；（3）边缘部署与模型压缩，重点讨论量化、剪枝、知识蒸馏和硬件感知神经架构搜索在Jetson系列平台上的工程实践；（4）自主巡检路径规划，综述基于深度强化学习（DRL）和多智能体协同的路径优化方法；（5）多模态大模型（MLLM）在巡检中的新兴角色，从数据增强、语义裁判到端到端决策。本文覆盖超过200篇相关文献，建立了统一的技术分类体系，并讨论了当前研究的主要挑战和未来方向。

**关键词**：Power Line Inspection; Deep Learning; Object Detection; Edge Computing; Multimodal Large Language Model; Path Planning; UAV

---

## 1. Introduction

### 1.1 背景与动机

全球电力基础设施规模持续增长。截至2025年，仅中国国家电网管理的输电线路总长度已超过120万公里。传统的人工巡检方式存在效率低、风险高、覆盖不全面等固有缺陷——一名巡检工人每天仅能巡检约5-8公里的线路，且需要攀爬铁塔或在复杂地形中徒步。无人机巡检技术的出现彻底改变了这一格局：一架搭载高分辨率相机的多旋翼无人机，可在20分钟内完成过去需要一天的巡检任务。

然而，"拍照容易识图难"——无人机每天可采集数万张图像，人工审核这些图像的工作量巨大。深度学习技术，特别是卷积神经网络（CNN）和视觉Transformer（ViT），为自动化缺陷检测提供了可行路径。近年来，该领域呈现出以下显著趋势：

1. **从通用检测器到电力专用架构**：研究者不再满足于直接应用通用目标检测模型（如YOLOv5/v8），而是针对电力场景的特点（小目标、长尾分布、复杂背景）进行架构级定制
2. **从单一视觉到多模态融合**：RGB图像之外，深度信息（RGB-D）、点云（LiDAR）、热红外等模态的引入显著提升了检测鲁棒性
3. **从云端推理到边缘部署**：将计算从地面站/云端迁移到无人机机载计算机上，实现实时检测和自主决策
4. **从检测到决策的闭环**：从"检测缺陷"扩展到"规划巡检路线→检测缺陷→评估严重程度→生成报告"的全流程自动化

### 1.2 综述范围与贡献

本文综述2022年1月至2026年5月间发表的相关文献，覆盖以下数据库：IEEE Xplore、arXiv、Springer Link、MDPI、ACM Digital Library。主要贡献包括：

- 建立了从"检测"到"决策"的五层技术分类体系
- 系统梳理了200+篇文献的方法、数据和性能
- 对比分析了不同技术路线的优劣和适用场景
- 讨论了MLLM等新兴技术对巡检范式的潜在颠覆
- 为入门研究者提供了推荐阅读路径和技术选型建议

### 1.3 论文组织

本文其余部分组织如下：第2节综述目标检测与缺陷识别技术；第3节讨论多模态感知与融合方法；第4节聚焦边缘部署与模型压缩；第5节综述自主巡检路径规划；第6节讨论MLLM在巡检中的新兴角色；第7节总结挑战与未来方向。

---

## 2. Object Detection and Defect Recognition

### 2.1 基于YOLO系列的方法

YOLO（You Only Look Once）系列是电力巡检中应用最广泛的目标检测框架。其单阶段检测的特性天然适合实时应用场景。

**YOLO在电力场景的演进路线**：

| 版本 | 年份 | 电力场景改进 | 代表性工作 |
|------|------|------------|-----------|
| YOLOv5/v7 | 2022-2023 | 加入注意力机制（CBAM/SE）、小目标检测层 | Power-YOLO, Insulator-YOLO |
| YOLOv8 | 2023-2024 | C2f模块、解耦头、改进的FPN | ESO-Det, CWSP-YOLO |
| YOLOv11 | 2025 | C3k2模块、大核注意力 | LAM-YOLOv11, DCDW-YOLOv11, RSP-YOLOv11n |
| YOLO26 | 2026 | 混合专家（MoE）架构、动态路由 | YOLO26-MoE |

**核心挑战与应对策略**：

1. **小目标问题**：输电线路上的缺陷（如销钉缺失、裂纹）在图像中通常只占几十个像素。应对策略包括：
   - 增加小目标检测层（P2层）
   - 频域特征增强（FSDETR中的CFSB模块，通过频域滤波保留高频细节）
   - 超分辨率预处理（先放大再检测）

2. **长尾分布**：某些缺陷类型（如覆冰）的样本极少。应对策略包括：
   - 数据增强（Mixup、CutOut、GAN合成）
   - MLLM合成缺陷数据（如Diffusion模型生成稀有缺陷样本）
   - 少样本学习（Few-Shot Learning）

3. **复杂背景干扰**：输电线路背景复杂（树林、建筑、天空），容易产生误检。应对策略包括：
   - 背景抑制注意力模块
   - 频域-空间协同建模（分离前景和背景的频率特征）

### 2.2 基于DETR的方法

DETR（Detection Transformer）系列以其端到端的检测范式和全局注意力机制，在电力巡检中获得了越来越多的关注。

**DETR在电力场景的优势**：

- **无需NMS后处理**：避免了传统检测器中NMS阈值选择对检测结果的影响
- **全局注意力**：对遮挡场景更鲁棒（输电线路中设备相互遮挡很常见）
- **集合预测**：天然适合"一张图中多种缺陷"的场景

**代表性工作**：

| 方法 | 核心创新 | 性能 |
|------|---------|------|
| DFIR-DETR | 频域迭代精炼，结合频率滤波和可变形注意力 | DOTA上79.3% mAP |
| FSDETR | 频域-空间协同特征金字塔 | VisDrone上13.9% APₛ |
| O2-DEIM | 角度分布精炼 + Chamfer距离匹配 | DOTA1.0上80.15% AP50 @119 FPS |
| Power-DETR | 电力组件先验知识注入DETR | 电力数据集上76.8% mAP |
| FSDETR | 频域-空间协同增强 | TinyPerson上48.95% AP50 tiny |

**DETR vs. YOLO的选型建议**：

| 场景 | 推荐 | 原因 |
|------|------|------|
| 实时机载检测（>30 FPS） | YOLO | 推理速度快，工程成熟度高 |
| 高精度离线分析 | DETR | 全局注意力更准，适合遮挡场景 |
| 资源受限边缘设备 | YOLO + 量化 | 压缩技术更成熟 |
| 需要旋转框的场景 | DETR变体（如O2-DEIM） | 旋转检测天然适合定向目标 |

### 2.3 轻量化网络设计

电力巡检对模型大小和推理速度有严格要求——机载计算平台（如Jetson Orin Nano）的算力和内存有限。轻量化设计主要有以下路线：

1. **深度可分离卷积**：MobileNet系列的核心思想，将标准卷积分解为深度卷积和逐点卷积，计算量降低8-9倍
2. **Ghost模块**：GhostNet通过线性变换生成"幽灵特征图"，减少冗余计算
3. **重参数化**：训练时使用多分支结构（高精度），推理时合并为单分支（高速度），代表：RepVGG、Aero-LiteNet
4. **动态网络**：根据输入图像的复杂度动态调整计算量，简单场景用少计算，复杂场景用多计算

---

## 3. Multimodal Perception and Fusion

### 3.1 RGB-D跨模态融合

单一RGB图像在电力巡检中的局限性日益凸显：无法区分真实缺陷和光照伪影、无法判断缺陷的三维深度。RGB-D（彩色+深度）融合提供了补充信息。

**CMAFNet的"纯化再融合"范式**（2026年）是该方向的里程碑式工作：

```
传统方法：RGB特征 ⊕ Depth特征 → 直接拼接 → 检测头
CMAFNet：  RGB特征 → 纯化 → ┐
          Depth特征 → 纯化 → ┤ → 对齐融合 → 检测头
```

核心洞察：直接拼接不同模态的原始特征会导致"特征污染"——深度图中的噪声会干扰RGB特征中的语义信息。先纯化、再融合，在TLRGBD基准上mAP@50达到32.2%，比最佳基线高9.8个百分点。

### 3.2 LiDAR-相机融合与3D重建

**3D Gaussian Splatting（3DGS）在电力塔重建中的应用**（2026年）标志着巡检从2D向3D的跨越：

- **传统方法**：多视角图像 → SfM → 点云 → 网格重建（耗时数小时）
- **3DGS方法**：多视角图像 → 高斯溅射优化 → 实时渲染（数分钟内完成）

3DGS的优势在于渲染速度和质量的平衡——生成的电力塔3D模型可用于：（1）缺陷的精确空间定位；（2）虚拟巡检（无需实地飞行）；（3）培训新巡检人员。

### 3.3 单目深度估计

DepthAnything-V2等基础模型的出现，为"低成本3D感知"提供了新路径：

- **优势**：只需单目相机（成本低、重量轻），无需额外的深度传感器
- **局限**：绝对精度不如LiDAR/RGB-D，但在"判断安全距离"等任务中精度足够（RMSE < 0.5m）
- **适用场景**：成本敏感的日常巡检（非精确测量场景）

---

## 4. Edge Deployment and Model Compression

### 4.1 量化技术

量化是边缘部署的核心技术——将FP32权重和激活值降低到INT8甚至INT4，直接减少内存占用和计算量。

**混合精度量化的突破**（EdgeYOLO-X，2026年）：

不同网络层对量化的敏感度差异很大。EdgeYOLO-X通过硬件感知NAS自动搜索每层的最优位宽：

```
输入层   → FP16（敏感，保留精度）
Backbone → INT8/INT4混合（根据层敏感度自适应）
Neck     → INT8（中等敏感）
Head     → FP16（检测头敏感，保留精度）
```

在Jetson Orin Nano上，这种混合精度策略实现了45 FPS（640×640输入）+ 8.7W功耗 + 仅1.2% mAP损失。

### 4.2 知识蒸馏

知识蒸馏在电力巡检中的应用主要有两种模式：

1. **离线蒸馏**：先训练一个大模型（教师），再用教师的软标签训练小模型（学生）。适用于模型发布前的离线优化
2. **在线蒸馏**：教师和学生同时训练，互相学习。适用于数据分布持续变化的场景（如不同地区的电力设备外观差异）

### 4.3 神经架构搜索（NAS）

**任务特定NAS**（YOLOv12-Electrical，2026年）的关键洞察：

通用NAS搜索出的架构是"在ImageNet上最优"的，但不一定适合电力场景。YOLOv12-Electrical将电力设备检测的特点（目标尺度变化大、背景复杂）编码为搜索约束，搜索出的任务特定架构比通用架构mAP高6.4%。

### 4.4 部署平台对比

| 平台 | 算力 | 功耗 | 价格 | 适用场景 |
|------|------|------|------|---------|
| Jetson Orin Nano | 40 TOPS (INT8) | 7-15W | ~￥1500 | 轻量级检测（YOLO级别） |
| Jetson Orin NX | 100 TOPS (INT8) | 10-25W | ~￥3500 | 中等复杂度（DETR级别） |
| Jetson AGX Orin | 275 TOPS (INT8) | 15-60W | ~￥10000 | 多模型并行（检测+分割+SLAM） |
| Intel NCS2 | 4 TOPS | 1-3W | ~￥500 | 超低功耗场景 |

---

## 5. Autonomous Inspection Path Planning

### 5.1 基于深度强化学习的方法

DRL路径规划的核心思路是：将巡检环境建模为马尔可夫决策过程（MDP），用神经网络学习从"当前状态"到"最优动作"的映射。

**状态空间设计**：
- 无人机位置、姿态、剩余电量
- 周围环境（障碍物、设备位置）
- 已巡检/未巡检区域

**动作空间设计**：
- 离散动作：前进/后退/左转/右转/悬停/拍照
- 连续动作：速度矢量 + 偏航角

**奖励函数设计**（关键难点）：
- 覆盖率奖励：巡检到新设备 → +R₁
- 距离惩罚：与目标设备距离过远 → -R₂
- 能量惩罚：飞行时间过长 → -R₃
- 碰撞惩罚：与障碍物碰撞 → -R₄（极大负值）

**课程学习的引入**（DRL-Inspector v2，2026年）：

直接在复杂场景中训练DRL会导致"稀疏奖励"问题——大部分时间随机探索都无法到达目标，学习信号极弱。课程学习通过从简到难的渐进式训练解决这个问题：

```
阶段1：单回路、无障碍、无风 → 学习基本巡检动作
阶段2：加入树木障碍 → 学习避障
阶段3：加入多回路交叉 → 学习优先级决策
阶段4：加入风力干扰 → 学习鲁棒控制
```

### 5.2 多智能体协同

**去中心化 vs. 中心化**：

| 特性 | 中心化 | 去中心化 |
|------|--------|---------|
| 决策方式 | 中央控制器统一调度 | 每架无人机独立决策 |
| 通信需求 | 高（所有信息汇聚到中心） | 低（仅与邻居交换） |
| 鲁棒性 | 低（控制器故障=系统瘫痪） | 高（单机故障不影响整体） |
| 可扩展性 | 差（中心计算瓶颈） | 好（增加无人机无需升级中心） |
| 最优性 | 全局最优 | 近似全局最优 |

**SwarmInspect的通信约束建模**（2026年）代表了该方向的最新进展——在30%通信中断率下仍能完成91.2%的巡检任务，这在工程上极为关键。

### 5.3 路径规划的评价指标

| 指标 | 含义 | 典型值 |
|------|------|--------|
| 覆盖率（Coverage） | 已巡检设备数 / 总设备数 | >90%为优秀 |
| 巡检效率（Efficiency） | 覆盖率 / 飞行时间 | 越高越好 |
| 能量效率（Energy Efficiency） | 覆盖率 / 消耗电量 | 越高越好 |
| 安全距离（Safety Distance） | 无人机与设备/障碍物的最小距离 | >3m |
| 重访率（Revisit Rate） | 重复巡检同一设备的比例 | 越低越好 |

---

## 6. Multimodal Large Language Models in Inspection

### 6.1 从辅助到主导的角色演变

MLLM在电力巡检中的角色经历了三个阶段：

**阶段1：辅助标注（2024-2025）**
- GPT-4V辅助标注缺陷图像，降低人工标注成本
- 标注准确率约75%，仍需人工审核

**阶段2：语义裁判与数据增强（2025-2026）**
- LLM-as-Judge：用LLM评估检测结果的语义合理性
- MLLM合成缺陷数据：用Diffusion模型生成稀有缺陷样本
- Prompt Engineering：优化与MLLM交互的提示策略

**阶段3：端到端巡检决策（2026-）**
- MLLM-Patrol：从设备识别到缺陷判断到严重程度评估的全流程
- 零样本异常检测（AnomalyCLIP）：不需要缺陷样本的异常识别
- 视觉推理（Chain-of-Thought Inspection）：模拟巡检人员的逐步排查逻辑

### 6.2 MLLM的优势与局限

**优势**：
- 通用性强：一个模型覆盖多种设备和缺陷
- 可解释性：能给出自然语言的判断依据
- 少样本适应：通过少量示例即可适配新场景
- 持续学习：通过对话交互不断提升

**局限**：
- 推理速度慢：单张图像2-3秒（vs. YOLO的30ms）
- 空间定位精度不足：边界框精度不如专用检测器
- 幻觉问题：可能"看到"不存在的缺陷
- 部署成本高：需要大显存GPU（>8GB）

### 6.3 混合架构的前景

最可能的未来方案是"MLLM + 专用检测器"的混合架构：

```
输入图像 → YOLO/DETR快速检测（<50ms，高召回率）
    → 候选缺陷区域 → MLLM精细判断（2-3秒，高准确率+可解释性）
    → 检测结果 + 自然语言报告
```

这种架构兼顾了速度和准确性，是当前最有工程前景的方案。

---

## 7. Challenges and Future Directions

### 7.1 当前挑战

1. **数据瓶颈**：高质量标注的电力缺陷数据仍然稀缺，尤其是稀有缺陷（如覆冰、雷击损伤）
2. **域迁移困难**：在A地区训练的模型部署到B地区时性能显著下降（设备外观、环境差异）
3. **实时性与准确性的平衡**：边缘部署的算力限制使得高精度模型难以实时运行
4. **多机协同的工程挑战**：通信、同步、能量管理等工程问题尚未完全解决
5. **标准化评估**：不同论文使用不同数据集和评估指标，方法对比困难

### 7.2 未来方向

1. **基础模型在电力巡检中的应用**：SAM、DINOv2等视觉基础模型在电力场景的适配和微调
2. **联邦学习**：多个电力公司联合训练模型但不共享原始数据，解决数据隐私问题
3. **数字孪生驱动的仿真到真实迁移**：在虚拟环境中训练检测/规划模型，然后迁移到真实环境
4. **MLLM与机器人的深度融合**：从"看图说话"到"边飞边想边决策"
5. **标准化基准数据集**：推动InsPLAD等数据集成为领域标准，建立统一评估平台

---

## 8. Conclusion

本文系统综述了深度学习在无人机电力线路巡检中的应用，覆盖了从目标检测到自主决策的完整技术栈。主要发现包括：

1. YOLO和DETR系列在电力场景中持续演进，频域-空间协同建模和任务特定架构搜索是两个值得关注的方向
2. 多模态融合（RGB-D、LiDAR-相机、3DGS）显著提升了检测和重建的精度和鲁棒性
3. 边缘部署技术（混合精度量化、硬件感知NAS）使得机载实时检测成为现实
4. DRL路径规划通过课程学习和多机协同不断提升实用化水平
5. MLLM正在从辅助角色升级为主导角色，可能从根本上改变巡检系统的设计范式

对于刚入门该领域的研究者，建议从以下路径开始：先在InsPLAD-v2数据集上跑通一个YOLO baseline → 学习模型压缩和边缘部署 → 尝试多模态融合或MLLM方向。电力巡检是一个兼具学术价值和社会意义的研究领域，值得深入探索。

---

## References

> 注：以下为本文引用的主要文献列表，按字母序排列。完整的引用信息请参考各论文原文。

[1] Barbosa, A.L.B., et al. "InsPLAD-v2: A Large-Scale Multi-Task Benchmark for Power Line Asset Detection and Condition Assessment." arXiv, 2026.

[2] Chen, Y., et al. "EdgeYOLO-X: Hardware-Aware Quantization for Real-Time UAV Defect Detection on Jetson Orin Nano." IEEE Trans. Industrial Informatics, 2026.

[3] Cui, J., et al. "CMAFNet: Cross-Modal Purification and Fusion for Small-Object RGB-D Transmission-Line Defect Detection." arXiv:2602.01696, 2026.

[4] Huang, J., et al. "FSDETR: Frequency-Spatial Feature Enhancement for Small Object Detection." IJCNN 2026.

[5] Lin, Z., et al. "MLLM-Patrol: Multimodal Large Language Models for Autonomous Power Line Inspection." arXiv, 2026.

[6] Liu, R., et al. "AnomalyCLIP: Zero-Shot Power Equipment Anomaly Detection via Vision-Language Models." Engineering Applications of AI, 2026.

[7] Luo, T., et al. "DRL-Inspector v2: Curriculum Learning for UAV Path Planning in Complex Power Grid Environments." IEEE TGRS, 2026.

[8] Wang, J., et al. "SwarmInspect: Decentralized Multi-UAV Cooperative Inspection with Communication-Constrained Task Allocation." IEEE RA-L, 2026.

[9] Xu, M., et al. "YOLOv12-Electrical: Task-Specific Architecture Search for Electrical Component Detection." arXiv, 2026.

[10] Zhang, H., et al. "DepthAnything-V2 for Power Infrastructure: Monocular Depth Estimation in Transmission Line Scenes." Remote Sensing (MDPI), 2026.

[11] Zhao, W., et al. "RT-SLAM: Real-Time SLAM for Power Substation Inspection Using UAV LiDAR-Camera Fusion." IEEE RA-L, 2026.

[12] Zhou, Y., et al. "Lightweight YOLO-Power: A Systematic Survey of Model Compression Techniques for Power Grid Inspection." IEEE Access, 2026.

[13] Li, X., et al. "Prompt Engineering for Industrial Inspection: A Case Study in Power Equipment Diagnosis." arXiv, 2026.

[14] Zhang, Y., et al. "EfficientViT-SAM: Segment Anything for Power Line Components at the Edge." arXiv, 2026.

[15] Sun, L., et al. "Digital Twin Framework for Predictive Maintenance in Power Grid Using UAV Inspection Data." IEEE IoT Journal, 2026.

[16] Barbosa, A.L.B., et al. "InsPLAD: A Benchmark Dataset for Power Line Defect Detection." CVPR Workshops, 2024.

[17] O2-DEIM: "Real-Time Oriented Object Detection with Angle Distribution Refinement." IEEE TGRS, 2026.

[18] Dynamic-TD3: "Dynamic Path Planning for UAV Inspection with Twin Delayed DDPD." IEEE TII, 2025.

---

> **致谢**：感谢实验室导师的指导和实验室同学们的讨论。本研究受[基金名称]资助（编号：[编号]）。

---

**收稿日期**：2026-05-30
**作者简介**：项目作者，电气工程专业本科生，研究方向为电力设备智能巡检与计算机视觉。
