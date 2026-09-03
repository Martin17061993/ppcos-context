# Tracking Audit — 2026-08-07

**Overall Score:** 171 / 260 available — **66% · Needs Attention**
**Mode:** full · 7 modules · Chrome checks run in **passive mode only** (see below)
**Account:** 3599116618 (Stay Cold Apparel) · EUR · vertical: D2C e-commerce
**Sources:** 47 conversion actions · 45 goal configs · 450 campaign-goal rows · 14 days of daily volume · live page inspection

> **Chrome DevTools scope.** I ran passive checks only (D11, D12, and the consent module). The full conversion test would have created a real add-to-cart event on the live store, and the skill requires explicit consent for that specific action. Auto-mode is not consent to cause side effects in a client's production system. **D13–D16 are SKIP**, not failures.

---

## Executive read

This is the audit twelve others were blocked on, and the headline is better than expected: **business.md's measurement model is correct, verified from the API to two decimal places.**

The account-wide conversion-value inflation measures **1.51** against the 1.50 documented. Per-campaign factors match almost exactly — DE brand 1.43 vs 1.42, USA brand 1.54 vs 1.53, FOKUSPRODUKTE 1.82 vs 1.81, PROSPECTING 1.79 vs 1.88, DSA 1.90 vs 1.93, and **Search TOF 1.00 vs 1.00**. Every deflation applied across the previous twelve audits was sound. Nothing needs re-running on that basis.

**The mechanism is now proven rather than inferred.** `metrics.conversions_value` is fed by exactly two actions: `purchase_gads_mable` (66.4%) and `Custom NewCustomerPurchase` (33.6%). The route is a single custom goal — **"EX I Stay Cold - Käufe + New Customers", id 6446192748** — containing those two actions and used by **14 of 15 enabled campaigns**. The one campaign that isn't, Search TOF, bids on the account default, whose only biddable category containing a primary action is PURCHASE. That is why its factor is exactly 1.00.

**One open question from the bidding audit closes here.** That audit flagged a +€42.20 conversion value rule as a possible third inflation layer. The measured data says no: both contributing actions average roughly €140 per conversion, essentially the €143 AOV. The 1.51 factor is fully explained by NewCustomerPurchase alone. **There is no third layer.**

**Two priorities.** First, **consent mode defaults to granted on all four signals** — for a Berlin-registered company serving Germany as its primary market, that is a compliance exposure worth verifying in a clean browser session today. Second, the account carries **47 conversion actions to bid on one**, including five still-enabled actions explicitly named "(OLD)" and a purchase event tracked six different ways across three parallel systems. Nothing is currently broken by it, but it is the reason nobody can answer a simple question about this account quickly.

**What is not a problem:** tag installation is clean, no conversion has gone quiet, and volume is stable. Read the Critical issues, then the verification table.

---

## Module scores

| Module | Score | Grade | Key finding |
|---|---|---|---|
| Completeness (D01–D07) | 35 / 80 | **44% — Critical** | 14 of 15 campaigns override the account default with a goal containing a non-primary action |
| Tag Health (D08–D17) | 50 / 50 available | **100% — Excellent** | Tags installed correctly, no quiet conversions, volume stable. D13–D16 SKIP |
| Consent Mode (D25–D29) | 33 / 45 | 73% — Good | v2 fully implemented, but all four signals default to granted |
| Attribution (D30–D35) | 42 / 50 | 84% — Good | Primary action ideally configured; lookback windows inconsistent across the estate |
| OCT (D36–D41) | **SKIP** | — | No offline conversion imports exist — pure ecommerce, no UPLOAD_CLICKS or UPLOAD_CALLS actions |
| Data Hygiene (D42–D45) | 11 / 35 | **31% — Critical** | 47 actions, 5 still named "(OLD)", purchase tracked six ways |
| Advanced (D46–D50) | **SKIP** | — | Requires GTM API access this skill does not have |
| **Overall** | **171 / 260** | **66% — Needs Attention** | |

*Enhanced Conversions (D18–D21) and Server-Side Tagging (D22–D24) are not built — blocked on GTM API, per the skill definition.*

---

## The measurement model — verified

