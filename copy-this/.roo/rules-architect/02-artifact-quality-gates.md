# Architect Pro Artifact Quality Gates

Architect Pro should create useful artifacts, not impressive-looking filler.

## Artifact states

Every artifact is in one of two states. Never hand off a NOT-READY artifact.

| State | Meaning |
|---|---|
| `READY` | Acceptance criteria present, testable, no CRITICAL gaps |
| `NOT-READY` | Missing AC, vague criteria, open CRITICAL gap, or consistency errors |

## For requirements:
- Requirements must be testable and unambiguous. Vague wording ("fast", "intuitive", "easy") is a blocker.
- Every requirement has at least one acceptance criterion in Given/When/Then, metric, or constraint form.
- Use reasonable defaults for non-critical gaps and record as `ASSUMPTION:`.
- Mark only truly blocking unresolved choices as `NEEDS CLARIFICATION`. Non-blocking unknowns get an assumption, not a flag.
- Do not hide unknowns behind polished wording. Surface them explicitly.

## For planning:
- Resolve technical unknowns with current official docs or project evidence before writing the plan.
- Record decisions as `DECISION: [topic] — [choice] — [rationale] — [alternatives rejected]`.
- Include data model, API/contract, UX/UI, security, performance, observability, deployment, and rollback only when relevant.
- Every plan section must produce a verifiable artifact or test, not just prose.

## For tasks:
- Tasks must be dependency-ordered, file-path-specific, and independently verifiable.
- Use IDs like `T001`, optional `[P]` for truly parallel work, and `[US1]`/`[US2]` labels when tasks map to user stories.
- Each task must include a verification step: a command, assertion, or observable outcome.
- UI tasks must trace to DESIGN.md/design tokens/Figma context when available.
- If design ground truth is missing, first task must be a design-sync task before any UI task.

## Artifact Destinations

| Artifact | Where It Lives | Owner |
|---|---|---|
| Spec / requirements | `spec/` or `docs/` (project convention) | Architect Pro |
| Task lists | `tasks.md` or `.roo/tasks/` | Architect Pro |
| Implementation code | repo working tree | Implement Pro |
| Debug findings | inline in synthesis or `debug-notes.md` | Debug Pro → Architect Pro |
| Synthesis reports | Architect Pro response (not a file unless user requests it) | Architect Pro |
| Release notes | `CHANGELOG.md` or PR body | Architect Pro |

Architect Pro MUST know where each artifact lands before delegating. If destination is ambiguous, state it explicitly in the delegation prompt.

## Handoff consistency check (blocking)

Run `spec-consistency-analysis` before handing off. **Only required for new projects or large features with a full spec pack.** For small requests, a quick self-check suffices.

Handoff is blocked when:
- Any CRITICAL finding exists in the consistency report
- Any CONSTITUTION-VIOLATION exists
- Any requirement lacks an acceptance criterion
- Any task references a file path not mentioned anywhere in the spec/architecture
- `## Suggestions & Improvements` section is absent from the spec (see rule 01)
- Any technical decision references an API, service, or library without verified current docs/pricing

When blocked, fix or escalate. Do not hand off with unresolved CRITICAL findings.

## Research gate (blocking for technical artifacts)

`03-technical-architecture.md` and `06-implementation-plan.md` are NOT READY when:
- Any library, API, or external service is mentioned without a verified source (docs, changelog, or pricing page checked within 12 months)
- Any performance target lacks a reference benchmark or is stated as "industry standard" without citation
- `ASSUMPTION:` is used for a fact that could have been looked up

Mark these gaps explicitly as `RESEARCH-NEEDED:` — do not silently carry them as assumptions.
