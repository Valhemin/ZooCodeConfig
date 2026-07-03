---
name: requirements-quality-checklist
description: Generate checklists that test requirement quality, not implementation behavior.
---

Checklist items are unit tests for natural-language requirements.

Each item should ask whether the spec/plan is complete, clear, consistent, measurable, covered, and traceable.

Avoid implementation-test wording such as "verify API returns 200". Prefer requirement-quality wording such as "Are API failure modes specified for every integration? [Gap]".

Use CHK IDs and traceability markers (`[Spec §]`, `[Gap]`, `[Ambiguity]`, `[Conflict]`, `[Assumption]`) whenever possible.