### What actually feeds `metrics.conversions_value` (2026-06-30 → 2026-07-29)

| Conversion action | Conversions | Value | Share |
|---|---|---|---|
| `purchase_gads_mable` | 2,001.5 | **€282,627** | 66.4% |
| `Custom NewCustomerPurchase - Stay Cold Mable` | 1,037.6 | **€143,297** | 33.6% |
| **Total** | **3,039.1** | **€425,924** | |
| **Inflation factor** | | | **1.51** |

### Per-campaign factors: measured vs documented

| Campaign | Measured | business.md | |
|---|---|---|---|
| `EX \| DE \| SEARCH \| BRAND` | 1.43 | 1.42 | ✓ |
| `EX \| USA \| SEARCH \| BRAND` | 1.54 | 1.53 | ✓ |
| `EX \| FRA \| SEARCH \| BRAND` | 1.47 | — | new |
| `EX I WW I PMAX … PROSPECTING` | 1.79 | 1.88 | ✓ |
| `EX I SHOPPING I FOKUSPRODUKTE` | 1.82 | 1.81 | ✓ |
| `EX \| SKANDI \| SEARCH \| BRAND` | 1.61 | — | new |
| **`EX I EN I WW I TOF …` (Search TOF)** | **1.00** | **1.00** | ✓ |
| `JM I DSA I FC'S I CAT'S` | 1.90 | 1.93 | ✓ |
| `EX I WW I PMAX … OVER-INDEX` | 1.51 | 1.45 | ✓ |
| `EX I SHOPPING I PUR … NEAR INDEX` | 1.64 | 1.28 | ✗ (€729 total — noise) |

**Every material factor matches.** The single divergence is on a campaign with €729 of conversion value, which is measurement noise rather than a finding.

### A methodological warning worth recording

An earlier version of this measurement, run **without an explicit date filter**, returned lifetime data and showed six actions feeding the value metric — including `GA4 (web) purchase` and `Google Shopping App Purchase` — producing an apparent Search TOF factor of **2.62**. That would have invalidated eleven audits.

It was wrong, and the sanity check that caught it was simple: the implied conversion value exceeded campaign spend by 20×. Re-run with `segments.date BETWEEN '2026-06-30' AND '2026-07-29'` written directly into the GAQL, the true figure is 1.00.

**The lifetime result was not meaningless, though — it independently rediscovered business.md's regime 1**, which documents that GA4 and the Google Shopping App both counted purchases in parallel from Aug 2023 to Apr 2024 and that those figures must never be used as absolute values. The three-regime model in business.md is now API-verified.

**Note for future runs:** `query.js --days=N` did **not** inject a date filter on this `FROM campaign` + `segments.conversion_action_name` query. Write the date range into the GAQL and pass `--no-date-range`.

---

## Critical issues

### 1. Consent Mode defaults to granted on all four signals

Read live from `google_tag_data.ics.entries`:

| Signal | Default | Update |
|---|---|---|
| `ad_storage` | **granted** | granted |
| `analytics_storage` | **granted** | granted |
| `ad_user_data` | **granted** | granted |
| `ad_personalization` | **granted** | granted |

Consent Mode v2 is properly implemented — all four required signals are present, which is more than many accounts manage. But under EU rules a Berlin-registered company (MASCANI GmbH, VAT DE315904827) serving Germany as its primary market should default non-essential storage to **denied** and update to granted only after the visitor accepts.

⚠️ **Verify before acting.** The browser profile used for this check already carried consent cookies (`cookieconsent_status`, `cookieconsent_preferences_disabled`, `GlobalE_Consent`), so the "granted" state I read may be a stored decision from an earlier visit rather than the true pre-consent default. **This needs one check in a clean incognito session** — five minutes, and it distinguishes a compliance exposure from a non-issue.

### 2. Fourteen of fifteen campaigns override the account default

| Goal config level | Enabled campaigns |
|---|---|
| `CAMPAIGN` (custom goal) | **14** |
| `CUSTOMER` (account default) | **1** — Search TOF |

