# eGora Docs — Mintlify Pilot

A **scoped evaluation** of whether [Mintlify](https://mintlify.com) (docs-as-code) is the right home for
eGora's internal knowledgebase. This is **not** the real documentation — it's a small, representative
slice with **non-sensitive sample content only**, built to test authoring, search/AI, German support,
the API reference, and cost.

See [`EVALUATION.md`](./EVALUATION.md) for the scoring rubric to fill in during the deploy test.

## What's here

| Path | Purpose |
| --- | --- |
| `docs.json` | Mintlify config: EN + DE languages, audience tabs (IT/Internal, Customers, Caterers, API). |
| `index.mdx`, `de/index.mdx` | Landing pages (EN / DE). |
| `it/` | IT/internal slice: overview, MCP connector setup, KPI catalog excerpt, release-communication pattern. |
| `customers/`, `caterers/` | Customer- and caterer-facing samples. |
| `de/` | German mirror of a representative subset (tests i18n). |
| `api-reference/openapi.json` | Trimmed OpenAPI sample → tests Mintlify's API playground. |
| `favicon.svg` | Placeholder favicon (eGora teal). |

Seed content was adapted from the app repo: `docs/mcp/setup-claude-desktop-ui.de.md`,
`docs/mcp/kpi-cards.md`, and `storage/api-docs/api-docs.json`. Originals were left untouched.

## Run locally

> **Node version:** the Mintlify CLI only supports **LTS Node (18 / 20 / 22)** — it refuses Node 25+.
> This machine currently has Node 25, so install an LTS first, e.g. `brew install node@22` and prepend
> it to `PATH`, or use `nvm install 22 && nvm use 22`. (Deploying to Mintlify does **not** need local
> Node — only local preview does.)

```bash
cd egora-docs-pilot
npx mintlify@latest dev      # serves at http://localhost:3000
npx mintlify@latest broken-links
```

(Or install globally: `npm i -g mintlify` then `mintlify dev`.)

## Deploy to the free Hobby tier

1. `git init` here and push to a **new GitHub repo** (a private repo is fine; the published site is
   public on the free tier).
2. Create a free account at [dashboard.mintlify.com](https://dashboard.mintlify.com), install the
   **Mintlify GitHub App**, and connect the repo.
3. Mintlify deploys to a `*.mintlify.app` subdomain and rebuilds on every push to the default branch.

## Notes

- **Public** site, so no real/sensitive data. A real internal KB would need authentication (SSO /
  password) — a paid Mintlify feature, captured as a cost line in `EVALUATION.md`.
- The OpenAPI sample is intentionally trimmed; the full app spec is stale (2023) and must be regenerated
  via l5-swagger before any real API reference.
- Brand colours in `docs.json` (`#38808a` teal, `#092440` navy) are taken from the eGora frontend; the
  logo is a placeholder favicon.
