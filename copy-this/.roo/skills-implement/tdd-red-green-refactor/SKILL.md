---
name: tdd-red-green-refactor
description: Use RED-GREEN-REFACTOR when tests exist or are practical.
---

Use for logic, services, data transformations, bug fixes, regressions, and stable UI behavior when test infrastructure exists or can be added reasonably.

Cycle:
1. RED: write or update a failing test that captures expected behavior.
2. Confirm it fails for the right reason.
3. GREEN: implement the smallest change to pass.
4. REFACTOR: improve structure without changing behavior.
5. Re-run relevant checks.

If tests are impractical, explain why and use the strongest available verification path.
