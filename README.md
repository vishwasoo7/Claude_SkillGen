# Claude SkillGen

A curated library of Claude AI skills, organized by category and version-controlled for easy deployment. Each skill is a standalone instruction set that activates Claude's specialized behavior for a specific domain or task type.

---

## About This Repository

Claude skills are structured prompt files (SKILL.md) that tell Claude how to behave when a particular type of task is detected. This repository collects, organizes, and maintains a growing set of skills across five functional categories.

All skills in this repository have been reviewed for completeness and are considered production-ready. Skills that are incomplete or too thin for reliable use are tracked separately under the Pending section below.

---

## Repository Structure

```
Claude_SkillGen/
├── farming/              # Natural farming, soil analysis, digital agriculture
├── ai-agents/            # Multi-agent orchestration and autonomous workflows
├── skill-management/     # Building, testing, and managing Claude skills
├── engineering/          # Code quality, RAG systems, prompt engineering
└── startup-business/     # Startup strategy, financial modeling, market analysis
```

---

## Categories

### Farming
Skills built for natural and organic farming operations, calibrated for Gujarat soil and climate conditions.
See [farming/README.md](./farming/README.md)

| Skill | Description |
|-------|-------------|
| agstack-farming | AgStack Foundation digital agriculture advisor with ETo calculations, pest risk scoring, and Gujarat-specific crop calendars |
| vedic-farming | Subhash Palekar ZBNF advisor covering Jeevamrut, Beejamrut, Panchgavya, lunar calendar planting, and organic pest preparations |
| soil-test-interpreter | Reads Indian soil lab reports and generates organic amendment prescriptions per Vigha |

---

### AI Agents
Skills for orchestrating multi-agent workflows, autonomous task execution, and meta-level AI behavior.
See [ai-agents/README.md](./ai-agents/README.md)

| Skill | Description |
|-------|-------------|
| brainstorming | Structured ideation framework to explore intent and design before implementation begins |
| dispatching-parallel-agents | Runs two or more independent tasks simultaneously to reduce time-to-completion |
| parallel-agents | Multi-agent orchestration patterns for tasks requiring different domain expertise in parallel |
| memory-systems | Architecture guide for short-term, long-term, and graph-based memory in AI systems |
| loki-mode | Fully autonomous multi-agent system that takes a PRD and builds a deployed product |
| using-superpowers | Meta-skill that ensures Claude always checks and invokes relevant skills before responding |
| skill-router | Surfaces the most relevant installed skills for any given prompt or task |

---

### Skill Management
Skills for creating, testing, debugging, and maintaining other Claude skills.
See [skill-management/README.md](./skill-management/README.md)

| Skill | Description |
|-------|-------------|
| skill-developer | Comprehensive guide for creating Claude Code skills, trigger patterns, hooks, and debugging workflows |
| verification-before-completion | Enforces evidence-based task completion by requiring verification before any success claim |

---

### Engineering
Skills for software quality, AI/ML engineering, and prompt design.
See [engineering/README.md](./engineering/README.md)

| Skill | Description |
|-------|-------------|
| kaizen | Continuous improvement, error-proofing, and standardization practices for code quality |
| rag-engineer | Builds Retrieval-Augmented Generation systems covering embeddings, vector databases, and chunking |
| prompt-engineer | Transforms raw prompts using structured frameworks including RTF, RISEN, CoT, RODES, RACE, and STAR |
| prompt-engineering-patterns | Advanced prompt patterns for LLM performance, reliability, and production-grade control |

---

### Startup and Business
Skills for startup strategy, financial planning, market research, and competitive analysis.
See [startup-business/README.md](./startup-business/README.md)

| Skill | Description |
|-------|-------------|
| startup-analyst | Full-spectrum startup analysis covering market sizing, financials, and competitive positioning |
| startup-business-analyst-business-case | Generates investor-ready business case documents with market, solution, and financial sections |
| startup-business-analyst-financial-projections | Builds detailed 3 to 5 year financial models with revenue, costs, cash flow, and scenarios |
| startup-financial-modeling | Forecasting, burn rate, runway estimation, and cash flow modeling for early-stage startups |
| startup-metrics-framework | SaaS metrics, CAC/LTV, unit economics, burn multiple, and Rule of 40 tracking |
| team-composition-analysis | Org chart design, hiring roadmap, compensation benchmarks, and equity allocation planning |
| competitive-landscape | Competitor analysis, market positioning, differentiation strategy, and Porter's Five Forces |
| market-sizing-analysis | TAM, SAM, and SOM calculation with structured market opportunity sizing methodology |
| pricing-strategy | Pricing, packaging, and monetization design based on customer value and growth objectives |

---

## Skill Counts

| Category | Skills |
|----------|--------|
| farming | 3 |
| ai-agents | 7 |
| skill-management | 2 |
| engineering | 4 |
| startup-business | 9 |
| **Total** | **25** |

---

## Pending Skills

The following skills exist but have not been added to this repository. They are considered incomplete and need further development before they meet the quality bar for inclusion.

| Skill | Reason Excluded |
|-------|-----------------|
| skill-seekers | Only 23 lines. Lacks sufficient instruction depth for reliable activation. |
| sales-automator | Only 60 lines. Too thin to handle the range of sales tasks it claims to cover. |

---

## How to Install a Skill

1. Browse to the category folder containing the skill you want.
2. Copy the skill folder (for example, `vedic-farming/`) to `/mnt/skills/user/` in your Claude environment.
3. The skill will activate automatically based on its trigger description when a matching task is detected.

---

## Maintainer

VP, Keshod, Gujarat, India.
Farm project: Rangpur village, Keshod Taluka, Junagadh district.
