# Geo-Schedule Audit — 2026-08-06

**Overall Score:** 75% (57 / 76 available points) — **Good**
**Mode:** full · 14 diagnostics across 3 modules · 3 SKIPped
**Account:** 3599116618 (Stay Cold Apparel) · EUR · vertical: D2C e-commerce (apparel) · primary KPI: ROAS, break-even clean **1.9**
**Windows:** geo / device / schedule 30 days · demographics 90 days

---

## Executive read

75% is a fair reading: targeting hygiene in this account is mostly clean, and the one real failure is a setting that is currently doing nothing — which is both the good news and the reason it is worth fixing.

**Every enabled campaign in this account runs Smart Bidding.** Target ROAS, Maximize Conversion Value or Target Impression Share — there is no manual CPC anywhere. That single fact governs this whole audit, because Smart Bidding ignores location, device and demographic bid modifiers; only a −100% exclusion still bites. So most of the levers this skill normally recommends are unavailable by construction, and the ones that look available are inert.

**The one failure is worth reading twice.** The non-brand Search campaign carries **eleven location bid modifiers at +15%**, and they are pointed at the wrong countries. Among the boosted geos are Denmark (reported ROAS **0.47** — the worst in the account), Czechia (0.92) and Estonia (**zero conversions on 114 clicks**), alongside Canada, Italy, Switzerland and Australia, all of which sit at or below break-even once the inflated conversion series is deflated. Only Finland and Slovakia among the eleven are genuinely strong. Because Smart Bidding ignores them nothing is being harmed today — but somebody set a deliberate +15% on the account's weakest markets, and those adjustments would activate the moment the campaign moved to a manual or portfolio strategy. Remove them: it costs nothing and eliminates a live misconfiguration that also misleads anyone reading the account.

**What is genuinely not a problem, despite looking like it.** There are **no dead time windows** — not one of 168 hour-by-day slots has meaningful clicks and zero conversions, and no campaign has any ad-schedule restriction at all. Device variance is inside tolerance: desktop runs 26% below account average but deflates to roughly 5.6 against a 1.9 break-even, so it is comfortably profitable and excluding it would destroy value. And every demographic segment is profitable once you stop comparing against an average inflated by the untargetable "undetermined" bucket — the apparent 50% shortfalls on 65+ and high-income are artefacts of that comparison, not findings.

**One number in this report should not be trusted.** The year-over-year geographic comparison flags 21 locations, but it spans the 2025-11-10 conversion-tracking change, so it compares a clean prior year against an inflated current one. Treat it as unusable until the conversion goals are repaired.

Read the module tables, then the three actions at the end. Baseline run — no prior score to compare against.

---

## Module scores

| Module | Score | Grade | Detail |
|---|---|---|---|
| Geographic (GS-D01–D05) | 22 / 30 available | **73% — Good** | Targeting method and exclusion coverage clean; real ROAS spread across markets, but exiting them is a strategy call |
| Schedule & Device (GS-D06–D09) | 23 / 23 available | **100% — Excellent** | No dead windows, no harmful device variance, patterns confirmable over 5 weeks |
| Demographics & Advanced (GS-D10–D14) | 12 / 23 available | **52% — Needs attention** | Carried entirely by the GS-D11 modifier failure; demographics themselves are healthy |
| **Overall** | **57 / 76** | **75% — Good** | |

*Points allocation within each module follows the shared severity scale and the stated module maxima: Geo D01 5 / D02 10 / D03 10 / D04 5 / D05 5 = 35. Schedule D06 10 / D07 10 / D08 3 / D09 5 = 28. Demo D10 5 / D11 10 / D12 3 / D13 5 / D14 5 = 28. Three diagnostics SKIPped (15 points) are excluded from the denominator, never scored 0.*

---

## Critical issues

### 1. GS-D11 — FAIL — Eleven bid modifiers on Smart Bidding campaigns, aimed at the weakest markets

`EX I EN I WW I TOF … Kollektionen + Types` runs `MAXIMIZE_CONVERSION_VALUE` and carries a **+15% location bid modifier** on eleven geo targets. Smart Bidding ignores location bid adjustments, so they are inert — but the selection is the finding:

