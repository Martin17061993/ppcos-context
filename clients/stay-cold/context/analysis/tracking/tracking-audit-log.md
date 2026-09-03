# Tracking Audit Log

## 2026-08-07 — Score: 171/260 (66% · Needs Attention) · Mode: full

- **Sources:** 47 conversion actions · 45 goal configs · 1 custom goal · 450 campaign-goal rows · 47 attribution rows · 14 daily rows · live page inspection (passive)
- **Chrome scope:** passive only. Full conversion test declined — it would create a real add-to-cart on the client's live Shopify store, and the skill requires explicit consent for that specific action. **D13–D16 SKIP, not FAIL.**

| Module | Score | Verdict |
|---|---|---|
| Completeness (D01–D07) | 35/80 (44%) | D01 PASS · D02 WARN · **D03 FAIL** · **D04 FAIL** · D05 WARN · D06 PASS · **D07 FAIL** |
| Tag Health (D08–D17) | 50/50 avail (100%) | D08–D12 all PASS · D13–D17 SKIP |
| Consent (D25–D29) | 33/45 (73%) | D25 PASS · **D26 FAIL** · D27 PASS · D28 PASS · D29 WARN |
| Attribution (D30–D35) | 42/50 (84%) | D30 PASS · D31 WARN · D32 WARN · D33/D34/D35 PASS |
| OCT (D36–D41) | SKIP | No offline imports exist — no UPLOAD_CLICKS / UPLOAD_CALLS actions |
| Hygiene (D42–D45) | 11/35 (31%) | **D42 FAIL** · **D43 FAIL** · D44 WARN · D45 PASS |
| Advanced (D46–D50) | SKIP | Needs GTM API |

### THE HEADLINE: business.md's measurement model is verified correct

`metrics.conversions_value` is fed by exactly two actions over 2026-06-30..07-29:

| Action | Conversions | Value | Share |
|---|---|---|---|
| `purchase_gads_mable` | 2,001.5 | €282,627 | 66.4% |
| `Custom NewCustomerPurchase - Stay Cold Mable` | 1,037.6 | €143,297 | 33.6% |
| **Account inflation factor** | | | **1.51** *(business.md: 1.50)* |

Per-campaign: DE brand 1.43/1.42 · USA brand 1.54/1.53 · FOKUSPRODUKTE 1.82/1.81 · PROSPECTING 1.79/1.88 · DSA 1.90/1.93 · OVER-INDEX 1.51/1.45 · **Search TOF 1.00/1.00**. Only divergence is NEAR INDEX (1.64 vs 1.28) on €729 of value — noise.

**All twelve prior audits' deflations are validated. No re-runs required on measurement grounds.**

### Mechanism proven, not inferred

Custom goal **6446192748 "EX I Stay Cold - Käufe + New Customers"** = `purchase_gads_mable` + `Custom NewCustomerPurchase` (the latter `primary_for_goal = false`, category DEFAULT). Used by **14 of 15 enabled campaigns** at CAMPAIGN level. The 15th (Search TOF) runs on the CUSTOMER default, whose only biddable category containing a primary action is PURCHASE — which is why its factor is exactly 1.00, derived from first principles rather than assumed.

**Corollary: the fix is to remove the 14 overrides, not to change the account default.** Confirms account-audit AUD-D24 exactly.

### Bidding audit's open question closed

The 2026-08-06 bidding audit flagged a +€42.20 conversion value rule as a possible third inflation layer. **Measured: no.** Both contributing actions average ~€140/conversion ≈ the €143 AOV. The 1.51 factor is fully explained by NewCustomerPurchase alone. No third layer.

### METHODOLOGY WARNING — a near-miss worth recording

An intermediate run of the same query **without an explicit date filter** returned lifetime data, showed six actions feeding the value metric (adding `GA4 (web) purchase` and `Google Shopping App Purchase`), and produced an apparent **Search TOF factor of 2.62**. That would have invalidated eleven audits and reversed two headline conclusions.

Caught by one sanity check: implied conversion value exceeded campaign spend by 20×. Re-run with the range written into the GAQL → 1.00.

**`query.js --days=N` did NOT inject a date filter** on this `FROM campaign` + `segments.conversion_action_name` query. Write `segments.date BETWEEN ...` into the GAQL and pass `--no-date-range`.

The lifetime result was not worthless — it independently rediscovered **business.md's regime 1** (Aug 2023 – Apr 2024, GA4 + Shopping App counting purchases in parallel). The three-regime model is now API-verified.

### Other findings

- **Consent Mode v2 fully implemented** — all four signals present — **but all four default to `granted`**. GDPR exposure for a Berlin-registered advertiser. ⚠️ Browser profile already held consent cookies, so this needs one clean-incognito check to confirm it isn't a stored-decision artefact
- **business.md's claim of "10 HIDDEN primary-for-goal legacy UA goals" is factually wrong** — only 2 of 47 actions are `primary_for_goal = true`, and all 47 are ENABLED (none HIDDEN)
- **`YouTube follow-on views` is primary** on a pure ecommerce account — but **0 of 45 goal rows have YOUTUBE_FOLLOW_ON_VIEWS biddable**, so it is inert today. Risk materialises only when Video/Demand Gen relaunches. Disable before the rebuild lands
- **47 actions to bid on one.** Purchase ×6, add-to-cart ×4, begin-checkout ×5, page-view ×4, across Mable / GA4 / Google Shopping App / legacy UA. Five actions still named "(OLD)" and ENABLED at zero conversions
- **`GA4 (web) sale` = 1,155,388 lifetime conversions** — 20× the primary purchase action. Almost certainly counting line items or sessions. Feeds nothing today; a reporting hazard, not a bidding one
- **Tag health is clean.** `gtag` present, containers **AW-939278187** + **G-J05E0KQ84Z** loaded, `_gcl_au` set, no quiet conversions, volume +7% across the 14-day window
- **Attribution on the primary action is ideal** — DATA_DRIVEN, 30d click / 1d view. Estate-wide it is mixed: 24 DATA_DRIVEN / 9 LAST_CLICK / 14 UNKNOWN, and 38 actions at 30d vs 9 at 90d
- **`url-health-check.js` 403s recorded 2026-08-06 remain a false positive** — bot protection, verified in a real browser

### Peer integration (Phase 3.5) — 12 fresh reports, zero contradictions

bidding 54 · budget 47 · keyword 85% · search-term 79% · strategy 77% · competitive 73 · lp 56% · offer 97% · account 75% · geo-schedule 75% · placement 48% · pmax. All 2026-08-06/07. Every one deflated using business.md factors that are now API-verified. **Unusually clean — the measurement risk carried as an open block through this entire session is real in effect but accurately quantified.**

### Routing

1. Verify consent defaults in clean incognito (5 min, only finding with legal weight)
2. Remove the 14 campaign-level goal overrides — **humans-only under guardrail DON'T-8, route to Jonas**
3. Disable `YouTube follow-on views` as primary before the DG/Video rebuild lands
4. Delete the five "(OLD)" actions + `Leads - Stay Cold Mable`
5. Investigate `GA4 (web) sale` at 20× the primary action
6. Re-baseline after the goal fix — reported ROAS becomes clean ROAS, and every target can be stated in one currency
7. Shopify reconciliation to close **Gap G1** (gross vs net — moves break-even 1.6↔1.9). Also resolves D17

**Report:** `context/analysis/tracking/tracking-audit.md`
