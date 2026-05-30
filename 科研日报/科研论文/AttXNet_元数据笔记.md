# AttXNet: Robust Lightweight Crack Classification for Real-Time UAV Bridge Inspection

## 📋 基本信息

| 字段 | 内容 |
|------|------|
| **分级** | 🔴 S级（必读） |
| **作者** | Wei Li, Haisheng Li, Weijie Li, Jiandong Wang, Kaichen Ma, Luming Yang |
| **出版信息** | arXiv:2604.27617 [cs.CV, cs.AI] |
| **发表日期** | 2026-04-30 |
| **首次收录** | 2026-05-20 |
| **领域标签** | cs.CV — 轻量CNN · CBAM注意力 · 裂纹分类 · 实时UAV部署 |
| **链接** | https://arxiv.org/abs/2604.27617](https://arxiv.org/abs/2604.27617 |

## 🎯 核心贡献

- **统一轻量CNN框架**，四大组件协同：轻量骨干网络 + CBAM（卷积块注意力模块）进行通道-空间双重增强 + 基于巡检场景先验的定向增强策略 + Focal Loss处理难样本
- **CBAM注意力关键作用**：Grad-CAM可视化证明CBAM将模型注意力从"分散区域"重新定向为"沿裂纹轨迹的精确跟踪"
- 专门针对桥梁巡检的四大障碍：裂纹特征弱、成像条件退化、严重类别不均衡、UAV计算资源受限

## 📊 关键数据

- **825 FPS，仅11.21M参数，1.82G FLOPs**
- F1-score提升2.51%，recall提升3.95%（相比基线）
- 在SDNET2018桥梁桥面数据集上验证

## 📍 定位

关键论文

## 📝 备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
