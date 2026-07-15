# Zoo Pro Setup Final

A drop-in configuration package for Zoo Code / Roo-style coding agents in VS Code.

This setup is designed for multi-project use. It keeps the workflow mode-native: choose a mode and work normally. There are no slash commands, no global install files, and no project-specific assumptions.

## Drop-in Usage

1. Extract this folder.
2. Copy everything inside this folder into the root of the project you want to use it with.
3. Reload VS Code / Zoo Code.
4. Select one of the three modes.

After copying, your project root should contain:

```text
.roomodes
.roo/
.rooignore
DESIGN.md          (optional — copy from .roo/templates/DESIGN.md.template for UI projects)
SETUP_ROO_CODE.md
```

No setup command is required for the Zoo configuration itself.

## Modes

| Mode | Use for |
| --- | --- |
| 📋 Architect Pro | Product requirements, specs, architecture, UX/UI docs, implementation plans, task breakdowns, checklists, and consistency analysis |
| ⚒️ Implement Pro | Production-ready implementation from specs/tasks, scope-by-scope delivery, self-review, verification, and docs updates |
| 🐞 Debug Pro | Evidence-driven reproduction, root cause analysis, minimal fixes, regression coverage, and verification |

## AgentMemory

This final setup replaces the default memory MCP with AgentMemory.

Project MCP config lives at:

```text
.roo/mcp.json
```

The included AgentMemory MCP entry uses:

```json
{
  "command": "npx",
  "args": ["-y", "@agentmemory/mcp"],
  "env": {
    "AGENTMEMORY_URL": "${env:AGENTMEMORY_URL}",
    "AGENTMEMORY_SECRET": "${env:AGENTMEMORY_SECRET}"
  }
}
```

For the full memory server, run AgentMemory separately in a terminal:

```bash
npx @agentmemory/agentmemory
```

If `AGENTMEMORY_URL` is not set, the MCP shim falls back to `http://localhost:3111`.

Recommended environment variables:

```bash
export AGENTMEMORY_URL="http://localhost:3111"
export AGENTMEMORY_SECRET=""
```

Memory rules are strict:

- Do not store secrets, tokens, passwords, API keys, private keys, customer data, or sensitive personal data.
- Store only durable engineering context: decisions, conventions, gotchas, recurring bugs, handoff summaries, and release notes.
- Treat memory as a hint, not a source of truth. Verify current code/docs before acting on it.

## Superpowers Methodology

This setup does not install the upstream Superpowers plugin directly. Instead, it ports the useful methodology into Zoo-native rules and skills:

- brainstorming before code when the goal is unclear
- writing concrete plans with exact files and verification
- executing in small batches with checkpoints
- TDD when tests exist or are practical
- systematic debugging
- verification before completion
- code review between implementation slices
- safe delegation for large tasks
- branch/readiness closure discipline

This keeps the setup generic and mode-native.


## ECC-inspired hardening

This setup selectively ports the strongest generic ideas from ECC without installing ECC itself:

- search-first engineering before custom code
- context-window and MCP budget discipline
- harness/config security audit mindset
- skill stocktake and setup hygiene
- quality gates before completion claims
- session checkpoints and durable handoff summaries
- build-fix loops for failing checks
- parallelization/worktree discipline for large separable work

It intentionally does **not** include ECC commands, hooks, dashboard, full agent catalog, full MCP catalog, or all ECC skills. The setup remains Zoo mode-native and drop-in.

### ECC command assessment

ECC has many useful commands, but most should not be copied into this setup because this setup is mode-native. The useful command ideas have been converted into skills/rules instead:

- `quality-gate` → `.roo/skills/quality-gate/`
- `build-fix` → `.roo/skills-implement/build-fix-loop/`
- `code-review` / `review-pr` → existing review/self-review skills
- `security-scan` / `harness-audit` → config/security audit skills
- `checkpoint`, `save-session`, `resume-session` → AgentMemory + session checkpoint skills
- `skill-health` / `skill-create` → skill stocktake skill
- `multi-*`, `orch-*`, `epic-*` → Architect Pro decomposition and parallelization skills

Language-specific commands such as `react-build`, `go-test`, `python-review`, etc. are intentionally not included by default. Add stack-specific skills only inside the project that needs them.

## Recommended Workflow

### Start a new project

```text
Use Architect Pro. Start a new production-ready project: [project description]. Collect context, identify critical unknowns, create a delivery roadmap, and delegate Architect Pro to produce the first spec pack before implementation.
```

### Create a feature spec

```text
Use Architect Pro. Create a production-ready spec pack for [feature]. Clarify only critical gaps, research current official docs when uncertain, create requirements, architecture, tasks, checklist, and consistency analysis.
```

### Implement a feature

```text
Use Implement Pro. Implement docs/specs/[feature]/10-tasks.md scope by scope. Self-review each scope, verify with project-native checks, mark tasks done only after actual completion, and continue until production-ready or I stop you.
```

### Debug an issue

```text
Use Debug Pro. Reproduce or narrow the issue, identify root cause with evidence, fix the smallest safe scope, add regression coverage where practical, and verify.
```

## Commit Guidance

Commit these files if you want the agent setup to travel with the repo:

```text
.roomodes
.roo/
.rooignore
SETUP_ROO_CODE.md
DESIGN.md          (if created for the project)
```

Do not commit:

```text
.env
.env.*
API keys
local credentials
node_modules/
build output
cache
logs
local databases
```

## Notes

- This setup is generic and can be used across many project types.
- Project-specific conventions should go into `AGENTS.md`, `DESIGN.md`, `.roo/rules-*`, or `.roo/skills-*`.
- Keep MCP servers minimal. Enable only what the project actually needs.
