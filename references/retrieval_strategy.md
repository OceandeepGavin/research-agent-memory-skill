# Memory Retrieval Strategy


## Core Principle

Retrieve the minimum amount of memory required to solve the current task.


Do not load all memory files by default.


---

## Default Retrieval:

Read:

- MEMORY_INDEX.md
- STATE.md
- TASKS.md


Use MEMORY_INDEX.md to locate additional information when needed.


Reason:

These represent current project status.


---

## Main Thread Coordination

When coordinating delegated work, the main controlling thread should read:

- MEMORY_INDEX.md
- STATE.md
- TASKS.md

Then retrieve only the specific files needed to prepare worker context.

The main thread should pass workers compact excerpts or task-specific summaries instead of the full memory set.


---


## Worker Thread Retrieval

Worker threads should not load all memory files by default.

Use the context supplied by the main thread first.

Read additional memory only when required for the assigned task.

If memory files are needed, prefer:

- TASKS.md for task ownership and expected output
- STATE.md for current status
- MEMORY_INDEX.md to locate one specific durable entry

Avoid reading SESSION_LOG.md unless doing a historical investigation.


---


## Code Modification Task


Load:

Required:

- STATE.md
- TASKS.md


Optional:

- ENVIRONMENT.md


Only load:

- relevant source files


Avoid:

- entire repository


---


## Experiment Analysis Task


Load:

- STATE.md
- EXPERIMENTS.md


If methodology related:

- DECISIONS.md


---


## Architecture Discussion


Load:

- PROJECT.md
- DECISIONS.md
- KNOWLEDGE.md


---


## Historical Investigation


Only when required:

Search:

SESSION_LOG.md

Do not load entire history.


---


## Context Expansion Rule


Start small.

Expand context only when current information is insufficient.


Priority:

1. Current state
2. Relevant task
3. Specific files
4. Historical records
5. Full project exploration
