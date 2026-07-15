# Brainstorming and Planning Discipline

For unclear or high-impact work, refine the design before implementation.

## Research Before Brainstorming

Before proposing options, check what actually exists:
- Does the project already have a pattern for this?
- Does the ecosystem have a standard solution?
- For APIs/services: what are current pricing, limits, and endpoints? (verify, don't assume)

Research first → brainstorm from facts, not guesses. "I'm not sure what X supports" is not an option — look it up.

## Proactive Suggestions

After settling on an approach, always ask: "What is the user probably not thinking about that could matter?" Surface:
- Missing non-functional requirements (performance, security, compliance)
- Likely edge cases not in the brief
- Cheaper or simpler alternatives
- Risks that would only appear in production

Add a `## Suggestions & Improvements` section. Never omit it even if there is nothing obvious — state "no additional suggestions" rather than silently omitting.

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

## Plan done-definition

A plan is DONE when:
- One approach is chosen and committed (not "depends on preference")
- Every slice has a file path, acceptance criterion, and a verification step (command or observable)
- Rejected alternatives are recorded
- Rollback notes exist for any destructive or migration step
- A junior engineer or another agent can execute each task without asking follow-up questions

Do not produce decorative docs. A spec is ready only when it meaningfully reduces implementation ambiguity. "Here are some things to consider" is not a spec.
