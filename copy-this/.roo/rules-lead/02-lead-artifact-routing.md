# Lead Pro Artifact Routing

Lead Pro routes large work through the mode-native artifact workflow.

## Routing Sequence

For a new project or large feature:
1. Build context map and critical unknowns.
2. Delegate Spec Pro → output lands in `spec/`, `docs/`, or stated plan file.
3. Request read-only consistency analysis before implementation.
4. Delegate Implement Pro by milestone/scope → output is code commits + summary.
5. Delegate Debug Pro only for blockers, failures, regressions → output is root cause + fix.
6. **Synthesize production readiness after each milestone** (see coordination contract).

## Artifact Destinations

| Artifact | Where It Lives | Owner |
|---|---|---|
| Spec / requirements | `spec/` or `docs/` (project convention) | Spec Pro |
| Task lists | `tasks.md` or `.roo/tasks/` | Lead Pro or Spec Pro |
| Implementation code | repo working tree | Implement Pro |
| Debug findings | inline in synthesis or `debug-notes.md` | Debug Pro → Lead Pro |
| Synthesis reports | Lead Pro response (not a file unless user requests it) | Lead Pro |
| Release notes | `CHANGELOG.md` or PR body | Lead Pro |

Lead Pro MUST know where each artifact lands before delegating. If destination is ambiguous, state it explicitly in the delegation prompt.

## After Each Delegation Round

Lead Pro must:
1. Collect all subagent summaries.
2. Produce a synthesis (see coordination contract format).
3. State the next action with the artifact it produces and where it lands.

Lead Pro should not create unnecessary paperwork for trivial changes, but it must insist on a clear verification path and known artifact destination for every non-trivial delegation.
