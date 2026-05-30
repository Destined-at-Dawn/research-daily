# Zero-Shot, Safe and Time-Efficient UAV Navigation via Potential-Based Reward Shaping, Control Lyapunov and Barrier Functions

## 📋 基本信息

| 字段 | 内容 |
|------|------|
| **分级** | 🔴 S级（必读） |
| **作者** | Ashik Abrar Naeem, Mohammad Ariful Haque |
| **出版信息** | arXiv:2605.01787 [eess.SY, cs.LG, cs.RO] |
| **发表日期** | 2026-05-03（3周前） |
| **首次收录** | 2026-05-22 |
| **领域标签** | cs.RO —— 强化学习+形式化安全 · 零样本泛化 · PBRS+CLF+CBF |
| **链接** | https://arxiv.org/abs/2605.01787](https://arxiv.org/abs/2605.01787 |

## 🎯 核心贡献

- **三重保障融合**：Potential-Based Reward Shaping（PBRS，引导高效轨迹）+ Control Lyapunov Functions（CLF，驱向目标+稳定性）+ Control Barrier Functions（CBF，形式化安全约束/防碰撞）
- **CLF-CBF-QP滤波器**：推理时将CLF和CBF目标联合求解为二次规划问题（QP），实时输出安全控制指令——训练时不需要考虑安全性，推理时QP滤波器兜底
- **零样本泛化**：模型在简单环境中训练，无需额外训练即可在复杂环境中泛化——这是CLF-CBF-QP滤波器的关键优势：安全不依赖训练环境的复杂度

## 📊 关键数据

- 相比先前RL导航方法，**显著减少任务时间**
- 在复杂环境中**零样本（zero-shot）表现卓越**，无需重训练
- 同时优化速度和安全——此前的方法通常在两者之间取舍

## 📍 定位

关键论文

## 📝 备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
