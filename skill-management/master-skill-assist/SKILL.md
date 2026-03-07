---
name: master-skill-assist
description: >
  Master orchestrator for all skill lifecycle operations. Use this skill whenever the
  user wants to create a new skill, upgrade or improve an existing skill, clone or
  adapt a skill for a new purpose, audit the skill library, fix a broken skill,
  build a skill from scratch, overhaul a skill, do a skill makeover, refactor a skill,
  review skill quality, plan skill improvements, or manage the skill library.
  Triggers on: create skill, build skill, new skill, upgrade skill, fix skill,
  improve skill, update skill, skill makeover, skill overhaul, skill audit,
  clone skill, adapt skill, port skill, skill library review, skill health check,
  skill roadmap, skill session, master skill, skill assist.
  Runs a structured six-phase session: environment scan, intent capture, roadmap,
  execution, verification, approval gate, and final build. Works on any platform.
  Adapts to whatever skills are installed. Never hardcodes skill names.
---

# Master Skill Assist

Orchestrates the complete skill lifecycle through a structured six-phase session.
Adapts to any platform and any installed skill library.
Every operation follows the same session model -- only the starting point differs.

---

## PHASE 0 -- ENVIRONMENT SCAN

Run this before anything else, every time.

**Step 1: Detect platform**

Observe available tools:
- `bash_tool` + `view` + `create_file` available -> file-based environment
- Only `Skill` tool available -> Claude Code with skill tool
- No file tools -> chat-only environment

**Step 2: Detect skill library path**

Try in order until one resolves:
1. `/mnt/skills/user/` (claude.ai standard)
2. `.claude/skills/` (Claude Code standard)
3. `~/skills/` (Antigravity / custom)
4. Ask user if none resolve

**Step 3: Build live skill inventory**

Scan every SKILL.md found. For each skill record:
- Name
- One-line description
- Line count
- Has references folder? Yes / No

Do not rely on memory or routing-map alone. Scan fresh every session.

**Announce result:**
```
Environment: [platform detected]
Skill path: [resolved path]
Skills found: [count] -- [name list]
```

---

## PHASE 1 -- INTENT CAPTURE

Detect operation type from user message:

| User intent signals | Operation |
|--------------------|-----------|
| "build", "create", "new skill", "make a skill for" | CREATE |
| "upgrade", "fix", "improve", "update", "overhaul", "makeover", "tweak", "refactor" | UPGRADE |
| "clone", "adapt", "port", "copy and modify", "based on existing" | CLONE |
| "audit", "review all", "what needs fixing", "health check", "library review" | AUDIT |

If operation type is unclear, ask one question:
> "Are you creating something new, improving something existing, or auditing the whole library?"

Once operation is confirmed, read the corresponding section in `references/01-operations.md`.

**Also capture:**
- Which skill(s) are involved (if upgrade/clone)
- What the skill should do (if create)
- Any constraints (line limit, platform, style preferences, no em dashes, etc.)
- Success criteria -- what does "done" look like?

---

## PHASE 2 -- ROADMAP GENERATION

This phase uses other installed skills to build a plan before touching any files.

**Step 1: Read brainstorming skill if installed**
Use it to structure the discovery conversation for the current operation.
Ask one question at a time. Propose 2-3 approaches with trade-offs.
Get explicit approval on the approach before proceeding.

**Step 2: Apply RAG pattern**
From `rag-engineer`: retrieval quality determines generation quality.
Scan installed skills for relevant knowledge that applies to this operation:
- Building a farming skill -> read agstack-farming, vedic-farming, soil-test-interpreter for context
- Building a business skill -> read startup-analyst, competitive-landscape for patterns
- Any skill build -> read skill-developer, skill-creator for structural rules

**Step 3: Draft the roadmap**

Present a roadmap with:
- Operation type confirmed
- Approach selected (with alternatives noted)
- Phases to execute
- Skills to invoke at each phase
- Files to create or modify
- Verification criteria

