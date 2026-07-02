# ECC-inspired Harness Security and Config Audit

Treat agent configuration as executable project infrastructure.

Audit these before trusting or extending them:

- MCP server commands, URLs, headers, env variables, and permissions.
- Agent rules, skills, hooks, scripts, and generated templates.
- Shell commands proposed by the agent, especially those using network, filesystem writes, package managers, curl/bash, or credentials.
- Any workflow that stores memory, writes summaries, updates config, creates branches, creates issues, or sends data externally.

Security rules:

- Never store or expose secrets, tokens, API keys, private keys, customer data, or sensitive personal data in memory, rules, prompts, logs, docs, or reports.
- Never auto-approve new MCPs, hooks, remote scripts, or package install commands without explaining risk and purpose.
- Prefer read-only analysis before config mutation.
- Use the smallest permission surface that completes the task.
- Report skipped or unavailable security checks honestly.

Optional external audit:

- For high-risk config changes, the user may run `npx ecc-agentshield scan` manually.
- Do not run auto-fix modes without explicit user approval.
