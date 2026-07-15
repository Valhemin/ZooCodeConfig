TRIGGER: spec or plan exists and must be split into independently delegatable subtasks spanning 2+ modes
OUTPUT: detailed — subtasks ordered by dependency, each with goal, context, constraints, ACs, verification, artifact destination
SKIP: small single-mode tasks that don't need decomposition; use project-kickoff if no spec exists yet

---

# Lead Decomposition

## When to Use

- A spec or plan exists and must be split into independently delegatable subtasks.
- Work spans 2+ modes (e.g., Spec → Implement → Debug) and needs explicit ordering.
- A feature is too large to delegate as a single task.
- User says: "Break this into tasks", "Plan the implementation of [X]", "Decompose [spec/feature]".

Use `project-kickoff` first if no spec exists yet.

## Subtask Requirements

Split into subtasks that are:
- Independently understandable.
- Independently verifiable.
- Ordered by dependency.
- Small enough to complete without flooding context.

Each subtask must include: goal, context, constraints, acceptance criteria, verification, and artifact destination.

## After Decomposition

Before delegating, Architect Pro states:
- How many subtasks, in what order.
- What each subtask produces and where it lands.
- Which subtasks can run in parallel vs. must be sequential.
- What the synthesis will look like after all subtasks complete.

## After Subtasks Return

Architect Pro collects results and produces a synthesis (see coordination contract). Does not forward individual subtask outputs raw. Makes a decision. States next action.

## Failure Handling

If a subtask fails: record in synthesis as `failed` or `partial`, check downstream dependency impact, propose resolution, continue unblocked subtasks.
