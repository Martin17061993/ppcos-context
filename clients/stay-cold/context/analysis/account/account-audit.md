# Account Audit Report

**Date:** 2026-08-06
**Account:** 3599116618 (Stay Cold Apparel) · MCC 5591362086
**Vertical:** D2C e-commerce (apparel), EUR
**Mode:** full (all 5 modules, 24 diagnostics)
**Overall Score:** 75% — Good

---

## Executive read

75% means the plumbing is in better shape than the account's economics suggest. Location targeting, exclusion method, ad rotation, tracking templates and Display-Network hygiene are all clean across all 15 enabled campaigns — the settings layer is not what is costing money here. The score is held down by one hard structural failure and one fragmentation problem, both concentrated in Performance Max.

Three things this week. **First, five enabled PMax campaigns have served zero impressions for 30 straight days** — `SCALING I BROAD`, `SKANDI I TESTING I PROSPECTING`, `FRA I TESTING I BROAD`, `USA I TESTING I BROAD`, `WW I PROSPECTING I BROAD` — while reporting `serving_status = SERVING` and holding €359/day of nominal budget. Nothing is being wasted in euros, but every budget-allocation and channel-mix number in this account is computed against budgets that cannot spend, and that is very likely part of Gap G7. Either fix the asset groups or pause them; leaving them enabled is the worst option. **Second, brand match types have drifted back to the thing that was measured as a 278% win when it was removed.** DE brand runs 5 of 5 enabled keywords on broad match, SKANDI runs 4 of 4 on broad. FRA runs all exact and posts the highest brand clean ROAS in the account (88.4) while SKANDI posts the lowest (25.8). business.md records "Removing broad match from brand — SKANDI 2024-09-23: +278%" and guardrail DON'T-4 says brand campaigns must not use broad match. The account is violating its own documented guardrail on its highest-value asset. **Third, the single ad group doing all non-brand search work is not tight** — `STAN I BROAD I HOME` carries 17 keywords across punk, tattoo, goth and metal, mixed with the generic head term `mens hoodies`, served by 3 RSAs. That is business.md's priority #3 campaign and its stated expansion candidate; splitting by subculture is the mechanism.

One finding that is not a problem but reads like one: 21% of enabled keywords appear in more than one campaign. All five are brand terms duplicated across the geo-separated DE/FRA/SKANDI/USA brand campaigns — that is correct multi-market structure, not cannibalisation, and acting on it would breach DON'T-4. Two DSA ad groups show zero ads; both are confirmed serving (6,545 and 3,363 impressions) and the gap is an artifact of an RSA-shaped data pull. AUD-D17 (ad schedule) is skipped by design — no GAQL coverage.

No peer audits exist yet in `context/analysis/`, so nothing could be cross-validated. That matters most for AUD-D02: brand separation is proven clean on the keyword side but unverifiable for the €10,900/mo PMax PROSPECTING campaign without served search-term data, which is why it lands at WARN rather than PASS.

Module scoring and the full diagnostic tables follow; jump to Critical Issues for the actionable list.

Baseline run — no prior score to compare against.

---

## Module Scores

| Module | Score | Grade | Checks Passed | Checks Failed | Checks Skipped |
|--------|-------|-------|---------------|---------------|----------------|
| Structure | 57% (43/75) | Needs Attention | 3 | 2 | 0 |
| Naming | 80% (8/10) | Good | 1 | 0 | 0 |
| Settings | 89% (47/53) | Good | 5 | 0 | 1 |
| Ad Groups | 92% (23/25) | Excellent | 3 | 0 | 0 |
| Defaults | 100% (5/5) | Excellent | 1 | 0 | 0 |
| **Overall** | **75% (126/168)** | **Good** | **13** | **2** | **1** |

*Passed = PASS. Failed = FAIL. Remaining 8 diagnostics are WARN (partial credit). Point denominators use the severity table in `diagnostic-rules-shared.md` (Critical 15 / High 10 / Medium 5 / Low 3), not the summary totals in SKILL.md, which are internally inconsistent — the skill itself sets this precedent for the Ad Groups module.*

---

## Critical Issues

