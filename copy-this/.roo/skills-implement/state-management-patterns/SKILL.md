---
name: state-management-patterns
description: Patterns for client-side state — store structure, derived state, normalization, async state. Use when adding or restructuring state in a frontend feature.
---

TRIGGER: adding a new data domain to client state, introducing a store, implementing derived state, or resolving stale/over-fetching bugs
OUTPUT: detailed — state domain, TypeScript shape, async state model, selectors added, cleanup path on unmount
SKIP: server state managed by React Query/SWR — prefer those libraries over manual store patterns for remote data

---


## When to Use

Use when: adding a new data domain to client state, introducing a store (Redux, Zustand, Jotai, Context+Reducer), implementing derived/computed state, or resolving state bugs (stale data, over-fetching, prop drilling).

## Decision Ladder

Before reaching for a store:

1. **Local component state** (`useState`, `useReducer`) — for state that only one component needs. Default choice.
2. **Lifted state** — when two sibling components need the same data. Lift to nearest common ancestor.
3. **Context** — for truly global but low-frequency data (theme, auth user, locale). Not for high-frequency updates.
4. **External store** (Redux, Zustand, Jotai) — when: data is shared across many unrelated components, or needs to persist outside React tree, or complex derived state with selectors is needed.

Never reach for a store to avoid prop drilling when lifting state or Context would work.

## Store Structure Rules

- **Normalize relational data.** Store entities by ID (`entities: { [id]: Entity }`), not nested arrays.
- **Separate server state from UI state.** Server cache (React Query, SWR, RTK Query) is not the same as UI state (selected tab, modal open). Do not conflate them.
- **Derive, don't duplicate.** If a value can be computed from existing state, compute it in a selector — do not store it separately.
- **Keep slices flat.** Deeply nested state is hard to update correctly. One level of nesting max.

## Derived State / Selectors

- Memoize expensive selectors (`createSelector` in Redux, `useMemo` for Zustand/Jotai).
- Selectors must be pure. No side effects, no async.
- Collocate selectors with the slice/atom they read from.
- When derived state depends on multiple slices: compose selectors rather than duplicating the derivation.

## Async State Shape

Every async operation needs four states. Model them explicitly:

```typescript
type AsyncState<T> =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: T }
  | { status: 'error'; error: string }
```

Never use boolean `isLoading` + `error` + `data` as three separate fields — they allow impossible states.

## Rules

- Never mutate state directly. Always return new references.
- Never store non-serializable values (functions, class instances, Promises) in a store.
- Always handle the `error` state in UI — do not render only the happy path.
- Reset state on unmount when the data is component-scoped — avoid stale data on re-mount.
- When using server state libraries (React Query, SWR): prefer them over manual fetch-in-store patterns for remote data.

## Checklist per State Domain

- [ ] Is this state actually shared, or can it be local?
- [ ] Is the store normalized (no nested arrays of objects with IDs)?
- [ ] Is async state modeled with status discriminant?
- [ ] Are derived values computed via selectors, not duplicated?
- [ ] Are impossible states prevented by the type?
- [ ] Is there a reset/cleanup path on unmount or navigation away?

## Output Contract

When adding state:
- State domain name and where it lives (store/slice/atom/context).
- Shape (TypeScript type or schema).
- Async state handling approach.
- Selectors added and what they derive.
- Any existing state reused or consolidated.

After implementation: run `api-testing` if the state domain is backed by an API endpoint.
