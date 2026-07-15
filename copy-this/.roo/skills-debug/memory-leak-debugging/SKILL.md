TRIGGER: process memory grows unboundedly over time, OOM errors appear, or heap snapshots show object count increasing with operation count
OUTPUT: detailed — growth confirmed with measurements, leak category, retained object owner traced, fix with before/after memory
SKIP: large-but-stable memory plateau that stabilizes (not a leak — may be a sizing issue)

---

# Memory Leak Debugging

Use when: process memory grows unboundedly, garbage collection pauses increase over time, OOM errors appear, or heap snapshots show growing retained object counts.

For frontend memory specifically, Chrome DevTools MCP can also assist. This skill covers the diagnostic process for any runtime (Node.js, browser, Python, JVM, etc.).

## When to Use

- Process RSS/heap grows steadily and does not stabilize.
- OOM crash after extended runtime.
- GC pauses increasing over time (visible in metrics or profiler).
- "Heap snapshot 1 vs snapshot 2" shows object count growing without bound.
- Memory usage correlates with request count or event count (not just data size).

## Process

### 1. Confirm the Leak
Before diagnosing, prove memory is actually leaking — not just growing to a stable plateau.

- Take 3 measurements: start, after N operations, after 2N operations.
- If growth is linear with N operations: leak candidate confirmed.
- If growth stabilizes: not a leak, may be a sizing issue.

### 2. Characterize Growth Rate
- Is growth constant per request? Per event? Per connection?
- Does memory release on idle? If yes: suspect large allocation not GC'd promptly (not a true leak).
- Does memory release at all? If no: strong leak indicator.

### 3. Identify Leak Category

| Category | Symptoms | Common Causes |
|---|---|---|
| Retained object graph | Objects count grows in heap snapshot | Forgotten listeners, caches without eviction, global maps/sets |
| Closure capture | Anonymous functions hold outer scope alive | Callbacks registered but never deregistered |
| Event listener buildup | `listenerCount` grows | `on()` without matching `off()`, repeated registration |
| External resource | File handles, DB connections, sockets not closed | Missing `finally` blocks, uncaught errors bypassing cleanup |
| Native/C bindings | RSS grows, heap does not | Buffer, stream, or native addon not releasing native memory |
| Circular reference (older runtimes) | GC cannot collect cycles | Rare in modern VMs, still possible with weak ref misuse |

### 4. Isolate

- Write a minimal reproducer: one operation that leaks, looped N times.
- Run with heap profiling enabled (e.g., `--inspect`, `tracemalloc`, async-profiler).
- Take heap snapshots before and after the loop. Diff retained objects.
- Sort by "retained size" or "count delta" — the top entries are the leak candidates.

### 5. Trace Ownership
- For the top retained object type: find where it is created.
- Find who holds a reference to it and why that reference persists.
- Common owners: module-level arrays/maps, event emitters, timer callbacks, closure scopes, cache objects.

### 6. Fix Minimally
- Add eviction to unbounded caches (LRU, TTL, max-size).
- Deregister listeners on teardown.
- Close resources in `finally` / `using` blocks.
- Remove from collections on destruction.
- Do not patch by increasing heap limit — fix the retention.

### 7. Verify
- Run the reproducer again after fix.
- Confirm memory stabilizes at start level after N operations.
- Run for 2N operations to confirm no regrowth.

## Partial Findings Rule

If leak source is unconfirmed, still report:
- Memory growth confirmed or ruled out (with measurements).
- Leak category candidates and ruling.
- Object type with highest retained size delta.
- Next profiling step.

## Output Contract

Every response must include:

- **Growth confirmed**: yes / no — with measurements (start / after N / after 2N).
- **Growth rate**: per request / per event / per connection / unclear.
- **Leak category**: from classification table, or "not yet determined."
- **Retained object type**: top candidate from heap diff (or "heap diff not yet taken").
- **Owner traced**: what holds the reference (if found).
- **Fix applied** (if any): change + memory measurements before/after.
- **Next step** if not resolved.