| Priority | ID | Issue | Impact | Routing |
|----------|----|-------|--------|---------|
| 1 | AUD-D08 | 5 enabled PMax campaigns with **0 impressions over 30 days**, all reporting `serving_status = SERVING` | €359/day nominal budget that cannot spend. Corrupts every budget-allocation, channel-mix and pacing figure. Likely contributor to Gap G7 | `/pmax-auditor` (asset groups), `/feed-auditor` (listing group / product exclusion), `/budget-auditor` |
| 2 | AUD-D05 | Budget fragmentation across **two** groups: the 5 dormant PMax campaigns (€35–105/day each), and `OVER-INDEX` (10.3 conv) + `NEAR INDEX` (3.0 conv), both far under the 50-conv/mo tROAS floor and overlapping FOKUSPRODUKTE/PROSPECTING intent | Data starvation. Neither index campaign can feed Smart Bidding; both fragment signal away from the two campaigns that carry 67% of spend | `/budget-auditor`, `/pmax-auditor` |
| 3 | AUD-D02 | Brand separation is **clean on keywords** (0 brand terms in non-brand Search) but **unverifiable for PMax** — no served search-term data exists | The €10,900/mo PMax PROSPECTING campaign may be harvesting brand demand and reporting it as prospecting. Would inflate its 1.96 clean ROAS | `/search-term-auditor` (ST-D25 owns PMax brand share) |
| 4 | AUD-D19 | URL expansion / text-asset automation not consistently configured. `TEXT_ASSET_AUTOMATION = OPTED_IN` on **USA brand**, Search TOF and DSA. No explicit URL-expansion setting on the €10,900/mo PROSPECTING campaign or `SCALING I BROAD` | Google auto-generates headlines/descriptions on a protected brand campaign, against the hard copy rules in business.md §10. PMax default URL expansion sends the biggest spender to arbitrary pages | `/pmax-auditor` (url-expansion module), `/ad-copy-specialist` |

**Not in this table but higher business impact than any of them:** the brand broad-match drift (AUD-D06 note) and the conversion-goal override pattern (AUD-D24). Both scored PASS because they satisfy the diagnostic's literal test, and both are the most consequential things this audit found. See those rows.

---

## Structure Results (AUD-D01–D08)

| ID | Diagnostic | Status | Points | Details |
|----|-----------|--------|--------|---------|
| AUD-D01 | Campaign type separation | PASS | 10/10 | 15 enabled campaigns: 6 SEARCH, 2 SHOPPING, 7 PERFORMANCE_MAX. All 6 Search campaigns have `target_content_network = false`. Clean separation. **Note:** two campaigns mix `SEARCH_STANDARD` and `SEARCH_DYNAMIC_ADS` ad groups (`Kollektionen + Types` and `JM I DSA`) — allowed by Google, but keyword and dynamic targeting compete inside one budget |
| AUD-D02 | Brand/non-brand separation | WARN | 6/10 | 5 dedicated brand campaigns (DE, USA, SKANDI, FRA enabled; ESP paused). **0** brand-matching keywords found in any non-brand campaign across all 1,022 keyword rows. Shopping/PMax cannot be verified — no `pmax-search-terms.csv` exists in any of the three canonical locations. Per rule step 5, capped at WARN. `EXCLUSIONS FOR BRAND` (3,135 negatives) is attached to FOKUSPRODUKTE per business.md §5, so Shopping is likely protected; the 7 PMax campaigns have no equivalent documented |
| AUD-D03 | Campaign-to-business alignment | WARN | 3/5 | Structure fits the ecommerce vertical (Shopping + PMax + Search + brand). The 10 spending campaigns map to roles documented in business.md §5. The 5 dormant PMax campaigns and the paused ESP brand campaign (Gap G22) have no documented purpose. Deeper issue: business.md §11 and Gaps G3/G4a record that **Google is not defined as a channel** in the client's own marketing strategy and no revenue target exists — so alignment cannot be fully validated against anything |
| AUD-D04 | Campaign count efficiency | PASS | 5/5 | Exactly 15 enabled campaigns — at the threshold, not over it. **Caveat that nearly inverts this:** 7 of 15 are below the 30-conv/month Smart Bidding floor (5 at zero, `OVER-INDEX` 10.3, `NEAR INDEX` 3.0). And these are *reported* conversions on the inflated series — on the clean purchase-only series, `JM I DSA` at 33.5 reported is likely ~17 and also below the floor. One more enabled campaign flips this to FAIL |
| AUD-D05 | Budget fragmentation | **FAIL** | 0/5 | **Two** groups of underfunded campaigns with overlapping intent. Group A: `SCALING I BROAD` €105/d, `USA I PMAX I TESTING I BROAD` €85/d, `SKANDI I PMAX I TESTING I PROSPECTING` €85/d, `FRA I PMAX I TESTING I BROAD` €49/d, `WW I PMAX I PROSPECTING I BROAD` €35/d — all zero conversions, all PMax prospecting/broad. Group B: `OVER-INDEX + INDEX + NEAR-INDEX` (€45/d, 10.3 conv) and `SHOPPING I PUR I T-ROAS I NEAR INDEX` (€95/d, 3.0 conv) — same index-based product segmentation already covered by FOKUSPRODUKTE and PROSPECTING |
| AUD-D06 | Redundant targeting overlap | PASS | 10/10 | 5 of 24 unique enabled keywords (20.8%) appear in >1 campaign — **all five are `stay cold` variants duplicated across the geo-separated DE / FRA / SKANDI / USA brand campaigns.** Correct multi-market structure, not competition; acting on it would breach DON'T-4. 0 duplicates across ad groups within a campaign. *Assumption stated: geo criteria are not pulled by this skill. Verify via `/geo-schedule-auditor` before treating the geo separation as proven.* **Separate finding surfaced here — see below** |
| AUD-D07 | Zero-conversion campaigns | WARN | 9/15 | Same 5 campaigns as D08. Zero conversions, but also **zero spend** — no euros are being wasted, so this does not meet the FAIL bar (>€100 spend). Flagged as hygiene, not waste. Root cause is D08 |
| AUD-D08 | Zero-impression campaigns | **FAIL** | 0/15 | 5 enabled campaigns, **0 impressions across the full 2026-07-04 → 2026-08-02 window**, all with `serving_status = SERVING`: `EX I WW I PMAX I SCALING I BROAD`, `EX I SKANDI I PMAX I TESTING I PROSPECTING`, `EX I FRA I PMAX I TESTING I BROAD`, `EX I USA I PMAX I TESTING I BROAD`, `EX I WW I PMAX I PROSPECTING I BROAD`. Combined nominal budget €359/day. `adgroups.csv` contains no rows for any of them. For feed-only PMax the usual causes are a missing or incomplete asset group, an empty listing group, or a feed-level product exclusion |

