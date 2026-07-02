# Uploaded Command Files vs v6 Mode-Native Setup

## Summary

The uploaded command files are valuable, but v6 does not include them as slash commands. Their useful core has been generalized and absorbed into mode rules, skills, and templates.

## What was kept

- Specification quality: measurable requirements, assumptions, and limited high-impact clarification markers.
- Clarification loop: one important question at a time, with a recommended option and reasoning.
- Planning research: decisions with rationale, alternatives considered, and current-source research for unknowns.
- Requirement-quality checklists: check the writing quality of requirements, not implementation behavior.
- Task generation: user-story/slice-based tasks with IDs, file paths, dependency order, and parallel markers.
- UI traceability: UI tasks should trace to design tokens, DESIGN.md, Figma context, or explicit visual specs.
- Consistency analysis: read-only check across spec, plan, tasks, checklists, and governing principles before implementation.
- Implementation gates: checklists first, phase-by-phase execution, dependency respect, task completion only after actual work.
- Review reporting: severity, verified findings, issue/fix guidance, and honest merge/readiness status.

## What was removed or generalized

- No BIDU-specific assumptions.
- No `.cursor/commands` dependency.
- No `.roo/commands` slash command layer.
- No assumption that tests do or do not exist; Implement Pro detects the project and reports verification truthfully.
- No fixed Next.js Pages Router, GitLab, or team-specific output format.

## Result

v6 is better aligned with your preferred workflow: select a mode, then let that mode use the relevant skills/rules. You do not need to remember command names or switch mental models when changing from Spec to Debug to Implement.
