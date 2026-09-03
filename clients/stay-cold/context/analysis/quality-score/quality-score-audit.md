# Quality Score Audit — 2026-08-07

**Score:** 57.4 / 94 available — **61% · Needs Attention**
**Mode:** full · 16 diagnostics · 90d evaluation window (2026-04-30 → 2026-07-29) · 180d history · 8d conversion lag
**Account:** 3599116618 (Stay Cold Apparel) · EUR
**Scope:** 37 keywords across 6 enabled Search campaigns · 28 carry a Quality Score · 5 ad groups · 7 RSAs

---

## Executive read

61% understates how clean this diagnosis is. The account has one Quality Score problem, it has exactly one cause, and the data separates it perfectly.

**Ad Relevance and Expected CTR are not below average on a single keyword in this account.** Not one, out of 28 scored. Ad Relevance is ABOVE AVERAGE on 27 of 28. That is unusual and it means the ads and the keyword-to-ad mapping are genuinely good. **Landing Page Experience is BELOW AVERAGE on 9 of 9 non-brand keywords and ABOVE AVERAGE on 19 of 19 brand keywords.** A 100% split, no exceptions either way.

**And every one of those keywords points at the same page.** All seven RSAs — four brand, three non-brand — send traffic to the Stay Cold homepage. Google scores that page above average when someone searches "stay cold apparel" and below average when they search "punk hoodie". Same page, two verdicts. That is not a page-quality problem; it is a **message-match** problem, and the account ran the controlled experiment by accident.

Brand keywords weight out at **QS 10.00**. Non-brand at **4.90**. The non-brand campaign carries **69% lost impression share to rank** on a weighted QS of 3.09, and the audit's own engine flagged it High: QS is what is keeping those ads off the page.

**This confirms four fresh peer reports rather than adding a new theory.** The 2026-08-06 LP audit (56%) found punk, goth, metal and rocker appear zero times on that page. The competitive audit (73) found 6 of 6 scored non-brand keywords BELOW AVERAGE on landing page experience — now 9 of 9 over a longer window. The keyword audit (85%) found 42% of non-brand keyword spend below break-even with 100% core-term concentration. The tracking audit (66%) confirmed Search TOF's numbers carry zero inflation, so its economics can be read at face value.

**What is not the problem: your ads, your keywords, or your brand campaigns.** Do not rewrite RSAs. Read the Evidence Ladder, then the LP queue.

---

## Diagnosis

**In one line:** Landing Page Experience is the sole limiting Quality Score component in this account, it affects only non-brand traffic, and it has never once been above average in 27 weeks of history.

**What's happening:** Every non-brand Search keyword resolves to the homepage, via a single ad group named `STAN I BROAD I HOME`. That ad group holds 17 keywords spanning at least four distinct subcultures — punk, goth, metal/rock, tattoo — plus generic apparel terms and one product name. The homepage speaks to none of them specifically. Google's landing page signal has read `BELOW AVERAGE` on those keywords for the entire measurable history, while the identical page reads `ABOVE AVERAGE` for brand queries, where the homepage is exactly what the searcher wanted.

**Where it hurts most:** `EX I EN I WW I TOF I BROAD I PUR I T-CPA II` — weighted QS **3.09**, impression share **10.0%**, **69.0% lost to rank**. €4,244 of non-brand keyword spend in the window sits behind that ceiling. The single worst keyword is `punk hoodie`: QS 4, €1,173 spent, the only keyword in the account whose Ad Relevance is not above average, and the only one whose QS is *declining*.

**What to do first:** Not the ads. `t shirt metal` already proves the copy lever has been pulled — its Quality Score climbed from **1 to 5** over 27 weeks, driven entirely by Ad Relevance improving from average to above average. Its landing page score stayed pinned at below average the whole time and capped the result. The remaining lever is the destination. Give the four subculture clusters pages that use their own language, and point the keywords there.

---

## Evidence Ladder

