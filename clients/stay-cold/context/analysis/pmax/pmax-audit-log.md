# PMax Audit Log

## 2026-08-06 — Run: full · 60-day window

- **Active Roster:** 7 of 12 campaigns scored · 5 excluded (dormant: paused, 0 impr) · 0 experiments · vertical `ecommerce` · 2 Feed-Only / 5 Full Assets
- **Mechanical scores:** 94–97/100 across all 7 ("strong"). **Do not quote as health** — for 5 of the 7 the score measures configuration on campaigns that cannot serve
- **Top hypothesis (Structural, high confidence): five enabled PMax campaigns are BFCM-2025 shells with every asset group paused.** 52 asset groups across the 5, **zero enabled**, all `ASSET_GROUP_PAUSED`. Listing groups intact (98–122 rows each, all feed-connected). Asset-group names are Black Week / BFCM '25 / Reign-of-Blood / Intra-Day promo assets — paused when those promos ended, campaigns never turned off with them

**Scorer blind spot documented (not silently corrected):** `asset-groups` scored 100/100 on a campaign with 14/14 groups paused — it counted paused groups as "eligible." The three modules that would have caught it (`asset-performance`, `channel-allocation`, `url-expansion`) all returned n/a *because* nothing served. Absence of serving was read three times as "not applicable" and never once as "broken." Mechanical scores left intact; serving status reported alongside every one.

**Cross-audit resolutions:**

| Prior finding | Status |
|---|---|
| Account AUD-D08 — "5 zero-impression PMax, cause unknown" | ✅ **Root-caused: all asset groups paused** |
| Account AUD-D19 — "PROSPECTING may run default-ON URL expansion" | ✅ **False alarm** — 0 expansion rows over 60 days; expansion is OFF. The USA-brand `TEXT_ASSET_AUTOMATION` half stands |
| Account AUD-D02 — "PMax brand separation unverifiable" (WARN) | ⬆️ **Substantially improved** — brand exclusion ON across all 7 (negative BRAND_LIST, shared set `10982324974`). Not fully closed; served-query proof still needs `/search-term-auditor` ST-D25 |
| Budget BUD-D16 — "5 zero-spend, likely policy/approval/targeting" | ✅ None of those — paused asset groups |
| Bidding BID-D01/D03 — "7 campaigns below volume floor" | ✅ 5 of 7 are these shells — structural, not a bidding decision |
| **My own feed note (today)** — "likely no asset group with populated listing group" | ❌ **Wrong on mechanism, corrected.** Listing groups are populated and feed-connected |

**New findings:**
- **104 policy-restricted assets, 61 live, 24 live-disapproved** — all in the 5 dormant shells (17 in `WW PROSPECTING BROAD`, 7 in `SCALING I BROAD`). Both serving campaigns are clean. Harmless today; a landmine the moment anything is re-enabled — and the changelog shows a creative rebuild in progress (113 Editor changes 2026-08-05, 38 on 08-06)
- **NCA mode is inconsistent** — `TARGET_NEW_CUSTOMER` on 4, `BID_HIGHER_FOR_NEW_CUSTOMER` on 3, `TARGET_ALL_EQUALLY` on 1 dormant. Both live spenders run the most aggressive setting (excludes existing customers entirely). business.md documents account intent as "bid for new customers only" — the 3 `BID_HIGHER` shells don't match it
- **PMX-D22 value-premium SKIPPED, not scored 0** — new-vs-existing LTV genuinely unavailable (Gap G2). Routes to `/strategy-specialist`
- **Creative quality is unmeasured** — 585 live creative assets, none above the 100-impression floor. No asset-level signal to select from if the rebuild proceeds
- Channel mix: 98.8% Shopping-share (SEARCH-feed 86.3% / CONTENT-feed 12.2%), YouTube €3.72 with 0 conversions. Expected shape for Feed-Only ecom; symptom-only, no PMax lever

**Phase 0 questions resolved from business.md, not asked** (auto-mode): vertical = ecommerce (§1 "no lead gen, no subscription"); NCA intent = ON/deliberate (§7, verified 2026-08-03); LTV = unavailable → SKIP (Gap G2). No writeback — nothing new learned.

**Routing:** Jonas (enable one asset group or pause, per campaign) → clear 24 live-disapproved assets before any re-enable → review existing budget / account / competitive reports (all fresh 2026-08-06, no re-run) → `/merchant-auth` + `/feed-auditor full` → `/search-term-auditor` (closes AUD-D02) → `/strategy-specialist` (NCA premium + mode inconsistency)

**Outputs:** `pmax-audit.md` · `campaign-inventory.{md,json}` · `module-scores/` (7 campaigns) · 8 `{module}-flags.json` for `/pmax-optimizer`
