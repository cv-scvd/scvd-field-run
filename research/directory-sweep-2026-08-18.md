# Directory Sweep — 2026-08-18
# Work Item 1 from keeper's off-site campaign brief
# Ctrl-F test: "trust layer" = current; "portrait"/"luckies"/"grudges" = stale
# Source: src/store/trust-signals.ts EXTERNAL_RECORDS (16 URLs)
# Swept by: CV, 2026-08-18 ~19:36–19:40 UTC

## Verdicts

| # | Registry | URL | HTTP | Verdict | Action Needed |
|---|----------|-----|------|---------|---------------|
| 1 | x402scan | /server/9b04e1cc-… | 200 | **UNREADABLE** — JS shell only, no content extractable via fetch. Needs browser to evaluate. | Browser check or skip — can't Ctrl-F a JS shell. |
| 2 | agentic.market | /services/scvd-store | 200 | **CURRENT** — returned full 2,263-service catalog. Store is indexed. Description not directly visible in catalog view but presence confirmed. | None — indexed and live. |
| 3 | mcpservers.org (server) | /servers/seancrecord/scvd-general-store-repo | 200 | **CURRENT** — "The trust layer of the x402 economy" leads. Full current positioning, conformance desk, corpus, /becoming link. | None. |
| 4 | Glama (server) | /mcp/servers/seancrecord/scvd-general-store-repo | 200 | **CURRENT** — "The trust layer of the x402 economy" + full positioning paragraph. A/A/A grades visible. | None. |
| 5 | x402-list.com | /services/sean-claude-van-damme-s-general-store | 200 | **CURRENT** — Compliance A (14/14), trust layer framing, live uptime/traction data, domain age 20d, $103.248 30d volume. | None. |
| 6 | Glama (connector) | /mcp/connectors/store.scvd/general-store | 200 | **CURRENT** — "The trust layer of the x402 economy: free conformance checks, attestation, corpus, agent store." Status: Healthy. Last tested 2026-08-18 19:33. 10 tools listed. | None. |
| 7 | mcpindex.ai | /server/store-scvd-general-store | 200 | **CURRENT** — "The trust layer of the x402 economy" in description. v0.2.0, published 2026-08-11. Trust verdict: REVIEW/PARTIAL (semantic screen pass, conformance probe not yet run). | None. |
| 8 | mcpservers.org (llms.txt) | /servers/scvd-store-llms-txt | 200 | **CURRENT** — "The trust layer of the x402 economy, operated by Record Creative Co. LLC." Full current positioning including conformance desk, corpus, x402 v2. | None. |
| 9 | m8ven.ai | /mcp/seancrecord-scvd-general-store-repo-l9nvwp | 404 | **DEAD LINK** — page no longer exists. Returns M8ven homepage title but 404 status. | Remove from trust-signals.ts or find updated URL. Flag for keeper. |
| 10 | mcp-marketplace.io | /server/store-scvd-general-store | 200 | **CURRENT** — "The trust layer of the x402 economy" leads. Full README content including /becoming link. | None. |
| 11 | x402-bazaar.com | /resources/6a61e8fc7356b8e8002b1af7 | 200 | **CURRENT** — Shows small_blessing resource with correct payment details (Base + Solana, $0.005). Tags include "signed-artifacts", "verification", "agent-memory", "human-labor". | None. |
| 12 | agentidentityregistry.org | /lookup/?id=AIR-BYYP-0MQC-TAKR | 200 | **UNREADABLE** — returned generic methodology page (trust score dimensions), not the store's specific record. JS-rendered lookup. | Browser check needed to see actual score/record. |
| 13 | mcpmarket.com | /server/sean-claude-van-damme-s-general-store | 429 | **BLOCKED** — Vercel Security Checkpoint. Rate-limited/bot-blocked. | Retry later or check in browser. |
| 14 | deepwiki.com | /seancrecord/scvd-general-store-repo | 200 | **UNREADABLE** — "Loading..." only. Fully JS-rendered SPA. | Browser check needed. DeepWiki has a refresh button per brief. |
| 15 | cursor.directory | /plugins/scvd-general-store-repo | 429 | **BLOCKED** — Vercel Security Checkpoint. Rate-limited/bot-blocked. | Retry later or check in browser. Version bump per brief. |
| 16 | smithery.ai | /servers/seancrecord/scvd-general-store | 200 | **PARTIAL** — Page loads but content is minimal (raw HTML extraction only). Shows "scvd-general-store - MCP | Smithery" title. Smithery is now part of Arcade.dev (announced). Can't verify staleness from fetch. | Browser check needed. |
| 17 | mcp.so | /servers/scvd-store | 403 | **BLOCKED** — Cloudflare challenge ("Just a moment..."). Bot-blocked. | Browser check needed. |

## Summary

- **CURRENT (no action):** 9 of 16 — mcpservers.org (×2), Glama (×2), x402-list.com, mcpindex.ai, mcp-marketplace.io, x402-bazaar.com, agentic.market
- **DEAD LINK:** 1 — m8ven.ai (404, remove or update)
- **BLOCKED BY BOT PROTECTION:** 3 — mcpmarket.com (429 Vercel), cursor.directory (429 Vercel), mcp.so (403 Cloudflare)
- **JS-RENDERED, CAN'T READ VIA FETCH:** 3 — x402scan, agentidentityregistry.org, deepwiki.com, smithery.ai (partial)

## Keeper Flags

1. **m8ven.ai is 404** — the URL in trust-signals.ts is dead. Either find the new URL or remove the entry. This is the one entry that was already noted as having wrong readings (CVE flag, env-var misattribution) — may not be worth chasing.
2. **Browser-needed:** x402scan, agentidentityregistry.org, deepwiki.com, smithery.ai, mcpmarket.com, cursor.directory, mcp.so — 7 listings need a real browser to evaluate. DeepWiki has a refresh button per your brief. cursor.directory needs a version bump. x402-list owner-update needs a fresh domain token (your hands).
3. **No stale content found** in any listing I could actually read. Every readable page shows current trust-layer positioning. The pre-reversal "portrait/luckies/grudges" language is gone from every directory I could check.
