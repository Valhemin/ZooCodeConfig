# Harness Audit

Use before adopting a new external agent pack, MCP catalog, hook system, or major rule/skill update.

## Audit Dimensions

- Does it duplicate existing mode/rule/skill behavior?
- Does it require a runtime not present in Zoo/Roo?
- Does it add commands when the project is mode-native?
- Does it require hooks or shell automation with elevated risk?
- Does it add many tools/MCPs that increase context cost?
- Can the useful core be ported into a small rule/skill instead?

## Recommendation Format

- Integrate directly.
- Port as rule/skill.
- Keep as optional reference.
- Reject / do not install.

Prefer small mode-native ports over wholesale imports.