| # | Layer | Hypothesis | Evidence | Confidence | Blocks | Handoff |
|---|---|---|---|---|---|---|
| 1 | Creative — LP | The homepage is not a relevant destination for subculture product queries | LP BELOW AVERAGE on **9/9** non-brand keywords and ABOVE AVERAGE on **19/19** brand keywords — **same URL for both**. LP has read below average for all 27 weeks of history on every non-brand keyword; never once above | **Very high** | No | `/lp-optimizer` |
| 2 | Competitive | QS is directly costing non-brand visibility | Search TOF: **69.0% lost IS (rank)** on weighted QS **3.09**, 10.0% impression share. Brand campaigns at QS 10 hold 84–95% IS with 4.6–16.2% rank loss | **Very high** | No | Resolved by #1 |
| 3 | Structural | One catch-all ad group cannot serve four subcultures with one destination | Ad group `STAN I BROAD I HOME`: 17 non-brand keywords covering punk / goth / metal / tattoo / generic apparel / one product name, all on one homepage URL. **Fails the Headline Test** | High | No | `keyword-restructurer` *(not yet built — brief below)* |
| 4 | Creative — AR | Copy work already done; lever largely exhausted | `t shirt metal` QS **1 → 5** over 27 weeks, AR **AVG → ABOVE AVG**, LP flat at below average throughout. AR now ABOVE AVERAGE on 27/28 keywords account-wide | High | No | **None — do not route to `/rsa-maker`** |
| 5 | Competitive | Modest CPC premium attributable to QS | Within non-brand: QS 4–5 pays **€1.25/click**, QS 6–7 pays **€1.14** — a **+10%** premium. Small sample on the 6–7 bucket (390 clicks) | Medium | No | Resolved by #1 |
| 6 | Distribution | A quarter of Search keywords carry no Quality Score at all | 9 of 37 keywords (24.3%), **€2,688 of spend**, have no QS — mostly phrase/broad non-brand terms that never accumulate exact-match query history. `rocker hoodies` alone: 7,977 impressions, €977, no score | Medium | No | Monitor |

---

## Module Scores

| Module | Score | Grade | Verdict |
|---|---|---|---|
| M1 — QS Distribution | 14.6 / 20 | 73% | D01 PASS · D02 PASS · **D03 WARN** · **D04 FAIL** · D05 WARN · D06 PASS |
| M2 — Component Breakdown | 29 / 45 | 64% | **D07 PASS** · **D08 PASS** · **D09 FAIL** · D10 WARN |
| M3 — Historical Trends | 9 / 9 avail | 100% | D11 PASS · D12 PASS · D13 SKIP · D14 SKIP |
| M4 — Competitive Context | 4.8 / 20 | 24% | **D15 FAIL** · D16 WARN |
| **Overall** | **57.4 / 94** | **61%** | **Needs Attention** |

*6 points excluded from the denominator (D13, D14 — both SKIP with reasoning below).*

---

## Actions — segmented by cascade state

### Outer cascade: all six Search campaigns run Smart Bidding

Severity is annotated `(dampened)` where it applies to **CPC** — the algorithm partially absorbs a Quality Score penalty at the bid level. **It does not apply to visibility.** Quality Score still determines Ad Rank, and Ad Rank still determines whether the ad appears at all. The 69% rank-based impression-share loss on Search TOF is a full-severity finding, not a dampened one. That distinction is the difference between "this costs a little more" and "this does not show".

### Do now

| # | Action | Why | Route |
|---|---|---|---|
| 1 | **Build subculture landing pages and repoint the keywords** | The only lever that lifts all 9 below-average keywords at once, and the only one that recovers impression share without spending anything | **Review the existing 2026-08-06 LP audit** at `context/analysis/lp/lp-audit.md` — top finding: *"punk, goth, metal and rocker appear zero times on the landing page the non-brand campaign uses."* No re-run needed |
| 2 | **Take the page copy from `brand.md`** | The material already exists and is rated excellent | **Review the existing 2026-08-06 offer audit** at `context/analysis/offer/offer-audit.md` — scored **97%**, top finding: the offer foundation and subculture language are already documented. This is a transfer job, not a writing job |
| 3 | **Fix `punk hoodie` first within that work** | QS 4, €1,173 spent, the account's only `HIGH_SPEND_LOW_QS` flag, the only declining keyword (5 → 4), and the only keyword whose Ad Relevance is not above average | Include in the LP work; recheck AR after |

