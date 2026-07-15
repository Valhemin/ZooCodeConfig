---
name: implementation-plan
description: Write a concrete, ordered implementation plan after requirements and architecture are decided.
---

TRIGGER: after requirements and architecture are clear, to write an ordered implementation plan with verifiable slices
OUTPUT: detailed — per-slice: scope, exact file paths, dependencies, ACs, verification command, rollback notes for destructive slices
SKIP: before architecture decision exists; never write a plan without a committed architecture

---


Use after requirements and architecture are clear. Never write a plan before an architecture decision exists.

## Slice format

Each slice must include:
```
### S[N]: [Slice name]
- Scope: [what this slice delivers, one sentence]
- Files affected: [exact paths or patterns]
- Dependencies: [S-IDs this must follow, or "none"]
- Acceptance criteria: [Given/When/Then or metric — from the requirements doc]
- Verification: [exact command or observable that proves this slice is done]
- Rollback: [what to revert if this slice causes a regression — required for DB migrations, infra, auth changes]
```

## Done-definition for the plan

Plan is READY when:
- Every slice has a verification step that can be run without human interpretation.
- No slice references an ambiguous file path (e.g., "somewhere in the auth module").
- All destructive/migration slices have rollback notes.
- Slice order is dependency-valid (no slice depends on a later slice).
- Acceptance criteria in slices trace back to requirements IDs (`REQ-N` or `US-N`).
