# Memory Retrieval Strategy


## Core Principle

Retrieve the minimum amount of memory required to solve the current task.


Do not load all memory files by default.


---


## Default Retrieval


For every new task:


Always load:

- STATE.md
- TASKS.md


Reason:

These represent current project status.


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