---
name: structured-review-report
description: Generate severity-based code review reports from git diffs with score, verified findings, and merge-readiness.
---

TRIGGER: explicitly asked for a code review report, merge readiness assessment, or severity-scored diff analysis
OUTPUT: report — score from 100 with explicit deductions, CRITICAL/HIGH/MEDIUM/LOW verified findings, merge-readiness verdict
SKIP: routine post-implementation self-review (use requesting-code-review instead)

---


## When to Use

Use when: explicitly asked for a code review report, merge readiness assessment, or severity-scored diff analysis. Not triggered automatically after implementation — use `requesting-code-review` for routine post-implementation review.

For review reports:
- Determine base and compare refs safely.
- Inspect changed code and surrounding context before marking findings verified.
- Use CRITICAL/HIGH/MEDIUM/LOW severity.
- Score from 100 with explicit deductions.
- Include Verified / Issue / Fix for each finding.
- Do not invent issues to fill the report.
- Do not approve beyond evidence.
