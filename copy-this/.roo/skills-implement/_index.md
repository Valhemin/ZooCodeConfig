# Skill Index

Read this before loading any skill. Match trigger → load only that skill.

| Skill | Load when | Skip when |
|---|---|---|
| feature-implementation | Building any feature from a spec | No spec; still in planning phase |
| tasks-md-execution | Implementing from a tasks.md file | No tasks.md exists |
| executing-plans-batched | Executing from a written implementation plan | No plan; still designing |
| build-fix-loop | Build, typecheck, lint, or tests fail | All checks passing |
| tdd-red-green-refactor | Tests exist or can be added reasonably | No test infrastructure available |
| api-testing | Any API/backend endpoint added or changed | Pure frontend or non-HTTP change |
| verification-before-completion | Before claiming task or feature complete | Mid-implementation, not done yet |
| research-before-implement | Unsure of correct API/library method | Pattern already known in project |
| safe-refactor | Restructuring code without behavior change | Adding new behavior simultaneously |
| docs-sync | Public behavior, API, or setup changed | Internal refactor, no public change |
| api-integration-workflow | Adding call to external API or service | Internal service-to-service call |
| db-migration-workflow | Changing database schema | No schema change involved |
| env-config-management | Adding env vars, secrets, or feature flags | Config hardcoded and intentional |
| error-handling-patterns | Adding error states or exception handling | No failure paths to handle |
| test-strategy | Adding or changing testable behavior | No behavioral change made |
| incremental-self-review | After each implementation scope ends | Before any implementation begins |
| requesting-code-review | After meaningful implementation slice done | Code not yet ready for review |
| structured-review-report | Explicit review report or merge readiness asked | Routine post-impl review |
| state-management-patterns | Adding or restructuring frontend client state | No frontend state involved |
| background-job-patterns | Work should not block HTTP response | Synchronous request-response flow |
| browser-testing-workflow | User explicitly requests E2E or UI testing | Automatic after implementation |
| visual-qa-playwright | User explicitly requests visual QA | Automatic after implementation |
| webhook-handling | Implementing inbound webhook endpoint | Outbound HTTP calls, not inbound |
| pagination-cursor | Adding list endpoint or infinite scroll | Single-item or non-list endpoint |
| figma-to-code | Figma link or design reference provided | No Figma input given |
