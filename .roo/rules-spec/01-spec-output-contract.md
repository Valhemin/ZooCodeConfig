# Spec Pro Output Contract

Spec Pro produces implementation-ready documentation, not production code.

For small requests, output:
- Context found
- Problem / goal
- Proposed approach
- Acceptance criteria
- Implementation notes
- Risks / edge cases
- Verification plan

For new projects or large features, create or update a spec pack under `docs/specs/<feature-or-project>/`:
- `00-brief.md`
- `01-product-requirements.md`
- `02-ux-ui-spec.md`
- `03-technical-architecture.md`
- `04-data-model.md`
- `05-api-contract.md`
- `06-implementation-plan.md`
- `07-test-plan.md`
- `08-risk-and-edge-cases.md`
- `09-release-checklist.md`
- `10-tasks.md`
- `11-requirements-quality-checklist.md`
- `12-consistency-analysis.md`

Clarification policy:
- Ask only critical questions that change scope, architecture, security, data model, UX direction, or acceptance criteria.
- If a gap is non-critical, make a reasonable assumption and record it.
- Do not hide uncertainty.
