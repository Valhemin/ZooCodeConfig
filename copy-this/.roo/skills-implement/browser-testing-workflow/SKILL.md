---
name: browser-testing-workflow
description: End-to-end browser testing workflow combining Playwright (interaction) and Chrome DevTools (performance). Enable MCPs before use.
---

Use after implementing UI features to verify both visual correctness and performance before shipping.

## MCP Requirements

Enable one or both depending on need:
- **Playwright** — interaction, screenshots, responsive testing.
- **Chrome DevTools** — performance, network, memory, rendering.

## Workflow

### 1. Smoke (Playwright)
- Navigate to the changed page/component.
- Screenshot desktop (1280px) + mobile (375px).
- Check for console errors.
- Verify no broken layout or missing content.

### 2. Interaction (Playwright)
- Walk through the primary user flow.
- Test form inputs, button clicks, navigation.
- Verify state transitions (loading → success, empty → filled).
- Screenshot each meaningful state.

### 3. Performance (Chrome DevTools)
- Check network waterfall for slow/failed requests.
- Measure DOM node count.
- Look for layout shifts and long tasks.
- Check memory for leaks (navigate away and back, compare heap).

### 4. Cross-check
- Compare screenshots against DESIGN.md tokens if available.
- Verify responsive behavior matches spec.
- Flag any performance regression vs baseline.

## Decision Matrix

| Situation | MCPs to enable |
|---|---|
| Visual change only (colors, layout, text) | Playwright only |
| Performance concern (slow load, jank) | Chrome DevTools only |
| New feature (UI + functionality) | Both |
| Regression after refactor | Both |

## Output

- Pass/fail per phase.
- Screenshots with annotations.
- Performance metrics (network timing, DOM count, CLS).
- Issues ranked by severity.
- Recommended fixes.
