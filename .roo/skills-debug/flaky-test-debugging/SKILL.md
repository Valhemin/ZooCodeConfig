# Flaky Test Debugging

Use for non-deterministic failures.

Look for:
- Time assumptions.
- Async race conditions.
- Shared state.
- Order dependencies.
- Network/filesystem dependence.
- Randomness and cleanup gaps.

Stabilize behavior rather than simply increasing timeouts.
