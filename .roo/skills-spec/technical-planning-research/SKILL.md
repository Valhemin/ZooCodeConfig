---
name: technical-planning-research
description: Resolve technical unknowns and produce implementation plans with decisions, rationale, alternatives, contracts, and validation.
---

Use before implementation when architecture, stack, integration, data model, or API behavior is unclear.

Process:
1. Fill technical context from repo evidence and user requirements.
2. Mark true unknowns as `NEEDS CLARIFICATION` only when they block a safe plan.
3. For library/API/runtime decisions, research current official docs, release notes, source, or issue trackers.
4. For each decision, document:
   - Decision
   - Rationale
   - Alternatives considered
   - Risks/trade-offs
   - Verification path
5. Produce only relevant artifacts: `research.md`, `data-model.md`, `contracts/`, `quickstart.md`, `test-plan.md`, `rollback.md`.
6. Re-check governing principles and production-readiness gates after design.
