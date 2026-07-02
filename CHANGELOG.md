# Changelog v6 — Generic Mode-Native Core

## Added

- Generic mode-native artifact workflow rule.
- Spec artifact quality gates.
- Implement checklist/task gates.
- Lead artifact routing.
- Generic skills:
  - `artifact-workflow-sequence`
  - `task-generation`
  - `technical-planning-research`
  - `constitution-governance`
  - `mode-workflow-routing`

## Changed

- Removed slash-command workflow dependency from v5.
- Generalized uploaded command-workflow ideas into project-agnostic rules and skills.
- Updated README and Mode Guide for mode-native operation.
- Removed team-specific review assumptions from defaults.

## Removed

- `.roo/commands/`
- `global/.roo/commands/`
- command workflow policy/routing skill
- team-specific command adapters

## Recommended version

Use v6 for general projects. Use v5 only if you explicitly want slash commands.
