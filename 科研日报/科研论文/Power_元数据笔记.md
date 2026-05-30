# Power Defect Detection with Improved YOLOv12 and ROI Pseudo Point Cloud Visual Analytics

## 📋 基本信息

| 字段 | 内容 |
|------|------|
| **分级** | 🔴 S级（必读） |
| **作者** | Minglang Xu, Jishen Peng（辽宁工程技术大学） |
| **出版信息** | Sensors (MDPI), Vol.26, No.2, Article 445 |
| **发表日期** | 2026-01-09 |
| **首次收录** | 2026-05-12 |
| **领域标签** | cs.CV — YOLOv12改进 · 多分类缺陷检测 · 3D可视化 |
| **链接** | https://pmc.ncbi.nlm.nih.gov/articles/PMC12845865/ |

## 🎯 核心贡献

- **Prior-Guided Region Attention (PG-RA)**：在检测头前插入先验引导的区域注意力模块，增强缺陷区域的特征响应
- **Lightweight Residual Efficient Layer Aggregation Network (LR-RELAN)**：轻量化残差高效层聚合网络，在保持精度的同时控制参数量
- **Dual-Spectrum Adaptive Fusion (DSAF) Loss**：双谱自适应融合损失函数，同时优化分类和定位
- **ROI级伪点云构建**：将2D检测结果投影为3D伪点云，对比SOR/ROR去噪算法实现可视化分析

## 📊 关键数据

- **mAP = 96.8%**（超越YOLOv12基线4.2个百分点），Precision 98.9%，Recall 93.2%，FPS 42.6
- 覆盖**17类电力设备缺陷**（含盖板损坏、开关柜闭合异常等），6601张图像/8753个标注实例
- 消融实验验证DSAF Loss贡献最大（Recall从86.5%→93.2%）

## 📍 定位

关键论文

## 📝 备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
