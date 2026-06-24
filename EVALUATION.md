# Mintlify Evaluation — Scoring Rubric

Pilot site: **https://egora-9ac3e24c.mintlify.app/** · Repo: `schaufenster/docs` · Tier: **Free (Hobby)**

Score each dimension **1–5** (1 = blocker, 3 = acceptable, 5 = excellent). Rows marked **TBD** need a
human to test Ask-AI answer quality (automated testing hit a bot-verification CAPTCHA).

| # | Dimension | Score | Findings (pilot, 2026-06-24) |
| - | --- | :-: | --- |
| 1 | **Authoring DX** | **5** | MDX + components (`Card`, `Steps`, `Note`, `Accordion`, `CodeGroup`, `Update`, `Tabs`) all rendered first try. Git workflow clean: push to `main` → auto-redeploy in ~1–2 min. Content swapped from existing `docs/mcp/` with zero rework. |
| 2 | **Search + Ask-AI** | **TBD** | Search UI + "Ask Assistant" panel present and enabled on the free tier. **Answer quality untested** — automated query triggered a CAPTCHA. Test manually in EN + DE (queries below) and score. |
| 3 | **i18n / German** | **5** | Excellent. `/de` fully localizes: tabs, search labels, sidebar, all our German content, *and* Mintlify's own chrome. EN↔DE switcher works. Critical for the German market. |
| 4 | **Multi-audience** | **4** | Audience tabs (IT/Internal, Customers, Caterers, API) are clean and obvious. −1 because **internal-vs-external gating needs auth = paid** (see #7); on the free tier everything is public. |
| 5 | **AI-feeding (Claude)** | **4** | `/llms.txt` (full page index incl. API) and `/llms-full.txt` (21 KB full content) auto-generated — directly usable to ground the Claude Team "eGora KAM Assistant." −1: **`llms.txt` lists English pages only**; the German `/de` pages are not indexed. |
| 6 | **API reference** | **4** | OpenAPI sample generated real interactive endpoint pages. Works well. Note: the *real* app spec (`storage/api-docs/api-docs.json`) is stale (2023) and must be regenerated via l5-swagger before a real API reference. |
| 7 | **Cost model** | **3** | Free (Hobby) tier already gives: public site, search, Ask-AI, `llms.txt`, full i18n, API reference, 1 editor. **Paid is required for what a real internal KB needs:** authentication/SSO (Private docs), custom domain (e.g. `docs.egora-catering.de`), analytics, and multiple editors. ⚠️ **Confirm current pricing/tiers at mintlify.com/pricing** — don't take a remembered number as fact. |
| 8 | **Maintenance fit** | **4** | Migrating existing material was trivial (copied `docs/mcp/` + adapted `egora-kam-assistant/knowledge/`). Open org question (not a tool issue): the discipline of writing a release note per shipped feature — the `it/feature-changelog` pattern is the proposed answer. |

## Test checklist

- [x] Site builds and is reachable at the `*.mintlify.app` URL.
- [x] All four tabs render; EN↔DE switch works; API tab shows generated endpoints.
- [x] `/llms.txt` and `/llms-full.txt` exist and contain pilot content.
- [ ] **Run ~5 EN + ~5 DE Ask-AI queries; record relevance per query.** ← your turn
- [ ] Confirm exactly which capabilities are gated behind paid tiers (auth, custom domain, analytics, seats) and the price.
- [ ] Check the analytics dashboard (likely paid-gated).

## Sample queries to try (EN / DE)

- "How do I connect Claude Desktop to eGora data?" / "Wie verbinde ich Claude Desktop mit eGora-Daten?"
- "What's the formula for the Converted KPI?" / "Wie ist der Converted-KPI definiert?"
- "What appears on the caterer delivery sheet?" / "Was steht auf dem Lieferschein?"
- "Which cities does eGora serve?" / "Welche Städte bedient eGora?"
- "How does the cancellation guarantee work?" / "Wie funktioniert die Stornogarantie?"

## Decision

**Recommendation (preliminary, pending Ask-AI test):** **Lean GO for a paid pilot.** Authoring, i18n, and
AI-feeding are strong; the deciding factors are (a) Ask-AI answer quality in German and (b) the real
monthly cost once auth + custom domain are required.

**Realistic monthly cost for a real internal KB:** _(fill after confirming pricing — needs the tier that
unlocks Private/auth + custom domain + analytics)_

**Key risks / conditions:**
- Internal content must be **auth-gated** before any real (non-sample) data goes in — paid feature.
- `llms.txt` German coverage gap if Claude grounding in German is wanted.
- API reference depends on regenerating the stale l5-swagger spec.

**If GO — next step:** evaluate Mintlify as the git-backed Claude-context source
(`PROPOSAL_CLAUDE_TEAM_ROLLOUT.md`) feeding both the human site and Claude via `llms.txt` / MCP,
replacing the manual `egora-kam-assistant` markdown→Project paste workflow.
