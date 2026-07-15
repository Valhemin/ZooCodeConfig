---
name: systematic-debugging-superpowers
description: Entry-point orchestrator — triage symptom, select the right debug skill, then apply it.
---

TRIGGER: symptom is unclear, the right debug skill is unknown, or this is the first debug invocation with no prior investigation
OUTPUT: compact — triage result with category, selected skill routed to, then that skill's output
SKIP: when the debug category is already known — go directly to the specific skill instead

---


## When to Use

Use THIS skill when the symptom is unclear or the right debug skill is unknown. It triages first, then routes to the specific skill. Do NOT use as a replacement for a specific skill once the category is known.

Trigger patterns:
- "Something is broken" with no further detail.
- Symptom spans multiple categories (e.g., intermittent AND environment-specific).
- First debug invocation on a bug with no prior investigation.

For a known category, go directly: `root-cause-debugging`, `flaky-test-debugging`, `memory-leak-debugging`, `concurrency-debugging`, `network-api-debugging`, `environment-config-debugging`, `performance-debugging`.

## Triage Step (always first)

Before applying any process, answer:
1. Is failure consistent or intermittent? → intermittent: `flaky-test-debugging` or `concurrency-debugging`
2. Is failure environment-specific? → `environment-config-debugging`
3. Is memory growing? → `memory-leak-debugging`
4. Is it slow (not broken)? → `performance-debugging`
5. Is it an HTTP/API failure? → `network-api-debugging`
6. None of above → `root-cause-debugging`

State the triage result and selected skill before proceeding.

## Process

1. Reproduce or narrow — confirm exact failure signal.
2. Trace from symptom to failing path.
3. Identify likely state transitions and boundaries.
4. Test hypotheses one at a time — each gets a verdict: confirmed / ruled out / inconclusive.
5. Fix the root cause minimally.
6. Add regression coverage when practical.
7. Verify the original failure and adjacent risks.

## Partial Findings Rule

If root cause is unknown after investigation, still report:
- What was confirmed (exact symptoms, logs, state).
- What was ruled out and why.
- Best current hypothesis with evidence.
- Single most diagnostic next step.

Never end a response with only "I need more info." Synthesize first.

## Output Contract

Every response must include all of:
1. **Failure signal** — exact error, behavior, or metric.
2. **Evidence gathered** — what was inspected.
3. **Hypotheses** — tested and their results.
4. **Best current hypothesis** — with supporting evidence.
5. **Next action** — most diagnostic step, or "fixed — verified."
6. **Fix + verification** (if applied).

Avoid broad rewrites, speculative fixes, and hidden error swallowing.
