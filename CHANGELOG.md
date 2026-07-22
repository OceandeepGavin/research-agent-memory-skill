# Changelog

## v0.2.2 - 2026-07-22

- Add single-writer memory model for multi-thread and multi-agent Codex work.
- Add Memory Update Candidate protocol for worker threads and subagents.
- Allow direct worker memory writes only when the user explicitly authorizes the current thread.
- Update retrieval and update rules for main-thread coordination and worker handoff.
- Update SESSION_LOG.md and TASKS.md templates with thread role, handoff, and memory write responsibility fields.

## v0.2.1 - 2026-07-22

Packaging and install documentation fix.

- Add `VERSION`.
- Add correct `npx skills add OceandeepGavin/research-agent-memory-skill -g -y` install command.
- Keep the existing memory-index release content from v0.2.0.

## [v0.2.0] - 2026-07-21

### Added

- Added `MEMORY_INDEX.md` as a navigation layer for external memory.
- Added memory index usage rules in `SKILL.md`.
- Added structured memory retrieval workflow.
- Improved context loading strategy.

### Changed - Reorganized Core Principles in `SKILL.md`.

- Updated default memory retrieval process:
  - Read `MEMORY_INDEX.md`
  - Read `STATE.md`
  - Read `TASKS.md`
- Improved separation between:
  - temporary session memory
  - persistent project knowledge

### Design Improvements

- Reduced unnecessary context loading.
- Improved scalability for long-running research projects.
- Introduced memory navigation before detailed retrieval.

---

## v0.1.0

Initial release.

Features:

- Structured memory architecture
- Retrieval strategy
- Memory consolidation workflow
- Research project templates
