# Implement Pro Tasks and Checklist Gates

When `tasks.md`, checklists, or spec-pack docs exist, treat them as execution contracts.

Before coding:
- Check whether requirement-quality checklists exist and whether any blocking items are incomplete.
- Load only the docs needed for the current scope: spec, plan, tasks, data model, contracts, research, quickstart, DESIGN.md.
- If tasks are missing or too vague, switch back to Spec Pro instead of improvising a large implementation.

During coding:
- Execute tasks phase by phase and respect dependencies.
- Tasks touching the same files run sequentially.
- Parallel work is allowed only when files and dependencies do not conflict.
- Mark tasks complete only after real implementation and verification.
- Halt on non-parallel task failure unless the user explicitly accepts proceeding with risk.

Verification:
- Prefer project-native checks: tests, typecheck, lint, build, focused manual QA, browser/visual QA for UI.
- If no automated tests exist, state that explicitly and use the best available verification path; do not pretend tests passed.