| Geo | Reported ROAS | Clean (÷1.50) | vs break-even 1.9 | Boosted +15%? |
|---|---|---|---|---|
| Denmark (2208) | **0.47** | 0.31 | ❌ worst in account | ✅ |
| Czechia (2203) | **0.92** | 0.61 | ❌ | ✅ |
| Estonia (2233) | — (**0 conversions**, 114 clicks) | — | ❌ | ✅ |
| Canada (2124) | 2.46 | 1.64 | ❌ | ✅ |
| Italy (2380) | 2.84 | 1.89 | ⚠️ at break-even | ✅ |
| Switzerland (2756) | 2.86 | 1.91 | ⚠️ at break-even | ✅ |
| Australia (2036) | 3.53 | 2.35 | ✅ thin | ✅ |
| Belgium (2056) | 5.43 | 3.62 | ✅ | ✅ |
| Slovakia (2703) | 10.32 | 6.88 | ✅ | ✅ |
| Finland (2246) | 15.06 | 10.04 | ✅ strong | ✅ |
| Luxembourg (2442) | below reporting volume | — | — | ✅ |

Nine of the eleven sit at or below the deflated break-even. **Recommendation:** remove all eleven. Zero risk (they do nothing today), removes a landmine if the bid strategy ever changes, and stops the account misrepresenting its own intent.
**Routing:** `/geo-schedule-optimizer` — remove ignored modifiers from Smart Bidding campaigns.

### 2. GS-D02 — WARN — €3,727 of 30-day spend sits below break-even by market

Thirty locations cleared the 50-click threshold. Deflating by the account-wide ×1.50 factor, these fall below the 1.9 break-even:

| Market | Cost | Reported ROAS | Clean |
|---|---|---|---|
| Canada | €1,378 | 2.46 | 1.64 |
| Netherlands | €797 | 2.22 | 1.48 |
| Denmark | €503 | 0.47 | 0.31 |
| Spain | €351 | 1.32 | 0.88 |
| Czechia | €325 | 0.92 | 0.61 |
| Ireland | €156 | 1.29 | 0.86 |
| Hungary | €96 | 1.36 | 0.91 |
| Ukraine | €68 | 0.00 | 0.00 |
| Estonia | €53 | 0.00 | 0.00 |
| **Total** | **€3,727** | | **10.8% of 30-day spend** |

Marginal (deflated 1.89–1.99, effectively at break-even): Italy €1,163, Switzerland €953, UK €1,711, Austria €320.

**Why this is a WARN and not a FAIL, and why I am not recommending exclusions.** business.md §1 states the business "sells worldwide" — broad geographic coverage in the WW campaigns is deliberate, not an oversight. Exiting nine markets is a strategy decision for Jonas, not a targeting-hygiene fix, and the deflation applies an account-wide factor to geo aggregates that mix campaigns with factors ranging 1.28–1.94, so per-market precision is limited. What is defensible is surfacing the number and letting the strategy owner decide.

### 3. GS-D03 — WARN — Two zero-conversion markets, €121 combined

Ukraine: 301 clicks, €68, zero conversions. Estonia: 114 clicks, €53, zero conversions. Both clear the 50-click gate. The euro impact is negligible, but 301 clicks with no conversion is a clean, safe exclusion — and Ukraine in particular is a market where fulfilment is likely impractical.
**Routing:** `/geo-schedule-optimizer geo` — exclude zero-conversion locations. Location exclusions **do** work under Smart Bidding, unlike modifiers.

---

