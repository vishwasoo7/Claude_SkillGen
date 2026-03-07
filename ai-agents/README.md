# AI Agents Skills

This category contains Claude skills for multi-agent orchestration, autonomous task execution, and meta-level AI behavior. These skills expand what Claude can do when working on complex, multi-step, or multi-domain problems by enabling it to coordinate agents, manage memory, route tasks, and operate with greater autonomy.

---

## Skills in This Category

### brainstorming

**File:** [brainstorming/SKILL.md](./brainstorming/SKILL.md)
**Lines:** 191

A universal brainstorming and idea development skill. Guides Claude through a 5-step flow (understand context, ask clarifying questions, propose 2-3 approaches, present plan in sections, hand off to action) before any idea is acted on. Fully platform-agnostic and topic-agnostic -- contains no hardcoded skill names, no platform-specific tools, and no domain assumptions.

Includes a Domain Adaptation Guide covering farming decisions, business strategy, software, writing, personal choices, and skill building. Works identically on claude.ai, Claude Code, API, terminal, or any other environment.

Activate before acting on any idea, plan, or decision where the approach is not yet fully clear -- regardless of domain or platform.

---

### dispatching-parallel-agents

**File:** [dispatching-parallel-agents/SKILL.md](./dispatching-parallel-agents/SKILL.md)
**Lines:** 180

Enables Claude to split a task into two or more independent subtasks and work on them simultaneously rather than sequentially. This significantly reduces time-to-completion when the subtasks have no shared state or dependencies.

Activate when facing multiple independent failures (different test files, different subsystems, different bugs), or when a complex task can be cleanly decomposed into parallel workstreams.

---

### parallel-agents

**File:** [parallel-agents/SKILL.md](./parallel-agents/SKILL.md)
**Lines:** 177

Provides multi-agent orchestration patterns for tasks that require different domain expertise operating in parallel. Useful when a problem benefits from multiple analytical perspectives running simultaneously.

Activate when comprehensive analysis requires more than one domain perspective, or when different parts of a task demand specialized knowledge that should be applied concurrently.

---

### memory-systems

**File:** [memory-systems/SKILL.md](./memory-systems/SKILL.md)
**Lines:** 229
**Source:** Agent Skills for Context Engineering (GitHub)

An architecture guide for designing short-term, long-term, and graph-based memory systems for AI agents and applications. Covers when to use each memory type, how to structure data, and how to manage context window constraints.

Activate when designing AI systems that need to persist information across sessions, manage conversation history, build knowledge graphs, or optimize context usage.

---

### loki-mode

**File:** [loki-mode/SKILL.md](./loki-mode/SKILL.md)
**Lines:** 280

A fully autonomous multi-agent system that takes a Product Requirements Document (PRD) and works through to a deployed product with minimal human intervention. Supports multiple AI providers including Claude, Codex, Gemini, Cline, and Aider.

Activate by saying "Loki Mode" in your prompt. Requires the `--dangerously-skip-permissions` flag in Claude Code. This skill makes decisions autonomously and does not stop to ask clarifying questions.

---

### using-superpowers

**File:** [using-superpowers/SKILL.md](./using-superpowers/SKILL.md)
**Lines:** 95

A meta-skill that establishes the rule that Claude must always check for and invoke relevant skills before responding to any prompt, including clarifying questions. It prevents Claude from answering from general knowledge when a more specialized skill is available.

This skill should be active at all times as a baseline behavior rule. It ensures the skill ecosystem is actually used rather than bypassed.

---

### skill-router

**File:** [skill-router/SKILL.md](./skill-router/SKILL.md)
**Lines:** 182

A smart routing skill that identifies and surfaces the most relevant installed skills for any given prompt. Works across all Claude environments including claude.ai, Claude Code, and Antigravity. It adapts dynamically to whatever skills are currently installed.

Activate when you are unsure which skill to use, want a recommendation, or need Claude to proactively suggest applicable skills before starting a task.

---

## Status

All 7 skills are production-ready.

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment.

Example:
```
cp -r brainstorming/ /mnt/skills/user/
```
