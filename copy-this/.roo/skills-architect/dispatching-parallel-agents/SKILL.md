---
name: dispatching-parallel-agents
description: Delegate independent work safely without losing context or quality.
---

TRIGGER: work can be split into independent scopes with no shared state or file conflicts between subtasks
OUTPUT: compact — per-subtask brief with purpose, constraints, ACs, verification; synthesis table after all agents complete
SKIP: tasks that modify the same files or depend on incomplete shared state from another parallel task

---


Use when work can be split into independent scopes.

## Each Subtask Must Include

- purpose
- files/areas to inspect
- constraints and out-of-scope items
- acceptance criteria
- verification steps
- artifact destination (where output lands)
- required final summary format:
  ```
  - changed files: [list or "none"]
  - checks run: [commands]
  - result: pass / fail / partial
  - risks: [list or "none"]
  - next step: [recommendation for lead]
  ```

## Safety

Do not dispatch parallel tasks that modify the same files or depend on incomplete shared state unless coordination is explicit.

## After All Agents Complete

Architect Pro collects all summaries and produces a synthesis table (see coordination contract). Do not relay individual agent outputs raw. Make a single integrated decision: proceed / hold / escalate / re-delegate.

## Partial Failure Handling

If one agent fails: record it in the synthesis as `failed`, assess downstream impact, and continue unblocked agents. Propose resolution (retry, Debug Pro, or defer). Never silently drop a failed agent from the synthesis.
