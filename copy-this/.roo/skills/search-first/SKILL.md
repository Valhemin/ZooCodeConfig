# Search First

Use when starting a non-trivial feature, adding a dependency/integration, writing a new utility, touching framework-specific behavior, or when the solution may already exist in the project or ecosystem.

## Workflow

1. Check project-local patterns first: existing modules, services, components, tests, docs, and conventions.
2. If current framework/library behavior matters, research official/current docs with Context7 or approved research MCPs.
3. Compare at least two paths when appropriate:
   - reuse existing project pattern
   - use a standard library/framework feature
   - add a dependency
   - custom implementation
4. Choose the smallest maintainable path with clear tradeoffs.
5. Document assumptions, source of truth, and why alternatives were rejected.

## Output Contract

Include:

- What was searched or inspected.
- What current source or repo pattern informed the decision.
- Decision and rationale.
- Risks, unknowns, and verification plan.

Do not invent a solution when research or repo inspection failed. State the gap and choose the safest reversible next step.
