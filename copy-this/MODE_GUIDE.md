# Mode Guide — Zoo Pro Setup

## Daily modes

### 📋 Spec Pro

Use for requirements, specs, clarification, planning, UX/UI docs, architecture, task generation, and consistency analysis.

Best for:
- New feature requirements
- Project/feature spec packs
- Architecture/API/data/UI decisions
- Requirements-quality checklists
- Task plans before implementation
- Read-only analysis across spec/plan/tasks

Default output style:
- Facts / assumptions / unknowns when ambiguous
- Acceptance criteria
- Risks and edge cases
- Verification plan
- File paths for generated docs

### ⚒️ Implement Pro

Use for coding and production delivery.

Best for:
- Implementing from spec/task docs
- Refactors
- Tests/checks
- UI polish
- Backend/frontend integration
- Documentation updates that must match code

Expected behavior:
- Read relevant docs/code first
- Implement one coherent scope at a time
- Self-review after each scope
- Verify before moving on
- Mark tasks done only after actual completion
- Report failures/skips honestly

### 🐞 Debug Pro

Use for failures and unexpected behavior.

Best for:
- Failing tests
- Runtime errors
- Broken UI
- Performance issues
- Regressions
- Flaky behavior

Expected behavior:
- Reproduce or narrow first
- Hypothesize with evidence
- Patch minimally
- Add regression coverage where practical
- Verify original failure path

### 🧭 Lead Pro

Use for large work, not simple direct edits.

Best for:
- Starting a new project
- Full feature delivery
- Large migrations/refactors
- Multi-phase work
- Coordinating Spec → Implement → Debug → Readiness

Expected behavior:
- Build context map
- Identify critical unknowns
- Create delivery roadmap
- Delegate to the right mode
- Keep parent context clean
- Synthesize production-readiness status

## Recommended flows

### New project

Lead Pro → Spec Pro → Lead Pro → Implement Pro → Debug Pro when needed → Lead Pro readiness summary

### Feature with unclear requirements

Spec Pro → clarify critical gaps → plan/research → tasks → consistency analysis → Implement Pro

### Small direct change

Implement Pro can handle it directly, but it should still collect enough context and verify.

### Bug

Debug Pro first. Do not use Implement Pro for unknown failures until root cause is clear.

## Core principle

v6 is mode-native. Do not rely on separate slash commands. The workflow is encoded in rules, skills, and templates attached to the active mode.


## Final Additions: AgentMemory + Superpowers Methodology

### AgentMemory

Use AgentMemory only for durable, non-sensitive engineering context. Memory is useful for prior decisions, conventions, recurring bugs, and handoff notes. It must never override current code, docs, or explicit user instructions.

### Superpowers-style workflow

Across all modes, prefer engineering process control over ad-hoc coding:

- Spec Pro: brainstorm, clarify, document, and write concrete plans.
- Implement Pro: execute in small slices, prefer TDD when practical, self-review, and verify before completion.
- Debug Pro: reproduce, trace, hypothesize, test, fix minimally, and verify.
- Lead Pro: delegate only when useful, keep context clean, and synthesize readiness evidence.


## ECC-inspired behavior added

These behaviors are now mode-native, not slash commands:

- Spec Pro uses search-first and requirements-quality discipline before writing plans.
- Implement Pro uses build-fix loops, quality gates, docs sync, and context budget control.
- Debug Pro can separate product bugs from Zoo/MCP/harness configuration bugs.
- Lead Pro can decide when parallelization or worktrees are worth the overhead.

Use commands only if you explicitly add them later. The default workflow remains: choose a mode and ask normally.
