# Parallelization Cascade

Use only for large, separable work where parallel subtasks reduce risk or time without creating merge conflicts.

## When to Use

- Independent modules or user stories.
- Multiple research spikes with separate outputs.
- Separate frontend/backend/API/docs slices with clear contracts.
- Large refactors that can be split by directory or boundary.

## When Not to Use

- Shared files with high conflict risk.
- Unknown root-cause debugging.
- Small edits that are faster in one context.
- Tasks lacking acceptance criteria.

## Delegation Contract

Each subtask must include:

- Objective.
- Relevant files and docs.
- Boundaries / files to avoid.
- Acceptance criteria.
- Verification command or manual check.
- Expected summary format.

Subtask summaries must include changed files, checks run, pass/fail, risks, and next action.
