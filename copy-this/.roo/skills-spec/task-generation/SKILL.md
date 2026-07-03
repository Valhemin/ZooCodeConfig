---
name: task-generation
description: Generate actionable dependency-ordered tasks from specs/plans for AI implementation.
---

Use when creating `tasks.md` or an implementation task list.

Task quality contract:
- Tasks must be immediately executable without hidden context.
- Organize by user story or independently deliverable slice.
- Each user story/slice should be independently implementable and verifiable where possible.
- Use format: `- [ ] T001 [P?] [US?] Action with exact file path`.
- `[P]` means parallelizable only when tasks touch different files and have no dependency conflict.
- Use `[US1]`, `[US2]`, etc. only when tied to user-story phases.
- Include setup/foundational tasks before story tasks.
- Include polish/cross-cutting tasks at the end.
- Include verification task(s) appropriate for the project, not fake test tasks.

For UI tasks:
- Trace to DESIGN.md, design tokens, Figma context, screenshots, or explicit visual spec.
- Include states: loading, empty, error, disabled, responsive, accessibility.
- If design ground truth is missing, add a design-sync/spec clarification task first.