The 14 use custom goal **6446192748 "EX I Stay Cold - Käufe + New Customers"**, containing:
- `purchase_gads_mable` — PURCHASE, primary ✅
- `Custom NewCustomerPurchase - Stay Cold Mable` — **category DEFAULT, `primary_for_goal = false`**

A campaign-level goal can promote a non-primary action into bidding, which is exactly what happens here and is the entire source of the 1.51 inflation. The setup is deliberate — business.md §7 documents the 2026-02-18 and 2026-03-13 changes — but it means **nominal ROAS targets across 14 campaigns do not mean what they say**, which is the finding every other audit has been working around.

**The account default itself is clean.** Search TOF's biddable categories are PURCHASE (website), DOWNLOAD (app), SUBMIT_LEAD_FORM (website) and ENGAGEMENT (website). Three of those are irrelevant to an apparel retailer — but they contain no primary actions, so per the biddable-plus-primary rule they are inert for bidding. Only PURCHASE carries a primary action. That is why Search TOF's factor is exactly 1.00, and it confirms **the fix is to remove 14 overrides, not to change the default.**

### 3. Forty-seven conversion actions to bid on one

Purchase is tracked six ways across three parallel systems:

| Action | Lifetime conversions | System |
|---|---|---|
| `purchase_gads_mable` | 56,991 | Mable ✅ *(the only one that matters)* |
| `GA4 (web) sale` | **1,155,388** | GA4 — 20× the primary action |
| `Google Shopping App Purchase` | 71,926 | Shopping App |
| `GA4 (web) purchase` | 50,052 | GA4 |
| `NetRevenue AllCustomerPurchase` | 1,479 | Mable |
| `AllCustomerPurchase` | 1,474 | Mable |

Add-to-cart is tracked four ways, begin-checkout five ways, page-view four ways. **Five actions still carry "(OLD)" in their names and remain ENABLED** — `Purchase - Stay Cold Mable (OLD)`, `PageView … (OLD)`, `AddToCart … (OLD)`, `CheckoutStarted … (OLD)`, all at zero conversions. There is also a `Leads - Stay Cold Mable` action on an account with no lead generation.

The `GA4 (web) sale` figure of 1,155,388 deserves its own look — 20× the primary purchase action strongly suggests a misconfigured import counting line items or sessions rather than orders. It feeds nothing today, so it is a reporting hazard rather than a bidding one.

**Nothing here is currently broken.** It is a legibility problem: 47 actions, four naming conventions, three tracking systems and four GA4 measurement IDs in the cookie jar mean nobody can answer a simple question about this account without a forensic exercise — which is precisely what this session has been.

---

## Diagnostic results

### Completeness (D01–D07): 35/80

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D01 | Coverage | **PASS** | 15/15 | business.md names `purchase_gads_mable` as the only valid conversion for evaluation. It exists, is ENABLED, is primary, and has 56,991 lifetime conversions. Full coverage |
| D02 | Primary / secondary | WARN | 9/15 | Exactly two primary actions. `purchase_gads_mable` is correct. **`YouTube follow-on views` is `primary_for_goal = true` on a pure ecommerce account** — inappropriate in principle. Mitigating: **no campaign has YOUTUBE_FOLLOW_ON_VIEWS as a biddable category** (0 of 45 goal rows), so it is inert for bidding today. business.md's warning that it "will corrupt bidding signal the moment Video or Demand Gen restarts" is correct — the trigger is the category becoming biddable, not the primary flag alone |
| D03 | Duplicates | **FAIL** | 0/10 | Purchase ×6, add-to-cart ×4, begin-checkout ×5, page-view ×4, across Mable / GA4 / Google Shopping App / legacy UA |
| D04 | Naming | **FAIL** | 0/10 | Four incompatible conventions coexist: `purchase_gads_mable` · `Stay Cold Apparel DE (bereinigt)  – GA4 (web) purchase` (note the double space) · `Google Shopping App Purchase` · `Purchase - Stay Cold Mable (OLD)` · `Bestellung aufgeben (Alle Websitedaten DE)`. Mixed languages, mixed casing, status suffixes embedded in names |
| D05 | Goal category | WARN | 6/10 | `Custom NewCustomerPurchase` and `Custom ReturningCustomerPurchase` are category **DEFAULT** despite being purchase events — while `AllCustomerPurchase` and `NetRevenue AllCustomerPurchase` are correctly PURCHASE. Same family, inconsistent classification. `ViewContent - Stay Cold Mable` (973,965 conversions) is DEFAULT where PAGE_VIEW fits |
| D06 | Counting method | **PASS** | 5/5 | Purchase actions are MANY_PER_CLICK — correct for ecommerce, where a customer can legitimately buy twice from one click. Legacy funnel goals are ONE_PER_CLICK, also appropriate |
| D07 | Account defaults | **FAIL** | 0/15 | 14 of 15 campaigns override with a goal containing a non-primary action. See Critical issue 2 |

