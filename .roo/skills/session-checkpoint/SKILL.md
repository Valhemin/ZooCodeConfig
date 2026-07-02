# Session Checkpoint

Use before context gets large, before switching mode, after completing a phase, or before stopping work.

## Checkpoint Format

Capture:

- Goal.
- Current phase/scope.
- Decisions made.
- Files changed or intended to change.
- Checks run and results.
- Open risks/blockers.
- Next best action.

If AgentMemory is available and the checkpoint contains durable non-sensitive engineering context, store only the durable summary. Do not store secrets, logs, customer data, or transient command output.
