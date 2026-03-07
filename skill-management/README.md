# Skill Management Skills

This category contains Claude skills for building, validating, and maintaining other Claude skills. These are meta-level tools aimed at developers and power users who want to create new skills, debug existing ones, enforce quality standards, and connect their Claude environment to external version control.

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

### github-connect

**File:** [github-connect/SKILL.md](./github-connect/SKILL.md)
**Lines:** 297

A platform-adaptive GitHub connector skill. The user provides a Personal Access Token, a repository URL, and a declared intended action. Claude then handles setup, execution, verification, commit, and push in a structured 5-stage protocol. Supports 6 actions: push-files, push-skill, update-readme, create-folder, sync-all, and inspect.

Works on claude.ai with computer use, Claude Code, Claude Desktop, and any self-hosted API environment with bash and git available. The token does not expire between sessions and can be reused without regenerating unless it was exposed publicly.

Activate when connecting to GitHub, pushing files or skills to a repo, syncing skills, updating a README in a remote repo, or inspecting repository state.

---

## Status

All 3 skills are production-ready.

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment.

Example:
```
cp -r github-connect/ /mnt/skills/user/
```
