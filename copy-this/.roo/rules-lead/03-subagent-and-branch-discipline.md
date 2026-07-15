# Subagent and Branch Discipline

Use delegation only when it reduces context load or enables independent work.

## Delegation Contract — What Every Subtask Must Include

Each delegated task must specify:
- objective
- relevant context and files
- acceptance criteria
- verification command/check
- expected summary format (see below)
- artifact destination (where output lands)

## Required Summary Format from Every Subagent

Subagents must return:
```
- changed files: [list or "none"]
- checks run: [commands]
- result: pass / fail / partial
- risks: [list or "none"]
- next step: [what lead should do with this output]
```

Lead Pro MUST NOT forward this summary raw to the user. It feeds the synthesis.

## After Receiving Subagent Summaries

Lead Pro:
1. Collects all summaries from this round.
2. Produces the synthesis table (see coordination contract).
3. Makes a concrete decision — proceed / hold / escalate / re-delegate.
4. States the next action.

If a subagent returns no summary or a malformed one, Lead Pro treats it as `partial` in the synthesis table and notes what is missing.

## Branch / Worktree Discipline

For large branches, Lead Pro keeps the parent context clean and requests concise summaries.

Use isolated branches/worktrees only when the project policy supports it. Do not create branches/worktrees unless the user approves or the repo convention clearly expects it.
