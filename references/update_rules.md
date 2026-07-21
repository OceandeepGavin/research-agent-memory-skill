# Memory Update Rules


## General Rule

Do not store everything.

Only store information that has future value.


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

Then important information should be promoted to:

- STATE
- DECISIONS
- EXPERIMENTS
- TASKS