## Module 1 — Geographic (GS-D01–D05): 22 / 30 (73%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| GS-D01 | Location targeting method | **PASS** | 5/5 | All enabled campaigns use `PRESENCE` for both positive and negative geo targeting. No deprecated `AREA_OF_INTEREST`. `PRESENCE` is the restrictive setting and the right one for a shipping-constrained retailer. Independently confirmed by account audit AUD-D13/D14 |
| GS-D02 | Geographic ROAS variance | **WARN** | 6/10 | 30 locations ≥50 clicks. Spread from France 47.93 to Denmark 0.47. €3,727 (10.8% of spend) below deflated break-even across 9 markets — see Critical issue 2 |
| GS-D03 | Zero-conversion locations | **WARN** | 6/10 | Ukraine (301 clicks, €68) and Estonia (114 clicks, €53). €121 combined — real but immaterial |
| GS-D04 | High-performing location opportunity | **SKIP** | —/5 | Impression-share data is not available at this location granularity, per the data-sufficiency gate. Noted for context: France 47.93, Greece 26.92, Norway 20.89, Sweden 17.06 — but these are largely brand-campaign driven and the brand campaigns are already at 92–96% impression share |
| GS-D05 | Exclusion coverage | **PASS** | 5/5 | Location exclusions are actively maintained: 195 negative LOCATION criteria across enabled campaigns (Search TOF 42, `SCALING I BROAD` 81, `OVER-INDEX` 72). Coverage is deliberate, not absent. Gap: Ukraine and Estonia are not among them (see GS-D03) |

**Top markets by spend (30 days, reported ROAS):** Germany €12,499 / 14.19 · USA €6,191 / 15.85 · Australia €3,570 / 3.53 · UK €1,711 / 2.99 · Canada €1,378 / 2.46 · Italy €1,163 / 2.84 · Finland €1,045 / 15.06 · Switzerland €953 / 2.86 · France €910 / **47.93** · Netherlands €797 / 2.22.

The pattern is clean and worth naming: **the markets with dedicated brand campaigns (DE, USA, FRA, SKANDI/Finland-Sweden-Norway) all perform strongly; the markets served only by the worldwide non-brand campaigns (CA, NL, DK, ES, CZ, IE, HU) are the ones below break-even.** That is a structural observation, not a geo-targeting one — it says brand demand carries this account, which every audit today has independently found.

---

## Module 2 — Schedule & Device (GS-D06–D09): 23 / 23 (100%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| GS-D06 | Device ROAS variance | **PASS** | 10/10 | Mobile 12.07 (+6% vs account, 35,220 clicks, €26,859) · Desktop 8.43 (−26%, 7,990 clicks, €7,460) · Tablet 29.77 (+163%, but only 188 clicks) · Connected TV zero traffic. No segment breaches ±30% with material volume. **Desktop deflates to ~5.6 against a 1.9 break-even — profitable. Do not exclude it.** Under Smart Bidding the only device lever is a −100% exclusion, which would destroy value here |
| GS-D07 | Ad schedule waste | **PASS** | 10/10 | **Zero dead windows.** Not one of 168 hour × day slots has ≥50 clicks and zero conversions. No campaign carries any `AD_SCHEDULE` criterion — everything runs 24/7, which is correct for e-commerce under Smart Bidding. Three weak hours exist but total €490: Sunday 06:00 (ROAS 0.91), Wednesday 06:00 (1.05), Friday 23:00 (1.65) |
| GS-D08 | Schedule consistency | **PASS** | 3/3 | 5 weeks of data (gate requires 4+). 793 of 1,568 slot-patterns are `confirmed` across weeks. Patterns are stable enough to act on — but there is nothing to act on, since GS-D07 found no waste |
| GS-D09 | Modifier stacking | **SKIP** | —/5 | No campaign carries two or more active modifier types. The only bid modifier anywhere in the account is the single location adjustment on Search TOF (GS-D11). Device criteria exist on every campaign but all sit at default with no adjustment |

**Day-of-week pattern (30 days, reported ROAS):** Friday **16.40** · Thursday 12.96 · Saturday 12.50 · Monday 10.57 · Tuesday 10.37 · Sunday 10.09 · Wednesday 9.72.

Friday is the standout, and it is not noise — the five best individual hour-slots in the account are **all Friday** (18:00 at 34.45, 05:00 at 28.91, 15:00 at 26.65, 19:00 at 25.04, 01:00 at 24.96). That aligns exactly with business.md §1: *"Drops, not seasons… weekly Friday drops (Thunder Drop Weeks)."* The demand pattern the business describes is visible in the hour data.

**No action recommended.** Smart Bidding already exploits time-of-day automatically, and adding a Friday schedule modifier would be ignored. This is confirmation that the drop cadence works, not a to-do.

---

