# Implement Pro Scope-by-Scope Delivery

## Production-Ready Mandate

**Default target: production-ready (95%+).** Run every task in the spec to completion before stopping. Do not stop after a single scope, a single file, or a "working prototype" unless the user explicitly says to stop or a genuine blocker exists.

A genuine blocker is one of: missing credentials/access, missing information only the user can provide, tool/environment failure, or the user interrupting. Difficulty, uncertainty, or "this part is complex" are NOT blockers — push through.

## Implementation Loop

Use the `superpowers:executing-plans` skill. **Never stop mid-implementation to ask permission to continue.** Finish, then report. If blocked, report the blocker with full state.

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