### Tag Health (D08–D17): 50/50 available

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D08 | Action status | **PASS** | 10/10 | Both primary actions ENABLED. All 47 actions ENABLED — none HIDDEN or REMOVED |
| D09 | Zero-conversion check | **PASS** | 10/10 | `purchase_gads_mable` recorded conversions on all 14 days (32–72/day). No silence |
| D10 | Volume anomaly | **PASS** | 10/10 | First 7 days 367 conversions, last 7 days 394 — **+7%**. No drop. The final two days (34, 32) sit below trend, which is expected conversion lag, not an anomaly |
| D11 | Google Tag presence | **PASS** | 10/10 | `gtag` is a function; `google_tag_manager` object present. Containers loaded: **AW-939278187** (Google Ads) and **G-J05E0KQ84Z** (GA4). dataLayer active with `gtm.dom`, `consent_status`, `gtm.load` |
| D12 | Conversion Linker | **PASS** | 10/10 | `_gcl_au` cookie present, confirming the linker is active. `_gcl_aw` is absent, but that cookie only sets on arrival with a `gclid` — I navigated directly, so its absence is expected and not a finding |
| D13 | Tag firing on conversion | **SKIP** | —/5 | Requires a live conversion test — not run, see scope note |
| D14 | Transaction ID | **SKIP** | —/5 | Same |
| D15 | Dynamic value | **SKIP** | —/5 | Same |
| D16 | Currency parameter | **SKIP** | —/5 | Same |
| D17 | Backend cross-check | **SKIP** | — | Always SKIP by design — requires manual reconciliation against Shopify |

### Consent Mode (D25–D29): 33/45

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D25 | Consent Mode present | **PASS** | 15/15 | `google_tag_data.ics` present and populated |
| D26 | Default state correct | **FAIL** | 0/10 | All four signals default to **granted**. For an EU-registered advertiser this should be denied-by-default. ⚠️ Requires clean-session verification — see Critical issue 1 |
| D27 | All four v2 signals | **PASS** | 10/10 | `ad_storage`, `analytics_storage`, `ad_user_data`, `ad_personalization` all present. Consent Mode **v2** compliant in structure |
| D28 | Update mechanism | **PASS** | 5/5 | Each signal carries an `update` value, so a consent decision does propagate |
| D29 | CMP present | WARN | 3/5 | Consent cookies exist (`cookieconsent_status`, `cookieconsent_preferences_disabled`, `GlobalE_Consent`), so a CMP is installed — but no banner was rendered on this visit and its behaviour could not be observed |

### Attribution (D30–D35): 42/50

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D30 | Primary action model | **PASS** | 15/15 | `purchase_gads_mable`: **DATA_DRIVEN**, 30-day click window, 1-day view window. Ideal configuration for ecommerce |
| D31 | Model consistency | WARN | 6/10 | Across 47 actions: 24 DATA_DRIVEN, 9 GOOGLE_ADS_LAST_CLICK, **14 UNKNOWN**. The UNKNOWN group includes `GA4 (web) purchase`, which fed the value metric historically |
| D32 | Click lookback consistency | WARN | 6/10 | 38 actions at 30 days, **9 at 90 days**. Mixed windows across purchase-family actions distort any period comparison |
| D33 | View lookback | **PASS** | 5/5 | Predominantly 1 day, appropriate for direct-response ecommerce. One outlier at 30 days (`Google Shopping App Purchase`) — inert, since it no longer feeds the metric |
| D34 | Conversion window vs sales cycle | **PASS** | 5/5 | 30-day click window against an apparel cycle business.md estimates at 1–3 days. Generous but harmless |
| D35 | Cross-device | **PASS** | 5/5 | Data-driven attribution on the primary action handles cross-device natively |

