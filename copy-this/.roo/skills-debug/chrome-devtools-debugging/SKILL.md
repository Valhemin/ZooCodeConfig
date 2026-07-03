---
name: chrome-devtools-debugging
description: Debug frontend performance, network, and rendering issues using Chrome DevTools MCP. Enable MCP before use.
---

Use for performance debugging, network inspection, rendering issues, and runtime analysis that Playwright alone cannot surface.

## MCP Tools

Chrome DevTools MCP provides: DOM inspection, network request monitoring, performance profiling, console access, CSS computed styles, and JavaScript evaluation.

Enable `chrome-devtools` MCP before use (disabled by default).

## When to Use (vs Playwright)

| Problem | Use |
|---|---|
| Visual bugs, interaction testing, screenshots | **Playwright** |
| Slow page load, layout thrashing, memory leaks | **Chrome DevTools** |
| Network waterfall, blocked requests, CORS | **Chrome DevTools** |
| Both visual + performance | **Both** — Playwright navigates, DevTools profiles |

## Protocol

### Network Debugging
1. Navigate to target URL.
2. Inspect network requests — look for failed requests (4xx/5xx), slow responses (>1s), large payloads (>1MB).
3. Check request headers, CORS issues, redirect chains.
4. Identify blocking resources in the critical path.

### Performance Debugging
1. Check DOM node count (>1500 is a warning).
2. Look for layout shifts (CLS sources).
3. Identify long tasks (>50ms) blocking main thread.
4. Check memory usage trends for leaks.
5. Inspect paint/composite layers for unnecessary repaints.

### CSS/Layout Debugging
1. Inspect computed styles on problematic elements.
2. Check box model for unexpected margins/padding.
3. Verify z-index stacking context.
4. Test CSS containment opportunities.

### Console & Runtime
1. Capture console errors and warnings.
2. Evaluate runtime state of key variables.
3. Check for unhandled promise rejections.
4. Inspect event listeners on problematic elements.

## Output

- Specific findings with evidence (network timings, DOM counts, error messages).
- Root cause analysis.
- Fix recommendations ranked by impact.
- Before/after metrics when fix is applied.
