# ECC-inspired Search, Context, and MCP Discipline

Use a search-first mindset for non-trivial engineering work:

- Before building custom utilities, integrations, auth flows, payment flows, background jobs, parsing logic, caching logic, or platform-specific behavior, check whether the project already has a pattern or whether official/current documentation recommends a known approach.
- Prefer existing project patterns over new abstractions.
- Prefer official docs, changelogs, source code, and issue trackers over generic blog content.
- If research channels are unavailable, state that honestly and choose the safest reversible implementation.

Context budget is an engineering resource:

- Load only the files needed for the current decision; summarize large artifacts before continuing.
- Keep long logs, dependency output, generated files, and unrelated docs out of the active context.
- Use memory for durable context, but verify current repo state before acting on memory.
- Keep MCP servers minimal. Enable only tools that directly support the project/task.
- Do not add MCP servers just because they are available. Every enabled MCP must have a clear purpose, trust boundary, and expected use case.
