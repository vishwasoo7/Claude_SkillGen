# Operations Guide
## Detailed step sequences for each operation type

---

## CREATE -- Building a New Skill From Scratch

### When to use
User wants a skill for something that does not exist yet in the library.

### Step sequence

**C1. Capture intent**
- What should this skill enable Claude to do?
- When should it trigger? (what phrases, contexts, situations)
- What is the expected output format?
- Who is the audience? (just this user, shareable, public)
- Any constraints? (line limit, platform, domain calibration)

**C2. Research existing patterns**
Scan installed skills for structural patterns to reuse:
- Find a skill in a similar domain for reference (not to copy, but for structure)
- Note how its YAML description is written
- Note whether it uses references/ or is single-file
- Note any domain-specific content that should link to the new skill

**C3. Decide architecture**
For simple skills (single clear purpose, under 300 lines of content):
-> Single SKILL.md file

For complex skills (multiple domains, deep reference material, calibration data):
-> SKILL.md + references/ folder

Rule: if writing SKILL.md and it approaches 400 lines, split into references/.

**C4. Write SKILL.md draft**
Structure order:
1. YAML frontmatter (name, description with rich trigger keywords)
2. One-line purpose statement
3. Quick decision table or orientation (if complex)
4. Core content sections
5. Reference file pointers (if references/ used)

Description writing rules:
- Include trigger phrases a real user would actually say
- Be specific about domains, not generic
- Be "pushy" -- err toward triggering rather than not
- Under 1024 characters
- No em dashes

**C5. Write reference files (if needed)**
Each reference file:
- Named with number prefix (01-name.md, 02-name.md)
- Has a one-line purpose statement at top
- Under 500 lines per file
- Has table of contents if over 200 lines
- Linked explicitly from SKILL.md with guidance on when to read

**C6. Self-review pass**
Read the draft with fresh eyes. Ask:
- Does the description make someone want to invoke this skill?
- Is every section pulling its weight?
- Are there MUST/NEVER instructions that could be explained as reasons instead?
- Is there any content that assumes a specific platform?

**C7. Continue to Phase 4 verification**

---

## UPGRADE -- Improving an Existing Skill

### When to use
User wants to fix, improve, update, overhaul, or refactor an existing skill.

### Step sequence

**U1. Read the current skill in full**
Use the `view` tool on the installed SKILL.md and all reference files.
Do not rely on memory or summaries.

**U2. Audit against quality checklist**
For each issue found, record:
- Location (file + line number)
- Issue type (broken ref, wrong platform, too long, missing content, etc.)
- Severity (critical / important / minor)
- Proposed fix

Standard audit checks:
- [ ] Line count under 500?
- [ ] Em dashes present? (must remove)
- [ ] Platform-specific tool references? (Skill tool, TodoWrite, EnterPlanMode, Read tool)
- [ ] Dead links to reference files that do not exist?
- [ ] Phantom skill names referenced that are not installed?
- [ ] YAML description has rich trigger keywords?
- [ ] Content matches stated purpose?
- [ ] Cross-links to related skills accurate?

**U3. Identify what to preserve**
List sections that are working correctly and must not change.
This becomes the "What did NOT change" section of the Phase 5 summary.

**U4. Snapshot original**
```
cp /path/to/skill/SKILL.md /home/claude/skill-snapshot-YYYYMMDD.md
```
Keep snapshot for diff comparison in verification.

**U5. Implement changes**
Work in `/home/claude/<skill-name>/` not in the installed path.
Make only the changes from the approved roadmap.
Every change traceable to a specific issue from U2.

**U6. Diff check**
Compare new version against snapshot.
Confirm only intended sections changed.
No accidental removals of good content.

**U7. Continue to Phase 4 verification**

---

## CLONE -- Adapting an Existing Skill for a New Purpose

### When to use
User wants to take an existing skill and adapt it for a different domain,
platform, audience, or use case while preserving the structural pattern.

### Step sequence

**CL1. Read the source skill in full**
Understand every section. Know what is structural (keep) vs domain-specific (replace).

**CL2. Clarify the target**
- What domain is the clone for?
- What stays the same? (structure, flow, verification approach)
- What changes? (all domain content, calibration data, examples, trigger phrases)
- New skill name?

**CL3. Extract the structural skeleton**
Create a stripped version with all domain content removed.
This is the template for the new skill.

**CL4. Fill with target domain content**
Apply the same research approach as CREATE step C2.
Look for domain-specific knowledge in installed skills.
Calibrate all content to the target domain.

**CL5. Rewrite YAML description**
Trigger phrases must match the new domain exactly.
No carry-over from the source skill's domain.

**CL6. Verify independence**
The clone must work standalone -- no dependency on the source skill.
No references back to the source unless explicitly intended as a related skill.

**CL7. Continue to Phase 4 verification**

---

## AUDIT -- Library-Wide Skill Health Review

### When to use
User wants a comprehensive review of all installed skills.
Not a single-skill operation -- covers the whole library.

### Step sequence

**A1. Build full inventory**
Scan the skill library path.
For every skill found, read SKILL.md and record:
- Name
- Line count
- Has references folder? (yes/no, how many files)
- Last known modification (if detectable)

**A2. Score each skill**
Apply a 5-point health score per skill:

| Criterion | Pass | Fail |
|-----------|------|------|
| Under 500 lines | +1 | 0 |
| No em dashes | +1 | 0 |
| No platform locks | +1 | 0 |
| Rich YAML description | +1 | 0 |
| Content matches purpose | +1 | 0 |

**A3. Categorize issues**
Group findings into:
- Critical (broken, misleading, wrong platform = immediate fix needed)
- Important (stale content, missing cross-links, line limit violations)
- Minor (polish, style, optimization opportunities)

**A4. Prioritize upgrade order**
Sort by: Critical first, then by most-used skills, then by importance.

**A5. Present audit report**
Format: one row per skill, columns: name / score / critical issues / recommendation.
Include a "fix now" list (top 3-5 highest priority) with brief action per item.

**A6. Offer to proceed**
"Want to start fixing these? I can run the UPGRADE operation on any of them."

---

## UNIVERSAL RULES (apply to all operations)

- Read every relevant skill before using it. Never assume content from memory.
- No em dashes in any output file.
- No platform locks. Every skill produced must be platform-agnostic.
- 500-line limit on every SKILL.md.
- Snapshot before modifying any existing file.
- All work in `/home/claude/` until Phase 6 final install.
- Announce every skill applied: "Reading `skill-name` to [purpose]..."
- One change at a time. Verify before next change.
