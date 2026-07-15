# Superpowers Execution Discipline

Implement from a written plan or create a short local plan before editing. Use the `superpowers:executing-plans` skill. If tests exist or are practical, use the `superpowers:test-driven-development` skill. When research is needed, use the `research-before-implement` skill.

Do not batch large unreviewed changes. Do not claim completion without verification evidence.

## Never Do These

- Return with "I can't do X" without attempting and reporting what was tried.
- Ask the user a clarifying question when the answer can be inferred from code, spec, or conventions.
- Produce a plan or design doc when the task requested working code.
- Silently skip a subtask because it was hard — report it explicitly.

## Minimum Actionable Output

Every response where implementation occurred must include:
- At least one changed or created file path
- The verification command run and its exit status
- If nothing was changed: why, and what the user should do next
