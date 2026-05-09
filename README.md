# Research Daily - AI-Powered Research Report System

> **每天 5 分钟，掌握前沿动态。输入一篇文献，输出一片天地。**

[English](#english) | [中文](#中文)

---

## English

### What is Research Daily?

Research Daily is an AI-powered research assistant that helps researchers in **Electrical Engineering (EE)**, **Integrated Circuits (IC)**, and **Artificial Intelligence (AI)** stay on top of the latest papers — not by flooding you with information, but by helping you **decide what to read**.

### The Problem

Every research paper tool focuses on "get more papers." None helps you decide "should I read this one?"

### The Solution: A Three-Stage Rocket

```
Stage 1: COLLECT  →  Automated paper discovery from arXiv, IEEE, SCI
Stage 2: FILTER   →  S/A/B grading with decision rationale
Stage 3: DECIDE   →  Innovation gap analysis + reading recommendations
```

### Key Features

| Feature | Description |
|---------|-------------|
| **Daily Research Report** | Automated daily paper discovery with S/A/B grading |
| **Paper Analysis** | Input any paper (title/DOI/PDF) → panoramic analysis card |
| **Innovation Gap Finder** | 7-dimension innovation dissection + 6-type Research Gap framework |
| **Multi-Paper Comparison** | Differential matrix + trend identification + innovation space mapping |
| **Academic Writing Toolkit** | Writing formulas extracted from top-journal papers |
| **Peer Review Simulator** | Reviewer-perspective feedback on your draft |
| **Cognitive Reading System** | S/A/B tiered reading methodology for 100-paper research foundation |

### Covered Domains

| Domain | arXiv Categories | Target Venues |
|--------|-----------------|---------------|
| **AI/ML** | cs.AI, cs.LG, cs.CV, cs.CL, stat.ML | NeurIPS, ICML, ICLR, AAAI |
| **Integrated Circuits** | — | IEEE JSSC, ISSCC, DAC, VLSI |
| **Electrical Engineering** | eess.SY, eess.SP, physics | IEEE TPEL, TIE, ECCE |
| **Interdisciplinary** | physics, math.OC | Nature/Science sub-journals |

### Five Workflows

```
Workflow A: Paper Input → Intelligent Matching & Panoramic Analysis
Workflow B: Daily Research Report (with S/A/B grading)
Workflow C: Innovation Gap Discovery Engine (7-dim dissection + Research Gap 6-type)
Workflow D: Academic Writing Formula Library (from top-journal paper teardowns)
Workflow E: Research Guidance (stage-based mentoring + peer review simulation)
```

### Quick Start

1. **Install the Skill**: Drop `科研日报/科研日报-skill.yaml` into your AI assistant's skill directory
2. **First Run**: The system will guide you through a 4-step setup (field positioning → paper baseline → reading mode → innovation focus)
3. **Daily Use**: Say "generate today's research report" or set up automation

```bash
# Example interactions
"生成今日科研日报"          # Generate today's report
"帮我看看这篇论文"          # Analyze a paper
"这个方向还有什么可以做？"    # Find innovation gaps
"对比这几篇论文"            # Multi-paper comparison
"帮我审一下这篇论文"        # Peer review simulation
```

### Automation

Supports scheduled daily/weekly/monthly report generation via cron jobs.

---

## 中文

### 这是什么？

科研日报系统是一个 AI 驱动的科研助手，面向 **电气工程（EE）**、**集成电路（IC）** 和 **人工智能（AI）** 领域的研究者。

**核心理念**：不做信息搬运工，做你的"论文导航员"。

### 解决什么问题？

调研了 4 个科研日报工具（news-bot、daily-arXiv-ai-enhanced、ChatDailyPapers、Arxiv-tracker），发现一个共同空白：

> **所有工具都在做"获取更多信息"，没人做"帮你决定读不读"。**

### 三级火箭架构

| 阶段 | 功能 | 输出 |
|------|------|------|
| **获取** | 自动采集 arXiv/IEEE/SCI 论文 | 原始论文列表 |
| **筛选** | S/A/B 三级分级 + 决策理由 | 值得读的论文 + 为什么值得读 |
| **决策** | 创新点拆解 + Research Gap 分析 | 该做什么 + 怎么做 |

### 五大工作流

| 工作流 | 功能 | 触发方式 |
|--------|------|---------|
| **A** | 文献输入→智能匹配与全景分析 | 输入论文标题/DOI/PDF |
| **B** | 每日科研日报生成 | "生成今日日报" / 定时触发 |
| **C** | 创新点发现引擎 | "创新点是什么" / "还有什么可以做" |
| **D** | 学术写作心法库 | "这篇论文怎么写这么好" |
| **E** | 科研指导 + 审稿模拟 | "帮我规划" / "帮我审稿" |

### 日报模块

| 模块 | 内容 | 筛选标准 |
|------|------|---------|
| 🔥 今日突破 | 1-2 条重大突破 | 影响力大 + 领域直接相关 |
| 📄 前沿论文 | 3-5 篇 S/A 级论文 | 含 S/A/B 分级决策理由 |
| 💡 技术洞察 | 论文间联系/趋势/交叉方向 | 引用链追踪 + 跨领域观察 |
| 🛠️ 工具与代码 | 开源工具/复现代码 | 可复现/可学习 |
| 📅 明日关注 | 截稿/会议/事件预告 | 领域相关 |
| 📊 学习笔记 | 可汇入认知系统的提炼 | 从论文中提的可学点 |

### 目录结构

```
research-daily/
│
├── 科研日报/                        ← 核心系统
│   ├── README.md                   ← 系统详细说明
│   ├── 科研日报-skill.yaml          ← AI Skill 定义（核心自动化）
│   ├── 与科研认知的衔接.md           ← 日报→精读→认知转化链路
│   ├── 配置/
│   │   ├── 信息源.md               ← arXiv/IEEE/SCI 源配置
│   │   ├── 领域关键词.md            ← IC/EE/AI 关键词体系
│   │   ├── SAB分级标准.md           ← S/A/B 论文分级标准
│   │   └── 自动化配置.md            ← 定时任务配置
│   ├── 复盘/
│   │   └── README.md               ← 复盘体系
│   └── 科研论文/
│       └── 元数据笔记.md            ← 论文元数据示例
│
└── 科研认知/                        ← 配套认知系统
    ├── README.md                   ← 系统说明
    ├── 文献阅读体系.md              ← 百篇文献阅读方法论
    └── readings/                   ← 精读记录
```

### 核心原则

1. **输入即分析** — 输入任何文献信息，自动关联已有文献、定位创新点
2. **对比出创新** — 创新不是凭空想出来的，是比出来的
3. **从文献到写作的闭环** — 每篇输入必须走完：分析→认知→写作心法→可转化材料

### 覆盖领域

- **AI/ML**: cs.AI, cs.LG, cs.CV, cs.CL, stat.ML → NeurIPS, ICML, ICLR, AAAI
- **集成电路 IC**: IEEE JSSC, ISSCC, DAC, VLSI
- **电气工程 EE**: eess.SY, eess.SP → IEEE TPEL, TIE, ECCE
- **交叉学科**: Nature/Science 子刊

### S/A/B 分级系统

| 级别 | 标准 | 处理方式 |
|------|------|---------|
| **S 级** | 顶刊+重大突破+高度相关（≥3项） | 逐字精读 → 进入科研认知系统 |
| **A 级** | 满足至少2项条件 | 精读 abstract+introduction+结论 |
| **B 级** | 满足不到2项 | 一句话跳过 |

### 创新点发现：七维解剖 × 六类 Gap

**七维创新分析**：问题定义 / 方法设计 / 理论框架 / 实验验证 / 数据资源 / 应用场景 / 性能表现

**六类 Research Gap**：理论缺口 / 方法缺口 / 应用缺口 / 数据缺口 / 实证缺口 / 人口缺口

---

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).

## Contributing

Issues and pull requests are welcome. For major changes, please open an issue first.

## Author

Built by [Destined-at-Dawn](https://github.com/Destined-at-Dawn) with AI assistance.
