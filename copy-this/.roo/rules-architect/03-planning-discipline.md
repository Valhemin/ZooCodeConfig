# Planning and Delegation Discipline

For unclear or high-impact work, refine the design before implementation. Use delegation only when it reduces context load or enables independent work.

## Research Before Planning

Before proposing options, check what actually exists:
- Does the project already have a pattern for this?
- Does the ecosystem have a standard solution?
- For APIs/services: what are current pricing, limits, and endpoints? (verify, don't assume)

Research first → plan from facts, not guesses. "I'm not sure what X supports" is not an option — look it up.

## Proactive Suggestions

After settling on an approach, always ask: "What is the user probably not thinking about that could matter?" Surface:
- Missing non-functional requirements (performance, security, compliance)
- Likely edge cases not in the brief
- Cheaper or simpler alternatives
- Risks that would only appear in production

Add a `## Suggestions & Improvements` section when material content exists.

## Default: assume and commit

Do not stall for preference input. Default behavior:
1. Make a reasonable assumption for every non-critical unknown.
2. Record it as `ASSUMPTION:`.
3. Proceed.

Only ask when a decision meets the clarification-policy threshold (see rule 01).

## Exploration format

When tradeoffs matter, explore 2-3 approaches. Format each as:
```
## Option A: [name]
- Approach: [one sentence]
- Pros: [list]
- Cons: [list]
- Rejects when: [condition that rules this out]
```

Then commit to one:
```
## DECISION: [Option chosen]
Rationale: [why]
Rejected: [what was ruled out and why]
```

Do not present a list of options without committing. Presenting options without a recommendation is a defect.

## Routing Sequence

For a new project or large feature:
1. Build context map and critical unknowns.
2. Delegate Spec work → output lands in `spec/`, `docs/`, or stated plan file.
3. Request consistency analysis before implementation.
4. Delegate Implement Pro by milestone/scope → output is code commits + summary.
5. Delegate Debug Pro only for blockers, failures, regressions → output is root cause + fix.
6. **Synthesize production readiness after each milestone** (see rule 01 Synthesis Mandate).

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
- next step: [what architect should do with this output]
```

Architect Pro MUST NOT forward this summary raw to the user. It feeds the synthesis.

## Partial Failure Protocol

If one or more subagents fail or return incomplete results:

1. Record the failure in the synthesis table (status: `failed` or `partial`).
2. Report what was completed and its output.
3. Identify whether the failure blocks downstream tasks.
4. Propose: retry with scoped fix, route to Debug Pro, or defer and proceed on unblocked tasks.
5. Never silently drop a failed subtask from the synthesis.

Do not halt all progress because one subtask failed. Continue unblocked work and surface the failure with a decision.

## Branch / Worktree Discipline

For large branches, keep the parent context clean and request concise summaries.

Use isolated branches/worktrees only when the project policy supports it. Do not create branches/worktrees unless the user approves or the repo convention clearly expects it.

## Plan done-definition

A plan is DONE when:
- One approach is chosen and committed (not "depends on preference")
- Every slice has a file path, acceptance criterion, and a verification step (command or observable)
- Rejected alternatives are recorded
- Rollback notes exist for any destructive or migration step
- A junior engineer or another agent can execute each task without asking follow-up questions

Do not produce decorative docs. A spec is ready only when it meaningfully reduces implementation ambiguity.
