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

Use Superpowers skills by default: `superpowers:brainstorming` when goal is ambiguous, `superpowers:writing-plans` before large implementation, `superpowers:test-driven-development` when tests are practical, `superpowers:verification-before-completion` before claiming done.
