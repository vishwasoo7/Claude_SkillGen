# Skill Management Skills

This category contains Claude skills for building, validating, and maintaining other Claude skills. These are meta-level tools aimed at developers and power users who want to create new skills, debug existing ones, or enforce quality standards in their Claude workflows.

---

## Skills in This Category

### skill-developer

**File:** [skill-developer/SKILL.md](./skill-developer/SKILL.md)
**Lines:** 429

A comprehensive guide for creating and managing Claude Code skills following Anthropic best practices. It covers skill file structure, trigger description writing, pattern matching, hook configuration, debugging workflows, and skill-rules.json management.

Activate when creating a new skill from scratch, modifying an existing skill, troubleshooting why a skill is not triggering correctly, or working with hooks and automation rules in Claude Code.

---

### verification-before-completion

**File:** [verification-before-completion/SKILL.md](./verification-before-completion/SKILL.md)
**Lines:** 139

Enforces a strict evidence-before-assertion rule: Claude must run verification commands and confirm output before claiming any task is complete, fixed, or passing. It prevents the common failure mode of declaring success without actually testing the result.

Activate before claiming work is done, before committing code, before creating pull requests, or whenever Claude is about to report that something is working.

---

## Status

Both skills are production-ready.

---

## Pending Skills Not Yet Added

| Skill | Reason |
|-------|--------|
| skill-seekers | Only 23 lines. Claims to convert documentation websites, GitHub repos, and PDFs into Claude skills, but lacks the instruction depth needed for that to work reliably. Needs significant expansion before inclusion. |

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment.

Example:
```
cp -r skill-developer/ /mnt/skills/user/
```
