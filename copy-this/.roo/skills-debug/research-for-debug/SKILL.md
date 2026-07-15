TRIGGER: debugging hit an external knowledge boundary — cryptic error, suspected library bug, version-specific breaking change, or behavior contradicts documented contract
OUTPUT: compact — verdict (known issue / local bug / unknown), evidence with source tiers, workaround or fix direction
SKIP: replacing internal code tracing; only trigger after internal investigation has produced a hypothesis to verify

---

# Research For Debug

Use when investigation hits an external knowledge boundary — cryptic error message, suspected library bug, framework behavior that may be a known issue, or a version-specific breaking change.

**This is not a replacement for code tracing.** Use only after internal investigation has produced a hypothesis or a confirmed symptom that needs external verification.

## When to Trigger

- Error message yields no results in local codebase or logs.
- Behavior is correct per local code but wrong at runtime — suspect library/runtime bug.
- Upgrading a dependency correlates with the bug appearing.
- Behavior is nondeterministic in a way that suggests a known upstream issue.
- Framework/platform behavior does not match documented contract.

## Depth Floor (non-negotiable)

- Minimum **2 independent sources** before concluding. If only 1 available, state that explicitly.
- Minimum **2 keyword variations** per search (e.g., exact error string + library name + version; then paraphrase + framework name).
- Use exact error strings (stripped of local paths/IDs) as the primary search term.

## MCP Priority

1. **Context7** — for library/framework docs and changelogs (`resolve-library-id` → `get-library-docs`). Check changelogs for the version range where the bug appeared.
2. **Tavily** — web search for error messages, GitHub issues, community reports (`tavily-search`). Enable if disabled.
3. **Brave Search** — fallback if Tavily unavailable (`brave_web_search`).
4. GitHub Issues on the relevant repo directly (via `fetch_url` or Tavily) — filter by version label.

Enable search MCPs before use if they are disabled by default.

## Search Strategy

For each search, try in order:
1. Exact error string (strip file paths and variable names).
2. Library name + version + symptom description.
3. Framework name + behavior description (for behavior-not-error cases).

Stop when 2+ independent sources confirm or contradict the hypothesis.

## Required Verdict

Every use of this skill must produce one of three verdicts:

| Verdict | Meaning |
|---|---|
| **Known issue** | 2+ sources confirm this is a reported upstream bug or breaking change. Include version range, issue/PR link, and official workaround if any. |
| **Local bug** | Sources show the library/framework behaves as expected; the bug is in the consuming code. Include what the correct behavior should be. |
| **Unknown** | No authoritative answer found. State what was searched, best hypothesis, and confidence level. |

Never return "you should research more" as the final output. Always synthesize.

## Output Contract

Every response must include:

- **Verdict**: `known issue` / `local bug` / `unknown`
- **Evidence**: sources found, what each confirmed or contradicted
- **Sources cited**: URL + quality tier (official / community / blog)
- **Workaround or fix direction**: concrete next step based on verdict
- **Feeds back into**: which hypothesis in the active debug session this confirms or rules out

If verdict is `unknown`:
- State exact search terms tried.
- State what partial evidence exists and its confidence (high / medium / low / unverified).
- Recommend safest reversible next diagnostic step.

## Source Quality Tiers

| Tier | Examples | Trust |
|---|---|---|
| 1 — Official | Library docs, source repo, spec, changelog | Highest |
| 2 — Release | GitHub release notes, migration guides | High |
| 3 — Issue tracker | GitHub Issues, official forums | Medium — flag as unofficial |
| 4 — Community | Stack Overflow, Reddit, Discord archives | Medium-low — cross-verify |
| 5 — Blog/Tutorial | Dev.to, Medium | Low — require corroboration |

When sources conflict: prefer higher tier. State the conflict explicitly.

## Integration With Debug Workflow

After returning the verdict, explicitly state how it affects the active debug session:

- **Known issue → confirmed**: update hypothesis list, apply official workaround, verify fix.
- **Known issue → workaround unavailable**: escalate or pin dependency version, document.
- **Local bug confirmed**: return to root-cause-debugging with narrowed search space.
- **Unknown**: re-rank hypotheses; do not block on external research — proceed with best local hypothesis.

Do not let external research stall the debug loop. One research pass, then back to investigation.
