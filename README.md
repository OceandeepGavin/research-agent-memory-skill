# Research Agent Memory

A research-oriented external memory system for AI agents.

## Overview

Large language model agents often waste tokens by repeatedly processing:

- long conversation histories
- duplicated explanations
- temporary debugging logs
- unnecessary project exploration

`research-agent-memory` provides a structured external memory framework that allows agents to maintain long-term project knowledge while minimizing context consumption.

The core idea:

> Conversation history is temporary. Structured memory is persistent.

---

## Motivation

Traditional agent workflows rely heavily on chat history:

```
Conversation History
 |
 ↓
 Agent
 |
 ↓
 More context
 |
 ↓
 Higher token cost
```

This skill introduces a structured memory workflow:

```
Session Activity

 |

 ↓

 SESSION_LOG.md

 |

 ↓

 Memory Consolidation

 |

 +----------------+

 |                |

 ↓                ↓

 Current State     Long-term Knowledge

 STATE.md          DECISIONS.md

 EXPERIMENTS.md

 KNOWLEDGE.md
```



## Features

- External project memory instead of raw conversation history
- Token-efficient context retrieval
- Structured research project tracking
- Experiment history management
- Decision rationale preservation
- Environment tracking
- Session memory consolidation

---

## Memory Architecture

The memory system consists of several structured files.

| File             | Purpose                                       |
| ---------------- | --------------------------------------------- |
| `PROJECT.md`     | Stable project identity and research overview |
| `STATE.md`       | Current project status and active problems    |
| `DECISIONS.md`   | Important decisions and their rationale       |
| `EXPERIMENTS.md` | Experimental configurations and results       |
| `TASKS.md`       | Task planning and progress tracking           |
| `ENVIRONMENT.md` | Computing environment information             |
| `KNOWLEDGE.md`   | Reusable technical knowledge                  |
| `SESSION_LOG.md` | Temporary session records                     |

---

## Directory Structure

```
research-agent-memory/

├── SKILL.md

├── templates/
 │   ├── PROJECT.md
 │   ├── STATE.md
 │   ├── DECISIONS.md
 │   ├── EXPERIMENTS.md
 │   ├── TASKS.md
 │   ├── ENVIRONMENT.md
 │   ├── KNOWLEDGE.md
 │   └── SESSION_LOG.md

├── references/
 │   ├── memory_policy.md
 │   ├── update_rules.md
 │   └── retrieval_strategy.md

└── README.md
```

## Workflow

The recommended workflow:

### 1. Initialize Context

Before starting a task, the agent should read:

```
STATE.md
TASKS.md
```

to understand:

- current objective
- active problems
- pending work

---

### 2. Retrieve Additional Information

Only load additional memory when necessary.

Examples:

| Task Type           | Additional Memory |
| ------------------- | ----------------- |
| Code modification   | `ENVIRONMENT.md`  |
| Experiment analysis | `EXPERIMENTS.md`  |
| Research decisions  | `DECISIONS.md`    |
| Project overview    | `PROJECT.md`      |

---

### 3. Execute Task

The agent performs the task using the minimum required context.

Avoid:

- loading the entire repository unnecessarily
- reading complete conversation history
- repeating previous exploration

---

### 4. Update Memory

After meaningful progress:

Update appropriate memory files:

- New status → `STATE.md`
- New decision → `DECISIONS.md`
- New experiment → `EXPERIMENTS.md`
- New task → `TASKS.md`
- New reusable knowledge → `KNOWLEDGE.md`

---

## Memory Consolidation

`SESSION_LOG.md` is temporary memory.

It records:

- user requests
- actions taken
- important findings
- changes made
- results

Important information should later be consolidated into:

- `STATE.md`
- `DECISIONS.md`
- `EXPERIMENTS.md`
- `TASKS.md`
- `KNOWLEDGE.md`

Raw session history should not become permanent memory.

---

## Design Philosophy

### Bad Memory

Examples:

- complete conversation dumps
- raw terminal logs
- repeated explanations
- outdated information

### Good Memory

Examples:

- current project state
- important decisions
- experimental conclusions
- reusable solutions

The goal is not to remember everything.

The goal is to preserve information that improves future decisions.

---

## Installation

Install this skill into your agent environment:

```bash
npx skills add OceandeepGavin/research-agent-memory-skill -g -y
```

List the skill before installing:

```bash
npx skills add OceandeepGavin/research-agent-memory-skill --list
```

## Version

Current version:

```
v0.2.1
```

Initial release:

- Structured research memory architecture
- Memory retrieval strategy
- Memory consolidation workflow

## License

MIT License
