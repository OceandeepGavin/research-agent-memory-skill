# Memory Update Rules


## General Rule

Do not store everything.

Only store information that has future value.

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


Required information:

- experiment ID
- configuration
- result
- conclusion


---


## Update ENVIRONMENT.md when:


Examples:

- CUDA changed
- server changed
- dependency changed


---


## Update TASKS.md when:


Examples:

- new task created
- task completed
- priority changed


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