### Do not do

| Action | Why not |
|---|---|
| **Rewrite RSAs** | Ad Relevance is ABOVE AVERAGE on 27 of 28 scored keywords and BELOW AVERAGE on zero. The AR handoff queue is **empty**. `t shirt metal` shows the copy lever was already pulled successfully — QS 1 → 5 on AR alone |
| **Work on Expected CTR** | ECTR is BELOW AVERAGE on zero keywords. Five non-brand keywords sit at AVERAGE, which is a consequence of the QS ceiling, not an independent fault |
| **Touch the brand campaigns** | Weighted QS **10.00** across all 19 brand keywords, every component above average, 84–95% impression share, flat and perfect across 27 weeks |
| **Pause the low-QS keywords** | Every one is a core product term — punk, goth, metal, tattoo, hoodie. **Review the existing 2026-08-06 keyword audit** at `context/analysis/keyword/keyword-audit.md` — scored 85%, and its own guardrail forbids pausing the front door of a business built on these categories |

### Worth flagging while here

**Search TOF meets the account's own budget-raise criterion, and this audit is where that first becomes visible.** Over 90 days it lost **25.1% of impression share to budget** alongside the 69% lost to rank. business.md's guardrail permits a raise at budget-lost IS ≥ 20%. The tracking audit confirms Search TOF carries **zero conversion-value inflation**, so its reported 3.74 return is its real return, comfortably above the 1.9 break-even.

**Two reasons to hold anyway.** First, the budget audit projects **€78–93k against a €32,500 monthly target** — the account is already ~2.7× over, and adding to that before the authorisation question is answered would be the wrong order. Second, raising budget on a campaign losing 69% to rank buys expensive impressions at a QS-3.09 ceiling. **Fix the pages, then raise the budget** — the same money buys materially more at a higher Quality Score.

---

## Handoff Queue — Ad Relevance (→ `/rsa-maker`)

**Empty.** Zero keywords carry `AR_BELOW_AVG`. Ad Relevance is ABOVE AVERAGE on 27 of 28 scored keywords and AVERAGE on one (`punk hoodie`).

This is the finding, not an absence of one. It rules out the most commonly recommended Quality Score fix and is the reason this report does not route any work to `/rsa-maker`.

## Handoff Queue — Expected CTR (→ `/offer-maker` + `/rsa-maker`)

**Empty.** Zero keywords carry `ECTR_BELOW_AVG`.

Five non-brand keywords sit at AVERAGE (`t shirt metal`, `punk hoodie`, `goth rock clothes`, `punk rock shirts`, `mens hoodies`). Under the inner cascade these are not independently actionable — with Ad Relevance already above average and Landing Page Experience below, the ECTR reading is downstream of the ad rarely reaching a competitive position.

## Handoff Queue — LP Experience (→ `/lp-auditor` → `/lp-optimizer`)

**The entire actionable queue.** All 9 keywords resolve to one URL through one ad group.

| URL | Ad group | Keywords below avg | Impressions | Spend |
|---|---|---|---|---|
| `https://staycoldapparel.com` *(homepage, inherited from the RSA — no keyword-level final URL is set)* | `STAN I BROAD I HOME` | **9** | 37,569 | **€4,244** |

