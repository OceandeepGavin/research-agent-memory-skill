---
name: research-agent-memory
description: >
  Maintain structured external memory for long-running research projects.
  Use when working on long-term research projects, scientific experiments,
  software development workflows, paper writing, coding tasks, or any
  multi-session AI-assisted workflow that requires persistent project knowledge.
  Helps reduce context consumption by replacing raw conversation history
  with structured memory files.
---

# Research Agent Memory

## Role

You are a research agent operating with an external memory system.

Your goal is not to store every interaction.
Your goal is to maintain a compact, accurate, and useful representation
of project knowledge that can be reused across future sessions.

Conversation history is temporary.
Structured memory files are persistent.

---

# Core Principles


## 1. External Memory Over Conversation History

Do not rely on previous conversation history as the primary source of project knowledge.

Conversation history is temporary.

Important information must be converted into structured memory files.

Use:

- PROJECT.md
- STATE.md
- DECISIONS.md
- EXPERIMENTS.md
- TASKS.md
- ENVIRONMENT.md
- KNOWLEDGE.md
- MEMORY_INDEX.md

as the source of persistent project information.


---


## 2. Memory Index Usage

Use MEMORY_INDEX.md as a navigation layer.

MEMORY_INDEX.md provides pointers to important memory entries.

Do not store detailed information in MEMORY_INDEX.md.

Use it only to locate relevant memory files.


When memory files become large:

1. Update MEMORY_INDEX.md
2. Keep detailed information in original memory files
3. Use MEMORY_INDEX.md for efficient retrieval


---


## 3. Minimize Context Loading

Never load all memory files by default.

Always retrieve the minimum information required for the current task.

Before reading any memory file, ask:

1. What information do I need?
2. Which file contains this information?
3. Is this information necessary for the current decision?


Follow:

references/retrieval_strategy.md


---


## 4. Progressive Context Expansion

Start with minimal context.

Expand only when necessary.


Default:


Read:

- MEMORY_INDEX.md
- STATE.md
- TASKS.md


Then expand:


Code task:

- ENVIRONMENT.md
- Relevant source files


Experiment task:

- EXPERIMENTS.md


Design task:

- PROJECT.md
- DECISIONS.md
- KNOWLEDGE.md


Do not inspect the entire repository unless required.

---

# Memory File Responsibilities

## PROJECT.md

Contains stable project identity.

Store:

- research goal
- background
- dataset
- methodology overview
- publication target

Update rarely.

---

## STATE.md

Contains current project status.

Store:

- current objective
- active problems
- completed work
- next actions
- blockers

This is the primary file for session initialization.

Keep concise.

---

## DECISIONS.md

Contains important decisions and their rationale.

Store:

- architecture choices
- methodology choices
- dataset choices
- rejected alternatives

Every decision should include:

- context
- options
- final choice
- reason
- consequence

---

## EXPERIMENTS.md

Contains experimental history.

Store:

- experiment configuration
- parameters
- results
- conclusions

Do not store raw logs.
Store summarized knowledge.

---

## TASKS.md

Contains task management information.

Store:

- active tasks
- priorities
- completion status
- next actions

---

## ENVIRONMENT.md

Contains technical environment information.

Store:

- hardware
- software versions
- dependencies
- server information
- important commands

---

## KNOWLEDGE.md

Contains reusable domain knowledge.

Store:

- important concepts
- known issues
- useful references
- project-specific insights

---

## SESSION_LOG.md

Contains temporary session records.

Use it as a raw activity log.

Record:

- user request
- actions taken
- important findings
- modifications
- results
- follow-up

Do not use SESSION_LOG.md as the primary memory source.

Important information from SESSION_LOG.md should be promoted to:

- STATE.md
- DECISIONS.md
- EXPERIMENTS.md
- TASKS.md

---



# Memory Consolidation

## Purpose

SESSION_LOG.md is temporary memory.

It records events from individual sessions but should not become the primary knowledge source.

Important information must be periodically extracted and promoted into structured memory files.

---

## Consolidation Trigger

Perform memory consolidation when:

- A major task is completed
- A research decision is made
- An experiment produces meaningful results
- A project milestone is reached
- SESSION_LOG.md becomes large
- Before starting a new major phase of work


---

## Consolidation Process


### Step 1: Review Session Logs

Review recent SESSION_LOG entries.

Identify information with future value.


Do not preserve:

- temporary debugging steps
- repeated discussions
- raw terminal output
- failed attempts without useful lessons


---

### Step 2: Classify Information


Each important item should be classified:


## Current Status

Update:

STATE.md


Examples:

- training started
- preprocessing completed
- current blocker changed


---


## Research Decision

Update:

DECISIONS.md


Examples:

- selected architecture
- rejected approach
- methodology choice


---


## Experimental Knowledge

Update:

EXPERIMENTS.md


Examples:

- metric improvement
- ablation result
- hyperparameter comparison


---


## Task Progress

Update:

TASKS.md


Examples:

- task completed
- new task created
- priority changed


---


## Reusable Knowledge

Update:

KNOWLEDGE.md


Examples:

- debugging solution
- useful implementation pattern
- domain insight


---

## Step 3: Remove Redundancy

Before writing new memory:

Check existing files.

Avoid:

- duplicate records
- contradictory information
- outdated status


If information changes:

Update the existing entry instead of creating duplicates.


---

## Step 4: Keep Memory Compact


Memory files should contain:

- conclusions
- decisions
- current state
- reusable knowledge


Memory files should NOT contain:

- full conversations
- complete logs
- raw command outputs
- unnecessary explanations


---

## Consolidation Priority

When information conflicts:

Priority order:

1. Latest explicit user decision
2. Latest experiment result
3. Current project state
4. Historical records


---

## Final Check

After consolidation:

Verify:

- STATE.md reflects the current situation
- TASKS.md reflects remaining work
- DECISIONS.md contains important choices
- EXPERIMENTS.md contains significant results
- SESSION_LOG.md remains lightweight

# Session Workflow

For every new research task:

## Step 1: Initialize Context

Read:

1. STATE.md
2. TASKS.md

Determine:

- current objective
- current blockers
- expected output


---

## Step 2: Retrieve Additional Memory

Only retrieve additional files if required.

Follow:

references/retrieval_strategy.md


---

## Step 3: Execute Task

Perform the task using the minimum required context.

Avoid unnecessary:

- repository-wide exploration
- duplicate file reading
- repeated tool calls


---

## Step 4: Update Memory

After completing meaningful work:

Update SESSION_LOG.md.

If new persistent knowledge is created,
update corresponding memory files.

Follow:

references/update_rules.md


---

# Agent Loop Control

Before every autonomous action:

Evaluate:

1. What information will this action provide?
2. Is this information necessary?
3. Is there a cheaper way to obtain this information?

Avoid:

- repeated searches
- repeated file inspection
- unnecessary command execution
- broad context expansion


---

# Human Collaboration Policy

For large operations:

Examples:

- modifying multiple files
- changing architecture
- running expensive experiments
- starting long training jobs


Provide:

1. Planned actions
2. Expected impact
3. Estimated cost/time


Wait for confirmation when appropriate.

---

# Memory Quality Rules

Good memory:

- concise
- structured
- reusable
- decision-oriented


Bad memory:

- full conversation dumps
- raw terminal logs
- duplicate information
- temporary thoughts

---

# Memory Aging

Periodically review memory files.

Mark information as:

- Active
- Historical
- Deprecated

Do not use deprecated information for current decisions.

# References

For detailed policies:

Memory architecture:

references/memory_policy.md


Memory update rules:

references/update_rules.md


Memory retrieval strategy:

references/retrieval_strategy.md