**Module Score:** 43/75 (57%) — Needs Attention

### Finding surfaced under D06 — brand broad-match drift (High)

Not scored, because D06 tests keyword duplication and this passes that test. Reporting it because it is the highest-confidence finding in the audit.

| Brand campaign | Enabled keywords | Match types | Clean ROAS (business.md §5) |
|---|---|---|---|
| `EX \| FRA \| SEARCH \| BRAND` | 5 | **5 exact** | **88.4** |
| `EX \| USA \| SEARCH \| BRAND` | 6 | 2 exact, 3 phrase, 1 broad | 60.3 |
| `EX \| DE \| SEARCH \| BRAND` | 5 | **5 broad** | 57.2 |
| `EX \| SKANDI \| SEARCH \| BRAND` | 4 | **4 broad** | **25.8** |

Match-type restrictiveness and clean ROAS rank in the same order across all four markets. business.md records "Removing broad match from brand — SKANDI 2024-09-23: **+278%**" under *What worked*, and guardrail DON'T-4 explicitly lists "no broad match" for brand campaigns. SKANDI is now back to 100% broad and is the weakest of the four. This is a documented win that has been undone.

Constraint: brand campaigns are do-not-touch (DON'T-4) and rollouts must be staggered 1–2 weeks per market (DON'T-9). This is a proposal for Jonas, single-market first — SKANDI, where the precedent was measured.

---

## Naming Results (AUD-D09–D10)

| ID | Diagnostic | Status | Points | Details |
|----|-----------|--------|--------|---------|
| AUD-D09 | Campaign naming convention | WARN | 3/5 | A convention exists (`OWNER I MARKET I TYPE I THEME`) but with **two incompatible delimiters**: 11 campaigns use the capital letter `I`, 4 brand campaigns use the pipe `\|`. Using `I` as a separator breaks programmatic parsing and is visually indistinguishable from `\|` — concretely, `config/ads-context.config.json → brandedCampaigns` lists the pipe form, so any tooling splitting on `\|` handles 4 campaigns and mis-parses 11. Also: 3 campaigns carry no market token (`EX I SHOPPING I FOKUSPRODUKTE`, `EX I SHOPPING I PUR I T-ROAS I NEAR INDEX`, `JM I DSA I FC'S I CAT'S`); 2 names exceed the 75-char guideline (103 and 78 chars); special characters `+` and `'` in use. **Worst single case:** `EX I EN I WW I TOF I BROAD I PUR I T-CPA II BROAD I NO PROMO I Kollektionen + Types` says `T-CPA` but the campaign runs `MAXIMIZE_CONVERSION_VALUE` — the name is factually wrong about its own bid strategy |
| AUD-D10 | Ad group naming consistency | PASS | 5/5 | 0 of 10 enabled ad groups use a generic name. All are descriptive (`STAN I BROAD I HOME`, `Sommer Fokus`, `SHIRTS + FOKUSMÄRKTE`, `DE \| STAN \| BRAND (EN)`, …). One generic name exists — `Anzeigengruppe 1` in SKANDI brand — but it is REMOVED and out of scope. Same `I` vs `\|` delimiter split as D09 |

