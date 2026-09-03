# Bidding Audit — 2026-08-06

**Score:** 54/100 (Critical)
**Window:** 30 days, lag-offset 8 days (≈ 2026-06-29 → 2026-07-28) | **Module scope:** full (27 diagnostics, 7 modules)
**Account:** 3599116618 (Stay Cold Apparel) · EUR · 15 campaigns in the Active Roster (82 pulled)
**Run by:** /bidding-auditor at 2026-08-06

---

## Executive read

54 is a Critical band score, and in this case the band is telling the truth — but not for the reason the red text suggests. Nothing is wrong with *how* the bid strategies are set up. The problem is that the currency they bid in is broken, so almost every target in the account is quietly steering somewhere nobody chose. That single fault caps this score and blocks every action underneath it.

Three things this week. **First, the measurement layer is blocking and must be cleared before any target is touched.** The account carries an ENABLED conversion value rule adding **€42.20** to conversions with no visible conditions — while business.md documents the new-customer bonus as **€16.46**. Those two numbers are 2.6× apart, and that sits on top of the already-verified NewCustomerPurchase double-count (×1.28–1.94 per campaign). Nobody currently knows the true inflation factor, which means nobody knows what any tROAS target actually means. **Second, once deflated, two of the three biggest spenders are at or below break-even and their CPCs are rising.** FOKUSPRODUKTE is at clean ROAS 1.72 against a 1.9 break-even, with CPC up 36% across three windows (€1.31 → €1.78). PROSPECTING is at clean 2.24 with CPC up 27%. Together that is 67% of spend getting more expensive in the exact place business.md says the money is being lost. **Third, the DSA campaign is the cheapest genuine win available** — clean ROAS ~5.9 against an effective clean target of 1.29, spending €17/day of a €650 budget, losing 90% of impression share to rank, not budget.

What is not a problem: seven BID-D01/D03 strategy failures look alarming but five of them are the zero-traffic PMax campaigns the account audit already caught — a structural fault, not a bidding one. There are no portfolio strategies and no manual-CPC campaigns, so two modules are largely N/A. And the entire Learning Phase module is unscored because `account-changelog.md` does not exist — learning state is unknown, not clean.

Skim Module scores → jump to Risks for the action list → Module details are reference.

---

## Diagnosis (technical)

The problem is at the **M (Measurement) layer** — conversion value reaching the bidding algorithm is inflated by an unquantified factor, so every nominal tROAS target maps to an unknown and materially lower real target. Two mechanisms compound: the NewCustomerPurchase double-count verified at ×1.28–1.94 per campaign on 2026-08-03, and an enabled conversion value rule adding €42.20 per conversion that no context file documents at that magnitude. The structural root cause is already identified in the account audit run the same day (AUD-D24): 14 of 15 enabled campaigns override the clean account-default conversion goal with custom goal `6446192748`; the one campaign that does not — Search TOF — is the only campaign in the account whose target means what it says. Until that is repaired, target validation is not merely unreliable, it is inverted: BID-D06 passes every campaign because it compares *nominal* targets (2.5–100) against break-even 1.9, while the *effective clean* targets for DSA (1.29), FOKUSPRODUKTE (1.95) and PROSPECTING (1.92) sit at or below that same break-even. Do not change a target in this account until the goal configuration is fixed.

---

## Top hypothesis

- **Layer:** M — Measurement (BLOCKING)
- **Name:** Conversion-value integrity failure — targets denominated in an unknown currency
- **Confidence:** **high**
- **Evidence:** BID-D26 (conversion value rule `35918909`, ADD +€42.20, ENABLED, no conditions in the pulled data, vs €16.46 documented in business.md §7). BID-D06 passes 13/13 campaigns only because it reads nominal targets; deflating by the per-campaign factors in business.md §6 puts DSA's effective clean target at 1.29 — below the 1.9 break-even. Cross-confirmed by the same-day account audit AUD-D24, which located the mechanism: 14 of 15 campaigns override the clean account default with custom conversion goal `6446192748`.

**Consequence per the cascade:** all target and strategy mutations are refused. The optimizer will hard-refuse while this layer is active.

---

## Module scores

