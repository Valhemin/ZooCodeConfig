---
name: agentmemory-recall
description: Recall durable project context from AgentMemory, then verify it against current repo state.
---

Use when the user references prior work, project conventions, recurring bugs, earlier decisions, or when starting a long-running task in a repo that may have stored memory.

Protocol:
1. Search memory for project name, feature name, architecture area, or error signature.
2. Treat results as hints, not truth.
3. Verify against current files, docs, tests, and user instructions.
4. Mention only decision-relevant memory in the working summary.

Never let memory override current code or explicit user direction.
