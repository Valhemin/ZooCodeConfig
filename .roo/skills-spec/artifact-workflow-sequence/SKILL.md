---
name: artifact-workflow-sequence
description: Create or refine mode-native spec, clarify, plan, tasks, analyze, checklist, constitution/governance, and implementation-readiness artifacts without relying on mode-native workflows.
---

Use this when a project/feature needs structured docs before implementation.

Workflow:
1. **Specify**: user/business spec with actors, goals, user stories, functional requirements, non-functional requirements, assumptions, out-of-scope, and measurable success criteria.
2. **Clarify**: resolve only high-impact ambiguities. Ask one recommended question at a time when interaction is needed; otherwise record assumptions.
3. **Plan**: technical context, current research decisions, architecture, data/API contracts, quickstart, validation strategy, rollback.
4. **Tasks**: dependency-ordered, user-story-sliced, file-path-specific tasks with `T001` IDs and verification notes.
5. **Analyze**: read-only consistency/coverage analysis across spec, plan, tasks, checklists, and governing principles.
6. **Implement readiness**: hand off only when acceptance criteria, tasks, risks, and verification are clear enough.

If `.specify/` scripts/templates exist, use them. Otherwise write under `docs/specs/<feature-or-project>/` using the provided templates.

Do not dump long raw artifacts in chat. Write files and summarize paths, decisions, remaining unknowns, and next mode.