## Module 3 — Demographics & Advanced (GS-D10–D14): 12 / 23 (52%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| GS-D10 | Demographic outliers | **PASS** | 5/5 | See the artefact note below — every known segment is profitable |
| GS-D11 | Smart Bidding modifier conflict | **FAIL** | **0/10** | 11 location modifiers at +15% on a `MAXIMIZE_CONVERSION_VALUE` campaign, aimed at the account's weakest markets. See Critical issue 1 |
| GS-D12 | Seasonal geo patterns | **WARN** | 2/3 | 21 locations flagged, but the comparison is unreliable — see below |
| GS-D13 | Demographic exclusion opportunity | **PASS** | 5/5 | 90 days of data (gate requires 60+). No segment qualifies for a −100% exclusion; all are profitable when deflated |
| GS-D14 | Geographic targeting optimization | **SKIP** | —/5 | Same impression-share gate as GS-D04 |

### The demographic "outliers" are a comparison artefact — not a finding

At first read the 90-day demographic data looks alarming: every known age band sits 17–50% below the account average, and high-income sits 55% below. That is entirely caused by the **untargetable `UNDETERMINED` bucket** — 22,981 clicks at ROAS 68.91 for age, 23,140 clicks at 67.64 for gender — which drags the blended average up to 23.70. That bucket is largely PMax and Shopping traffic where Google cannot resolve a demographic; it is not a segment anyone can bid on.

Recomputed against a **known-segments-only** baseline of **17.64**:

| Age band | Clicks | Cost | Reported ROAS | vs known-segment avg | Clean (÷1.50) |
|---|---|---|---|---|---|
| 25–34 | 31,935 | €20,776 | 19.57 | **+11%** | 13.0 |
| 35–44 | 11,477 | €7,804 | 16.16 | −8% | 10.8 |
| 18–24 | 8,979 | €5,953 | 15.01 | −15% | 10.0 |
| 55–64 | 1,149 | €695 | 17.65 | 0% | 11.8 |
| 45–54 | 3,361 | €2,399 | 13.06 | −26% | 8.7 |
| 65+ | 488 | €309 | 11.89 | −33% | 7.9 |

Only 65+ exceeds a 30% shortfall, on €309 of spend, and it still returns roughly **four times break-even**. There is no exclusion candidate here.

**Gender:** Male 16.95 (€29,698), Female 20.45 (€8,157) — female converts better per euro, both far above break-even. **Income:** the weakest bands are 90k+ (10.73) and 80–90k (11.58), which deflate to 7.2 and 7.7 — still roughly four times break-even.

The audience is exactly what business.md describes: a 25–34-skewed, male-majority subculture buyer. Nothing here needs targeting intervention.

### GS-D12 — the year-over-year comparison is not usable

`geo-seasonal-comparison.csv` flags 21 of 45 locations, with deviations like Spain +517%, Italy +207%, Netherlands +132%, Germany +77%. **Do not act on these.**

The comparison puts a current 30-day window (July 2026) against the same window a year earlier (July 2025) — but those two periods sit in **different conversion-counting regimes**. business.md §7 documents the boundary precisely: until 2025-09 the account counted only `purchase_gads_mable` (regime 2, clean); from 2025-11-10 it also counts `Custom NewCustomerPurchase` (regime 3, inflated ×1.28–1.94 per campaign). Every "prior year" figure in that file is clean and every "current" figure is inflated.

The distortion also runs in a counter-intuitive direction: inflation *adds* conversions to the current period, which *lowers* current CPA. So where the file shows CPA rising — Germany +77%, for instance — the real deterioration is **worse** than reported, not better. Germany's €8.85 current CPA against €4.99 prior becomes roughly €12.57 versus €4.99 once deflated by the DE brand factor of 1.42, i.e. **+152%**.

Two campaigns also changed budget by +42% to +109% inside this window (see the account changelog), which independently breaks any seasonal read.

**Verdict: WARN, with the recommendation being "fix measurement, then re-run" rather than any targeting change.**

---

## Recommended next steps

Peer reports were checked per Phase 2.5. Five are fresh and are quoted rather than re-run.

