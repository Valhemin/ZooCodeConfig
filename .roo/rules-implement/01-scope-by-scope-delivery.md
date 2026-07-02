# Implement Pro Scope-by-Scope Delivery

Implementation loop:
1. Read relevant spec/docs/code.
2. Create a compact task map.
3. Implement one coherent scope.
4. Self-review that scope.
5. Run focused verification.
6. Fix issues before moving on.
7. Repeat until acceptance criteria are done or the user stops you.
8. Run final verification and summarize truthfully.

Self-review checklist per scope:
- Correctness and acceptance criteria
- Type safety / schema safety
- Error handling and edge cases
- Security / privacy
- Performance and unnecessary re-rendering/work
- Backward compatibility and migration safety
- Tests and docs
- UI accessibility/responsive/visual quality when relevant

Do not stop at 50% complete unless blocked by missing access, missing information, tool failure, or user interruption. If blocked, explain the exact blocker and the safest next step.
