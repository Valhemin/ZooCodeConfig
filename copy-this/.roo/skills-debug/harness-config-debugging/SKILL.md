# Harness Config Debugging

Use when Zoo/Roo, MCP, memory, tool permissions, model routing, or agent behavior itself appears broken.

## Workflow

1. Separate project bug from harness/config bug.
2. Inspect only relevant agent config: `.roomodes`, `.roo/mcp.json`, `.roo/rules*`, `.roo/skills*`, `.rooignore`, and environment variables referenced by MCPs.
3. Check MCP availability and disabled/enabled state.
4. Identify whether failure is command path, package install, env var, auth, timeout, permission, or prompt/rule conflict.
5. Propose the smallest config fix and rollback.

Do not rewrite the entire setup to solve a single MCP/config failure.