**Module Score:** 8/10 (80%) — Good

---

## Settings Results (AUD-D11–D19)

| ID | Diagnostic | Status | Points | Details |
|----|-----------|--------|--------|---------|
| AUD-D11 | Display Network opt-in | PASS | 10/10 | All 6 enabled SEARCH campaigns: `target_content_network = false`. The #1 budget-wasting misconfiguration is absent. (PMax showing `true` is inherent to the type, not a finding) |
| AUD-D12 | Search Partners review | WARN | 3/5 | Enabled on 5 of 8 Search/Shopping campaigns: Search TOF, DE brand, USA brand, FRA brand, `SHOPPING I PUR I T-ROAS I NEAR INDEX`. Disabled on 3: DSA, SKANDI brand, **FOKUSPRODUKTE**. business.md records "Disabling search partners — FOKUSPRODUKTE 2025-09-18: **+17%**" under *What worked* — so the one campaign where it was tested and won has it off, and the lever was never rolled out anywhere else. No documented rationale for the current split. Note DON'T-9: stagger, do not roll out account-wide same-day |
| AUD-D13 | Location targeting method | PASS | 10/10 | All 15 enabled campaigns: `positive_geo_target_type = PRESENCE`. No deprecated `AREA_OF_INTEREST`. Fully consistent, and `PRESENCE` is the restrictive/preferred setting for a brand shipping to defined markets — this looks deliberate |
| AUD-D14 | Location exclusion method | PASS | 10/10 | All 15: `negative_geo_target_type = PRESENCE`. Exclusions actually block users physically in excluded areas |
| AUD-D15 | Language targeting consistency | WARN | 3/5 | Heuristic check (language criteria are not in this skill's GAQL). `EX I EN I WW I TOF …` encodes language explicitly. DE brand runs an English ad group (`DE \| STAN \| BRAND (EN)`) — consistent with business.md §13 "Working language: English". **The gap is SKANDI:** one campaign covers a four-language region (SE/NO/DK/FI) with a single ad group named `SWE \| STAN \| BRAND`. SKANDI also has the weakest brand clean ROAS of the four markets (25.8). No language separation |
| AUD-D16 | Ad rotation | PASS | 3/3 | All 15 enabled campaigns: `ad_serving_optimization_status = OPTIMIZE`. No `ROTATE_INDEFINITELY` |
| AUD-D17 | Ad schedule appropriateness | SKIP | — | Excluded from denominator per rule. Ad schedule data is not available in the campaign-settings GAQL. Owned by `/geo-schedule-auditor` |
| AUD-D18 | Tracking template consistency | PASS | 5/5 | **100% coverage, byte-identical across all 15 enabled campaigns:** `{lpurl}?trc_gcmp_id={campaignid}&trc_gag_id={adgroupid}&trc_gad_id={creative}` (Tracify, per business.md §7). business.md records "Targeted tracking-template cleanup — 2026-03-06 across three brands: +66 / +25 / +17%" — that work is complete and has held |
| AUD-D19 | URL expansion audit | WARN | 3/5 | Across 13 enabled Search/PMax campaigns, `FINAL_URL_EXPANSION_TEXT_ASSET_AUTOMATION` is OPTED_IN on 2 (Search TOF, USA brand), OPTED_OUT on 6, and **absent on 5** — including the €10,900/mo `PMAX I SCALING I FEED ONLY I PROSPECTING` and `PMAX I SCALING I BROAD`, which carry only a `GENERATE_IMAGE_EXTRACTION` entry. Absent means default, and the PMax default is ON. **Stated limitation:** the authoritative PMax field is `campaign.url_expansion_opt_out`, which this skill does not pull — the PMax reading is inferred, not confirmed. **Firmer sub-finding from the same field:** `TEXT_ASSET_AUTOMATION = OPTED_IN` on **USA brand**, Search TOF and DSA — Google auto-generates headlines and descriptions there. On the USA brand campaign that collides with business.md §10's hard copy bans ("Premium Quality", "Community", "Streetwear", emojis, fake urgency) and with the documented auto-apply incident that removed exact `[stay cold]` from DE brand two days before BFCM week 2024 |

**Module Score:** 47/53 (89%) — Good

---

## Ad Group Results (AUD-D20–D23)

| ID | Diagnostic | Status | Points | Details |
|----|-----------|--------|--------|---------|
| AUD-D20 | Thematic tightness | WARN | 3/5 | 4 of 5 enabled Search ad groups with 3+ keywords are tight = 80%, on the WARN boundary. The 4 tight ones are the brand ad groups — tight only because each holds 4–6 variants of one term. **The one loose ad group is the entire non-brand search program.** `STAN I BROAD I HOME` (€5,045/mo, 3 RSAs) holds 17 keywords diverging on two axes at once: subculture (punk ×5, tattoo ×4, goth ×4, metal/rock ×3) and product type (`punk rock shirts` vs `punk hoodie` vs `punk and rock outfit`), plus the generic head term `mens hoodies`. Fails the Single Ad Test — no one RSA credibly serves `cute goth clothes`, `t shirt metal` and `mens hoodies`. Per the rules table, product-type divergence is an *always split* |
| AUD-D21 | Ads per ad group | PASS | 10/10 | All 5 enabled standard Search ad groups have ≥1 enabled approved RSA (Search TOF has 3; each brand ad group has 1). The 2 ad groups showing zero ads — `DYN I BROAD I HOME` and `BROAD I DYN I Kategorie` — are `SEARCH_DYNAMIC_ADS`, which serve dynamically generated ads that do not populate `responsive_search_ad.headlines`. Both are confirmed serving (3,363 and 6,545 impressions; 34.7 and 33.5 conversions), so this is a data artifact, not a gap. **Note:** the 4 brand ad groups each run exactly **1** RSA against a 2–3 recommendation. Brand assets demonstrably move this account ("Clearing expired sale assets — SKANDI 2026-01-13: +396%"), but DON'T-4 makes this Jonas's call |
| AUD-D22 | Impression distribution | PASS | 5/5 | All 10 enabled ad groups clear the operative >10 impressions/week criterion (window = 4.29 weeks). Against the rule's headline 1,000/wk data-density guideline, 2 fall short: `DYN I BROAD I HOME` (784/wk) and `STAN I BROAD I LOW & TOP` (**127/wk**). The latter is the whole of `SHOPPING I PUR I T-ROAS I NEAR INDEX` — €24 spend, 3 conversions — and is genuinely data-starved, reinforcing D05 Group B. *The rule text is internally inconsistent (headline <1,000/wk vs PASS criterion >10/wk); scored on the explicit PASS criterion, both reported* |
| AUD-D23 | SKAG detection | PASS | 5/5 | 0 of 5 enabled Search ad groups with keywords contain exactly one keyword. SKAG rate 0%. No legacy single-keyword fragmentation |

**Module Score:** 23/25 (92%) — Excellent

---

## Defaults Results (AUD-D24)

| ID | Diagnostic | Status | Points | Details |
|----|-----------|--------|--------|---------|
| AUD-D24 | Account-level defaults | PASS | 5/5 | Conversion goals are intentionally configured, not left at Google's defaults — which is what this diagnostic tests. **But the configuration is the inverse of what you would assume, and that is the finding.** 14 of 15 enabled campaigns override the account default with `goal_config_level = CAMPAIGN` pointing at one shared custom goal, `customConversionGoals/6446192748`. Exactly one campaign — `EX I EN I WW I TOF … Kollektionen + Types` — uses `CUSTOMER`, the account default. This is the mechanical explanation for the anomaly business.md §6 flags but does not resolve: Search TOF records zero NewCustomerPurchase and its nominal tROAS 5.19 means 5.19, while the other 14 are inflated ×1.28–1.94. **So the account default is the clean configuration; the 14 campaign-level overrides are what break target comparability.** business.md §6's preferred fix — "remove NCP from the bidding goals so targets mean what they say" — is therefore *remove or repoint 14 campaign-level overrides*, not *change the account default*. Hard constraint: DON'T-8, account-level conversion changes are humans-only, never agent-executed. Also noted: 21 paused campaigns still carry CAMPAIGN-level overrides (legacy clutter). Auto-apply manual-review item is already answered in business.md §7 (keyword/asset auto-apply off; bidding auto-apply paused 2026-07-03). Account-level audience defaults remain unverified — not available via GAQL |

**Module Score:** 5/5 (100%) — Excellent

---

## Routing Recommendations

No peer audit reports exist in `context/analysis/` — this is the first audit run for this client, so nothing could be cross-validated and every handoff below is a fresh run.

| Specialist | Why | Priority |
|-----------|-----|----------|
| Run `/pmax-auditor` | Owns AUD-D08's most likely root cause (asset groups) and the url-expansion module for AUD-D19. 7 of 15 enabled campaigns are PMax and 5 of them serve nothing. Also closes Gap G21 (PMax asset-group deep dive, pulled 2026-07-03, never analysed) | **High** |
| Run `/search-term-auditor` | Only way to resolve AUD-D02 to PASS or FAIL. ST-D25 owns PMax brand-share analysis — needed to know whether the €10,900/mo PROSPECTING campaign's 1.96 clean ROAS is prospecting or harvested brand demand | **High** |
| Run `/keyword-auditor` | Owns the brand broad-match drift (D06 note) and the `STAN I BROAD I HOME` split (AUD-D20). Both are proposals for Jonas under DON'T-4 / DON'T-9, not direct actions | **High** |
| Run `/budget-auditor` | AUD-D05 fragmentation plus €359/day of budget attached to non-serving campaigns. Also the right place to close Gap G7 (why FOKUSPRODUKTE / PROSPECTING report budget-constrained at ~30% utilisation) | **High** |
| Run `/tracking-specialist` | AUD-D24: quantify and stage the removal of the 14 campaign-level goal overrides. This is the single highest-leverage item in the account per business.md §6, and it is DON'T-8 humans-only | **High** |
| Run `/feed-auditor` | Secondary candidate root cause for AUD-D08 — feed-only PMax with an empty listing group or product-level exclusion serves nothing | Medium |
| Run `/bidding-auditor` | Nominal tROAS targets are not comparable across campaigns until D24 is resolved. Owns the FOKUSPRODUKTE 3.53 → ~4.5 and PROSPECTING 3.60 → ~4.7 recalibration | Medium |
| Run `/geo-schedule-auditor` | Owns AUD-D17 (skipped here). Also verifies the geo separation this audit assumed when passing AUD-D06, and the SKANDI multi-language question from AUD-D15 | Medium |
| Run `/ad-copy-specialist` | AUD-D19 sub-finding: `TEXT_ASSET_AUTOMATION` opted in on the USA brand campaign against business.md §10 copy rules. Also the 1-RSA-per-brand-ad-group note from AUD-D21 | Medium |
| Run `/account-changelog` | Not run — `context/account-changelog.md` does not exist. Without it, none of these findings can be dated. The 5 zero-impression PMax campaigns in particular need a "when did this start" answer | Medium |

---

## Data Freshness

| Data Source | Last Updated | Status |
|-------------|-------------|--------|
| `account/campaigns-settings.csv` | 2026-08-06 | Pulled fresh (45 rows) |
| `account/keywords-all.csv` | 2026-08-06 | Pulled fresh (1,022 rows) |
| `account/conversion-goal-config.csv` | 2026-08-06 | Pulled fresh (45 rows) |
| `campaigns.csv` | 2026-08-03 | OK — 3 days old, 84 rows, window 2026-07-04 → 2026-08-02 |
| `adgroups.csv` | 2026-08-03 | OK — 3 days old, 11 rows |
| `ads.csv` | 2026-08-03 | OK — 3 days old, 22 rows |
| `keywords.csv` | 2026-08-03 | OK — 3 days old, 38 rows (not used; superseded by `keywords-all.csv`) |
| `context/account-changelog.md` | — | **Missing.** Recent-change context unavailable for all findings |

**Notes on scope and exclusions:**
- 2 ended experiment campaigns exist in the account (`… Exact Match vs Broad - DE I DACH I SEARCH`, `… EX I Keyword Options Final Test`). Neither is ENABLED, so no exclusion filtering was required.
- `EX | ESP | SEARCH | BRAND` is PAUSED and therefore outside all enabled-campaign checks. Gap G22 (dormant by design or overlooked) remains open.
- All conversion figures cited from `campaigns.csv` are the **reported** series, inflated ×1.28–1.94 per campaign. Where that changes a conclusion it is called out (AUD-D04).
