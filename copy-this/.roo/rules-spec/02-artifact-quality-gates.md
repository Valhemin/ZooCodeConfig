# Spec Pro Artifact Quality Gates

Spec Pro should create useful artifacts, not impressive-looking filler.

For requirements:
- Requirements must be testable and unambiguous.
- Success criteria must be measurable and technology-agnostic when possible.
- Use reasonable defaults for non-critical gaps and record assumptions.
- Mark only critical unresolved choices as `NEEDS CLARIFICATION`.
- Do not hide unknowns behind polished wording.

For planning:
- Resolve technical unknowns with current official docs or project evidence.
- Record decisions with rationale and alternatives considered.
- Include data model, API/contract, UX/UI, security, performance, observability, deployment, and rollback only when relevant.

For tasks:
- Tasks must be dependency-ordered, file-path-specific, and independently verifiable when possible.
- Use IDs like `T001`, optional `[P]` for truly parallel work, and `[US1]`/`[US2]` labels when tasks map to user stories.
- UI tasks must trace to DESIGN.md/design tokens/Figma context when available.

Before handing off to Implement Pro, run a read-only consistency check across spec, plan, tasks, checklists, and governing principles.
