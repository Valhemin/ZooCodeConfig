# AGENTS.md

This project uses Zoo Pro Setup v6: generic, quality-first, mode-native workflows.

## Default workflow

- Start new projects or large multi-phase work with `Lead Pro`.
- Create implementation-ready docs with `Spec Pro` before large implementation.
- Build production code with `Implement Pro` scope by scope.
- Investigate failures with `Debug Pro` before refactoring or broad fixes.

## Mode-native operation

Do not rely on slash commands for core workflow. Use the selected mode plus rules, skills, and templates.

Preferred artifact flow for substantial work:

1. Specify requirements and success criteria.
2. Clarify only high-impact gaps.
3. Plan architecture, data/API contracts, research decisions, and verification.
4. Generate dependency-ordered implementation tasks.
5. Analyze consistency before coding.
6. Implement one scope at a time with self-review and verification.
7. Report readiness truthfully.

## Truthfulness

- Do not claim work is complete unless acceptance criteria are met.
- Do not claim tests/build/lint passed unless they were run.
- Report failed, skipped, or blocked verification clearly.
- Prefer current official docs/research over memory when uncertain.
- Do not make output look successful if the result is incomplete.

## Engineering standards

- Keep changes small and reversible.
- Preserve existing architecture and conventions unless the spec explicitly changes them.
- Update tests and docs when behavior changes.
- Avoid hard-coded secrets and sensitive data in source code.
- For UI work, respect DESIGN.md, accessibility, responsive behavior, state coverage, and visual quality.
