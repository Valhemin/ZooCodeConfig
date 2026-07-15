TRIGGER: creating subtasks to delegate to Spec Pro, Implement Pro, or Debug Pro with a structured delegation prompt
OUTPUT: compact — delegation prompt with objective, context, constraints, ACs, verification, artifact destination, summary format
SKIP: tasks handled entirely within the current mode without delegation needed

---

# Subagent Delegation

Use when creating subtasks.

## Mode Selection

- Architect Pro: requirements, docs, architecture, UX, API/data planning.
- Implement Pro: scoped implementation and tests.
- Debug Pro: failing tests, runtime errors, unknown breakages.

## Delegation Prompt Must Include

1. Objective (one sentence).
2. Relevant files and context.
3. Constraints and out-of-scope items.
4. Acceptance criteria.
5. Verification command or manual check.
6. Artifact destination (where the output should land).
7. Required summary format:
   ```
   - changed files: [list or "none"]
   - checks run: [commands]
   - result: pass / fail / partial
   - risks: [list or "none"]
   - next step: [recommendation for lead]
   ```

## After Collecting Summaries

Do not relay summaries to the user raw. Feed them into the Architect Pro synthesis (see coordination contract). Make a decision. State the next action.

## Partial Failure Handling

If a subagent fails or returns incomplete output:
- Mark it `partial` or `failed` in the synthesis table.
- Determine if it blocks downstream tasks.
- Propose: retry / route to Debug Pro / defer and proceed on unblocked work.
