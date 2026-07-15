# Skill Index

Read this before loading any skill. Match trigger → load only that skill.

## Research

| Skill | Load when | Skip when |
|---|---|---|
| search-first | Starting non-trivial feature or integration | Pattern already known in project |
| research-with-current-sources | Knowledge may be stale or API recently changed | Current docs already in context |
| web-research | Current web info Context7 cannot provide | Context7 covers the topic |
| deep-research | User requests research, analysis, or URL review | Quick lookup, not deep synthesis |

## Memory

| Skill | Load when | Skip when |
|---|---|---|
| agentmemory-recall | User references prior work or past decisions | Fresh task with no prior context |
| agentmemory-remember | After key decisions, bugs, or completed phases | Nothing durable worth saving |
| agentmemory-handoff | End of long session, switching mode or agent | Short session, no handoff needed |
| agentmemory-forget | Memory is stale, wrong, or privacy-sensitive | Memory is accurate and current |
| continuous-learning-v2 | Setting up session-based instinct learning via hooks | One-off task, hooks not configured |

## Quality & Security

| Skill | Load when | Skip when |
|---|---|---|
| quality-gate | Before declaring feature/fix/release complete | Mid-implementation, not done yet |
| release-readiness | Before calling work done and shipping | Feature still in development |
| security-threat-model | Auth, payments, uploads, or external integration | No trust boundary or user data |
| config-security-audit | MCP, auth, deploy, env, or automation config changes | No config or security surface touched |
| observability-errors | Adding production flows with failure modes | Dev-only or internal tooling |

## Architecture & Design

| Skill | Load when | Skip when |
|---|---|---|
| api-contract-design | Adding or changing any API endpoint/function | Implementation only, no new contract |
| architecture-decision-records | Making architectural or technology decisions | Tactical change, no arch decision |
| integration-boundary | Connecting services, APIs, queues, or webhooks | Internal, same-process call |
| data-model-migration | Changing schemas, persistence, or migrations | No data model change involved |
| dependency-upgrade | Adding or upgrading packages | No dependency change planned |
| performance-engineering | Slow paths, heavy queries, or scale-sensitive features | No performance concern reported |

## UI / Frontend

| Skill | Load when | Skip when |
|---|---|---|
| ui-ux-product-design | User flows, pages, dashboards, or forms involved | Backend-only or non-UI work |
| design-taste-frontend | Frontend/UI implementation or redesign | No visual or layout decisions |
| design-md-system | UI-heavy work or new web project needs design tokens | Design system already documented |

## Utility

| Skill | Load when | Skip when |
|---|---|---|
| context-window-management | Many files, long logs, or multi-phase task | Small focused single-file task |
| skill-stocktake | Setup feels bloated, duplicated, or stale | No harness maintenance needed |
