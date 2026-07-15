# Debug Pro Evidence Contract

Debugging must be evidence-driven.

## Workflow

Use the `superpowers:systematic-debugging` skill for the full evidence-driven workflow.

## Partial Findings Rule

If root cause cannot be fully determined yet, **still report what was found**:
- What symptoms were confirmed.
- Which hypotheses were ruled out and why.
- Which path is most likely and what evidence supports it.
- What specific next step would narrow it further.

**Never**: return "need more information" as the entire response without reporting current evidence.

## Output Contract

Every debug response must produce, at minimum:

1. **Symptom confirmed** — exact error, stack, or observed behavior.
2. **Evidence gathered** — logs, diffs, code paths inspected.
3. **Hypotheses tested** — each with result (confirmed / ruled out / inconclusive).
4. **Best current hypothesis** — even if unproven, with supporting evidence.
5. **Next action** — the single most diagnostic step remaining (or "none — fixed").
6. **Fix applied** (if applicable) — minimal change with verification result.

## Verification Scale

Scale verification to fix size — do not run full build/test suite for every change:

| Fix size | Verification |
|---|---|
| Single-line / trivial (typo, missing null check, obvious logic fix) | Read the changed lines, confirm logic correct. No build needed. |
| Small (1–3 functions, isolated change) | Run the single failing test or directly test the affected path only. |
| Medium (multiple files, data flow change) | Run affected test suite or the specific test file. |
| Large (cross-cutting, auth, migration, config) | Full build + full test suite required. |

Never run `npm run build` or full test suite for a one-line bug fix. Match cost to impact.

If root cause is unknown: still produce items 1–5. Never omit. Never return only a question.

## Prohibitions

Do not shotgun-edit, silence errors with broad catch blocks, remove failing tests, weaken assertions, or claim root cause without evidence.

Do not defer entirely to the user when partial findings exist — synthesize what is known and give a best-hypothesis path forward.
