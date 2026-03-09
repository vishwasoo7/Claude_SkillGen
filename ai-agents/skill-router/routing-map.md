# Routing Map — Installed Skill Index
## Generated: 2026-03-09 | Skills Indexed: 39 | Environment: claude.ai
## To regenerate: say "update the router" or "I added a new skill"

---

## HOW TO USE THIS FILE

This file is the router's long-term memory. It is the curated, human-readable index
of every skill currently installed — grouped by domain, with trigger phrases and
pairing logic. The router reads this when filesystem scanning is unavailable or slow.

**This file goes stale when skills are added or removed.**
Regenerate it using the self-update protocol in SKILL.md any time the library changes.

---

## DOMAIN: Farming & Agriculture 🌾

Skills for natural farming, soil analysis, crop planning, digital agriculture tools.

---

**`agstack-farming`** — Open-source digital agriculture advisor (AgStack Foundation / OpenAgri ecosystem)
- Triggers on: farm planning, irrigation scheduling, ETo calculation, pest risk, crop calendar, field registration, carbon credits, supply chain traceability, AgStack tools, OpenAgri, INATrace, APMC selling, PGS certification logging
- Pairs with: `vedic-farming` for organic practice logging | `soil-test-interpreter` when soil data is available | `docx` to produce farm reports
- 300 lines | References: 10 files (field registry, weather, irrigation, farm calendar, pest, supply chain, carbon, AI platform, deployment, APMC-PGS)

**`vedic-farming`** — Subhash Palekar ZBNF system, Rishi Krishi practices, Saurashtra/Gujarat calibrated
- Triggers on: Jeevamrut, Beejamrut, Panchgavya, Ghanjeevamrut, Neemastra, Agniastra, Brahmastra, Dashaparni Ark, natural farming, ZBNF, lunar calendar, Tithi, Nakshatra, cow dung, neem, organic pest spray, green manure, mulching, vermicompost
- Pairs with: `soil-test-interpreter` when soil numbers available | `agstack-farming` for logging practices | `farm-journal` for observation records
- 117 lines | References: 7 files (liquid preparations, pest remedies, lunar calendar, soil amendments, agstack integration, chemical land detox, crop-specific guides)
- STATUS: Installed at `/mnt/skills/user/vedic-farming/`

**`soil-test-interpreter`** — Indian lab report → organic amendment prescription per Vigha
- Triggers on: soil test, soil report, pH reading, OC percentage, organic carbon, NPK values, available nitrogen, phosphorus, potassium, EC value, zinc deficiency, boron deficiency, GSFC lab, KVK lab, soil health card, micronutrient deficiency, upload lab report PDF or image, chemical detox
- Pairs with: `vedic-farming` for applying prescribed inputs | `agstack-farming` for logging corrections | `docx` for formal prescription document
- 208 lines | References: 6 files (parameter ranges, macronutrient corrections, micronutrient corrections, pH/EC corrections, lab report reading, chemical detox retesting)
- STATUS: Installed at `/mnt/skills/user/soil-test-interpreter/`

**`farm-journal`** — Structured farm observation and activity logging, Rangpur village / Keshod / Junagadh
- Triggers on: journal entry, farm log, log today, record observation, farm diary, weekly farm notes, soil check, earthworm count, crop appearance, irrigation note, Jeevamrut batch, pest found, harvest recorded, season summary, detox progress, soil recovery check
- Pairs with: `vedic-farming` for preparation logs | `agstack-farming` for Farm Calendar sync | `pgs-india-roadmap` for certification evidence | `soil-test-interpreter` for test comparison
- 381 lines | Single file (7 entry templates: soil observation, preparation log, crop observation, irrigation, pest event, harvest, seasonal summary)

**`water-irrigation-emergency`** — Borewell / motor / power failure emergency protocol, Keshod farm
- Triggers on: borewell failed, motor stopped, no water, power cut, pump not working, bore well problem, crops wilting, water shortage, irrigation stopped, emergency irrigation, which crop survives without water, water crisis, water rationing
- Pairs with: `seasonal-crop-rotation-planner` for crop triage | `farm-journal` to log the event | `gujarat-govt-schemes` for solar pump upgrade path
- 200 lines | References: 1 file (crop water tolerance with triage priority, survival windows, emergency sources)

**`pgs-india-roadmap`** — PGS-India certification step-by-step from April 2026 to first certificate March 2027
- Triggers on: PGS certification, organic certificate India, peer group, peer inspection, KVK certification, NCOF portal, how to prove my farm is organic, PGS renewal, log for PGS, what documents for organic certification
- Pairs with: `agstack-farming` for Farm Calendar log formats | `farm-journal` for observation records as evidence | `gujarat-govt-schemes` for PKVY cluster which PGS unlocks
- 122 lines | References: 2 files (month-by-month roadmap with phase checklists, peer inspection forms and renewal)

