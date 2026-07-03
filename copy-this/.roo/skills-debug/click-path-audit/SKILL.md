---
name: click-path-audit
description: Trace every interactive touchpoint through its full state change sequence to find bugs where handlers silently undo each other or leave inconsistent state.
---

Find bugs that static code reading and unit tests miss: state interaction side effects, race conditions between sequential calls, and handlers that silently undo each other.

## When to Use

- Systematic debugging found no bugs but users report broken buttons/interactions.
- After major refactor touching shared state (Zustand/Redux/Context/signals).
- Buttons/forms that "do nothing" despite code looking correct.
- State management bugs where A works, B works, but A→B breaks.

## Protocol

For EVERY interactive touchpoint in the target area:

### 1. Identify
Find all handlers: `onClick`, `onSubmit`, `onChange`, `onKeyDown`, etc.

### 2. Trace (in execution order)
For each function call in the handler:
- What state does it **read**?
- What state does it **write**?
- Does it have **side effects** on shared state?
- Does it **reset/clear** any state as a side effect?

### 3. Conflict Check
- Does any later call **undo** a state change from an earlier call?
- Do async operations create a race where the final state depends on timing?
- Do shared state subscribers trigger cascading updates that conflict?

### 4. Verify with Browser MCP (optional)
If Playwright MCP is available:
1. Click the touchpoint.
2. Observe actual state changes vs expected.
3. Screenshot before/after.
4. Check if the UI reflects the intended final state.

## Example

```
Button: "New Email"
Handler calls:
  1. setComposeMode(true)    → writes composeMode = true
  2. selectThread(null)      → writes selectedThread = null
                             → SIDE EFFECT: resets composeMode = false
Result: composeMode = false  → Button does nothing
```

## Output

Per touchpoint:
- Handler chain with state reads/writes.
- Conflicts found (with evidence).
- Fix recommendation.
- Severity: critical (feature broken) / major (inconsistent state) / minor (cosmetic).
