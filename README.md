# Claude SkillGen

> **34 production-ready Claude AI skills** — multi-agent orchestration, prompt engineering, RAG systems, Vedic natural farming (ZBNF), government scheme navigation, and startup strategy. Drop any `SKILL.md` into Claude to unlock domain-expert behavior instantly.

[![Skills](https://img.shields.io/badge/skills-34-blue)](https://github.com/vishwasoo7/Claude_SkillGen)
[![Categories](https://img.shields.io/badge/categories-5-green)](https://github.com/vishwasoo7/Claude_SkillGen)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## What is a Claude Skill?

A **Claude skill** is a structured `SKILL.md` instruction file that activates specialized, expert behavior in Claude for a specific domain. When Claude detects a relevant trigger phrase in your conversation, it reads the matching skill file and responds as a domain expert — not a generalist.

**Without a skill:** Claude gives a generic answer.  
**With a skill:** Claude runs a structured protocol, asks the right questions, uses domain-specific logic, and produces expert-grade output.

This repository collects, organizes, and maintains a growing library of skills across five functional categories — all battle-tested in real workflows.

---

## Quick Start

**Using claude.ai with computer use or Claude Code:**

```bash
# 1. Clone the repo
git clone https://github.com/vishwasoo7/Claude_SkillGen.git /mnt/skills/user

# 2. In your Claude system prompt, reference the skill directory:
#    "Skills are available at /mnt/skills/user/"

# 3. Tell Claude to read a skill before responding:
#    "Use the rag-engineer skill to help me build a vector search pipeline."
```

**Skills are self-activating** — include `using-superpowers` and `skill-router` and Claude will automatically detect and invoke the correct skill for every prompt.

---

## Repository Structure

```
Claude_SkillGen/
├── farming/              # Vedic natural farming, ZBNF, soil analysis, digital agriculture
├── ai-agents/            # Multi-agent orchestration, autonomous workflows, memory systems
├── skill-management/     # Building, testing, debugging, and syncing Claude skills
├── engineering/          # RAG systems, prompt engineering, code quality
└── startup-business/     # Startup strategy, financial modeling, market analysis
```

---

## Skills by Category

### Farming

Skills for natural and organic farming operations. Calibrated for **Indian soil lab reports**, **Gujarat climate**, **Subhash Palekar ZBNF** (Zero Budget Natural Farming), and the **AgStack Foundation** open-source digital agriculture stack.

| Skill | What It Does |
|-------|-------------|
| [`agstack-farming`](./farming/agstack-farming/) | AgStack Foundation digital agriculture advisor — ETo calculations, pest risk scoring, Gujarat crop calendars, APMC market intelligence, INATrace traceability, PGS-India certification logging |
| [`vedic-farming`](./farming/vedic-farming/) | Full Subhash Palekar ZBNF system — Jeevamrut, Beejamrut, Panchgavya, Agniastra, Dashaparni Ark, lunar planting calendar, chemical land detox protocol, crop-specific guides for groundnut, cumin, sesame, bajra, vegetables |
| [`soil-test-interpreter`](./farming/soil-test-interpreter/) | Reads Indian soil lab reports (GSFC, KVK formats) and generates organic amendment prescriptions per Vigha — pH correction, NPK, micronutrients, chemical detox retesting schedule |
| [`farm-journal`](./farming/farm-journal/) | Structured farm observation and activity logging — 7 entry types, soil recovery milestones, season-comparison review |
| [`water-irrigation-emergency`](./farming/water-irrigation-emergency/) | Borewell / motor / power failure emergency protocol — immediate action checklist, crop triage, water rationing, emergency sources, long-term solar pump upgrade path |
| [`pgs-india-roadmap`](./farming/pgs-india-roadmap/) | Step-by-step PGS-India certification roadmap from Day 1 (April 2026) to first Scope Certificate (March 2027) — peer group formation, KVK registration, NCOF portal, fillable inspection and declaration templates |
| [`seasonal-crop-rotation-planner`](./farming/seasonal-crop-rotation-planner/) | 5-year crop rotation plan for a chemical-transition farm — season-by-season tables, 10 crop profiles, intercropping combinations, Kharif-to-Rabi succession windows, soil recovery stage logic |
| [`gujarat-govt-schemes`](./farming/gujarat-govt-schemes/) | Gujarat government schemes navigator with live web-search verification — PM-KUSUM solar pump, PKVY organic cluster, Kisan Credit Card, Soil Health Card, ATMA, NHM/MIDH drip irrigation, i-Khedut portal guide |

**Keywords:** ZBNF, Subhash Palekar natural farming, Jeevamrut preparation, Indian soil test interpretation, organic farming Gujarat, AgStack open source, ETo calculation, PGS-India certification, crop rotation Keshod, government schemes farmer India, PM-KUSUM solar pump subsidy

---

### AI Agents

Skills for orchestrating **multi-agent workflows**, autonomous task execution, and meta-level AI system behavior.

| Skill | What It Does |
|-------|-------------|
| [`loki-mode`](./ai-agents/loki-mode/) | Fully autonomous multi-agent system — takes a PRD and builds a deployed product with minimal human intervention |
| [`dispatching-parallel-agents`](./ai-agents/dispatching-parallel-agents/) | Runs 2+ independent tasks simultaneously using parallel agent dispatch |
| [`parallel-agents`](./ai-agents/parallel-agents/) | Multi-agent orchestration patterns for tasks requiring different domain expertise in parallel |
| [`memory-systems`](./ai-agents/memory-systems/) | Architecture guide for short-term, long-term, and graph-based memory in AI agent systems |
| [`brainstorming`](./ai-agents/brainstorming/) | Structured ideation framework that explores intent and approach before implementation begins |
| [`skill-router`](./ai-agents/skill-router/) | Smart adaptive skill router — surfaces the most relevant installed skills for any given prompt |
| [`using-superpowers`](./ai-agents/using-superpowers/) | Meta-skill that ensures Claude always checks and invokes the correct skill before responding |

**Keywords:** Claude multi-agent system, AI agent orchestration, autonomous Claude workflow, parallel agent dispatch, Claude Code agents, LLM memory architecture, Claude system prompt patterns

---

### Skill Management

Skills for **creating, testing, debugging, and deploying** other Claude skills.

| Skill | What It Does |
|-------|-------------|
| [`master-skill-assist`](./skill-management/master-skill-assist/) | Master orchestrator for the full skill lifecycle — create, upgrade, clone, audit, repair |
| [`skill-developer`](./skill-management/skill-developer/) | Comprehensive guide for creating Claude Code skills — trigger patterns, hooks, parameter schemas, debugging |
| [`verification-before-completion`](./skill-management/verification-before-completion/) | Universal output verifier — requires evidence before any success claim, applies to every response type |
| [`github-connect`](./skill-management/github-connect/) | Platform-adaptive GitHub connector — push, sync, inspect, and update skills across all Claude environments |
| [`skill-seekers`](./skill-management/skill-seekers/) | Converts documentation websites, GitHub repos, and PDFs into Claude skills automatically |

**Keywords:** Claude skill development, SKILL.md format, Claude Code hooks, skill trigger patterns, Claude system prompt engineering, skill library management

---

### Engineering

Skills for **software engineering quality**, AI/ML systems, and production-grade prompt design.

| Skill | What It Does |
|-------|-------------|
| [`rag-engineer`](./engineering/rag-engineer/) | Builds RAG systems — embedding model selection, vector database architecture, chunking strategies, retrieval optimization |
| [`prompt-engineering-patterns`](./engineering/prompt-engineering-patterns/) | Advanced prompt patterns for LLM performance, reliability, and production-grade output control |
| [`prompt-engineer`](./engineering/prompt-engineer/) | Transforms raw prompts using RTF, RISEN, Chain of Thought, RODES, RACE, STAR, SOAP, CLEAR frameworks |
| [`kaizen`](./engineering/kaizen/) | Continuous improvement, error-proofing, and standardization practices for code quality |

**Keywords:** RAG system design, retrieval augmented generation, prompt engineering frameworks, Chain of Thought prompting, LLM system prompts, Claude prompt optimization, vector database, embedding strategy

---

### Startup and Business

Skills for **startup strategy, financial planning, competitive research, and investor-ready deliverables**.

| Skill | What It Does |
|-------|-------------|
| [`startup-analyst`](./startup-business/startup-analyst/) | Full-spectrum startup analysis — market sizing, financials, competitive positioning |
| [`startup-business-analyst-business-case`](./startup-business/startup-business-analyst-business-case/) | Generates investor-ready business case documents |
| [`startup-business-analyst-financial-projections`](./startup-business/startup-business-analyst-financial-projections/) | Builds 3–5 year financial models with revenue, costs, cash flow, and scenarios |
| [`startup-financial-modeling`](./startup-business/startup-financial-modeling/) | Forecasting, burn rate, runway, and cash flow modeling for early-stage startups |
| [`startup-metrics-framework`](./startup-business/startup-metrics-framework/) | SaaS metrics, CAC/LTV, unit economics, burn multiple, and Rule of 40 |
| [`team-composition-analysis`](./startup-business/team-composition-analysis/) | Org chart design, hiring roadmap, compensation benchmarks, equity allocation |
| [`competitive-landscape`](./startup-business/competitive-landscape/) | Competitor analysis, market positioning, Porter's Five Forces |
| [`market-sizing-analysis`](./startup-business/market-sizing-analysis/) | TAM, SAM, SOM calculation with structured market opportunity sizing |
| [`pricing-strategy`](./startup-business/pricing-strategy/) | Pricing, packaging, and monetization design based on customer value |
| [`sales-automator`](./startup-business/sales-automator/) | Cold email sequences, follow-up campaigns, proposal templates, outreach scripts |

**Keywords:** startup financial model, TAM SAM SOM calculation, investor business case, SaaS unit economics, competitive analysis framework, Claude business analyst

---

## Skill Count

| Category | Skills |
|----------|--------|
| farming | 8 |
| ai-agents | 7 |
| skill-management | 5 |
| engineering | 4 |
| startup-business | 10 |
| **Total** | **34** |

---

## How Skills Are Structured

Every skill follows this format:

```
skill-name/
└── SKILL.md        # The full instruction set Claude reads at runtime
```

A `SKILL.md` contains:
- **Trigger definition** — what phrases or task types activate this skill
- **Protocol** — step-by-step behavior Claude follows
- **Domain logic** — calibrated rules, formulas, or domain-specific knowledge
- **Output format** — how Claude structures its response

Skills are intentionally self-contained. Drop any single skill into a project and it works without dependencies — or combine them for compound workflows.

---

## Contributing

1. Fork the repository
2. Create your skill folder under the appropriate category
3. Add a `SKILL.md` following the existing format
4. Submit a pull request with a one-line description of the skill's trigger condition

All contributions must include a clear trigger definition. Skills without triggers will not be merged.

---

## Related Resources

- [Anthropic Claude Documentation](https://docs.anthropic.com)
- [Claude Code](https://claude.ai/code) — primary environment for skill deployment
- [AgStack Foundation](https://agstack.org) — open-source digital agriculture framework
- [Subhash Palekar Natural Farming](https://spnf.org) — ZBNF methodology behind the vedic-farming skill

---

## License

MIT License. Use, modify, and distribute freely. Attribution appreciated but not required.

---

*Built and maintained using Claude AI with the `github-connect` and `master-skill-assist` skills from this repository.*
