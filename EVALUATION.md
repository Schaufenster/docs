# Mintlify Evaluation — Scoring Rubric

Fill this in during the deploy test (Phase 2). Score each dimension **1–5** and add notes. At the end,
write a **go / no-go** recommendation plus the realistic monthly cost for a *real* internal, auth-gated,
German eGora KB.

How to score: 1 = blocker, 3 = acceptable, 5 = excellent / best-in-class.

| # | Dimension | What to check | Score (1–5) | Notes |
| - | --- | --- | :-: | --- |
| 1 | **Authoring DX** | MDX + components, git workflow, branch-preview deploys, edit-to-live speed | | |
| 2 | **Search + Ask-AI** | Answer relevance for real eGora questions, **especially in German** | | |
| 3 | **i18n / German** | EN↔DE switcher, German rendering, German search quality | | |
| 4 | **Multi-audience** | Tabs/groups per audience; how cleanly internal-vs-external would gate behind auth | | |
| 5 | **AI-feeding (Claude)** | Quality of auto-generated `/llms.txt` + `/llms-full.txt`; MCP-server option → fit for the Claude Team "eGora KAM Assistant" | | |
| 6 | **API reference** | Quality of the OpenAPI-generated playground | | |
| 7 | **Cost model** | Free tier vs what real use needs: auth/SSO, custom domain, analytics, >1 editor — and price | | |
| 8 | **Maintenance fit** | Effort to migrate `/plans/` + `egora-kam-assistant/knowledge/`; keeping docs in sync with shipped features | | |

## Test checklist (Phase 2)

- [ ] Site builds and is reachable at the `*.mintlify.app` URL.
- [ ] All four tabs render; EN↔DE switch works; API tab shows the playground.
- [ ] Run ~5 **English** and ~5 **German** queries against search + Ask AI; record relevance per query.
- [ ] Fetch `<site>/llms.txt` and `<site>/llms-full.txt`; confirm they contain the pilot content.
- [ ] Note exactly which capabilities are gated behind paid tiers (auth, custom domain, analytics, seats).
- [ ] Check the analytics dashboard (if available on the tier).

## Sample queries to try (EN / DE)

- "How do I connect Claude Desktop to eGora data?" / "Wie verbinde ich Claude Desktop mit eGora-Daten?"
- "What's the formula for the Converted KPI?" / "Wie ist der Converted-KPI definiert?"
- "What appears on the caterer delivery sheet?" / "Was steht auf dem Lieferschein?"
- "Which cities does eGora serve?" / "Welche Städte bedient eGora?"
- "How does the cancellation guarantee work?" / "Wie funktioniert die Stornogarantie?"

## Decision

**Recommendation:** _(go / no-go / go-with-conditions)_

**Realistic monthly cost for a real internal KB:** _(tier + price; what it unlocks)_

**Key risks / conditions:** _…_

**If go — next step:** evaluate Mintlify as the git-backed Claude-context source
(`PROPOSAL_CLAUDE_TEAM_ROLLOUT.md`) feeding both the human site and Claude via `llms.txt` / MCP.
