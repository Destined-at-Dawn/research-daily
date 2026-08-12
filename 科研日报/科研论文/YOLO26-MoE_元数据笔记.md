# YOLO26-MoE: A Novel YOLO26-MoE Optimized by an LLM Agent for Insulator Fault Detection Considering UAV Images

##  基本信息

| 字段 | 内容 |
|------|------|
| **分级** |  S级（必读） |
| **作者** | João Pedro Matos-Carvalho, Laio Oriel Seman, Stefano Frizzo Stefenon 等 |
| **出版信息** | arXiv:2605.19595 [cs.CV, cs.AI] |
| **发表日期** | 2026-05-19（3天前！） |
| **首次收录** | 2026-05-20 |
| **领域标签** | cs.CV — YOLO26 · 混合专家(MoE) · LLM超参优化 · 绝缘子缺陷 |
| **链接** | https://arxiv.org/abs/2605.19595](https://arxiv.org/abs/2605.19595 |

##  核心贡献

- **YOLO26-MoE架构**：在YOLO26单阶段检测器的高分辨率分支中嵌入稀疏混合专家（Sparse Mixture-of-Experts, MoE）模块，使模型能自适应地为不同缺陷模式激活不同的"专家"子网络
- **LLM Agent驱动优化**：用工具增强的大语言模型（LLM Agent）协调超参数调优、最终训练和评估全流程——从"人工调参"升级为"AI调AI"
- MoE模块专门解决绝缘子缺陷检测中的核心痛点：**缺陷区域小、故障形态异构、背景复杂、成像条件多变**

##  关键数据

- **[mAP@0.5](mailto:mAP@0.5) = 0.9900**，**[mAP@0.5](mailto:mAP@0.5):0.95 = 0.9515**
- 超越了所有最新YOLO版本（包括YOLOv8/v9/v10/v11/v12）
- 稀疏MoE在不显著增加推理开销的前提下实现了自适应特征精炼

##  定位

关键论文

##  备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
