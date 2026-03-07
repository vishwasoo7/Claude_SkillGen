# Summary Template
## Structured summary format for Phase 5 Approval Gate

---

## WHEN TO USE THIS TEMPLATE

Use this exact structure for the Phase 5 summary.
Do not abbreviate or skip sections.
The summary is the user's primary review surface before final build.

---

## TEMPLATE

```
==============================================
SKILL SESSION SUMMARY -- [OPERATION TYPE]
Target: [skill-name]
Phase: 5 of 6 -- Awaiting Approval
==============================================

OPERATION OVERVIEW
------------------
Operation:  [CREATE / UPGRADE / CLONE / AUDIT]
Skill:      [skill name]
Platform:   [detected environment]
Started:    [brief description of starting state]
Goal:       [what user asked for]

WHAT CHANGED
------------
[Use a table for upgrades/clones. For CREATE, describe what was built.]

| Section / File          | Before                        | After                          | Reason                        |
|------------------------|-------------------------------|--------------------------------|-------------------------------|
| [section name]          | [old content / "did not exist"] | [new content / "added"]       | [specific reason]             |

WHAT DID NOT CHANGE
-------------------
[List sections preserved exactly and why.]
- [Section name]: [reason preserved]

SKILLS APPLIED THIS SESSION
----------------------------
[Every skill read and used, in order applied]
- [skill-name]: [what it contributed]

VERIFICATION SCORECARD
-----------------------
[Every check with pass/fail evidence]

Check  1: [description] -- [PASS / FAIL] -- [evidence]
Check  2: [description] -- [PASS / FAIL] -- [evidence]
...
Check N: [description] -- [PASS / FAIL] -- [evidence]

Result: [N]/[N] PASS | [N] FAIL

FILES PRODUCED
--------------
[Every file created or modified, with path and line count]

[created]  /path/to/SKILL.md              ([N] lines)
[created]  /path/to/references/XX-name.md  ([N] lines)
[snapshot] /path/to/original-snapshot.md   (original preserved)

PENDING ITEMS
-------------
[Anything deferred, known limitations, or follow-up actions needed]
- [item]: [description and recommended action]

If nothing pending: "None. Skill is complete as specified."

INSTALL INSTRUCTIONS
--------------------
1. Download: [zip file path or file links]
2. Upload to: [platform-specific instruction]
   - claude.ai:   Customize > Skills > Upload zip
   - Claude Code: Copy folder to .claude/skills/[skill-name]/
   - Antigravity:  Copy folder to ~/skills/[skill-name]/
3. After install: [any post-install steps, e.g., "say 'update the router'"]

==============================================
APPROVAL REQUEST
==============================================
Please review the summary above.

Options:
  A) Approve -- proceed to final build and install
  B) Approve with changes -- describe what to modify first
  C) Request more changes -- describe what is missing or wrong

Waiting for your response before Phase 6.
```

---

## NOTES ON FILLING THE TEMPLATE

**What Changed table:**
- Every intentional change gets one row
- "Before" should quote or describe the original precisely, not vaguely
- "Reason" must connect to a specific user requirement or quality issue found in the audit
- If CREATE operation: replace table with a section-by-section description of what was built

**Verification Scorecard:**
- Evidence means: actual output, line count, grep result, diff line count
- Not acceptable as evidence: "should be", "looks correct", "I believe"
- If a check failed and was fixed: show both the fail evidence and the fix evidence

**Pending Items:**
- Be honest about limitations
- If the skill cannot do something the user wanted, say so here
- Do not bury limitations in the What Changed table

**Install Instructions:**
- Always include all three platform variants
- If the skill has dependencies on other skills, list them
- If skill-router needs updating after install, say so explicitly