| Keyword | Match | QS | AR | ECTR | LP | Impressions | Spend |
|---|---|---|---|---|---|---|---|
| `t shirt metal` | Broad | 5 | ABOVE AVG | AVG | **BELOW AVG** | 17,428 | **€1,912** |
| `punk hoodie` | Broad | **4** | AVG | AVG | **BELOW AVG** | 10,604 | **€1,173** |
| `goth rock clothes` | Phrase | 5 | ABOVE AVG | AVG | **BELOW AVG** | 5,558 | €692 |
| `tattoo clothing` | Phrase | 7 | ABOVE AVG | ABOVE AVG | **BELOW AVG** | 1,606 | €254 |
| `punk clothing` | Exact | 7 | ABOVE AVG | ABOVE AVG | **BELOW AVG** | 1,298 | €130 |
| `tattoo shirts` | Exact | 7 | ABOVE AVG | ABOVE AVG | **BELOW AVG** | 472 | €62 |
| `punk rock shirts` | Exact | 5 | ABOVE AVG | AVG | **BELOW AVG** | 331 | €22 |
| `mens hoodies` | Exact | 5 | ABOVE AVG | AVG | **BELOW AVG** | 0 | €0 |
| `sinner hoodie` | Exact | 7 | ABOVE AVG | ABOVE AVG | **BELOW AVG** | 0 | €0 |

**Peer finding to act on without leaving this report** — 2026-08-06 LP audit, `context/analysis/lp/lp-audit.md`, scored 56%: *punk, goth, metal and rocker appear zero times on this page.* The words being bought do not appear at the destination. That is the mechanism behind every row above.

---

## Pending handoff — structural split (`keyword-restructurer`, skill not yet built)

**Headline Test: FAILS** for ad group `STAN I BROAD I HOME`.

Asked directly — can one headline address `punk hoodie`, `goth rock clothes`, `t shirt metal`, `tattoo clothing`, `rocker hoodies`, `mens hoodies` and `sinner hoodie` without sounding generic? No. Those span four distinct subcultures, one generic apparel term and one product name. Any headline covering all of them collapses into "alternative clothing", which is precisely the undifferentiated message the landing page already delivers.

**Restructure brief:**

- **Source ad group:** `STAN I BROAD I HOME` (17 non-brand keywords, €6,742, 59,181 impressions)
- **Proposed split, each with its own destination page:**
  - **Punk** — `punk hoodie`, `punk clothing`, `punk rock shirts`, `punk shop`, `punk and rock outfit`
  - **Goth** — `goth rock clothes`, `goth and punk clothing`, `cute goth clothes`, `goth rock fashion`
  - **Metal / Rock** — `t shirt metal`, `rocker hoodies`
  - **Tattoo** — `tattoo clothing`, `tattoo shirts`, `tattoo streetwear`, `tattoo hoodies`
  - **Generic / product** — `mens hoodies`, `sinner hoodie` *(evaluate separately; `mens hoodies` is broad enough to warrant its own review)*
- **Sequencing:** the pages come first. Splitting the ad group without new destinations changes the label on the problem, not the problem — all five splits would still point at the homepage and still score below average.

---

## Module Details

### M1 — QS Distribution (14.6/20)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D01 | Account weighted QS | **PASS** | 4/4 | **8.85** impression-weighted across 28 scored keywords. Above the 7.0 threshold — **but read it with care**: it is carried by brand. Brand weights to **10.00** on 131,637 impressions; non-brand to **4.90**. The account-level number is arithmetically true and strategically misleading |
| D02 | Low-QS concentration | **PASS** | 4/4 | **Zero keywords at QS ≤ 3.** The floor is 4 (`punk hoodie`). No critical-tier concentration exists |
| D03 | High-spend low-QS | WARN | 1.8/3 | One flag, severity Critical: `punk hoodie`, QS 4, **€1,173** — 8% of Search keyword spend. Contained to a single keyword, which is why WARN rather than FAIL |
| D04 | QS by campaign | **FAIL** | 0/3 | `EX I EN I WW I TOF I BROAD I PUR I T-CPA II` weighted QS **3.09** — the entire non-brand Search operation sits below 6. Brand campaigns run 8.96–10.00 |
| D05 | QS by ad group | WARN | 1.8/3 | Only 5 ad groups exist. All 9 below-average keywords sit in one: `STAN I BROAD I HOME`. Same finding as D04 at a different grain, so scored once at reduced weight rather than twice |
| D06 | Null QS coverage | **PASS** | 3/3 | 9 of 37 keywords (**24.3%**) carry no Quality Score — under the 30% threshold. Worth watching: those 9 hold **€2,688** of spend, led by `rocker hoodies` at 7,977 impressions and €977. Cause is standard — phrase and broad terms that never accumulate enough exact-match query history for Google to score |