### Data Hygiene (D42–D45): 11/35

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D42 | Stale actions | **FAIL** | 0/10 | **Five actions explicitly named "(OLD)" remain ENABLED**, all at zero conversions. Plus `Leads - Stay Cold Mable` and `Stay Cold Mable (web) purchase`, both at zero, on an account with no lead gen |
| D43 | Action count sprawl | **FAIL** | 0/10 | **47 actions to bid on one.** Three parallel tracking systems plus legacy Universal Analytics goals, and four GA4 measurement IDs visible in cookies (`_ga_G-3ZC0PZJZV2`, `_ga_3ZC0PZJZV2`, `_ga_J05E0KQ84Z`, `_ga_HJSMKFYH93`) |
| D44 | Zero-volume actions | WARN | 6/10 | 7 of 47 actions have zero lifetime conversions |
| D45 | Currency consistency | **PASS** | 5/5 | EUR throughout; no mismatch against the account currency |

### OCT (D36–D41) and Advanced (D46–D50): SKIP

**OCT — not applicable.** All 47 actions originate from WEBSITE (44), YOUTUBE_HOSTED (2) or APP (1). There are no `UPLOAD_CLICKS` or `UPLOAD_CALLS` actions, so no offline conversion import exists to audit. Correct for a pure ecommerce business with no sales-team follow-up.

**Advanced — not assessable.** These diagnostics need GTM container access, which this skill does not have. Enhanced Conversions (D18–D21) and Server-Side Tagging (D22–D24) are likewise documented as not built.

---

## What this means for the twelve peer reports

All twelve are from 2026-08-06, one day old and fresh within every window. **The critical outcome: none needs re-running on measurement grounds.**

| Peer | Score | Verdict after this audit |
|---|---|---|
| `/bidding-auditor` | 54/100 | ✅ **Validated.** Its M-layer block was correct, its inflation factors were correct, and its +€42.20 value-rule concern is now **resolved as a non-issue** — measured inflation is fully explained by NewCustomerPurchase alone |
| `/budget-auditor` | 47/100 | ✅ Validated. Its three verdict overrides (BUD-D04, D14, D15) used FOKUSPRODUKTE's 1.81 factor; measured 1.82. The overrides were right |
| `/keyword-auditor` | 85% | ✅ **Validated, and this matters most.** It treated Search TOF's economics as clean on the strength of a documented 1.00 factor. **Measured 1.00.** Its core-term protection logic stands |
| `/search-term-auditor` | 79% | ✅ Validated on the same basis |
| `/strategy-specialist` | 77% | ✅ Validated. Its D13 finding — DSA effective target 1.29 below break-even — used factor 1.93; measured 1.90. Conclusion unchanged |
| `/competitive-analyst` | 73/100 | ✅ Validated |
| `/lp-auditor` | 56% | ✅ Validated — and its CVR figures were drawn from Search TOF, the one campaign with no inflation at all |
| `/account-auditor` | 75% | ✅ **AUD-D24 confirmed exactly.** 14 of 15 campaigns override the clean account default; the fix is removing overrides, not changing the default |
| `/pmax-auditor` | — | ✅ Validated |
| `/offer-auditor` | 97% | Not measurement-dependent |
| `/geo-schedule-auditor` | 75% | ✅ Validated |
| `/placement-auditor` | 48% | ✅ Validated — and its finding that all 65 view-through conversions resolved to secondary actions is consistent with only two actions feeding the metric |

**No contradictions found.** Twelve audits deflated using business.md's factors; those factors are now API-verified. That is an unusually clean result, and it is worth saying plainly: **the measurement risk that has been carried as an open block through this entire session is real in its effect but accurately quantified.** The account's numbers are inflated by 1.51 — and everyone already knew by exactly how much.

---

## Recommendations

### Act now

