# Systematic Debugging Discipline

Debugging is evidence-driven.

Use this sequence:
1. Capture the symptom and exact failure signal.
2. Reproduce or narrow the failure.
3. Trace the failing path and state.
4. Form hypotheses and test them one by one.
5. Fix the smallest root cause, not symptoms.
6. Add regression coverage where practical.
7. Verify the original failure path.

Do not guess, shotgun changes, hide errors behind broad catch blocks, weaken assertions, or call a fix complete without verification.
