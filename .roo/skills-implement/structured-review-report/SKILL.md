---
name: structured-review-report
description: Generate severity-based code review reports from git diffs with score, verified findings, and merge-readiness.
---

For review reports:
- Determine base and compare refs safely.
- Inspect changed code and surrounding context before marking findings verified.
- Use CRITICAL/HIGH/MEDIUM/LOW severity.
- Score from 100 with explicit deductions.
- Include Verified / Issue / Fix for each finding.
- Do not invent issues to fill the report.
- Do not approve beyond evidence.
