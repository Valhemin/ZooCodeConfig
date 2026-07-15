# Definition of Done

Use this checklist proportional to task size. **Small tasks (bug fix, single file, minor change):** check only the "All Tasks" section. **API/backend tasks:** add the API section. **UI tasks:** add UI section only when explicitly requested.

Do not run the full checklist on every response — apply what's relevant.

---

## All Tasks

- [ ] All spec acceptance criteria satisfied (each criterion verified, not assumed)
- [ ] No regressions: existing tests pass (or failures are pre-existing and documented)
- [ ] Build passes (compile/lint/typecheck — whichever apply)
- [ ] No TODOs left in changed files unless explicitly deferred below
- [ ] Suggestions & Improvements section from spec addressed or explicitly deferred with reason
- [ ] Changed files summarized in completion output

---

## API / Backend Tasks

- [ ] Happy path tested: correct status code + response body schema asserted
- [ ] Edge cases tested (minimum 8 — drawn from the api-testing skill):
  - [ ] Invalid input → 400, error identifies bad field
  - [ ] Missing required fields → 400, error names missing field
  - [ ] Auth absent → 401
  - [ ] Auth present but insufficient permission → 403
  - [ ] Unexpected content-type → 400 or 415, not 500
  - [ ] Boundary values (min/max length, 0, negative, empty string)
  - [ ] Null / empty payload → meaningful error, not 500
  - [ ] Rate limit (if applicable) → 429 + Retry-After header
- [ ] Error handling on every code path (no unhandled exceptions reaching the client)
- [ ] Input validation at all trust boundaries (not just inside business logic)
- [ ] Auth enforced on every protected route (verified — not assumed from middleware)
- [ ] Logging present on critical paths (request received, error thrown, external call made)
- [ ] New env vars documented in `.env.example` with placeholder values and comments
- [ ] No secrets or credentials in changed files

---

## UI / Frontend Tasks

*(Apply only when a UI task was explicitly requested.)*

- [ ] Visual QA: rendered output matches design/spec intent
- [ ] Accessibility checked: keyboard navigable, ARIA roles correct, contrast passes
- [ ] Responsive tested: layout holds at mobile, tablet, and desktop breakpoints
- [ ] No console errors in the browser during normal use flows

---

## 95%+ Production-Ready Definition

Work is production-ready when **all applicable items above are checked**, OR each unchecked item has an explicit deferral entry:

```
DEFERRED: [item] — reason: [why] — follow-up: [ticket/note]
```

Do not claim production-ready if: a critical acceptance criterion is incomplete, tests fail without documented pre-existing cause, auth is unverified, or env vars are undocumented.

See also: `rules/04-production-readiness-gate.md` for final status output format.
