---
name: figma-to-code
description: Convert Figma designs to code using Figma MCP (cloud) or Figma Desktop MCP (local). Enable one before use.
---

Use when a Figma link, selection, or design reference is provided.

## MCP Options

| MCP | When to use | Enable |
|---|---|---|
| **figma** (cloud) | Figma not open locally, or working from shared links | `"disabled": false` in mcp.json |
| **figma-desktop** | Figma Desktop app running with Dev Mode | `"disabled": false` in mcp.json |

Only enable one at a time.

## Protocol

1. **Inspect existing code first** — check project components, tokens, design system.
2. **Pull design context** via Figma MCP:
   - Layer structure, auto-layout, constraints.
   - Variants and component properties.
   - Design tokens (colors, spacing, typography).
   - Assets (icons, images) — note export format.
3. **Map to existing primitives** before creating new ones:
   - Match colors to existing CSS variables/tokens.
   - Match spacing to existing scale.
   - Match typography to existing text styles.
   - Reuse existing components where design matches.
4. **Implement responsive states**, not just static pixels:
   - Auto-layout → flexbox/grid mapping.
   - Constraints → responsive behavior.
   - Breakpoint variants if designed.
5. **Handle states**: hover, focus, active, disabled, loading, error, empty.
6. **Verify visually** — use Playwright MCP if available for screenshot comparison.

## Output

- Components created/modified with file paths.
- Tokens added/reused.
- Design decisions where Figma was ambiguous.
- States implemented vs states not designed (flag gaps).