**`seasonal-crop-rotation-planner`** — 5-year crop rotation plan, Kharif 2026 to Rabi 2030-31
- Triggers on: what to plant, crop rotation, what crop next season, Kharif planning, Rabi planning, intercropping, soil restoration crop, nitrogen fixing crop, 5 year plan, what after Kali Jeeri, chemical detox rotation, crop combination, succession planting
- Pairs with: `agstack-farming` for APMC prices | `water-irrigation-emergency` for drought tolerance | `soil-test-interpreter` for amendment prescriptions | `vedic-farming` for ZBNF inputs per crop
- 156 lines | References: 2 files (5-year rotation tables, 10 crop profiles + 7 intercropping combos)

**`gujarat-govt-schemes`** — Government schemes navigator with live web-search verification before every response
- Triggers on: government scheme, subsidy, PM-KUSUM, solar pump subsidy, PKVY, organic farming scheme, Kisan Credit Card, soil health card, ATMA scheme, NHM, i-Khedut, apply for subsidy, what schemes am I eligible for, new farming scheme Gujarat
- Pairs with: `pgs-india-roadmap` (PGS cert required for several schemes) | `water-irrigation-emergency` (solar pump upgrade path) | `farm-journal` + `vedic-farming` (PKVY documentation)
- 148 lines | References: 2 files (7 scheme profiles with live queries + change indicators, i-Khedut portal guide)

---

## DOMAIN: Business & Finance 💼

Skills for startup analysis, financial modeling, market research, competitive strategy, team planning.

---

**`startup-analyst`** — Expert startup business analyst: market sizing, financial modeling, competitive analysis, strategic planning
- Triggers on: business analysis, startup strategy, investor presentation, market research, unit economics, go-to-market, business model
- Pairs with: `startup-financial-modeling` for numbers | `competitive-landscape` for market position | `startup-business-analyst-business-case` for full document output
- 324 lines

**`startup-financial-modeling`** — 3–5 year financial models: revenue projections, cost structure, cash flow, scenarios
- Triggers on: financial projections, financial model, forecast revenue, burn rate, runway, cash flow, 3-year model, 5-year model
- Pairs with: `startup-analyst` for strategic framing | `xlsx` to produce a spreadsheet output
- 494 lines

**`startup-business-analyst-business-case`** — Investor-ready business case document
- Triggers on: business case, investor document, pitch document, business plan, market + solution + financials + strategy
- Pairs with: `startup-financial-modeling` for financial section | `docx` for Word output | `pptx` for presentation output
- 492 lines

**`startup-business-analyst-financial-projections`** — Detailed 3–5 year financial projections with scenarios
- Triggers on: financial projections, revenue model, cost model, scenario planning, P&L forecast
- Pairs with: `startup-financial-modeling` | `xlsx` for spreadsheet
- 358 lines

**`competitive-landscape`** — Competitive analysis, Porter's Five Forces, market positioning, differentiation
- Triggers on: analyze competitors, competitive landscape, market positioning, differentiation, Porter's Five Forces, competitive strategy
- Pairs with: `market-sizing-analysis` | `startup-analyst`
- 527 lines

**`market-sizing-analysis`** — TAM/SAM/SOM calculations, market opportunity sizing
- Triggers on: TAM, SAM, SOM, total addressable market, market sizing, market opportunity, size the market
- Pairs with: `competitive-landscape` | `startup-analyst`
- 451 lines

**`startup-metrics-framework`** — Key startup metrics: SaaS metrics, unit economics, CAC, LTV, burn multiple, Rule of 40
- Triggers on: startup metrics, SaaS metrics, CAC, LTV, unit economics, burn multiple, rule of 40, marketplace metrics, KPIs
- Pairs with: `startup-financial-modeling` | `startup-analyst`
- 564 lines ⚠️ Over 500-line limit

**`team-composition-analysis`** — Team structure, hiring plan, org chart, compensation, equity allocation
- Triggers on: team structure, hiring plan, org chart, headcount, compensation, equity, team design
- Pairs with: `startup-analyst` | `startup-financial-modeling`
- 437 lines

**`pricing-strategy`** — Pricing, packaging, monetization strategy based on value and willingness to pay
- Triggers on: pricing strategy, pricing model, packaging, monetization, willingness to pay, price point
- Pairs with: `startup-analyst` | `market-sizing-analysis`
- 362 lines

