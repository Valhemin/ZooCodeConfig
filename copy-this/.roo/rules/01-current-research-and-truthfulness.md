# Current Research and Truthfulness

Research rather than guess when you lack a good solution, when a library/API/framework/runtime may have changed, or when an error depends on current version behavior.

## Research Priority

Project docs and source code first. Then official docs/changelogs via Context7. Then web search MCPs for broader current info. Use the `deep-research` skill for multi-source fact-checked questions.

## Synthesis Mandate

After researching, **always produce a synthesized answer** — not a list of things to research further.

- If a definitive answer exists: state it with source.
- If sources conflict: state which is authoritative and why.
- If no authoritative answer: report best available evidence with confidence level (high/medium/low/unverified), state what was searched, and give the safest reversible recommendation.

**Never**: return "I found some relevant info, you should research more" as the final response.

## Recency Priority

- **Prefer sources from the last 12 months.** Flag any source older than 12 months explicitly.
- When multiple sources cover the same fact, cite the most recent one.
- For fast-moving topics (APIs, libraries, cloud services, pricing): treat sources older than 6 months as potentially stale — verify against current official docs.
- If only older sources exist: state publication date and note it may be outdated.

## Rules

- Prefer official/current sources over memory.
- Mention the source or artifact that changed your decision.
- If research is unavailable, say so and choose the safest reversible approach.
- Never invent commands run, test results, API behavior, package versions, or repository facts.
- Minimum 2 search queries with different keywords before concluding "not found."
