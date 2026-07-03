# Research With Current Sources

Use when knowledge may be stale, an API/library has changed, or no clear solution is known.

## MCP Priority

1. Project docs and source code.
2. Official docs and release notes.
3. **Context7** — library/framework docs lookup (`resolve-library-id` → `get-library-docs`).
4. **Tavily** — web search for recent issues, migration notes, blog posts, changelog entries (`tavily-search`). Enable MCP first if disabled.
5. **Brave Search** — fallback web search if Tavily unavailable (`brave_web_search`). Enable MCP first if disabled.

Use the most specific source first. Do not web-search when Context7 has the answer.

## When to enable search MCPs

Tavily and Brave Search are disabled by default. Enable only when:
- Context7 lacks coverage for the library/topic.
- The question is about current events, recent releases, or community discussions.
- You need multiple independent sources to cross-verify.

## Output Contract

- Decision-relevant findings only.
- Source used (which MCP or local file).
- Impact on implementation/spec.
- Uncertainties that remain.
- If sources conflict, state the conflict and recommend the safer path.
