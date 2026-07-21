# Implement Pro Scope-by-Scope Delivery

## Production-Ready Mandate

**Default target: production-ready (95%+).** Run every task in the spec to completion before stopping. Do not stop after a single scope, a single file, or a "working prototype" unless the user explicitly says to stop or a genuine blocker exists.

A genuine blocker is one of: missing credentials/access, missing information only the user can provide, tool/environment failure, or the user interrupting. Difficulty, uncertainty, or "this part is complex" are NOT blockers — push through.

## Implementation Loop

Use the `superpowers:executing-plans` skill. **Never stop mid-implementation to ask permission to continue.** Finish, then report. If blocked, report the blocker with full state.

## User-Facing Content

UI text, labels, messages, tooltips, empty states, and error messages are product copy — not code comments. Apply these rules everywhere text appears in the UI:

- **Write for the user, not the dev.** Never expose internal logic, system state, or technical reasons as UI text. Bad: "AI Provider chưa được cấu hình, dừng để tránh tốn quota." Good: "Hãy thêm API key để bắt đầu."
- **Every message must answer one of:** What happened? What can the user do next? Why does this matter to them?
- **Error messages:** user-friendly description + actionable next step. Never raw exception text.
- **Empty states:** explain what goes here + how to populate it. Not just "No data."
- **Loading states:** describe what's happening in user terms. Not "Processing..." — "Đang tìm video phù hợp..."

## UX Complexity Principle

Default flow must work with zero configuration. Advanced/technical settings belong in a separate layer:

- **Happy path first:** core features must work out-of-the-box with sensible defaults
- **Progressive disclosure:** hide advanced config (API keys, rate limits, technical toggles) behind "Advanced settings", "Cài đặt nâng cao", or a gear icon — not in the main flow
- **Never block the main flow** with setup steps that most users don't need
- When implementing a feature: ask "can a first-time user complete this without reading docs?" If no, simplify the default path or add a setup wizard
- **Complex features need inline guidance:** if a feature requires non-obvious input or configuration, add a short description, placeholder text, or tooltip explaining what to do — don't assume the user knows

## UI/UX Consistency

Same feature = same patterns. When a feature has multiple tabs, panels, or sections:

- **Consistent interaction placement:** same action (expand, delete, save, filter) must appear in the same position across all tabs. Never expand-button-top in tab 1 and expand-button-bottom in tab 2.
- **Consistent behavior:** same interaction must produce the same type of result. If tab 1 shows a confirmation dialog before delete, tab 2 must too.
- **Consistent visual hierarchy:** headings, spacing, button styles, icon usage must follow the same pattern across sibling tabs/panels.
- **When you implement a UI pattern in one place, scan for sibling components and apply the same pattern there immediately** — don't leave inconsistencies for later.

## DRY Sweep — Fix One, Fix All

When fixing a bug or implementing a pattern, always scan for the same issue elsewhere:

- **Bug in one place:** search for the same logic pattern in sibling components, other tabs, or parallel features. Fix all instances in the same PR — not just the one reported.
- **Logic repeated 2+ times:** extract to a shared utility/hook/component before moving on. Duplication compounds — catch it at 2, not 10.
- **UI component repeated 2+ times with slight variations:** extract to a common component with props. Inconsistency creeps in through copies.
- After any fix or implementation, ask: "Does this pattern exist elsewhere? Should it be shared?" Act on the answer.

## Implementation Confidence Gate

Before implementing any feature or integration, assess feasibility:

- **Confident (implement):** official docs exist, behavior is clear, production path is known, no major unknowns.
- **Uncertain (report, don't implement):** behavior depends on undocumented API, third-party service has unclear limits, production edge cases are unresolved, or research yielded conflicting/stale results.

When uncertain: **stop and produce a report instead of implementing.** The report must include:
- What was researched and what sources were found
- Specific unknowns that block production-readiness
- Risk assessment: what could break and under what conditions
- Recommendation: research further / descope / find alternative

Never ship a half-confident implementation that looks done but has hidden failure modes. A clear "not yet implementable" report is more valuable than broken code.

## Anti-Deferral Rule

Never return empty-handed. Attempt before escalating. If something cannot be completed, still deliver everything that can be — then report state.

## Partial Completion Protocol

When blocked mid-task, output ALL of:
- Completed: list of scopes/files done with verification status
- Blocked: exact task that failed, the error or missing input verbatim
- Attempted: what was tried to unblock
- Next action: the single most useful next step the user or a follow-up agent can take

## Completion Output Format

At task end (done or blocked), output:
- What was implemented (files changed, behavior added)
- Verification run: command and result (pass / partial / fail with details)
- Known gaps or risks
- Follow-up items if any

Before declaring complete, verify against `rules/05-definition-of-done.md` checklist. Every unchecked item must be explicitly deferred with reason.
