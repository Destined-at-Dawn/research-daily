# YOLO-PL: Lightweight Power-Line Visual Detection in Agricultural UAV Scenarios

##  基本信息

| 字段 | 内容 |
|------|------|
| **分级** |  A级（重要） |
| **作者** | Yi-Tong Ge, Bao-Ju Wang, Shuai Sun, Yu-Bin Lan（山东理工大学） |
| **出版信息** | PMC12787835 / MDPI Sensors |
| **发表日期** | 2026年（Sensors, Vol.26, Article 109） |
| **首次收录** | 2026-05-22 |
| **领域标签** | cs.CV —— YOLOv12n轻量化 · 动态蛇形卷积 · 多尺度交叉轴注意力 · MoE检测头 · Jetson部署 |
| **链接** | https://pmc.ncbi.nlm.nih.gov/articles/PMC12787835/](https://pmc.ncbi.nlm.nih.gov/articles/PMC12787835/ |

##  核心贡献

- **EfficientNetV2骨干**：Fused-MBConv + MetaPruning通道剪枝，FLOPs减少约60%
- **DSM-A2C2f颈部**：动态蛇形卷积（DSConv，捕获电力线的细长弯曲特征）+ 多尺度交叉轴注意力（MSCAAttention，将复杂度从O(HW×HW)降至O(HW×(H+W))）
- **Detect-PDY检测头**：嵌入参数网络（ParameterNet）中的MoE层，动态卷积系数αᵢ对每个输入样本自适应生成
- **分段连续标注策略**：替代传统边界框标注，更适合细长电力线

##  关键数据

- 仅**2.05M参数，2.8 GFLOPs，4.1 MB模型大小** —— 所有对比模型中最轻
- **mAP@0.5 = 75.5%**，超越YOLOv8n（+13.53%）、YOLOv11n（+15.09%）、Line-YOLO（+7.54%）
- **mAP@0.5:0.95 = 60.9%** —— 所有对比模型中最高
- **Jetson AGX Xavier上88.36 FPS** —— 最快推理
- DSConv单独贡献了**+14.58% mAP@0.5**（消融实验中最显著的增益）

##  定位

重要论文

##  备注

- 详细分析见对应日期日报
- 分级：S级（必读）> A级（重要）> B级（参考）

---

*生成日期：2026-05-30 | 科研日报系统*
