# Engineering Skills

This category contains Claude skills for software engineering quality, AI and ML system design, and prompt engineering. These skills are intended for developers and engineers who want Claude to operate with deeper technical precision across code quality, retrieval systems, and language model interaction design.

---

## Skills in This Category

### kaizen

**File:** [kaizen/SKILL.md](./kaizen/SKILL.md)
**Lines:** 733

A comprehensive skill based on the Kaizen philosophy of continuous improvement. It guides Claude through code quality improvement, error-proofing, standardization, and incremental refactoring. The skill emphasizes making small, verifiable improvements over large rewrites.

Activate when improving existing code quality, refactoring a codebase, discussing process improvements, applying error-proofing patterns (poka-yoke), or standardizing code conventions across a project.

---

### rag-engineer

**File:** [rag-engineer/SKILL.md](./rag-engineer/SKILL.md)
**Lines:** 95
**Source:** vibeship-spawner-skills (Apache 2.0)

A specialized skill for building Retrieval-Augmented Generation (RAG) systems. It covers embedding model selection, vector database setup and optimization, chunking strategies, retrieval pipeline design, and evaluation of RAG system performance.

Activate when building a RAG system, selecting a vector database, designing a document chunking strategy, optimizing retrieval quality, or debugging why a RAG pipeline is returning poor results.

---

### prompt-engineer

**File:** [prompt-engineer/SKILL.md](./prompt-engineer/SKILL.md)
**Lines:** 249
**Category:** Automation

A practical prompt transformation skill that rewrites user prompts using established engineering frameworks. Supported frameworks include RTF (Role, Task, Format), RISEN, Chain of Thought, RODES, Chain of Density, RACE, RISE, STAR, SOAP, CLEAR, and GROW.

Activate when you want to improve a prompt you have written, need a prompt reformatted for a specific use case, or want Claude to apply a named prompting framework to a given instruction.

---

### prompt-engineering-patterns

**File:** [prompt-engineering-patterns/SKILL.md](./prompt-engineering-patterns/SKILL.md)
**Lines:** 216

An advanced skill covering production-grade prompt engineering techniques for maximizing LLM performance, reliability, and controllability. It goes beyond basic prompting to cover patterns used in real production systems, including structured outputs, tool use, multi-step reasoning chains, and failure mode prevention.

Activate when designing prompts for production systems, improving LLM output reliability, building prompt templates for applications, or studying advanced prompting techniques beyond standard few-shot or chain-of-thought approaches.

---

## Status

All 4 skills are production-ready.

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment.

Example:
```
cp -r kaizen/ /mnt/skills/user/
```