1. **Remove the 11 location bid modifiers from Search TOF.** Zero risk — they are already ignored. Removes a misconfiguration aimed at the account's worst markets and stops the settings misrepresenting intent. → `/geo-schedule-optimizer` (dry-run first)
2. **Exclude Ukraine and Estonia.** 415 clicks, €121, zero conversions. Location exclusions work under Smart Bidding where modifiers do not. → `/geo-schedule-optimizer geo`
3. **Take the €3,727 below-break-even market list to Jonas as a strategy question, not a targeting fix.** Nine markets, 10.8% of spend. business.md commits to selling worldwide; market exit is his call. → **Jonas**
4. **Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100, top finding: *an enabled conversion value rule adds +€42.20 per conversion against €16.46 documented, and 14 of 15 campaigns override the clean account-default conversion goal*. That is the same measurement fault that makes GS-D12 unusable and forces every ROAS figure in this report to be deflated by hand. **No re-run needed.**
5. **Review the existing 2026-08-06 competitive audit** at `context/analysis/competitive/competitive-audit.md` — 73/100, top finding: *landing page experience is BELOW_AVERAGE on 6 of 6 scored non-brand keywords*. It explains the geographic pattern here: the non-brand worldwide campaigns serve the below-break-even markets, and their constraint is page quality, not geography. **No re-run needed.**
6. **Review the existing 2026-08-06 budget audit** at `context/analysis/budget/budget-audit.md` — 47/100, top finding: *projected August spend of €78–93k against a €32,500 target*. Relevant because the budget increases of 17–24 July fall inside this audit's 30-day geo window and inflate the market-level spend figures above. **No re-run needed.**
7. **Re-run `/geo-schedule-auditor demo` after the conversion goals are repaired** — GS-D12 cannot produce a usable answer until then.
8. **No schedule action.** GS-D07 and GS-D08 are clean; the Friday strength is the drop cadence working as designed and Smart Bidding already exploits it.

### Cross-audit reconciliation

| Prior finding | Status after this audit |
|---|---|
| Account audit **AUD-D17** — ad schedule SKIPped, "requires additional API query", routed here | ✅ **Resolved.** No ad-schedule criteria exist on any campaign; all run 24/7; zero dead windows across 168 slots |
| Account audit **AUD-D13/D14** — geo targeting and exclusion method both PASS | ✅ Confirmed independently |
| Account audit **AUD-D06** — geo separation of brand campaigns assumed but unverified | ✅ **Confirmed.** Per-campaign LOCATION criteria show distinct market targeting; the brand-term duplication across DE/FRA/SKANDI/USA is genuinely geo-separated, not competing |
| Bidding audit **BID-D19/D20/D21** — bid adjustments PASS, 11 location modifiers noted as inert | ⬆️ **Escalated.** They are not merely inert — they are aimed at the weakest markets in the account. Scored FAIL here |

---

## Data freshness

| File | Rows | Status |
|---|---|---|
| `geo-schedule/campaign-criteria.csv` | 699 | Pulled fresh 2026-08-06 |
| `geo-schedule/schedule-performance.csv` | 1,568 | Pulled fresh — 30 days, 168 slots |
| `geo-schedule/demographics-age.csv` | 70 | Pulled fresh — 90 days |
| `geo-schedule/demographics-gender.csv` | 30 | Pulled fresh — 90 days |
| `geo-schedule/demographics-income.csv` | 57 | Pulled fresh — 90 days |
| `geo-user-location.csv` | 123 | Re-pulled 2026-08-06 (3-day window) |
| `device-performance.csv` | 32 | Re-pulled 2026-08-06 |
| `campaigns.csv` | 84 | Re-pulled 2026-08-06 |
| `evidence/schedule-consistency.csv` | 1,568 | Generated — 5 weeks, 793 confirmed patterns |
| `evidence/geo-seasonal-comparison.csv` | 45 | Generated — **unreliable, see GS-D12** |

⚠️ **Two standing caveats on every figure above.** (1) All ROAS values are the platform's inflated series; clean figures in this report apply the account-wide ×1.50 deflation, which is approximate at geo and segment level because per-campaign factors range 1.28–1.94. (2) The 30-day geo/device/schedule window contains the budget increases of 17–24 July (+42% to +109%), so market-level spend is not representative of a steady state.

**Tooling note:** `geo-schedule-auditor/scripts/` had no installed dependencies; `node_modules` was junctioned from `gads-context/scripts/` to make the two analyzer scripts executable.
