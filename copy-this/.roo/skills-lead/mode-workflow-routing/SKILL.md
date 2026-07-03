---
name: mode-workflow-routing
description: Route work through Lead, Spec, Implement, and Debug modes without relying on mode-native workflows.
---

Choose the mode/workflow based on artifact readiness:

- No project direction or multi-phase goal: Lead Pro.
- Need initial requirements/spec pack: Spec Pro with artifact-workflow-sequence.
- Spec has high-impact ambiguity: Spec Pro with clarification-loop.
- Need technical plan/research/contracts: Spec Pro with technical-planning-research.
- Need actionable implementation tasks: Spec Pro with task-generation.
- Need consistency check before code: Spec Pro with spec-consistency-analysis.
- Ready to build from tasks/spec: Implement Pro with tasks-md-execution or feature-implementation.
- Tests fail or behavior is unknown: Debug Pro with root-cause-debugging.
- Need diff/MR review: Implement Pro or Spec Pro with structured-review-report.

Do not create a separate command workflow. Keep the selected mode as the source of behavior.
