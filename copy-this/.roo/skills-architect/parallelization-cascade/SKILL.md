TRIGGER: large separable work — independent modules, multiple research spikes, or separate frontend/backend slices with clear contracts
OUTPUT: detailed — delegation contract per subtask, synthesis table identifying merge conflicts/integration risks after completion
SKIP: shared-file changes with high conflict risk, small edits faster done sequentially, or tasks without acceptance criteria

---

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
- Artifact destination (where output lands).
- Expected summary format:
  ```
  - changed files: [list or "none"]
  - checks run: [commands]
  - result: pass / fail / partial
  - risks: [list or "none"]
  - next step: [recommendation for lead]
  ```

## After Cascade Completes

Architect Pro must:
1. Collect all subtask summaries.
2. Produce a synthesis table (see coordination contract) — not a raw list of summaries.
3. Identify merge conflicts or integration risks across parallel outputs.
4. Make a concrete decision: integrate / hold / re-delegate failed subtasks.
5. State next action with owner and artifact destination.

## Partial Failure Protocol

If a subtask fails: mark `failed` in synthesis, assess whether it blocks integration, and continue unblocked subtasks. Propose retry, Debug Pro route, or deferral. Never drop a failed subtask silently.