### M2 — Component Breakdown (29/45)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D07 | Ad Relevance health | **PASS** | 12/12 | **0 of 28 below average.** ABOVE AVERAGE on 27, AVERAGE on 1. No COMPETITOR-class keywords needed excluding — there are none |
| D08 | Expected CTR health | **PASS** | 11/11 | **0 of 28 below average.** ABOVE AVERAGE on 23, AVERAGE on 5 |
| D09 | LP Experience health | **FAIL** | 0/12 | **9 of 28 below average (32.1%)** — and **9 of 9 non-brand (100%)**, against **0 of 19 brand (0%)**. Both groups point at the same homepage |
| D10 | Dominant limiting component | WARN | 6/10 | `LP` is the dominant limiting component on **100%** of flagged keywords. Total concentration in one component. Scored WARN rather than FAIL because a single clean cause is the most actionable diagnosis available — and because D09 already carries the penalty for the underlying fault |

### M3 — Historical Trends (9/9 available)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D11 | QS trend overall | **PASS** | 5/5 | Of 21 keywords with sufficient history: **19 STABLE, 1 IMPROVING, 1 DECLINING.** No account-level deterioration. Improving: `t shirt metal` (1 → 5). Declining: `punk hoodie` (5 → 4) |
| D12 | Component trends | **PASS** | 4/4 | No component is deteriorating. Ad Relevance improved on `t shirt metal` (AVG → ABOVE AVG) and held everywhere else. **Landing Page Experience has read BELOW AVERAGE on every non-brand keyword for all 27 weeks of history — it has never once been above average, and it has never worsened either.** A permanent floor, not a decline |
| D13 | Post-optimization correlation | **SKIP** | —/3 | 42 changelog events loaded, but 22 register as "near" almost every keyword. These are account-wide budget and target changes, not keyword-level optimisations, so temporal proximity carries no signal. Scoring a correlation here would be spurious |
| D14 | Seasonal patterns | **SKIP** | —/3 | 180 days of history — under the 52 weeks needed for a year-on-year comparison |

### M4 — Competitive Context (4.8/20)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| D15 | Lost IS (rank) vs QS | **FAIL** | 0/12 | Search TOF: **69.0% lost IS (rank)** on weighted QS **3.09**, impression share 10.0%. Flagged High — QS is dragging Ad Rank. Correctly *not* flagged: USA Brand at 16.2% rank loss on a healthy QS 8.96, where the cause is competitive, not quality. **`JM I DSA I FC'S I CAT'S` loses 90.0% to rank** but carries no keywords and therefore no Quality Score — it cannot be diagnosed by this audit. Worth noting alongside the 2026-08-07 strategy audit finding that DSA's effective clean target is **1.29, below the 1.9 break-even** |
| D16 | CPC premium by QS tier | WARN | 4.8/8 | Within non-brand, QS 4–5 pays **€1.25/click** against **€1.14** at QS 6–7 — a **+10% premium**. Real but modest, and the QS 6–7 bucket holds only 390 clicks. **The headline €0.19 vs €1.25 gap between brand and non-brand is not a Quality Score effect** — those are different auctions with different competition, and attributing that 6.6× spread to QS would be wrong |

---

## Classifier Results

