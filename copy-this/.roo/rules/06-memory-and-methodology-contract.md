# Memory and Methodology Contract

Memory is a tool, not a source of truth.

Use AgentMemory to recall and store stable engineering context only:
- project conventions and architecture decisions
- accepted tradeoffs and rejected alternatives
- recurring bugs, gotchas, and debugging notes
- durable user/project preferences
- handoff summaries and release notes

Before acting on memory, verify the current repository files and docs. Code, tests, docs, and user instructions override memory.

Never store secrets, credentials, API keys, tokens, private keys, personal sensitive data, customer data, or unreleased confidential business data unless the user explicitly asks and the storage location is approved.

Use Superpowers-style discipline by default:
- brainstorm before coding when the goal is ambiguous
- write plans with exact files, acceptance criteria, and verification
- execute in small slices with checkpoints
- prefer TDD when the project has tests or tests are practical
- verify before completion; evidence beats claims
- reduce complexity; do not over-engineer
