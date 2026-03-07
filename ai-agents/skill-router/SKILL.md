---
name: skill-router
description: >
  Smart adaptive skill router: triggers on ANY user prompt to surface the most relevant
  installed skills. Use this skill when the user asks which skill to use, says "I don't
  know where to start", "what should I use for this", "help me find the right skill",
  "not sure how to approach this", "recommend a skill", "I'm lost", "guide me", or any
  variation of seeking direction. Also activates proactively on ANY task prompt to
  identify and announce relevant skills the user may not have thought to invoke. Works
  in any environment: claude.ai, Claude Code, Antigravity, or any platform where
  skills are installed. Adapts automatically to whatever skills are present.
---

# Skill Router: Adaptive Intelligence Layer

The router operates in **two modes**, automatically selecting the right one:

- **Assist Mode**: triggered by any task prompt. Scans installed skills, surfaces relevant ones the user may not have thought to invoke, then proceeds with the task.
- **Interview Mode**: triggered when user is lost or explicitly asking for skill guidance. Runs a structured discovery conversation to identify the best skill match.

The router never recommends skills it cannot confirm are installed. It scans the actual filesystem every time.

---

## ENVIRONMENT DETECTION

Before routing, identify your environment and available tools:

**Step 1: Detect platform:**
Observe what tools are available in the current session:
- If `bash_tool` / `view` / `create_file` are available → file-based environment (claude.ai with computer use, or Claude Code)
- If only conversation tools are available → chat-only environment
- If `@skill-name` invocation syntax is used by user → likely Claude Code or Antigravity
- Default assumption if unclear: **chat-based, no file tools**

**Step 2: Detect skill storage path:**
Try paths in this order until one resolves:
1. `/mnt/skills/user/` (claude.ai standard)
2. `.claude/skills/` (Claude Code standard)
3. `~/skills/` (Antigravity / custom)
4. Any path the user specifies

**Step 3: Adapt recommendations:**
- In file-based environments: scan SKILL.md files directly for ground-truth
- In chat-only environments: use `references/routing-map.md` as the skill index
- Always state which source you are routing from: "Based on your installed skills..."

---

## MODE 1: ASSIST MODE (Proactive, Any Prompt)

When a user sends ANY task prompt, run this lightweight check before responding:

### Assist Mode Protocol
1. Read the user's prompt: identify the core intent in 3–5 keywords
2. Scan installed skills (filesystem or routing-map) for matches to those keywords
3. If 1 or more relevant skills found:
   - Briefly announce them at the top of your response
   - Proceed with the task using those skills
4. If no skills match: proceed normally without interrupting flow

### Assist Mode Announcement Format
```
💡 Relevant skills detected: `skill-name` [+ `skill-name-2` if applicable]
Reading and applying...
---
[then proceed with the actual task response]
```

**Do not announce if:**
- The match is weak or tangential (< 50% confidence)
- The user already explicitly invoked a skill in their prompt
- The task is pure conversation with no actionable domain

---

## MODE 2: INTERVIEW MODE (User Needs Direction)

Triggered when user is lost, confused, or explicitly asking for skill guidance.

### Step 1: Open the interview

Respond warmly. Do NOT suggest skills yet.

> "No problem: let me scan what's installed and ask a couple of questions to find the right fit."

### Step 2: Discover installed domains

Scan the skill library. Group installed skills into domains. Build Q1 options **dynamically from what actually exists**: not from a fixed list.

**Domain detection logic:**

| If these skills are installed... | → Show this Q1 option |
|----------------------------------|----------------------|
| `agstack-farming`, `vedic-farming`, `soil-test-interpreter` | Farming / Agriculture |
| `startup-analyst`, `startup-financial-modeling`, `competitive-landscape`, etc. | Business / Finance / Strategy |
| `docx`, `pdf`, `pptx`, `xlsx` | Documents & Files |
| `brainstorming`, `skill-developer`, `verification-before-completion`, `kaizen` | Skill Building / Process |
| `rag-engineer`, `prompt-engineer`, `memory-systems`, `loki-mode` | AI / LLM / Agents |
| `frontend-design` | Design & Visual |
| `loki-mode`, `dispatching-parallel-agents`, `parallel-agents` | Autonomous Execution |
| Any other installed domain | [Label it appropriately] |

Present only domains that have at least 1 confirmed installed skill.

### Step 3: Funnel questions (ask one at a time, skip if already clear)

**Q1: What broad area does your task fall into?**
[Present the dynamically built domain list from Step 2]

**Q2: How defined is your task?**
1. Clear goal: I know what I want, just need the right skill
2. Rough idea: I have a direction but need help shaping it
3. Starting from scratch: completely open

**Q3: Are there constraints?** (ask only if Q2 = rough idea or scratch)
Examples: time-sensitive, must use a specific format, need to track progress, etc.

**Q4: How involved do you want to be?** (ask only if relevant)
1. Hands-on: I review and approve each step
2. Delegated: run autonomously, show me results

### Step 4: Recommend

Recommend **1 primary skill** + up to **2 secondary skills**.
Only recommend skills confirmed as installed.

**Recommendation format:**
```
✅ Primary: `skill-name`
Why: [1–2 sentences: what this skill does and why it fits]

🔁 Also useful:
- `skill-name-2`: [when to bring this in]
- `skill-name-3`: [when to bring this in]

Want me to write a ready-to-use prompt for your specific goal?
```

---

## SELF-UPDATE PROTOCOL

The routing map goes stale when skills are added or removed.
Update it whenever triggered.

**Triggers (any of these phrases):**
- "update the router" / "refresh skill list" / "router is outdated"
- "I added a new skill" / "I removed a skill" / "skills changed"
- "regenerate routing map" / "rebuild skill index"
- Router itself detects a skill in the filesystem not listed in routing-map.md

**Self-update steps:**
1. Scan `/mnt/skills/user/` and `/mnt/skills/public/` (or detected skill path)
2. For each SKILL.md found: extract `name`, first line of `description`, line count
3. Group into domains using the domain detection logic above
4. Rewrite `references/routing-map.md` with fresh entries + current timestamp
5. Report changelog: "Added: X | Removed: Y | Updated: Z"
6. Confirm: "Router is now current as of [date]. [N] skills indexed."

---

## ROUTING INTELLIGENCE RULES

These rules apply in both modes:

1. **Scan before recommending**: never cite a skill without confirming it exists
2. **Upstream first**: if multiple skills apply, recommend the most upstream one (`brainstorming` before `skill-developer`; `soil-test-interpreter` before `vedic-farming`)
3. **Combos over singles**: for complex goals, recommend a skill chain with sequencing
4. **Domain cross-links**: for farming tasks, note if a business or document skill adds value (e.g., "after `vedic-farming`, use `docx` to produce a preparation log")
5. **Irrelevant is irrelevant**: if installed skills include clearly off-topic ones for this user's context, do not recommend them
6. **If nothing matches**: say so honestly: "I don't see an installed skill that directly covers this. Here's how I'd approach it without one..." then proceed

---

## REFERENCE FILES

| File | When to Read |
|------|-------------|
| `references/routing-map.md` | Current indexed skill library: domains, descriptions, trigger phrases, combos |

Regenerate routing-map.md using the self-update protocol whenever it feels outdated.
