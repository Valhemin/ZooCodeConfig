# Setup Guide — Zoo Pro Setup

Read this file to understand modes, MCP servers, and workflows before using the setup.

## Modes

### 📋 Architect Pro

Use for requirements, specs, clarification, planning, UX/UI docs, architecture, task generation, and consistency analysis.

Best for:
- New feature requirements
- Project/feature spec packs
- Architecture/API/data/UI decisions
- Requirements-quality checklists
- Task plans before implementation
- Read-only analysis across spec/plan/tasks

### ⚒️ Implement Pro

Use for coding and production delivery.

Best for:
- Implementing from spec/task docs
- Refactors, tests, UI polish
- Backend/frontend integration
- Browser testing (Playwright MCP) and visual QA
- Figma-to-code (Figma MCP)

### 🐞 Debug Pro

Use for failures and unexpected behavior.

Best for:
- Failing tests, runtime errors, broken UI
- Performance issues (Chrome DevTools MCP)
- Regressions, flaky behavior
- Click-path audits (state interaction bugs)

## MCP Servers

| MCP | Purpose | Default | API key needed |
|---|---|---|---|
| **context7** | Library/framework docs | enabled | No |
| **agentmemory** | Memory across sessions | enabled | No |
| **tavily** | Web search (articles, issues) | disabled | `TAVILY_API_KEY` |
| **brave-search** | Web search (broad, news) | disabled | `BRAVE_API_KEY` |
| **playwright** | Browser automation, UI testing | disabled | No |
| **chrome-devtools** | Performance, network debug | disabled | No |
| **github** | PR/issue management | disabled | `GITHUB_PERSONAL_ACCESS_TOKEN` |
| **figma** | Figma cloud design access | disabled | No (browser auth) |
| **figma-desktop** | Local Figma Desktop access | disabled | No (app running) |

**Enable/disable**: set `"disabled": false/true` in `.roo/mcp.json`. Keep disabled MCPs off until needed — each adds token overhead.

## Recommended flows

### New project

Architect Pro → Implement Pro → Debug Pro when needed → Architect Pro readiness summary

### Feature with unclear requirements

Architect Pro → clarify critical gaps → plan/research → tasks → consistency analysis → Implement Pro

### Small direct change

Implement Pro directly. Still collects context and verifies.

### Bug

Debug Pro first. Do not use Implement Pro for unknown failures until root cause is clear.

### UI feature with design

Enable Figma MCP → Implement Pro (figma-to-code skill) → enable Playwright MCP → visual QA → ship

### Performance issue

Enable Chrome DevTools MCP → Debug Pro (chrome-devtools-debugging skill) → fix → verify metrics

## Core principles

- **Mode-native**: workflow is encoded in rules, skills, and templates. No slash commands needed.
- **Search-first**: check project patterns and Context7 docs before building custom solutions.
- **MCP-minimal**: enable only what the current task needs, disable after.
- **AgentMemory**: durable engineering context only. Never overrides current code or user instructions.
- **Verify before completion**: every task needs evidence of passing, not just claims.
