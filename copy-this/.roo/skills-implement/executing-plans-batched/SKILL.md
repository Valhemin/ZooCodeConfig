---
name: executing-plans-batched
description: Execute plans in small batches with checkpoints and truthful progress.
---

TRIGGER: implementing from a task list or implementation plan with defined slices and checkpoints
OUTPUT: compact — completed scope with verification status, blocked task with error verbatim, next action
SKIP: exploratory work without a defined plan or task list

---


Use when implementing from tasks or an implementation plan.

Batch execution:
1. Select a coherent slice.
2. Implement only that slice.
3. Self-review for spec compliance and code quality.
4. Run focused checks.
5. Fix failures before moving on.
6. Update task status only after real completion.

If blocked, report ALL of:
- Completed: scopes done, files changed, verification status
- Blocked at: exact task name and the error or missing input verbatim
- Attempted: what was tried
- Next action: one concrete next step

Never return with only "I am blocked." Always deliver the completed portion first.

## API Testing After Backend Slices

After any slice that adds or modifies a backend endpoint or API handler: run `api-testing` skill before moving to the next slice. Default behavior — no user request needed. Skip only for pure frontend slices or explicit "skip tests" instruction.
