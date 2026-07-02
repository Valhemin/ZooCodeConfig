# Mode-Native Artifact Workflow

This setup does not rely on mode-native workflows. Use modes, rules, skills, and templates directly.

When a request needs structured delivery, use this artifact sequence:

1. **Specify** — capture user value, scope, assumptions, measurable success criteria, and testable requirements.
2. **Clarify** — ask only high-impact questions that materially change scope, architecture, data model, UX, security, operations, or validation.
3. **Plan** — resolve technical unknowns with current research, document decisions, architecture, data/API contracts, quickstart, verification, and rollback.
4. **Tasks** — create dependency-ordered tasks that are specific enough for an AI agent or developer to execute without hidden context.
5. **Analyze** — run a read-only consistency pass across spec, plan, tasks, checklists, and governing principles before implementation.
6. **Implement** — execute one coherent scope at a time, self-review, verify, and only mark done when actually complete.
7. **Review** — produce evidence-based findings with severity, verification status, fix guidance, and honest readiness.

If a project already has `.specify/` scripts/templates, prefer them. If not, use `docs/specs/<feature-or-project>/` and this bundle's templates.

Do not use command names as the workflow source of truth. The workflow belongs to the selected mode and relevant skills.
