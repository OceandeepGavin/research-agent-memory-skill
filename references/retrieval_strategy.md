# Memory Retrieval Strategy


## Core Principle

Retrieve the minimum amount of memory required to solve the current task.


Do not load all memory files by default.


---

## Default Retrieval:

Read:

- memory/MEMORY_INDEX.md
- memory/STATE.md
- memory/TASKS.md


Use MEMORY_INDEX.md to locate additional information when needed.


Reason:

These represent current project status.

If files are stored at the project root instead of memory/, use MEMORY_INDEX.md, STATE.md, and TASKS.md at the root.

When STATE.md or TASKS.md has a Current Override or Current Board section, read it first.
Treat older ACTIVE, BLOCKED, or TODO entries below that section as historical unless the override points to them.


---

## Memory and Management Layers

If both memory/ and management/ exist, read memory first, then the smallest necessary management control files.

Startup order:

1. memory/MEMORY_INDEX.md
2. memory/STATE.md
3. memory/TASKS.md
4. management/PROJECT_TREE.md when route or artifact location is needed
5. management/PROJECT_STATUS.md when current control status is needed
6. the current row or section of management/TASK_BOARD.md when task board state is needed

Conditional management reads:

- Read management/AGENT_REGISTRY.md only for role boundaries, thread routing, or file ownership.
- Read management/PROJECT_CONFIG.md only for policy, privacy, training permissions, open or release policy, token mode, sync mode, or notification rules.

Avoid:

- all memory files by default
- all management files by default
- all reports by default
- long thread histories as context


---

## Main Thread Coordination

When coordinating delegated work, the main controlling thread should read:

- memory/MEMORY_INDEX.md
- memory/STATE.md
- memory/TASKS.md

Then retrieve only the specific files needed to prepare worker context.

The main thread should pass workers compact excerpts or task-specific summaries instead of the full memory set.


---


## Worker Thread Retrieval

Worker threads should not load all memory files by default.

Use the context supplied by the main thread first.

Read additional memory only when required for the assigned task.

If memory files are needed, prefer:

- memory/TASKS.md for task ownership and expected output
- memory/STATE.md for current status
- memory/MEMORY_INDEX.md to locate one specific durable entry

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