| Module | Score | Status |
|---|---|---|
| Target Validation | 8.4/14 available (25 nominal — D05, D07 SKIP) | 60% — Needs Attention |
| Strategy Selection | 5/20 | 25% — Critical |
| Learning Phase | N/A — all 4 diagnostics INFO (changelog missing) | Unscored |
| Portfolio Health | 5.8/7 available (15 nominal — D14, D16 excluded) | 83% — Good |
| CPC & Cost Health | 7.2/10 | 72% — Needs Attention |
| Conversion Value Rules | 5/10 | 50% — Critical |
| Bid Adjustments | 3/3 available (5 nominal — D18 INFO) | 100% — Excellent |
| **Total** | **34.4 / 64 available** | **54/100 — Critical** |

*36 of 100 nominal points were removed from the denominator as SKIP/INFO: BID-D05 (8, no tCPA campaigns exist), BID-D07 (3), the whole Learning module (15, changelog missing), BID-D14 (4, no portfolios), BID-D16 (4), BID-D18 (2). Formula per `scoring-model.md`: 34.4 / (100 − 36) × 100 = 53.75 → 54.*

### Two engine verdicts I overrode, and why

| Diagnostic | Engine | Reported here | Reason |
|---|---|---|---|
| BID-D06 (target vs break-even) | PASS 13/13 | **WARN** (4.8/8) | The engine compares nominal targets against break-even 1.9. Every nominal target (2.5–100) clears 1.9 trivially. On the effective clean basis documented in business.md §6, DSA is at 1.29 (below break-even), FOKUSPRODUKTE 1.95 and PROSPECTING 1.92 (marginal). A trivially-true PASS would misrepresent the account. |
| BID-D26 (conversion value integrity) | INFO | **FAIL** (0/5) | D26 is the diagnostic that owns the M layer. Declaring M active-blocking while scoring its own diagnostic as INFO would be incoherent. The €42.20-vs-€16.46 discrepancy plus the NCP double-count is a genuine value-integrity failure. |

---

## Risks (segmented by cascade state)

### 🔍 Investigate first (blocking handoffs)

- **Conversion value rule `35918909` adds +€42.20 per conversion, ENABLED, no conditions visible in the pull — business.md §7 documents €16.46.** Either the file is stale or this is a second, undocumented rule. Resolve before any target work → `/tracking-specialist`
- **14 of 15 enabled campaigns override the clean account-default conversion goal with custom goal `6446192748`** (source: account audit AUD-D24, 2026-08-06). This is the mechanism behind the ×1.28–1.94 inflation. Fix is DON'T-8 — humans only, never agent-executed → `/tracking-specialist`, then Jonas
- **Gap G1 remains open** — whether Google receives gross or net conversion values moves break-even between 1.6 and 1.9, a factor of 1.19 on the account's most important threshold. Needs Shopify `read_orders` → `/strategy-specialist`

### 🔧 Structural fix needed