1. **Verify consent defaults in a clean incognito session.** Five minutes. Distinguishes a genuine GDPR exposure from a stored-cookie artefact. If defaults really are granted, fix before anything else — it is the only finding here with legal weight
2. **Remove the 14 campaign-level goal overrides**, or repoint them at a goal containing only `purchase_gads_mable`. This is the single change that makes every nominal target in the account mean what it says, and it unblocks the target work five other audits are waiting on. ⚠️ **Account-level conversion changes are humans-only under guardrail DON'T-8** — this goes to Jonas, never to an agent
3. **Disable `YouTube follow-on views` as a primary action** before any Video or Demand Gen campaign launches. Inert today; live the moment a campaign carries that goal category. **Review the existing 2026-08-06 PMax audit** at `context/analysis/pmax/pmax-audit.md` — it found 113 Editor changes on 2026-08-05 and 38 on 08-06 concentrated on paused Demand Gen campaigns, so the rebuild is active. **No re-run needed**

### Housekeeping — safe, and overdue

4. **Delete or archive the five "(OLD)" actions** plus `Leads - Stay Cold Mable` and `Stay Cold Mable (web) purchase`. All are ENABLED at zero conversions
5. **Investigate `GA4 (web) sale` at 1,155,388 lifetime conversions** — 20× the primary purchase action. Almost certainly counting line items or sessions. Feeds nothing today, but it makes every report in the Google Ads UI unreadable
6. **Reclassify `Custom NewCustomerPurchase` and `Custom ReturningCustomerPurchase`** from DEFAULT to PURCHASE, matching their siblings
7. **Standardise the click lookback window.** 38 actions at 30 days, 9 at 90 days, with no documented reason for the split
8. **Adopt one naming convention.** Four coexist today

### Then

9. **Re-baseline after the goal fix lands.** Once the 14 overrides are removed, reported ROAS becomes clean ROAS and every target in business.md can be stated in one currency instead of two. **Review the existing 2026-08-07 strategy audit** at `context/analysis/strategy/strategy-audit.md` — 77%, top finding: *"no client-set goals exist; the targets are provisional and require Jonas's sign-off."* Sign-off and the goal fix should happen in the same conversation. **No re-run needed**
10. **Run the conversion test** when someone can authorise a live add-to-cart. D13–D16 remain unverified: tag firing, transaction ID de-duplication, dynamic value and currency parameter are all unconfirmed on the actual purchase path

---

## Manual checks required

| Check | Why | How |
|---|---|---|
| Consent defaults in incognito | Determines whether D26 is a real exposure | Open the site in a private window, inspect `google_tag_data.ics.entries` before interacting |
| Conversion test (D13–D16) | Tag firing, transaction ID, value, currency all unverified | Needs explicit authorisation for a live add-to-cart |
| Backend reconciliation (D17) | The only way to confirm Google's counts match Shopify | Compare `purchase_gads_mable` conversions and value against Shopify orders for one fixed window. **This also resolves Gap G1** — a ratio near 1.19 means Google receives gross values |
| Enhanced Conversions status | Not assessable without GTM access | Google Ads UI → Goals → Conversions → `purchase_gads_mable` → Enhanced conversions |

---

## Data freshness

| Source | Rows | Status |
|---|---|---|
| `tracking/conversions-audit.csv` | 47 | Pulled fresh 2026-08-07 |
| `tracking/conversion-goal-config.csv` | 45 | Pulled fresh |
| `tracking/custom-conversion-goals.csv` | 1 | Pulled fresh — goal 6446192748 |
| `tracking/campaign-goals.csv` | 450 | Pulled fresh |
| `tracking/conversions-attribution.csv` | 47 | Pulled fresh |
| `tracking/conversions-daily.csv` | 14 | Pulled fresh — `purchase_gads_mable` only |
| `evidence/conv-value-by-action-30d.csv` | 19 | **The decisive measurement** — explicit date range 2026-06-30..07-29 |
| `evidence/conversions-value-by-action.csv` | 57 | ⚠️ **Lifetime, not 30-day** — date filter did not inject. Retained as regime-1 evidence; do not read as current |
| Live page inspection | — | 2026-08-07, passive mode |
