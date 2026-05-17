# Positioning

## What This Is

Research Daily is an **AI-powered research decision engine** for graduate students and early-career researchers in IC, EE, and AI fields. It runs as a Claude Code skill that integrates into your daily workflow.

It answers one question: **"What should I read today, and why?"**

Unlike paper aggregators that dump 50 abstracts on your desk, Research Daily applies a three-stage filtering pipeline (Collect -> Grade -> Decide) and outputs 3-5 papers with decision rationale, innovation analysis, and actionable next steps.

## What This Is Not

- **Not a paper search engine.** It doesn't crawl the entire arXiv. It curates.
- **Not an autopilot system.** It recommends, you decide. Every S/A/B grade comes with transparent reasoning you can audit and override.
- **Not a generic tool.** It's calibrated for IC/EE/AI domains with venue-specific knowledge (JSSC, ISSCC, DAC, TPEL, NeurIPS, ICML).
- **Not a writing ghost.** It extracts writing patterns from papers to teach you technique, not to write for you.

## Design Philosophy

### 1. Decide, Don't Dump

> "The bottleneck isn't access to papers — it's knowing which ones matter."

Research Daily's core value is **curation with reasoning**. Every paper recommendation includes:
- Why it was selected (which criteria triggered S/A/B grade)
- What makes it innovative (seven-dimension dissection)
- What to do next (read / compare / replicate / write about)

### 2. Comparison Reveals Innovation

> "Innovation isn't brainstormed — it's discovered through structured comparison."

The Innovation Gap Engine doesn't generate random "research ideas." It systematically compares your work / interests against existing literature across seven dimensions, identifies gaps, and classifies them into six types (Theory / Method / Application / Data / Empirical / Population).

### 3. Reading -> Writing Closed Loop

> "Every paper must produce at least one usable output."

Reading without extraction is wasted effort. Research Daily enforces a closed loop:
- Paper input -> Panoramic analysis -> Writing technique extraction -> Cognitive system integration
- You never leave a paper empty-handed.

### 4. Vertical Depth Over Horizontal Breadth

> "A tool that knows JSSC's review criteria beats one that indexes everything."

Research Daily doesn't try to cover all academic fields. It goes deep in IC/EE/AI, with:
- Venue-specific grading weights (a DAC paper gets different treatment than a workshop paper)
- Domain keyword systems tuned for circuit design, power electronics, and ML
- Cross-domain bridge detection (where IC meets AI, where EE meets physics)

## Target Users

| User | Pain Point | How Research Daily Helps |
|------|-----------|--------------------------|
| **M.S. student (IC/EE)** | "I don't know what to read" | Daily curated report with S/A/B grades |
| **Ph.D. student (AI)** | "I have an idea but don't know if it's novel" | Innovation Gap Engine with six-type framework |
| **Early-career researcher** | "I can read papers but can't write like them" | Writing Formula Library with pattern extraction |
| **Conference deadline approaching** | "Which venue should I target?" | Submission strategy with venue matching |

## Allowed Uses

- Personal research assistance (daily reading, literature review, innovation scouting)
- Teaching and methodology training (demonstrating systematic paper analysis)
- Non-commercial academic collaboration (research groups sharing workflows)

## Discouraged Uses

- Submitting AI-generated analysis as original research without verification
- Treating S/A/B grades as ground truth without reading the paper yourself
- Using the writing formulas as templates without understanding the underlying technique

## Roadmap Alignment

| Milestone | Status | Description |
|-----------|--------|-------------|
| v1.0 Daily Report | Done | Core S/A/B grading + daily report generation |
| v2.0 Research Workstation | Done | 5 workflows + innovation engine + writing library |
| v2.1 Automation | Done | CronCreate daily scheduling |
| v3.0 Plugin Ecosystem | In Progress | Claude Code marketplace integration + error handling |

---

*Research Daily: From paper discovery to research decision, in 5 minutes a day.*