**`sales-automator`** — Cold emails, follow-ups, proposal templates, pricing pages, case studies, sales scripts
- Triggers on: cold email, sales outreach, follow-up email, proposal, sales script, lead nurturing, pitch email
- Pairs with: `startup-analyst` for context | `docx` for document output
- 60 lines

---

## DOMAIN: Skill Building & Process 🛠️

Skills for creating skills, improving workflows, planning, and verification.

---

**`brainstorming`** — Turns vague ideas into clear designs through structured dialogue. MUST run before any creative or implementation work.
- Triggers on: I have an idea, help me think through, not sure what to build, rough concept, design before building, explore options, which approach
- Pairs with: any implementation skill (always upstream) | `skill-developer` for skill creation | `verification-before-completion` after
- 96 lines

**`skill-developer`** — Create and manage skills following Anthropic best practices: YAML, 500-line rule, progressive disclosure, triggers
- Triggers on: create a skill, add a skill, modify skill triggers, skill rules, YAML frontmatter, 500-line rule, skill activation, hook system
- Pairs with: `brainstorming` (run first) | `skill-creator` | `verification-before-completion`
- 429 lines

**`skill-seekers`** — Convert documentation websites, GitHub repos, and PDFs into Claude skills
- Triggers on: convert documentation to skill, make a skill from this repo, GitHub to skill, PDF to skill, documentation skill
- Pairs with: `skill-developer` for refinement | `brainstorming` for scoping
- 23 lines

**`kaizen`** — Continuous improvement, error-proofing, standardization. Code quality and process improvements.
- Triggers on: improve code quality, refactor, process improvement, continuous improvement, error proofing, standardize
- Pairs with: `verification-before-completion` | `brainstorming`
- 733 lines ⚠️ Over 500-line limit — needs trimming

**`verification-before-completion`** — Requires running verification commands before any completion claim. Evidence before assertions.
- Triggers on: claiming work is done, saying tests pass, about to commit, about to complete a task, done with implementation
- Pairs with: every implementation skill — always runs last
- 139 lines

**`using-superpowers`** — Establishes how to find and use skills. Instructs skill invocation before any response.
- Triggers on: starting any conversation, how do I use skills, skill activation rules
- Pairs with: `skill-router` (complementary) | any skill
- 95 lines

**`skill-router`** — This skill. Adaptive routing across all installed skills.
- Triggers on: which skill, where to start, help me find, not sure which, I'm lost, recommend a skill
- 207 lines (new version)

---

## DOMAIN: Documents & Files 📄

Skills for creating and working with Word, PDF, Excel, and PowerPoint files.

---

**`docx`** — Create, read, edit Word documents (.docx). Reports, memos, letters, templates.
- Triggers on: Word document, .docx, report, memo, letter, template, create a document, formal write-up
- Pairs with: any domain skill to package its output as a formal document
- Public skill

**`pdf`** — Everything with PDF files: create, read, extract, merge, split, watermark, OCR, fill forms.
- Triggers on: PDF, .pdf, extract from PDF, combine PDFs, fill PDF form, OCR, scan to text
- Pairs with: `docx` for conversion workflows | any content-creation skill
- Public skill

**`pptx`** — Create, edit, parse .pptx presentations, slide decks, pitch decks.
- Triggers on: presentation, slides, deck, .pptx, PowerPoint, pitch deck, slide show
- Pairs with: `startup-business-analyst-business-case` for investor decks | `agstack-farming` for farm reports
- Public skill

**`xlsx`** — Create, read, edit spreadsheets (.xlsx, .xlsm, .csv, .tsv). Formulas, charts, cleaning data.
- Triggers on: spreadsheet, Excel, .xlsx, .csv, table, formula, chart, data cleaning, financial model output
- Pairs with: `startup-financial-modeling` | `startup-business-analyst-financial-projections`
- Public skill

---

## DOMAIN: AI / LLM / Agents 🤖

Skills for building RAG systems, prompt optimization, memory architectures, multi-agent systems.

---

**`rag-engineer`** — RAG systems: embeddings, vector databases, chunking, retrieval optimization
- Triggers on: RAG, retrieval augmented generation, vector database, embeddings, chunking, semantic search, retrieval pipeline
- Pairs with: `prompt-engineer` | `memory-systems`
- 95 lines

**`prompt-engineer`** — Transforms prompts using RTF, RISEN, Chain of Thought, RODES, RACE, RISE, STAR frameworks
- Triggers on: optimize my prompt, improve this prompt, prompting frameworks, better prompt, make this prompt work, prompt for AI task
- Pairs with: `prompt-engineering-patterns` for deeper theory | `rag-engineer`
- 249 lines

