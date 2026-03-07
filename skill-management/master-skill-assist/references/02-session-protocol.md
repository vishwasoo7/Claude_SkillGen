# Session Protocol
## Phase tracking, skill orchestration, and session state management

---

## SESSION STATE

Track these variables throughout a master-skill-assist session:

```
SESSION STATE
-------------
Operation type:   [CREATE / UPGRADE / CLONE / AUDIT]
Target skill:     [skill name or "new"]
Current phase:    [0-6]
Platform:         [claude.ai / Claude Code / Antigravity / unknown]
Skill path:       [resolved path]
Skills in use:    [list of skills read this session]
Files modified:   [list of paths]
Approval status:  [pending / approved / approved-with-changes]
```

Announce phase transitions clearly:
```
--- PHASE [N]: [PHASE NAME] ---
```

---

## SKILL ORCHESTRATION RULES

### How to select skills for each phase

Skills are selected dynamically from the live inventory, never hardcoded.
The selection logic below uses skill categories, not skill names.
Any skill matching the category description qualifies.

**Phase 2 (Roadmap) -- always look for:**
- A brainstorming-type skill (helps structure discovery and approach selection)
- A RAG or retrieval-type skill (helps find relevant knowledge in the library)
- Any domain skill matching the target skill's domain

**Phase 3 (Execution) -- look for:**
- A skill-developer or skill-creation skill (structural rules, YAML patterns)
- Any skill with content relevant to the domain being built
- A prompt-engineering skill (helps write better skill descriptions)
- Document creation skills if packaging is needed (docx, pdf, pptx)

**Phase 4 (Verification) -- always look for:**
- A verification skill (evidence-before-claims, quality gates)
- Any skill with specific quality criteria for this domain

**Skill selection announcement format:**
```
Skills selected for this session:
  Phase 2 (Roadmap):   brainstorming, rag-engineer
  Phase 3 (Execution): skill-developer, [domain skill]
  Phase 4 (Verify):    verification-before-completion
```

### Reading a skill during execution

Use the `view` tool (file-based) or the `Skill` tool (Claude Code) or recall from context (chat-only).
Always read the full SKILL.md before applying a skill.
If a skill has references/, read only the relevant reference file for the current task.

---

## PHASE TRANSITION RULES

```
Phase 0 -> Phase 1:  Always automatic. Environment scan must complete first.
Phase 1 -> Phase 2:  After operation type and target confirmed.
Phase 2 -> Phase 3:  GATE. Roadmap must be approved. Never skip.
Phase 3 -> Phase 4:  After all execution steps complete.
Phase 4 -> Phase 5:  After all verification checks pass (or failures fixed).
Phase 5 -> Phase 6:  GATE. Approval must be explicit. Never skip.
Phase 6 -> done:     After final verification passes on live files.
```

Hard gates (Phase 2->3 and Phase 5->6) cannot be bypassed.
If user pushes to skip: explain why the gate exists and offer to shorten it, not remove it.

---

## MULTI-SKILL SESSIONS (Audit or batch upgrades)

When operating on multiple skills in one session (e.g., audit + fix top 3):

1. Complete Phase 0-2 once for the whole session (environment + overall roadmap)
2. For each skill, run Phase 3-6 independently
3. Track per-skill state separately
4. Present one summary per skill in Phase 5, then a combined final summary

Session log format for multi-skill operations:
```
SKILL 1: [name] -- [status: done / in-progress / pending]
SKILL 2: [name] -- [status]
SKILL 3: [name] -- [status]
```

---

## HANDLING UNEXPECTED SITUATIONS

**Skill path not writable:**
Work in `/home/claude/<skill-name>/` throughout.
In Phase 6, attempt copy to skill path.
If copy fails, deliver zip to `/mnt/user-data/outputs/` and tell user to install manually.

**Skill exceeds 500 lines after changes:**
Stop. Do not save over-limit files.
Move excess content to a new reference file.
Update SKILL.md with a pointer to the new reference file.
Re-run line count check before proceeding.

**Installed skill has no SKILL.md:**
Flag as broken in audit.
Do not attempt to upgrade until SKILL.md exists.

**User modifies scope mid-session:**
Acknowledge the change.
Revise the session state.
If in Phase 3 or later, assess whether to re-run Phase 2 or absorb the change inline.
State which choice you are making and why.

**Verification fails after Phase 6 install:**
Do not announce completion.
Fix the issue on the live files directly.
Re-run the failed check.
Report the fix in the final announcement.

---

## QUALITY PRINCIPLES

These apply to every skill produced in any operation:

**Write reasons, not commands.**
Instead of "ALWAYS do X", explain why X matters.
LLMs follow reasoning better than arbitrary rules.

**Lean prompts beat verbose ones.**
Remove any section that is not actively improving outputs.
Every line in a skill should earn its place.

**Platform-agnostic by default.**
If a step requires a specific tool, wrap it in environment detection.
Never write "In Claude Code:" without also writing what to do in other environments.

**Trigger phrases must be real.**
Description keywords must match what a real user would type.
Test mentally: "Would someone say this when they need this skill?"

**Generalize from examples, do not over-fit to them.**
A skill that only works for the exact example used to build it is useless.
After drafting, ask: "Would this work for a completely different user with the same need?"
