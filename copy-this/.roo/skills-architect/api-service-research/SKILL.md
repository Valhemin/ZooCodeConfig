---
name: api-service-research
description: Evaluate external APIs or service providers against explicit criteria and produce a comparison table with a per-option verdict.
---

TRIGGER: deciding whether to adopt an external API, SaaS, or data provider when multiple options exist to compare
OUTPUT: report — provider comparison table, gap flags, per-option verdict (USE/DON'T USE/USE WITH CAVEATS), concrete recommendation
SKIP: evaluating internal service design or single-provider decisions with no alternatives to compare

---


Use when a spec agent must decide whether to adopt an external API, SaaS, or data provider — especially when multiple options exist (e.g., RapidAPI providers, payment gateways, mapping services).

## Trigger patterns

- User supplies evaluation criteria (pricing, endpoints, auth, freshness, risk, etc.)
- "Which [API/provider] should we use?"
- "Evaluate [A] vs [B] vs [C] for [use case]"
- "Is [provider X] reliable / worth paying for?"
- "Compare [RapidAPI provider A] and [RapidAPI provider B]"

## Input contract

Accept from user (any format — table, list, prose):
- The provider/option names to evaluate.
- The evaluation criteria (or derive sensible defaults if not supplied; see Default Criteria below).

## Default criteria (use when user supplies none)

| Criterion | What to check |
|---|---|
| Pricing / limits | Tiers, free quota, overage cost, rate limits |
| Endpoint coverage | Does it expose the data/operations the feature needs? |
| Data freshness | How often is data updated? Real-time, daily, weekly? |
| Auth mechanism | API key, OAuth, IP allowlist — complexity of integration |
| Reliability / SLA | Uptime claims, known outages, community reports |
| Documentation quality | Complete, versioned, includes error codes? |
| Vendor risk | Company age, funding, open support issues, data ownership |

## Workflow

### Phase 1 — Per-provider research (minimum sources)

For each provider/option:
1. Fetch official docs or product page (source tier 1).
2. Fetch at least 1 independent source: community discussion, review, changelog, or news (source tier 3–4).
3. For pricing: verify at the official pricing page; never infer from blog posts.

Minimum 2 sources per provider. If only 1 source exists, mark all data from that provider as `confidence: low`.

### Phase 2 — Comparison table (mandatory output)

Produce this table. Never omit it. Never replace it with prose-only findings.

```
## Provider Comparison

| Criterion | [Provider A] | [Provider B] | [Provider C] |
|---|---|---|---|
| Pricing / limits | ... [tier label] | ... | ... |
| Endpoint coverage | ... | ... | ... |
| Data freshness | ... | ... | ... |
| Auth mechanism | ... | ... | ... |
| Reliability / SLA | ... | ... | ... |
| Documentation | ... | ... | ... |
| Vendor risk | ... | ... | ... |
```

Source quality labels (append to every cell where data came from a source):
- `[official]` — from vendor's own docs/pricing page
- `[community]` — from GitHub Issues, Stack Overflow, Reddit, forum
- `[news]` — from reputable news or analysis
- `[inferred]` — derived from indirect evidence, not stated explicitly

### Phase 3 — Gap flags (mandatory)

For every criterion that cannot be verified with available sources:
- Mark the cell: `UNVERIFIED — [what was tried]`
- Do NOT omit the criterion.
- Do NOT mark it as "N/A" unless the criterion genuinely does not apply to that provider.

### Phase 4 — Verdict (mandatory, one per option)

After the table, produce a verdict block:

```
## Verdicts

**[Provider A]**: USE / DON'T USE / USE WITH CAVEATS
Reason: [one sentence]
Caveats (if any): [specific conditions or risks]

**[Provider B]**: ...
```

Allowed verdicts: `USE`, `DON'T USE`, `USE WITH CAVEATS`. Never: "more research needed", "depends on your needs", or deferral to the user without a recommendation.

### Phase 5 — Recommendation (mandatory)

```
## Recommendation

Choose: [Provider X]
Because: [top 2–3 reasons in priority order]
Risk to monitor: [biggest remaining uncertainty]
```

If two options are genuinely equal, pick the one with lower vendor risk or lower integration complexity and state that as the tiebreaker.

## Gap reporting rules

- UNVERIFIED data is reported in the table, not hidden.
- If official pricing is paywalled or undisclosed, state that explicitly in the cell and note that pricing was obtained from community sources.
- If no source can answer a criterion, write: `UNVERIFIED — no source found after searching [terms tried]`.

**Never** end with "you should research X more" as the final output.

## Output length and destination

- 1–2 providers: summary in chat is sufficient.
- 3+ providers or complex criteria: write to `docs/research/<feature>-provider-comparison.md` and summarize in chat.

## Source quality tiers

| Tier | Examples | Trust |
|---|---|---|
| 1 — Official | Vendor docs, pricing page, source repo, API reference | Highest — `[official]` |
| 2 — Release | Changelogs, release notes, migration guides | High — `[official]` |
| 3 — Reputable | Tech news, analyst reports (≤12 months) | Medium-high — `[news]` |
| 4 — Community | GitHub Issues, Stack Overflow, Reddit, forums | Medium — `[community]` |
| 5 — Blog/tutorial | Dev.to, Medium, personal blogs | Low — cross-verify required |