**HARD GATE:** Do not proceed to Phase 3 until user approves the roadmap.
If user wants changes, revise and re-present. Never skip this gate.

---

## PHASE 3 -- EXECUTION

Execute the approved roadmap. Read `references/01-operations.md` for the
detailed step sequence for your specific operation type.

**Core execution rules:**

1. Read each relevant skill before using it. Never rely on memory of a skill.
2. Announce each skill you are applying: "Reading `skill-name` to [purpose]..."
3. One phase at a time. Complete and confirm before moving forward.
4. Snapshot any file before modifying it.
5. All outputs go to `/home/claude/<skill-name>/` first. Never write directly to
   the installed skills path until Phase 6 final build.
6. No em dashes in any skill content produced.
7. Track every file created or modified.

**Execution log format** (maintain throughout Phase 3):
```
[CREATED]  path/to/file -- reason
[MODIFIED] path/to/file -- what changed
[SKIPPED]  path/to/file -- why
[APPLIED]  skill-name   -- what it contributed
```

---

## PHASE 4 -- VERIFICATION

Run `verification-before-completion` before claiming anything is done.

**Standard verification checklist (run on every skill produced):**

- [ ] SKILL.md line count under 500
- [ ] YAML frontmatter has name + description
- [ ] Description contains trigger keywords (not vague)
- [ ] Zero em dashes anywhere in any file
- [ ] Zero platform-specific tool locks (no "Claude Code only", no "TodoWrite", no "EnterPlanMode")
- [ ] All referenced files exist (no dead links to references/)
- [ ] No phantom skill names referenced that are not installed
- [ ] Environment detection present if skill needs to access files
- [ ] Core content correct and complete per the approved roadmap
- [ ] Diff from original confirms only intended sections changed (for upgrades)

Run each check with evidence. State pass or fail per item.
Do not claim completion until all checks pass.

If any check fails: fix it, re-run the failed check, confirm pass before moving on.

---

## PHASE 5 -- APPROVAL GATE

Present a structured summary. Read `references/03-summary-template.md` for the
exact format to use.

The summary must cover:
1. Operation type and skill name
2. What changed (table: section / before / after / reason)
3. What did NOT change and why
4. Verification scorecard (N/N checks passed)
5. Files produced (list with paths and sizes)
6. Pending items (anything deferred, any known limitations)
7. Install instructions

**HARD GATE:** Ask explicitly:
> "Please review the summary above. Approve to proceed to final build,
> or share any changes, additions, or removals you want made first."

Do not proceed to Phase 6 until user gives explicit approval or approval with modifications.
If modifications requested: implement them, re-run verification, re-present summary.

---

## PHASE 6 -- FINAL BUILD + FINAL CHECK

Only runs after explicit Phase 5 approval.

**Step 1: Install to live path**
Copy final files from `/home/claude/<skill-name>/` to the resolved skill library path.

**Step 2: Run final verification on live files**
Re-run the full Phase 4 checklist against the files at their installed location.
Evidence must come from the live path, not the build path.

**Step 3: Package for upload**
Create a zip at `/mnt/user-data/outputs/<skill-name>.zip`
Present files for download.

**Step 4: Update skill-router**
After any install, check if skill-router is installed.
If yes, prompt: "Say 'update the router' to add this skill to the routing index."

**Step 5: Final announcement**
```
SKILL SESSION COMPLETE
Operation: [type]
Skill: [name]
Status: LIVE at [path]
Verification: [N]/[N] checks passed
Download: [zip path]
```

---

## REFERENCE FILES

| File | Read when |
|------|-----------|
| `references/01-operations.md` | Phase 3 -- detailed steps per operation type |
| `references/02-session-protocol.md` | Any phase -- session state, skill orchestration rules |
| `references/03-summary-template.md` | Phase 5 -- structured summary format |
