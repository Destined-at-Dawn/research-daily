# Changelog

All notable changes to Research Daily will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

- Plugin Marketplace integration (`.claude-plugin/` structure)
- Error handling & state management layer
- POSITIONING.md design philosophy document
- SECURITY.md vulnerability reporting policy

---

## [2.2] - 2026-05-30 — Research Data Expansion

### Added
- **10 daily research reports** (May 11-22, 2026): UAV powerline inspection field, covering YOLO detection, 3DGS reconstruction, DRL path planning, multi-agent systems, LLM-assisted inspection, edge deployment
- **109 paper metadata notes** in : structured metadata for 144 unique papers extracted from daily reports
  - S-level (must-read): 35 papers
  - A-level (important): 65 papers
  - B-level (reference): 44 papers
- New  directory for daily report outputs

### Coverage
- Domains: cs.CV, cs.RO, cs.AI, eess.SP
- Sources: arXiv, IEEE, Springer, MDPI, Nature, Sensors
- Time span: 2025-11 to 2026-05
- All personal references sanitized for public repository

---

## [2.1] - 2026-04-25 — Automation & Onboarding

### Added
- **B0 Automated Scheduling**: Users can opt into daily auto-generation via CronCreate during onboarding. No manual trigger needed.
- **Onboarding flow**: 4-step guided setup (Field Positioning -> Paper Baseline -> Reading Mode -> Innovation Focus) runs on first use, persists to `配置/领域关键词.md`.

### Changed
- Skill description updated to reflect "research workstation" positioning instead of "daily report generator".

### Design Decisions
- Automation is opt-in, not default. Users who prefer manual control are never forced into cron tasks.
- Onboarding writes to a persistent config file so the skill doesn't repeat questions across sessions.

---

## [2.0] - 2026-04-25 — Research Workstation (Major Rewrite)

> **Architectural shift**: from "daily report generator" to "full-lifecycle research workstation". This is the most significant release in the project's history.

### Added
- **Workflow A: Paper Input -> Panoramic Analysis** — Accepts title/DOI/PDF/arXiv ID/notes. Auto-searches arXiv + local reading records. Outputs a structured "Panoramic Card" with innovation dissection, S/A/B grading, and action items.
- **Workflow C: Innovation Gap Engine** — Seven-dimension innovation anatomy (Problem / Method / Theory / Experiment / Data / Application / Performance) cross-referenced with six Research Gap types (Theory / Method / Application / Data / Empirical / Population). Supports single-paper analysis, multi-paper comparison, and gap recommendation.
- **Workflow D: Academic Writing Formula Library** — Extracts reusable writing patterns from high-quality papers. Covers Abstract, Introduction, Method, Results, Discussion sections. Injects "Cognitive Book" writing principles.
- **Workflow E: Research Guidance** — Stage-aware guidance (topic selection / experiment stuck / writing difficulty / paper rejected / preparing defense). Includes peer review simulation with structured scoring rubric. Submission strategy with venue matching.
- **Comparison Matrix**: Differential matrix for multi-paper comparison. Trend identification across papers. Cross-domain observation.
- **Cognitive Book Integration**: Writing guidance automatically references principles from the "100 Cognitive Books" collection.
- **Archive System**: Structured output naming convention (`{YYYYMMDD}_{type}_{topic}_v{version}.md`). Cross-system pipeline (outputs flow to reading system, newsletter, cognitive book).

### Changed
- **Workflow B (Daily Report)**: Preserved v1.0 capabilities intact. Now one of five workflows instead of the only workflow.
- **S/A/B Grading**: Now supports user-profile weighting from onboarding data.
- **Innovation Analysis**: Upgraded from ad-hoc to systematic seven-dimension framework.

### Design Philosophy
- **"Input = Analysis"**: Any paper input triggers immediate panoramic analysis, not just passive storage.
- **"Comparison reveals innovation"**: Innovation is discovered through structured comparison, not brainstorming.
- **"Reading -> Writing closed loop"**: Every paper must produce at least one usable output (technique, writing pattern, research direction).

---

## [1.1] - 2026-04-25 — Onboarding & Personalization

### Added
- **4-step onboarding wizard**: Field positioning, paper baseline (user submits 1-3 "impressive papers"), reading mode preference, innovation focus area.
- **User Profile persistence**: Onboarding answers stored in `配置/领域关键词.md` under "User Profile" section. All subsequent workflows reference this profile for personalized grading and recommendations.
- **Profile update trigger**: User can say "update my profile" or "my direction changed" to re-run onboarding.

### Design Decisions
- Profile is stored alongside domain keywords (not in a separate file) because the profile's primary purpose is to weight keyword relevance.
- Onboarding is mandatory on first use but skippable thereafter. This respects returning users while ensuring new users get calibrated.

---

## [1.0] - 2026-04-25 — Initial Release

### Added
- **Daily Research Report generation**: Automated paper discovery from arXiv, IEEE Xplore, SCI sources.
- **S/A/B Paper Grading**: Three-tier classification with decision rationale:
  - **S-tier**: Top venue + major breakthrough + high relevance (>=3 criteria) -> Full reading
  - **A-tier**: Meets >=2 criteria -> Read abstract + introduction + conclusion
  - **B-tier**: Meets <2 criteria -> One-sentence skip
- **Report Modules**:
  - Today's Breakthrough (1-2 items)
  - Frontier Papers (3-5 S/A-tier items with grading rationale)
  - Technical Insights (cross-paper connections, trends)
  - Tools & Code (reproducible resources)
  - Tomorrow's Watch (deadlines, conferences, events)
  - Study Notes (extractable learning points)
- **Domain Coverage**:
  - AI/ML: cs.AI, cs.LG, cs.CV, cs.CL, stat.ML
  - Integrated Circuits: IEEE Xplore (JSSC, ISSCC, DAC, VLSI)
  - Electrical Engineering: eess.SY, eess.SP (TPEL, TIE, ECCE)
  - Interdisciplinary: physics, math.OC
- **Configuration System**:
  - `配置/信息源.md` — Source configuration (arXiv, IEEE, SCI endpoints)
  - `配置/领域关键词.md` — Domain keyword system (IC/EE/AI)
  - `配置/SAB分级标准.md` — S/A/B grading criteria
  - `配置/自动化配置.md` — Automation settings
- **Research Cognition Bridge**: `与科研认知的衔接.md` defines how S-tier papers flow into the deep reading system.

### Design Decisions
- **"Decide what to read, not just find more"**: Every other tool shows 50 papers; Research Daily tells you which 3 to read.
- **Decision rationale is mandatory**: Every S/A/B grade includes the reasoning. Users can audit and override.
- **IC/EE/AI vertical focus**: Not a generic paper aggregator. Domain-specific keyword weighting, venue knowledge, and grading criteria.

---

## Version History Summary

| Version | Date | Theme | Key Metric |
|---------|------|-------|------------|
| 1.0 | 2026-04-25 | Daily Report | 1 workflow, S/A/B grading |
| 1.1 | 2026-04-25 | Personalization | 4-step onboarding, user profiles |
| 2.0 | 2026-04-25 | Research Workstation | 5 workflows, 7-dim analysis, writing library |
| 2.1 | 2026-04-25 | Automation | CronCreate daily scheduling |
| Unreleased | — | Plugin Ecosystem | Marketplace integration, error handling |
