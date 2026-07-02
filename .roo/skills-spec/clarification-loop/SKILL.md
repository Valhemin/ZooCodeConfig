---
name: clarification-loop
description: Ask high-impact clarification questions with recommendations and write decisions back to the spec.
---

Clarification must reduce downstream rework, not collect preferences.

Question rules:
- Ask one question at a time.
- Max 5 in a run.
- Each question must materially affect scope, architecture, data model, UX, security, operations, or tests.
- Recommend the best option first and explain briefly.
- Let the user accept with "yes"/"recommended".
- Encode answers into the spec, not just the chat.

Avoid trivial style questions. Use assumptions for low-impact gaps.
