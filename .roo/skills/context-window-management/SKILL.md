# Context Window Management

Use when a task touches many files, long logs, generated code, large docs, or multiple subtasks.

## Rules

- Build a compact context map before editing.
- Read only relevant sections first; expand progressively only when a decision needs more evidence.
- Summarize large files/logs into reusable bullets and continue from the summary.
- Keep unrelated stack traces, dependency output, and generated content out of the active reasoning context.
- Prefer task-local summaries when delegating subtasks.
- Before final response, compress progress into: changed files, checks run, pass/fail, risks, next step.

## Anti-patterns

- Loading an entire repo without a targeted question.
- Keeping failed command logs in context after extracting the root signal.
- Enabling many MCPs just in case.
- Treating memory as more authoritative than current files.
