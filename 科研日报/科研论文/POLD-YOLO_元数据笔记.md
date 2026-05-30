# POLD-YOLO: A Lightweight YOLO11-Based Algorithm for Insulator Defect Detection in UAV Aerial Images

## 📋 基本信息

| 字段 | 内容 |
|------|------|
| **分级** | 🔴 S级（必读） |
| **作者** | Bo Hu, Fanfan Wu, Pengchao Zhang, Jinkai Cui, Yingying Liu |
| **出版信息** | Sensors (Basel), Vol.26, No.5, Article 1733 |
| **发表日期** | 2026-03-09 |
| **首次收录** | 2026-05-11 |
| **领域标签** | cs.CV — 轻量化检测 · 注意力机制 |
| **链接** | https://pmc.ncbi.nlm.nih.gov/articles/PMC12986859/ |

## 🎯 核心贡献

- 基于YOLO11n的四模块创新：PoolingFormer + CGLU增强backbone、全维度自适应下采样（OD-ADown）、轻量共享卷积检测头、Focaler-MPDIoU损失函数
- PoolingFormer将池化操作引入注意力机制，CGLU（Convolutional Gated Linear Unit）增强通道交互

## 📊 关键数据

- **mAP@0.5 = 92.4%**（超越YOLOv5n 3.6%、YOLOv8n 1.6%、YOLO10n 1.4%、YOLO11n 1.6%）
- **参数量仅1.55M**，FLOPs仅3.8G（较YOLO11n基线减少40%参数、39.7%计算量）
- NEU-DET工业缺陷数据集上76.4% mAP，验证泛化能力

## 📍 定位

关键论文

## 📝 备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
