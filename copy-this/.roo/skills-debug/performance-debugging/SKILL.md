TRIGGER: specific slow behavior is reported or measured — slow page load, API response, renders, or test suite with a concrete symptom
OUTPUT: compact — baseline measured, hot paths inspected with cost, bottleneck identified, before/after numbers after fix
SKIP: without a concrete measured symptom; do not trigger automatically or optimize without a baseline

---

# Performance Debugging

## When to Use

Use when: a performance problem is reported or measured — slow page load, slow API response times, slow renders, slow test suite, high CPU/memory under load. Not triggered automatically. Requires a concrete symptom to investigate.

Use for slow behavior — slow page loads, slow API calls, slow renders, slow tests.

## Process

1. Define the symptom precisely: what is slow, by how much, under what conditions.
2. Measure — get a baseline number before touching anything (time, flame chart, query plan).
3. Identify likely hot paths — don't guess, profile or instrument.
4. Narrow to the bottleneck — N+1 queries, unnecessary re-renders, blocking I/O, large payloads, missing indexes.
5. Patch the narrowest root cause only.
6. Measure again — confirm improvement with numbers.

Do not optimize without a baseline. Do not rewrite broad scope to solve a narrow bottleneck.

## Partial Findings Rule

If bottleneck is unconfirmed, still report:
- Baseline metric gathered.
- Hot paths inspected and their measured cost.
- Leading candidate with supporting data.
- Next measurement step.

Never return "it might be slow because X." Show the measurement.

## Output Contract

Every response must include:
- **Symptom**: what is slow, measured baseline.
- **Paths inspected**: each with measured cost or "unable to measure — reason."
- **Bottleneck identified / best hypothesis**: with evidence.
- **Fix applied** (if any): change + before/after numbers.
- **Next step** if not resolved.
