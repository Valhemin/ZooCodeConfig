# Zoo Pro Setup

A drop-in configuration package for Zoo Code / Roo-style coding agents in VS Code.

The goal of this setup is to turn Zoo Code into a high-quality coding agent workflow for many types of projects: starting a new project, writing specs, designing architecture, implementing production-ready features, debugging, self-reviewing, and checking release readiness.

## Structure

```text
.
├── .roomodes
├── .roo/
│   ├── mcp.json
│   ├── rules/
│   ├── rules-spec/
│   ├── rules-implement/
│   ├── rules-debug/
│   ├── rules-lead/
│   ├── skills/
│   ├── skills-spec/
│   ├── skills-implement/
│   ├── skills-debug/
│   └── skills-lead/
├── .rooignore
├── AGENTS.md
├── DESIGN.md
├── templates/
├── MODE_GUIDE.md
├── README_INSTALL.md
├── CHANGELOG.md
└── CORE_EXTRACTION_REPORT.md
```

## Modes

This setup uses 4 main modes:

| Mode             | Role                                                                                                                    |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 📋 Spec Pro      | Creates specs, docs, architecture, requirements, implementation plans, test plans, and risk analysis                    |
| ⚒️ Implement Pro | Implements from specs/tasks, self-reviews each scope, verifies continuously, and aims for production readiness          |
| 🐞 Debug Pro     | Collects context, reproduces issues, identifies root cause, applies the smallest safe fix, and adds regression coverage |
| 🧭 Lead Pro      | Used for larger projects: breaks work into phases, coordinates Spec/Implement/Debug, maintains roadmap and readiness    |

## How to Use in a Project

Extract this setup folder, then copy everything inside it into the root of the project where you want to use it.

After copying, your project root should look like this:

```text
your-project/
├── .roomodes
├── .roo/
├── .rooignore
├── AGENTS.md
├── DESIGN.md
├── templates/
└── ...
```

Then reload VS Code / Zoo Code. No setup command is required.

## Recommended Workflow

### Starting a New Project

```text
Use Lead Pro. Start a new production-ready project: [project description]. Collect context, identify critical unknowns, create a delivery roadmap, and delegate Spec Pro to produce the first spec pack before implementation.
```

### Creating a Feature Spec

```text
Use Spec Pro. Create a production-ready spec pack for [feature]. Clarify only critical gaps, research current official docs when uncertain, create requirements, architecture, tasks, checklist, and consistency analysis.
```

### Implementing a Feature

```text
Use Implement Pro. Implement docs/specs/[feature]/10-tasks.md scope by scope. Self-review each scope, verify with project-native checks, mark tasks done only after actual completion, and continue until production-ready or I stop you.
```

### Debugging an Issue

```text
Use Debug Pro. Reproduce or narrow the issue, identify root cause with evidence, fix the smallest safe scope, add regression coverage where practical, and verify.
```

## Core Principles

* Quality-first, not minimal-answer-first.
* Collect enough context before changing code.
* Do not fake test/build/lint results.
* Do not claim production readiness without verification.
* Do not perform broad rewrites unless they are necessary.
* Do not add dependencies without a clear reason.
* When unsure about an API, library, or framework behavior, research the latest official source.
* UI/web work should rely on `DESIGN.md`, design tokens, visual QA, accessibility, and responsive behavior.
* Tasks should include clear acceptance criteria, file paths, dependencies, and verification steps.
* Implement in small scopes, self-review after each scope, and avoid deferring all review until the end.

## MCP

Project-level MCP configuration lives at:

```text
.roo/mcp.json
```

Keep MCP usage minimal by default to reduce token cost and avoid unnecessary tool noise.

Common MCP servers:

* `context7`: current, version-specific API documentation.
* `fetch`: URL reading and web research.
* `sequential-thinking`: multi-step reasoning support.
* `playwright`: visual QA and UI testing when enabled.
* `figma`: design context when the project uses Figma.
* `serena`: semantic code navigation for large repositories.
* `github` / `gitlab`: issues, PRs, CI, and repository operations when needed.

Enable only the MCP servers that are actually useful for the project.

## What to Commit

Recommended to commit:

```text
.roomodes
.roo/
.rooignore
AGENTS.md
DESIGN.md
templates/
MODE_GUIDE.md
README_INSTALL.md
CHANGELOG.md
CORE_EXTRACTION_REPORT.md
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

This is a generic setup for many project types. It is not tied to a specific team, framework, or product.

For project-specific conventions, update `AGENTS.md`, `DESIGN.md`, `.roo/rules-*`, or `.roo/skills-*`.
