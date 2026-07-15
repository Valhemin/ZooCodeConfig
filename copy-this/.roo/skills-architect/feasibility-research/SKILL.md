TRIGGER: before planning or delegating — a technology, API, service, or approach must be evaluated before committing to a roadmap item
OUTPUT: report — VIABLE/NOT VIABLE/VIABLE WITH CAVEATS verdict, feasibility summary, blockers, caveats, recommended next step
SKIP: after a decision has already been committed; use implementation-plan once the approach is decided

---

# Feasibility Research

Use BEFORE planning or delegating — when a technology, API, service, or approach must be evaluated before committing to a roadmap item or kickoff.

## Trigger Patterns

- "Is [technology/API/service] viable for this use case?"
- "Should we build vs. buy vs. integrate?"
- "Evaluate [third-party service] for [requirement]"
- "Can [approach] handle [constraint]? Estimate effort/risk."
- "Compare [option A] vs [option B] before we start"
- Evaluation table provided (pricing / endpoints / limits / risk)
- Roadmap item flagged as unknown or risky before planning

## Workflow

### Phase 1 — Decompose the Question

Before searching, break the feasibility question into 3–5 specific sub-questions. Examples for "evaluate API provider X":

- What endpoints / capabilities does it expose?
- What are the pricing tiers, rate limits, and quota risks?
- How mature and stable is it? (release history, SLA, known outages)
- What auth, compliance, or data-residency requirements apply?
- What are the integration risks or known blockers?

For build vs. buy:
- What is the estimated build effort (hours/weeks)?
- What does the best existing solution cost at our scale?
- What is the maintenance burden of each path?
- What are the lock-in risks?

### Phase 2 — Multi-Source Fetch (depth floor)

- Minimum **3 unique sources** per topic.
- For URL inputs: fetch the URL + at least 2 corroborating or contrasting sources.
- Use 2–3 keyword variations per sub-question.
- Enable Tavily/Brave Search MCP if needed (inform user first).

Source priority:
1. Official docs / pricing pages / API reference
2. Release notes / changelogs / SLA agreements
3. Reputable news or analyst sources (≤12 months)
4. Community signals (GitHub Issues, Stack Overflow, Reddit engineering threads)
5. Benchmarks / case studies — flag methodology before trusting

### Phase 3 — Synthesize Verdict (mandatory)

Never stop at raw findings. Always produce:

#### Verdict (required, always)

```
VIABLE | NOT VIABLE | VIABLE WITH CAVEATS
Confidence: high | medium | low
```

- **VIABLE**: Meets requirements with acceptable risk and cost.
- **NOT VIABLE**: Blocking issue found (missing capability, cost ceiling, compliance failure, unacceptable risk).
- **VIABLE WITH CAVEATS**: Works but requires mitigation steps, workarounds, or risk acceptance. List the caveats explicitly.

Even under high uncertainty: give a verdict with `low` confidence rather than deferring. State exactly what is unknown and the safest reversible next step.

#### Required Output Sections

1. **Verdict** — one of the three above + confidence level + one-sentence rationale.
2. **Feasibility Summary** — per sub-question finding with evidence and source.
3. **Evaluation Table** (when comparing options):
   | Dimension | Option A | Option B |
   |---|---|---|
   | Cost at scale | | |
   | Key capability | | |
   | Integration effort | | |
   | Risk | | |
   | Verdict | | |
4. **Blockers Found** — any hard no-go items (missing feature, pricing cliff, compliance gap). If none, state "none found."
5. **Caveats & Mitigations** — conditions that must hold for VIABLE verdict to remain valid.
6. **Recommended Next Step** — concrete: "proceed to delivery-roadmap", "spike for 2 days on X", "reject and evaluate alternative Y", etc.
7. **Gaps** — what could not be verified, why, and whether it materially affects the verdict.
8. **Sources** — all sources cited with quality tier label.

## Source Quality Labels

| Tier | Examples | Trust |
|---|---|---|
| 1 — Official | API docs, pricing page, spec, source repo | Highest |
| 2 — Release | Changelog, release notes, SLA | High |
| 3 — Reputable | TechCrunch, analyst report, official blog ≤12mo | Medium-high |
| 4 — Community | GitHub Issues, Stack Overflow, Reddit | Medium (flag as unofficial) |
| 5 — Blog/Tutorial | Dev.to, Medium | Low — cross-verify required |

## Gap Reporting Rules

If authoritative answer is unavailable:
- Report best available evidence with confidence label.
- State exactly which sources were tried and what they returned.
- Give a verdict under uncertainty rather than deferring to the user.
- Recommend the safest reversible next step (spike, prototype, pilot).

**Never**: return "I couldn't verify enough, you'll need to research more" as the final output.

## Feed Into

- `delivery-roadmap` — feasibility verdict informs milestone risk and slice order.
- `project-kickoff` — unknown tech direction resolved here before kickoff proceeds.
- `subagent-delegation` — delegate research spikes when live testing is needed to fill gaps.

## Output Length

- Single technology or API: verdict + summary in chat.
- Multi-option comparison or broad landscape: summary in chat + write detailed report to `docs/research/<topic>.md`.
