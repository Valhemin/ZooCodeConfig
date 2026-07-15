# Skill Index

Read this before loading any skill. Match trigger → load only that skill.

## Group A — Planning & Spec

| Skill | Load when | Skip when |
|---|---|---|
| new-project-discovery | Brand-new project, no spec or brief | Continuing in-progress work |
| brainstorming-design-refinement | Goal vague or multiple viable designs | Single clear design already chosen |
| product-requirements | Converting requests to testable requirements | Requirements already written |
| user-story-mapping | 3+ user roles or unclear feature scope | Single-role, clearly scoped feature |
| technical-architecture | Designing system or feature architecture | Architecture already committed |
| technical-planning-research | Technical unknowns block safe planning | Architecture already clear |
| api-service-research | Evaluating / comparing external APIs or SaaS | Single option, no comparison needed |
| feasibility-research | Evaluating tech viability before committing | Technology already decided |
| ui-ux-spec | UI feature needs state-complete spec | Non-UI or already specced feature |
| non-functional-requirements | Feature has perf/security/scale/compliance needs | Pure functional, no NFRs |
| data-privacy-compliance | Feature stores/transmits user data | No user data involved |
| implementation-plan | Writing ordered plan after architecture decided | Architecture still unclear |
| writing-plans-superpowers | Writing concrete verifiable implementation plan | Plan already written |
| spec-pack-authoring | New project or major feature needs full spec pack | Small feature or spec already exists |
| clarification-loop | Spec has ambiguities that block implementation | Requirements already clear |
| acceptance-test-planning | Writing test plan for defined acceptance criteria | No acceptance criteria defined |
| requirements-quality-checklist | Reviewing requirements before gate | Requirements not yet written |
| spec-self-review | After authoring spec, before handoff | Spec already reviewed |
| spec-consistency-analysis | Cross-artifact consistency gate before impl | Single-artifact, no cross-checks needed |
| task-generation | Creating tasks.md from spec/plan | tasks.md already exists |
| constitution-governance | Project needs stable non-negotiable principles | Principles already documented |
| artifact-workflow-sequence | Feature needs structured docs before impl | Docs already exist and current |

## Group B — Coordination & Delivery

| Skill | Load when | Skip when |
|---|---|---|
| project-kickoff | New project, no spec or task list exists | Spec or plan already exists |
| lead-decomposition | Splitting work into delegatable subtasks | Work is single-mode, no delegation |
| subagent-delegation | Creating mode-specific subtasks | Work stays in current mode |
| dispatching-parallel-agents | Work splits into independent parallel scopes | Sequential work or shared state |
| parallelization-cascade | Large separable work with cascade dependencies | Work has shared state |
| delivery-roadmap | Planning production delivery with milestones | No delivery planning needed yet |
| finishing-development-branch | All tasks complete, checking final readiness | Work still in progress |
| incident-coordination | Production down, degraded, or critical bug live | Non-production or planned work |
| canary-watch | Post-deploy monitoring of live URL/endpoint | Pre-deploy or local environment |
| production-audit | Pre-launch or post-merge readiness review | Development-phase work |
| retrospective-postmortem | Sprint/milestone complete or incident resolved | Work still in progress |
| technical-debt-triage | Debt slowing delivery, needs priority | No debt pressure on current work |
| cross-team-dependency-tracking | Blocked on external team, vendor, or upstream | All deps owned internally |
| github-workflow | PR/issue management via GitHub MCP | No GitHub MCP or repo access |
| using-git-worktrees | Risky parallel branches need isolation | Simple single-branch work |
| harness-audit | Evaluating new agent pack, MCP, or rule update | No harness changes planned |
| mode-workflow-routing | Routing work between Architect/Implement/Debug | Mode already chosen |