- **5 enabled PMax campaigns serve zero impressions** (`SCALING I BROAD`, `SKANDI I TESTING I PROSPECTING`, `FRA I TESTING I BROAD`, `USA I TESTING I BROAD`, `WW I PROSPECTING I BROAD`). They generate 5 of the 7 BID-D01/D03 failures. This is not a bidding fault — fixing the bid strategy on a campaign that cannot serve changes nothing → `/pmax-auditor`, `/feed-auditor` (already the #1 routing item in the 2026-08-06 account audit, AUD-D08)
- **CPC ceiling €2.50 on `EX | SKANDI | SEARCH | BRAND`** (Target Impression Share, currently 92.0% IS against the 95–99% target, 8.0% rank-lost). The cap is a credible constraint on reaching target. Notably this is one of the *few* brand actions guardrail DON'T-4 explicitly permits — "bids upward only" → proposal for Jonas
- **11 location bid modifiers at +15% on Search TOF** under MAXIMIZE_CONVERSION_VALUE. Smart Bidding ignores location bid adjustments — these are inert and misleading to anyone reading the account. Harmless, worth cleaning

### 🔄 Recover efficiency first

Neither the Eff nor the Conv layer can be cleared — no search-term, keyword, quality-score, LP or offer audit exists for this account.

- **DSA at 90.0% rank-lost impression share** and **Search TOF at 58.7% rank-lost** are both ad-rank problems, not bid problems. Only a QS audit can tell you whether the cause is Quality Score or bid → `/quality-score-auditor`
- **business.md §15 flags two open CVR blockers** — "price-vs-quality perception" and the "PDP truth gap" — on exactly the non-brand traffic running at break-even → `/lp-auditor`, `/offer-auditor`
- Non-brand search waste is unquantified → `/search-term-auditor`

### ✅ Act now (safe)

Nothing on the target or strategy side survives the M-layer block. What remains genuinely safe:

- **`/account-changelog`** — still missing. It is the reason the entire Learning Phase module is unscored, and it is required to resolve the FOKUSPRODUKTE budget contradiction below. Zero risk, run it first
- Remove the 11 inert location bid modifiers on Search TOF (cosmetic only)

### ⚠️ Hold (in learning)

**Unknown — not clear.** `learning-state.csv` returned empty `last_strategy_change` and `last_target_change` for all 15 campaigns because `context/account-changelog.md` does not exist. Per the skill's own edge-case rule, all four learning diagnostics degrade to INFO. The `in_learning = no` column is a default, not a measurement. Treat learning state as unknown until the changelog is pulled.

---

## Opportunities

| # | Type | Campaign | Projected impact | Action |
|---|---|---|---|---|
| 1 | starvation_recovery | `JM I DSA I FC'S I CAT'S` | Clean ROAS ~5.9 vs effective clean target 1.29; 90.0% rank-lost IS; spending €17/day of a €650/day budget. Largest efficiency-to-volume gap in the account | **Blocked by M layer.** The nominal 2.50 target is meaningless until goal config is fixed — and note the direction trap: lowering a tROAS target buys volume, but this target already sits *below* break-even in real terms. Fix measurement → `/quality-score-auditor` for the rank-lost cause → then `/bidding-optimizer adjust-targets --rationale=starvation-recovery` |
| 2 | budget_lost_recovery | `EX I EN I WW I TOF … Kollektionen + Types` (Search TOF) | Engine projects +1,810 clicks, +43.9 conv, +€2,181 cost at €49.71 CPA. 31.7% budget-lost IS at 65% budget utilisation. Clean ROAS 3.74 — the only non-brand unit clearly above target | The clearest scaling candidate in the account. But business.md records 0 of 6 budget increases above +90% were positive, and "+77% at 56% budget-lost IS still measured −17%". Max +30% per step, ≥7 days apart → `/budget-auditor` first |
| 3 | budget_lost_recovery | `EX I SHOPPING I FOKUSPRODUKTE` | Engine projects +3,405 clicks, +103.3 conv, +€4,241 at €41.04 CPA | **Do not act on this.** The campaign is at clean ROAS 1.72, *below* the 1.9 break-even — buying more of it buys more loss. The projection is computed on the inflated series. Listed only so it is not mistaken for an opportunity later |
| 4 | brand_is_gap | `EX \| USA \| SEARCH \| BRAND` | IS 84.3%, rank-lost 15.7%, budget-lost 0%. business.md priority #2; measured precedent +261% (2026-03-13) | Rank-limited, not budget-limited — confirmed. Closing it needs ad quality or bids, and bids are blocked by the M layer → `/quality-score-auditor` |

---

## The FOKUSPRODUKTE budget contradiction (partial answer to Gap G7)

business.md Gap G7 asks why FOKUSPRODUKTE and PROSPECTING report budget-constrained while spending ~30% of their daily budgets. This audit splits the question and answers half of it:

| Campaign | Daily budget | Actual spend/day | Utilisation | Budget-lost IS | Rank-lost IS | Verdict |
|---|---|---|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | €1,150 | €411 | 36% | **25.6%** | 23.1% | **Contradictory** — a campaign cannot lose 25.6% of impressions to budget while using 36% of it. Almost certainly a mid-window budget change (business.md logs a cut to €550/day on 2026-06-30; the €1,150 figure suggests a later restoration). Resolvable only with the changelog |
| `EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING` | €1,250 | €371 | 30% | **0%** | 48.2% | **Answered — not budget-limited at all.** It is rank-limited. business.md's "reports as budget-constrained" framing is wrong for this campaign in this window |

That correction matters: the €10,900/month campaign will not respond to a budget increase, and any plan built on "it's budget-constrained" is built on a false premise.

---

## Clean vs reported — the deflation table

Reported ROAS is what the API returns. Clean ROAS applies the per-campaign inflation factors verified in business.md §6 on 2026-08-03. Break-even is 1.9.

| Campaign | Spend | Nominal tROAS | Reported ROAS | Factor | **Clean ROAS** | vs BE 1.9 | Effective clean target |
|---|---|---|---|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | €12,316 | 3.53 | 3.12 | 1.81 | **1.72** | ❌ below | 1.95 |
| `EX I WW I PMAX … PROSPECTING` | €11,121 | 3.60 | 4.21 | 1.88 | **2.24** | ✅ above | 1.92 |
| `EX I EN I WW I TOF …` (Search TOF) | €4,697 | 5.19 | 3.74 | 1.00 | **3.74** | ✅ above | 5.19 (missing target by 28%) |
| `EX \| DE \| SEARCH \| BRAND` | €1,807 | 100 | 87.16 | 1.42 | **61.38** | ✅ | 70.7 |
| `EX \| USA \| SEARCH \| BRAND` | €819 | 42.64 | 100.07 | 1.53 | **65.40** | ✅ | 27.8 |
| `EX \| SKANDI \| SEARCH \| BRAND` | €668 | tIS (cap €2.50) | 44.46 | — | — | ✅ | — |
| `EX I WW I PMAX … OVER-INDEX` | €545 | 3.50 | 4.79 | 1.45 | **3.31** | ✅ | 2.42 |
| `JM I DSA I FC'S I CAT'S` | €515 | 2.50 | 11.40 | 1.93 | **5.90** | ✅ | **1.29 — below break-even** |
| `EX \| FRA \| SEARCH \| BRAND` | €433 | tIS (cap €2.00) | 128.30 | — | — | ✅ | — |
| `EX I SHOPPING I PUR … NEAR INDEX` | €31 | 4.00 | 23.39 | 1.28 | 18.27 | ✅ (n=5, noise) | 3.13 |

⚠️ **Window caveat.** This pull covers ≈ 2026-06-29 → 2026-07-28 (lag offset 8 days). business.md's figures cover 2026-07-04 → 2026-08-02. The windows differ by 5 days, so cross-window deltas (e.g. FOKUSPRODUKTE 1.72 here vs 1.73 there, PROSPECTING 2.24 here vs 1.96 there) are **not** reliable trend evidence. Do not read them as movement.

---

## CPC trend detail (BID-D22 / BID-D23)

| Campaign | Pattern | Values | Note |
|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | **Spike +30% AND rising 3 periods** | €1.31 → €1.32 → €1.78 (+36%); recent 14d €1.53 vs prior €1.17 | The only campaign firing both. Already below break-even — rising CPC deepens the loss |
| `EX I WW I PMAX … PROSPECTING` | Rising 3 periods | €0.96 → €1.06 → €1.22 (+27%) | €10,900/mo at clean 2.24. Erodes a thin margin |
| `EX I EN I WW I TOF …` (Search TOF) | Rising 3 periods | €1.16 → €1.21 → €1.25 (+7.7%) | Mild. The profitable campaign — monitor, don't act |

67% of account spend sits in the first two rows. Both are getting more expensive. `/competitive-analyst` would give auction context, but per the cascade this is informational and does not block.

*The engines print `$`; the account is EUR. All figures above are EUR — the symbol in raw engine output is cosmetic.*

---

## Learning state (permanent fixture)

| Campaign | Strategy | Last strategy change | Last target change | Days since | In learning |
|---|---|---|---|---|---|
| `JM I DSA I FC'S I CAT'S` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I EN I WW I TOF … Kollektionen + Types` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I SHOPPING I FOKUSPRODUKTE` | TARGET_ROAS | unknown | unknown | — | **unknown** |
| `EX I WW I PMAX I SCALING I BROAD` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I SHOPPING I PUR I T-ROAS I NEAR INDEX` | TARGET_ROAS | unknown | unknown | — | **unknown** |
| `EX I SKANDI I PMAX I TESTING I PROSPECTING` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I FRA I PMAX I TESTING I BROAD` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I WW I PMAX … OVER-INDEX + INDEX + NEAR-INDEX` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX \| USA \| SEARCH \| BRAND` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX \| SKANDI \| SEARCH \| BRAND` | TARGET_IMPRESSION_SHARE | unknown | unknown | — | **unknown** |
| `EX \| DE \| SEARCH \| BRAND` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I USA I PMAX I TESTING I BROAD` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX \| FRA \| SEARCH \| BRAND` | TARGET_IMPRESSION_SHARE | unknown | unknown | — | **unknown** |
| `EX I WW I PMAX I PROSPECTING I BROAD` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |
| `EX I WW I PMAX … FEED ONLY I PROSPECTING` | MAXIMIZE_CONVERSION_VALUE | unknown | unknown | — | **unknown** |

Every cell is unknown because `context/account-changelog.md` does not exist. The raw `learning-state.csv` writes `no` in the final column — that is the engine's default when it has no dates, **not** a finding. Run `/account-changelog` and re-run `/bidding-auditor learning` to populate this table.

---

## Module details

### Module 1 — Strategy Selection (5/20)

| ID | Verdict | Points | Evidence | Next step |
|---|---|---|---|---|
| BID-D01 | **FAIL** | 0/5 | Smart bidding below the absolute volume minimum on **7 of 15** campaigns: 5 zero-traffic PMax (0 conv), `OVER-INDEX` (18.2 conv), `NEAR INDEX` (5 conv) — all against a 30-conv/30d floor. On the clean series these are worse still (~12.5 and ~3.9) | 5 are structural → `/pmax-auditor`. 2 are real volume problems → Vol sub-cascade below |
| BID-D02 | PASS | 5/5 | 15/15 — strategy type matches campaign objective everywhere. No mismatched strategies | — |
| BID-D03 | **FAIL** | 0/10 | Same 7 campaigns. `MAXIMIZE_CONVERSION_VALUE` / `TARGET_ROAS` with insufficient conversion data to optimise | Options menu below |
| BID-D04 | INFO | 0 | 15 INFO — no points at stake | — |

**Vol sub-cascade — options for the 2 genuine low-volume campaigns** (`OVER-INDEX`, `NEAR INDEX`). The auditor does not pick; you do:

- **A. Consolidate into FOKUSPRODUKTE / PROSPECTING.** Both target index-based product segmentation those campaigns already cover. Matches the account audit's AUD-D05 fragmentation finding and business.md's "structure over budget" precedent (+29% from FOKUSPRODUKTE ad-group restructuring, 2026-01-23)
- **B. Switch to Maximize Conversion Value with no target** — works at any volume, removes the target-calibration problem entirely for these two
- **C. Raise budget** to reach the volume floor. Weak option: NEAR INDEX spends €1/day of €95 — budget is not the binding constraint
- **D. Accept 30 more days** and re-evaluate

Recommendation: **A**, and it should be sequenced with the PMax structural work rather than treated as a bidding change.

### Module 2 — Target Validation (8.4/14 available)

| ID | Verdict | Points | Evidence | Next step |
|---|---|---|---|---|
| BID-D05 | SKIP | —/8 | All 15 SKIP. No tCPA campaign exists in this account — every campaign runs Target ROAS, Maximize Conversion Value, or Target Impression Share | Excluded from denominator |
| BID-D06 | **WARN** (overridden from PASS) | 4.8/8 | Engine: 13 PASS, comparing nominal targets (2.5–100) against break-even 1.9 — trivially true. Deflated: DSA effective clean target **1.29 < 1.9**, FOKUSPRODUKTE 1.95 and PROSPECTING 1.92 marginal | Blocked by M layer |
| BID-D07 | SKIP | —/3 | All 15 SKIP | Excluded |
| BID-D08 | WARN | 1.8/3 | 5 campaigns deviate materially from target: DSA −326%, NEAR INDEX −485%, USA brand −137%, OVER-INDEX −37%, Search TOF +30%. Large deviations in *both* directions are themselves a symptom of the inflated currency | Blocked by M layer |
| BID-D09 | WARN | 1.8/3 | DSA: actual ROAS 1140% vs target 250%, rank-lost IS 90% — classic starvation signature | See Opportunity 1 |

### Module 3 — Learning Phase (N/A — unscored)

| ID | Verdict | Points | Evidence |
|---|---|---|---|
| BID-D10 | INFO | — | 15 INFO |
| BID-D11 | INFO (degraded from PASS) | — | Engine returned PASS, but with no change dates available the PASS is unfounded. Skill edge-case rule: "account-changelog missing → learning-state findings degrade to INFO" |
| BID-D12 | INFO | — | 15 INFO |
| BID-D13 | INFO (degraded from PASS) | — | Same as D11 |

15 points removed from the denominator. Run `/account-changelog` to restore this module.

### Module 4 — Portfolio Health (5.8/7 available)

| ID | Verdict | Points | Evidence | Next step |
|---|---|---|---|---|
| BID-D14 | SKIP | —/4 | `bidding-strategies.csv` returned **0 rows** — the account uses no portfolio bid strategies at all. Every strategy is campaign-inline | Excluded |
| BID-D15 | WARN | 1.8/3 | 2 active campaigns carry a CPC ceiling under Target Impression Share: SKANDI brand €2.50, FRA brand €2.00. (A third, paused ESP brand, also €2.50.) Caps constrain smart bidding — and SKANDI sits at 92.0% IS against a 95–99% target | Raising the SKANDI cap is DON'T-4-compliant ("bids upward only") → proposal for Jonas |
| BID-D16 | INFO | — | Excluded from denominator |
| BID-D17 | PASS | 4/4 | No shared budgets anywhere in the account (`explicitly_shared = false` on all 82 rows), so no shared-budget/portfolio conflict is possible | — |
| BID-D27 | SKIP | 0 | 0-point diagnostic | — |

### Module 5 — CPC & Cost Health (7.2/10)

| ID | Verdict | Points | Evidence | Next step |
|---|---|---|---|---|
| BID-D22 | WARN | 2.4/4 | 1 spike: FOKUSPRODUKTE €1.53 vs €1.17 prior 14d (+30%). 7 PASS, 7 SKIP (zero-traffic campaigns) | `/competitive-analyst` for context |
| BID-D23 | WARN | 1.8/3 | 3 rising trends: FOKUSPRODUKTE +36%, PROSPECTING +27%, Search TOF +7.7% | Informational — does not block |
| BID-D24 | PASS | 3/3 | 13 PASS, 2 INFO. Bid-simulator opportunity gaps surfaced as the two budget_lost_recovery items in Opportunities | — |

### Module 6 — Conversion Value Rules (5/10)

| ID | Verdict | Points | Evidence | Next step |
|---|---|---|---|---|
| BID-D25 | PASS | 5/5 | Value-rule configuration is structurally valid — 1 rule, status ENABLED, well-formed | — |
| BID-D26 | **FAIL** (overridden from INFO) | 0/5 | Rule `35918909`: operation ADD, value **+€42.20**, ENABLED, with **no audience, device or geo condition present in the pulled data**. business.md §7 documents the new-customer bonus as **€16.46** — a 2.6× discrepancy. Suggestive arithmetic, unconfirmed: Search TOF's value-per-conversion is €186.12, and €186.12 − €42.20 = €143.92, almost exactly the account's clean AOV of €143 — which would mean even Search TOF, the one campaign business.md treats as inflation-free, is carrying this rule | `/tracking-specialist` — establish the rule's real conditions and true magnitude before any target work |

**Caution against overclaiming:** the GAQL may simply not return condition detail for this rule type. The defensible statement is that the account's true value inflation is *unknown*, and that unknown is what blocks the M layer — not that a third confirmed inflation layer exists.

### Module 7 — Bid Adjustments (3/3 available)

| ID | Verdict | Points | Evidence |
|---|---|---|---|
| BID-D18 | INFO | — | Excluded from denominator |
| BID-D19 | PASS | 1/1 | No conflicting adjustments |
| BID-D20 | PASS | 1/1 | No device adjustment problems |
| BID-D21 | PASS | 1/1 | No demographic adjustment problems |

**INFO note:** the only bid adjustments in the entire account are 11 location modifiers at **+15%** on Search TOF (geo targets 2036, 2056, 2124, 2203, 2208, 2233, 2246, 2380, 2442, 2703, 2756). The campaign runs MAXIMIZE_CONVERSION_VALUE, and Smart Bidding ignores location bid adjustments. They are inert — no performance impact, but they mislead anyone reading the campaign's settings.

---

## Peer report integration (Phase 3.5)

| Peer | Report | Status | Used how |
|---|---|---|---|
| `/account-auditor` | `context/analysis/account/account-audit.md` | **FRESH — 2026-08-06 (today)**, score 75% (Good) | Integrated throughout. Its AUD-D24 finding supplied the *mechanism* for this audit's top hypothesis (14 of 15 campaigns overriding the clean account-default goal). Its AUD-D08 finding explains 5 of the 7 BID-D01/D03 strategy failures as structural, not bidding — which is why they route to `/pmax-auditor` rather than `/bidding-optimizer`. Its AUD-D05 fragmentation groups are the same 2 campaigns behind this audit's Vol sub-cascade |
| `/tracking-specialist` | — | Missing | Blocking handoff — run it |
| `/quality-score-auditor` | — | Missing | Needed for DSA 90% and Search TOF 58.7% rank-lost IS |
| `/search-term-auditor` | — | Missing | Eff layer cannot be cleared |
| `/keyword-auditor` | — | Missing | Eff layer cannot be cleared |
| `/budget-auditor` | — | Missing | Needed before Search TOF scaling |
| `/lp-auditor`, `/offer-auditor` | — | Missing | Conv layer cannot be cleared |
| `/competitive-analyst` | — | Missing | Informational only — CPC trend context |
| `/strategy-specialist` | — | Missing | Gap G1 (gross vs net) |

**Where the fresh peer report agrees rather than contradicts:** the account audit reached 75% (Good) while this audit reaches 54 (Critical). That is not a conflict — they measure different things. Account structure and settings hygiene really are in good shape; the bidding *currency* is broken. Both audits independently converge on the same root cause from opposite directions, which raises rather than lowers confidence.

---

## Configuration snapshot

- **Primary KPI:** roas
- **Break-even ROAS:** 1.9 (clean/purchase-only basis) — Martin's ruling 2026-08-06 over the 1.6 net-value alternative; Gap G1 still open
- **Posture:** growth (PAR target 1.2 → implied clean target 2.28) — Martin's ruling 2026-08-06; business.md labels the account "Cost Control" but its own numeric target of clean 2.5 is 1.32× break-even, nearest the growth PAR
- **Primary conversion action:** `purchase_gads_mable` (€143 representative value)
- **tCPA safety margin:** 0.7 (inert — no tCPA campaigns exist)
- **Experiments:** excluded (`experiment_type = 'BASE'` only)
- **Window:** 30 days, lag offset 8
- **Last confirmed:** 2026-08-06 | **business.md hash:** `7bbedf9130b8a944`

### Data freshness

| Source | Date | Status |
|---|---|---|
| `bidding/campaigns-bidding-perf.csv` | 2026-08-06 | Pulled fresh (82 rows) |
| `bidding/campaigns-bidding-daily.csv` | 2026-08-06 | Pulled fresh (262 rows) |
| `bidding/campaigns-criteria-bidding.csv` | 2026-08-06 | Pulled fresh (11 rows) |
| `bidding/conversion-value-rules.csv` | 2026-08-06 | Pulled fresh (1 row) |
| `bidding-strategies.csv` | 2026-08-06 | Pulled fresh (**0 rows** — no portfolios exist) |
| `bidding/bidding-data-exclusions.csv` | 2026-08-06 | Pulled fresh (**0 rows** — no data exclusions configured) |
| `context/account-changelog.md` | — | **Missing.** Cost: the entire Learning Phase module (15 pts) and the FOKUSPRODUKTE budget contradiction |
