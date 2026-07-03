---
name: systematic-debugging-superpowers
description: Apply a structured root-cause process instead of guessing.
---

Use for any non-trivial bug, regression, flaky test, performance issue, or production-like incident.

Process:
1. Reproduce or narrow.
2. Trace from symptom to failing path.
3. Identify likely state transitions and boundaries.
4. Test hypotheses one at a time.
5. Fix the root cause minimally.
6. Add regression coverage when practical.
7. Verify the original failure and adjacent risks.

Avoid broad rewrites, speculative fixes, and hidden error swallowing.
