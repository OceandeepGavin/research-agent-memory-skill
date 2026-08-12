# Memory Update Rules


## General Rule

Do not store everything.

Only store information that has future value.

Store durable truth in memory/.
Store control state and routing in management/ when a project uses a separate project-management layer.

Do not copy the same information at length into both layers.
Memory records reusable facts, conclusions, and current truth.
Management records task board state, project routing, ownership, gates, and operating controls.

For multi-thread or multi-agent work, use a single-writer model:

- The main controlling thread writes shared memory by default.
- Worker threads return Memory Update Candidates instead of editing memory files.
- A worker thread may write memory directly only when the user explicitly asks that thread to update or record memory.


---


## Memory Update Candidate

Worker threads and delegated agents should end meaningful work with a compact candidate update.

Use this format:

```markdown
## Memory Update Candidate

### Completed Work

-

### Files or Artifacts Changed

-

### Decisions or Rationale

-

### Reusable Findings

-

### Remaining Tasks or Blockers

-

### Suggested Memory Updates

- SESSION_LOG.md:
- STATE.md:
- TASKS.md:
- DECISIONS.md:
- EXPERIMENTS.md:
- KNOWLEDGE.md:
- MEMORY_INDEX.md:
```

The main controlling thread should review the candidate, remove duplication, and promote only durable information.

Do not paste full worker transcripts, raw terminal output, or broad implementation logs into memory.


---


## Direct Worker Memory Writes

If the user explicitly instructs a worker thread to update memory, the worker may write memory files directly.

Allowed examples:

- "Update memory before finishing."
- "Record this result in memory."
- "Remember this decision."
- "Write the memory files from this thread."

Direct worker writes should be narrow:

- Update only the relevant memory files.
- Preserve current entries unless they are outdated.
- Add SESSION_LOG.md entries for traceability.
- Update MEMORY_INDEX.md only when a new or moved durable entry needs navigation.
- Avoid changing STATE.md if the worker does not own the overall project status.


---


## Update STATE.md when:


Examples:

- current goal changes
- task progress changes
- blocker appears
- milestone completed
- training launches, completes, fails, or stops
- evaluation verdict changes the current next step
- current owner or focus changes


Example:

Before:

Training unstable


After:

Training stabilized after LR adjustment


---


## Update DECISIONS.md when:


Examples:

- architecture choice
- dataset choice
- experimental strategy choice
- preferred checkpoint, branch, method, architecture, or strategy choice
- accepted operating rule or user correction that should guide future sessions


A decision should include:

- context
- alternatives
- final choice
- reason


---


## Update EXPERIMENTS.md when:


Examples:

- training result
- ablation result
- parameter comparison
- evaluation PASS, FAIL, or verdict
- reusable conclusion from a run, probe, benchmark, or QA check


Required information:

- experiment ID
- configuration
- result
- conclusion
- artifact, run, report, checkpoint, or evaluation path when available


---


## Update ENVIRONMENT.md when:


Examples:

- CUDA changed
- server changed
- dependency changed
- server class or access pattern changed
- command, path, Windows, Git, QA, or environment rule changed


---


## Update TASKS.md when:


Examples:

- new task created
- task completed
- priority changed
- owner reassignment
- thread takeover
- archived or superseded task
- blocker appeared or resolved
- watch or notification responsibility changed


---

## Update KNOWLEDGE.md when:

Examples:

- repeated pitfall is discovered
- code, training, QA, or release rule is accepted
- user correction should influence future work
- durable project operating lesson emerges

Do not hide these in SESSION_LOG only.


---


## Current Override and Current Board

Long projects accumulate historical ACTIVE and BLOCKED entries.
To prevent stale entries from misleading future agents, maintain a current override section at the top of STATE.md and TASKS.md when history is large or ambiguous.

STATE.md should include Current Override for:

- current PM or owner
- current focus
- current running or waiting items
- active blockers
- next action

TASKS.md should include Current Board for:

- active task
- waiting task
- completed task
- owner
- artifact/report pointer

The override section supersedes old entries below it.
Do not rewrite history unless consolidating; mark old sections historical instead.


---


## Evidence Pointer Over Copy

Prefer conclusions plus pointers.

For runs, evaluations, reports, and artifacts, store:

- artifact or report path
- checkpoint, run, evaluation, or branch identifier when relevant
- verdict and necessary key metrics
- next action

Do not paste:

- full logs
- full reports
- raw terminal output
- complete thread histories

A thread final answer is not durable memory by itself.
Important results should have an artifact or report path, then durable conclusions should be promoted to the relevant memory file.


---


## Management Sync Hints

When research-project-manager or a management/ control plane is in use, tell the PM or main controlling thread to update related management files after durable memory updates.

Default mapping:

- task state, owner, takeover, archived/superseded status -> management/TASK_BOARD.md
- current status, blockers, next operation -> management/PROJECT_STATUS.md
- artifact/report route or branch ownership -> management/PROJECT_TREE.md
- role boundary, thread routing, file ownership -> management/AGENT_REGISTRY.md
- policy, privacy, permission, notification, token, sync mode -> management/PROJECT_CONFIG.md

The memory skill should not duplicate management content at length.
It should provide a compact sync hint when management files need PM attention.


---


## Routine Update Summary

Use this short format for routine memory updates:

```markdown
STATE:
DECISION or VERDICT:
NEXT:
ARTIFACT:
```

If a heartbeat, automatic check, or monitor finds no durable state change, do not update multiple memory files and do not send a long notification.
Use DONT_NOTIFY or a quiet status when supported by the surrounding system.


---


## SESSION_LOG relationship


Every important session event is first recorded in SESSION_LOG.

For delegated work, SESSION_LOG should identify whether the entry was written by:

- main controlling thread
- worker thread with explicit user authorization
- main controlling thread after reviewing a worker Memory Update Candidate

Then important information should be promoted to:

- STATE
- DECISIONS
- EXPERIMENTS
- TASKS
- ENVIRONMENT
- KNOWLEDGE

SESSION_LOG is not the source of truth.
Keep it lightweight and never let it become a long chat transcript.