**`prompt-engineering-patterns`** — Advanced prompt engineering: few-shot learning, CoT, template systems, system prompt design
- Triggers on: few-shot learning, chain of thought, prompt template, system prompt design, prompt optimization, production prompts
- Pairs with: `prompt-engineer` | `rag-engineer`
- 216 lines

**`memory-systems`** — Short-term, long-term, graph-based memory architectures for agents
- Triggers on: agent memory, persist across sessions, knowledge graph, temporal memory, vector store memory, memory architecture
- Pairs with: `rag-engineer` | `parallel-agents`
- 229 lines

**`parallel-agents`** — Multi-agent orchestration patterns for independent parallel tasks
- Triggers on: multi-agent, parallel tasks, orchestration, agent coordination, run simultaneously, multiple agents
- Pairs with: `dispatching-parallel-agents` for execution | `memory-systems` for shared state
- 177 lines

**`dispatching-parallel-agents`** — Execute 2+ independent tasks in parallel when no shared state needed
- Triggers on: run in parallel, do these at the same time, independent tasks, parallel execution, dispatch agents
- Pairs with: `parallel-agents` for architecture | `loki-mode` for full autonomy
- 180 lines

**`loki-mode`** — Fully autonomous multi-agent startup system. PRD → deployed product with minimal intervention.
- Triggers on: "Loki Mode", fully autonomous, take over, just do it all, hands-off execution, autonomous agent
- Pairs with: `brainstorming` (run first to define PRD) | `verification-before-completion` at end
- 280 lines | Requires specific permission flags in CLI environments

---

## DOMAIN: Design & Visual 🎨

---

**`frontend-design`** — Production-grade frontend interfaces, web components, landing pages, dashboards
- Triggers on: design a UI, build a component, landing page, dashboard, web interface, frontend, React component, HTML layout, style this
- Pairs with: `brainstorming` for spec | `pptx` if output is a presentation
- Public skill

---

## DOMAIN: Platform & Meta ⚙️

Skills about how Claude works, product knowledge, self-knowledge.

---

**`product-self-knowledge`** — Accurate facts about Anthropic products: Claude Code, Claude API, claude.ai plans, features
- Triggers on: how does Claude Code work, API pricing, claude.ai Pro vs Team, how to install, what model, what features
- Public skill

---

## SKILLS NOT RECOMMENDED FOR THIS CONTEXT 🚫

These skills are installed but serve use cases not applicable here:

| Skill | Reason not recommended |
|-------|----------------------|
| `care-coordination-model` | Healthcare coordination — not applicable |
| `risk-manager` | Financial portfolio risk (stocks) — not applicable |
| `risk-metrics-calculation` | Portfolio VaR/CVaR — not applicable |
| `vp-real-estate` | Commercial real estate — not applicable |

---

## QUICK COMBO CHAINS

Most common multi-skill workflows for this installation:

**Soil test → Prescription → Action:**
`soil-test-interpreter` → `vedic-farming` → `agstack-farming` (log it)

**Crop planning → Rotation → ZBNF inputs:**
`seasonal-crop-rotation-planner` → `vedic-farming` → `farm-journal` (log it)

**Water emergency → Crop triage → Recovery:**
`water-irrigation-emergency` → `seasonal-crop-rotation-planner` → `farm-journal`

**Government scheme → Certification → Premium market:**
`gujarat-govt-schemes` → `pgs-india-roadmap` → `agstack-farming` (ref10 APMC)

**New farm idea → Plan → Document:**
`brainstorming` → `agstack-farming` or `vedic-farming` → `docx`

**New skill creation:**
`brainstorming` → `skill-developer` → `verification-before-completion`

**Business case → Financials → Presentation:**
`startup-business-analyst-business-case` → `startup-financial-modeling` → `pptx`

**Improve a prompt → Build a RAG system:**
`prompt-engineer` → `rag-engineer` → `memory-systems`

**Complex parallel work:**
`brainstorming` → `dispatching-parallel-agents` → `verification-before-completion`

---

## REGENERATION LOG

| Date | Skills Added | Skills Removed | Notes |
|------|-------------|----------------|-------|
| 2026-03-06 | vedic-farming, soil-test-interpreter | (initial build) | First generation of smart router |
| 2026-03-09 | water-irrigation-emergency, pgs-india-roadmap, seasonal-crop-rotation-planner, gujarat-govt-schemes, farm-journal (installed) | (none) | Session 3: 5 new farming skills added; soil-test-interpreter upgraded to 208 lines + ref06; agstack-farming upgraded to 300 lines + ref10; status warnings cleared |