| Class | Count | Treatment |
|---|---|---|
| BRANDED | 20 | Excluded from non-brand rollups. All at QS 10 with every component above average — nothing to route |
| GENERIC | 17 | Standard cascade. 9 scored, all LP-limited |
| COMPETITOR | **0** | business.md confirms *"no active competitor campaign"*, and no keyword text matches the seven configured rival brands (Killstar, DropDead, Disturbia, Sullen, Named Collective, Blackcraft Cult, Bad Monday). Competitor traffic reaches this account as **search terms via broad match**, not as keywords — the 2026-08-06 search-term audit measured €2,141 on competitor brand queries, and business.md forbids negating them |
| INFORMATIONAL | **0** | Semantic pass over all 37 keyword texts found no research-intent terms. Every keyword is commercial or product-level. Nothing routes to `/keyword-auditor` on this basis |

**Anti-pattern guard — all four checks clean.** No COMPETITOR keyword in the AR queue (queue is empty). No ECTR fix proposed on an AR-below keyword (neither exists). No INFORMATIONAL keyword in any queue (none exist). No Smart Bidding finding silenced — the dampening annotation is applied to CPC severity only and stated explicitly, and the visibility finding is carried at full severity.

---

## Data Sufficiency Notes

- **Evaluation window set to 90 days, not the 30-day default.** Ruling made under auto-mode and recorded in `config/ads-context.config.json → qualityScoreAudit`. With only 37 keywords in the account, a 30-day window would have pushed most below the impression floor and tagged them `UNSTABLE_QS`, gutting the M2 denominators. Quality Score itself is point-in-time; the window governs only how much impression weight backs each score.
- **13 of 37 keywords are tagged `UNSTABLE_QS`** (under 1,000 impressions in the window) and are excluded from M2 component denominators. 11 of those are brand keywords at QS 10.
- **14 of 35 keywords (40%) fell below the weekly-impression floor** for trend analysis and are marked `INSUFFICIENT_DATA` in M3. Under the 50% threshold that would trigger a threshold-lowering prompt, so the default was kept.
- **No ad customizers exist anywhere in the account** — attributes, ad-group, keyword, campaign and customer scopes all returned zero rows. All 5 ad groups report `NO_CUSTOMIZERS`. Nothing is broken; the feature is simply unused. The Headline Test therefore ran in `STANDARD` mode.
- **No keyword-level final URLs are set.** All destinations inherit from the RSA, which is why the LP queue groups to a single URL.
- **`bidding-strategies.csv` returned 0 rows** — no portfolio strategies exist. All campaigns carry inline targets, so `target_source` is `campaign_inline` throughout and no portfolio caveat applies.

---

## Data Freshness

| Source | Rows | Status |
|---|---|---|
| `keywords-qs-period.csv` | 37 | Pulled fresh 2026-08-07 |
| `keywords-qs-timeseries.csv` | 767 | Pulled fresh — 180d |
| `qs-ads.csv` | 7 | Pulled fresh |
| `campaigns-settings.csv` | 15 | Pulled fresh |
| `campaigns-is.csv` | 6 | Pulled fresh — 90d |
| Customizer pulls (5 files) | 0 | Pulled fresh — none exist |
| `bidding-strategies.csv` | 0 | Pulled fresh — no portfolios |

---

## For the record — machine-readable

```yaml
top_hypothesis:
  layer: Creative-LP
  name: Homepage is not a relevant destination for subculture product queries
  confidence: very_high
  explains_waste_pct: 100
  blocking: false
  handoff: /lp-optimizer
  evidence:
    lp_below_avg_nonbrand: 9/9
    lp_below_avg_brand: 0/19
    shared_url: true
    weeks_never_above_average: 27
queues:
  ad_relevance: { keywords: 0, impressions: 0, spend_eur: 0 }
  expected_ctr: { keywords: 0, impressions: 0, spend_eur: 0 }
  lp_experience: { keywords: 9, impressions: 37569, spend_eur: 4244, urls: 1, ad_groups: 1 }
pending_handoff:
  skill: keyword-restructurer
  status: not_built
  ad_group: STAN I BROAD I HOME
  headline_test: FAIL
  proposed_splits: 5
bidding_mode: smart_bidding_all
cpc_severity: dampened
visibility_severity: full
```
