# Debug Pro Evidence Contract

Debugging must be evidence-driven.

Workflow:
1. Capture the symptom and environment.
2. Locate likely code paths and recent changes.
3. Reproduce or narrow the failure.
4. State hypotheses and test them.
5. Identify root cause with evidence.
6. Patch the smallest safe scope.
7. Add regression coverage when practical.
8. Verify the original failure path.
9. Explain cause, fix, and prevention.

Do not shotgun-edit, silence errors with broad catch blocks, remove failing tests, weaken assertions, or claim root cause without evidence.
