# Feed Audit Log

## 2026-08-06 — BLOCKED at preflight (no score)

- Requested mode: `full` (auto-mode selection) | **Not run** — Merchant API preflight gate not cleared
- **Blocker: OAuth, not configuration.** Merchant account ID was recoverable from Google Ads data (`116274940`, from `shopping_product.resource_name`), and a live pull was attempted. `pull-data.js` validated Google Ads access, then failed: `[oauth-failed] Could not exchange GOOGLE_ADS_REFRESH_TOKEN for an access token.` The stored token carries Ads scopes but not Merchant scopes. Requires an interactive browser sign-in → `/merchant-auth "Stay Cold Apparel"`
- `merchantCenter.enabled` deliberately left **false**; discovered `accountId` saved so the auth step is pre-answered
- Feed label **DE** only (1,817/1,817) — no main-market ambiguity when the audit does run
- Report: `context/analysis/feed/feed-preflight-blocked.md` — **not** a feed audit, no score, do not cite as coverage

**Ads-side evidence gathered while blocked (answers open questions from three earlier audits):**

| Finding | Detail |
|---|---|
| **Zero products fully eligible** | 817 `ELIGIBLE_LIMITED` (45%), 1,000 `NOT_ELIGIBLE` (55%), 0 unrestricted. 278 are IN_STOCK but NOT_ELIGIBLE — the actionable set |
| **Real DE issues are apparel attributes** | Missing `color` 1,009 (55.5%), `age group` 674 (37.1%), `gender` 674 (37.1%) — all required for apparel in DE. Plausible contributor to FOKUSPRODUKTE's 31.1% rank-lost IS |
| **Three "100%" issues are noise** | `invalid_currency_for_country`, `missing_shipping…`, `missing_business_registration_number` all hit 1,817/1,817 — but `affected_regions` is **KR/BR only**. Irrelevant to a DE feed. Reading the counts without the region field produces a badly wrong conclusion |
| **The 5 dead PMax campaigns serve zero products** | Only 4 campaigns appear in `shopping-performance.csv`. Narrows AUD-D08 from "unknown cause" to **product coverage** — not budget, bid strategy or approval |
| **OVER-INDEX and NEAR INDEX are starved upstream** | 13 and **1** product respectively. Three audits called them "sub-scale for smart bidding"; the real cause is that they point at almost no inventory |
| Feed plumbing intact | 0 missing brand / category / title / price |
| 6 products | `landing_page_error` — "Product page unavailable". Small and easy, and it feeds the LP-experience problem the competitive audit found |

**Next:** `/merchant-auth "Stay Cold Apparel"` → set `enabled: true` → re-run `/feed-auditor full`. The `images` module is the priority once unblocked — business.md's documented "PDP truth gap" is an image problem, and today's competitive audit tied below-average landing page experience to 6 of 6 scored non-brand keywords.
