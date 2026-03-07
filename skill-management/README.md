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

### master-skill-assist

**File:** [master-skill-assist/SKILL.md](./master-skill-assist/SKILL.md)
**Lines:** 229

A master orchestrator for the full skill lifecycle. Runs a structured six-phase session (environment scan, intent capture, roadmap generation, execution, verification, approval gate, final build) to create, upgrade, clone, audit, or repair any Claude skill. Adapts to whatever skills are installed and works across all platforms.

Activate when creating a new skill from scratch, upgrading or overhauling an existing skill, cloning a skill to a new purpose, auditing the full skill library, or running a skill health check.

---

### skill-seekers

**File:** [skill-seekers/SKILL.md](./skill-seekers/SKILL.md)
**Lines:** 23

Automatically converts documentation websites, GitHub repositories, and PDFs into Claude AI skills. Designed to accelerate skill creation by sourcing external knowledge and structuring it into the standard SKILL.md format.

Activate when converting a GitHub repo, documentation site, or PDF into a new Claude skill.

---

## Status

All 5 skills are production-ready.

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment.

Example:
```
cp -r github-connect/ /mnt/skills/user/
```
