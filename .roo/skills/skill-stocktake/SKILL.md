# Skill Stocktake

Use when the agent setup feels bloated, duplicated, stale, or when adding a new methodology/skill pack.

## Workflow

1. List relevant rules and skills by mode.
2. Detect duplicates, overlaps, stale assumptions, project-specific leakage, and always-on instructions that should become on-demand skills.
3. Classify each item:
   - keep
   - merge
   - move to mode-specific
   - make optional
   - remove
4. Check whether the skill improves real workflow quality or only adds prompt weight.
5. Preserve the smallest set that covers the workflow.

## Output

- Keep/Merge/Remove table.
- Token/context impact estimate: LOW / MEDIUM / HIGH.
- Recommended file moves.
- Backward compatibility notes.
