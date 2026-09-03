# Keyword Audit — 2026-08-06

**Score:** 85 / 100 — **Good**
**Scope:** full · 17 diagnostics · 5 modules · 37 keywords across 5 campaigns
**Period A:** 30 days, 8-day conversion lag (≈ 2026-06-29 → 2026-07-28) · **Period B:** prior 30 days
**Account:** 3599116618 (Stay Cold Apparel) · EUR · primary KPI ROAS · break-even **clean 1.9**

---

## Executive read

85 is the right score and it is slightly misleading, because the one thing that fails is the thing that matters. Structurally the keyword set is in good shape: no match-type redundancy, no genuine duplicates, no zombies, every keyword eligible and approved, no informational-intent junk, and brand terms cleanly confined to brand campaigns. What fails is the economics of the non-brand set — and the cause is not in the keywords at all.

**Five keywords are running below break-even on €1,961, which is 42% of the entire non-brand search budget.** `t shirt metal` alone accounts for €1,006 at a clean ROAS of 1.50 against a 1.9 floor, and it degraded from HERO in the prior period. `punk hoodie` slid from HERO to merely-above-target. Six keywords degraded a tier between periods, and the two biggest non-brand spenders are both among them.

**The skill's most important guardrail fires here, and I am honouring it: do not pause any of them.** Every one of the five unprofitable keywords is a core product term — punk, goth, tattoo, metal, hoodie, shirt — giving 100% core-term concentration against a 50% threshold. These are the front door of the business, not waste. And there is an independently-verified reason they underperform: today's competitive audit (73/100) found landing page experience rated **BELOW AVERAGE on six of six scored non-brand keywords**, while ad relevance is ABOVE AVERAGE on five of six. Their Quality Scores sit at 4–7, capped entirely by the page they point at. Brand keywords, pointing elsewhere, score a perfect 10.

**So this week: fix the landing page, not the keyword list.** The second thing worth doing is a negative-keyword sweep — Performance Max is absorbing 80 distinct queries that overlap these keywords, and **27 of them are other brands or the wrong subculture entirely**: a flood of "cyberpunk hoodie" variants, plus Metallica, Gildan and CM Punk merch. None of that is Stay Cold's audience.

**What is not a problem despite being flagged.** The engine reported 18 cross-campaign match conflicts and 6 duplicate keywords — all of them brand terms across the geo-separated DE, FRA, SKANDI and USA campaigns. Today's geo audit verified that separation directly from per-campaign location criteria. They do not compete. And the two "zombie" keywords were added six days ago via API, after this measurement window closed — they are new, not dead.

Read the Diagnosis, then the Actions. Baseline run — no prior score.

---

## Business context

| | |
|---|---|
| **Primary KPI** | ROAS |
| **Break-even** | clean **1.9** (Gap G1 open — 1.6 if Google receives net values) |
| **Primary conversion action** | `purchase_gads_mable` (€143 representative value) |
| **Core product tokens** | hoodie · tee · shirt · tattoo · oversized · heavyweight · 400gsm · apparel · clothing · clothes · punk · goth · metal · rock · rocker · streetwear · outfit |
| **Fallback mode** | none — real economics available |

*Tokens derived from business.md §9 ("Core product-category terms — heavyweight hoodie, oversized tee, 400gsm, tattoo/dark apparel — the scene core") and §1 ("heavyweight apparel for metal / tattoo / hardcore / dark-streetwear culture"). Economics inherited from the `biddingAudit` block Martin confirmed the same day.*

> ⚠️ **A measurement note that cuts in an unusual direction.** Account-wide, conversion value is inflated ×1.28–1.94, which normally blocks all pause recommendations. But `EX I EN I WW I TOF … Kollektionen + Types` — the campaign holding every non-brand keyword — is **the one campaign in the account with an inflation factor of 1.00**. business.md §6 records it takes zero NewCustomerPurchase conversions, and today's account audit (AUD-D24) found it is the single campaign using the clean account-default conversion goal rather than the inflating override. **So the keyword economics below are already clean and are more trustworthy than anything else in this account.** The caveat is the +€42.20 conversion value rule the bidding audit found: if it applies here too, every ROAS below drops ~29%, and `rocker hoodies` (€715) flips from above-target to below break-even. Sensitivity is flagged where it changes a verdict.

---

## Diagnosis

**The problem is at the Conversion layer — the landing page, not the keyword set.** Five core-product keywords are burning €1,961 below break-even, and the mechanism is now documented from two independent directions. Quality Score on every scored non-brand keyword is capped by `post_click_quality_score = BELOW_AVERAGE` while `creative_quality_score` is ABOVE_AVERAGE on five of six — the ads are good, the keywords are relevant, and the destination page is what drags the score to 4–7. That low score simultaneously produces the 64% rank-lost impression share the competitive audit measured and the poor conversion economics measured here; they are the same fault seen from two angles. Because 100% of the unprofitable spend sits on core product terms, the B3 gate prohibits a pause recommendation outright — pausing `punk hoodie` and `t shirt metal` would amputate the front door of a business whose entire proposition is punk/goth/tattoo apparel. The correct sequence is landing-page repair first, then offer, then a target review; only after those are exhausted would any keyword-level pause be defensible, and even then only on non-core terms, of which there are currently none. A second, independent finding sits alongside: Performance Max is absorbing 80 distinct queries that overlap these same keywords, a third of them for other brands entirely, and none is covered by a negative.

---

## Evidence ladder

### Conversion layer — H1 (active, high confidence, explains ~100% of flagged waste)

- Landing page experience is `BELOW_AVERAGE` on **6 of 6** non-brand keywords carrying a Quality Score → **H1**
- Ad relevance is `ABOVE_AVERAGE` on 5 of those 6; expected CTR is ABOVE_AVERAGE or AVERAGE on all 6 → the fault is isolated to the page → **H1**
- Quality Scores land at 4, 5, 5, 7, 7, 7 — every one capped by the single weak component → **H1**
- Brand keywords, pointing at different pages, score **10** with all three components ABOVE_AVERAGE → **H1**
- business.md §15 independently lists the "PDP truth gap" as an open risk and describes it verbatim as a *"Returns driver and LP-experience/Quality-Score driver"* → **H1**

### Business layer — H2 (active, blocks pause actions)

- **B3 core-term concentration = 100%.** All 5 UNPROFITABLE keywords carry `is_core_term = true`; €1,961 of €1,961 → **H2 — pause prohibited**
- Every unprofitable keyword contains a token from the documented scene core: `t shirt metal`, `goth and punk clothing`, `goth rock clothes`, `punk and rock outfit`, `tattoo hoodies` → **H2**
- Campaign target is tROAS 5.19 against a 1.9 break-even — a 2.7× gap. Keywords at 2.4–3.4 are labelled OVER_TARGET yet are genuinely profitable → target calibration, not keyword quality → **H2**

### Measurement layer — H3 (partially active, unusually favourable here)

- Account-wide inflation ×1.28–1.94 would normally block all pause recommendations → **H3**
- **But** Search TOF's factor is 1.00 (business.md §6; corroborated by AUD-D24) — these numbers are already clean → **H3 downgraded for this campaign specifically**
- Residual risk: the +€42.20 conversion value rule found by today's bidding audit may still apply. If so, `rocker hoodies` at 2.42 becomes 1.87 — below break-even → **H3 sensitivity**

### Traffic layer — H4 (active, independent of H1)

- 108 PMax overlap flags spanning **80 distinct** PMax search terms, **0 covered by any negative** → **H4**
- **27 of 80 (34%) are other brands or the wrong subculture**: 15+ "cyberpunk hoodie" variants (a sci-fi aesthetic, not punk subculture), plus `represent t shirt metallica`, `t shirt metallica`, `gildan t shirt metal`, `t shirt metal mulisha`, `cm punk hoodie` → **H4**
- 6 keywords degraded a tier between periods, including both top non-brand spenders: `t shirt metal` HERO → UNPROFITABLE, `punk hoodie` HERO → OVER_TARGET → **H1/H4**

---

## Module scores

| Module | Score | Grade | Key finding |
|---|---|---|---|
| Match Type Health | 20 / 20 | **100%** | Clean. No redundancy, all broad sits on Smart Bidding, flagged cross-campaign conflicts are geo-separated false positives |
| Performance Segmentation | 17.6 / 30 | **59%** | €1,961 (42% of non-brand spend) below break-even; 6 tier degradations; bottom-heavy distribution |
| Cannibalization & Duplicates | 22.6 / 25 | **90%** | Duplicates are geo-separated brand terms. Real finding is PMax absorbing 80 overlapping queries, a third off-brand |
| Keyword Hygiene | 10 / 10 | **100%** | All 37 keywords `ELIGIBLE` and `APPROVED`. No below-first-page bids |
| Intent Alignment | 15 / 15 | **100%** | No informational-intent keywords. Brand terms cleanly confined to brand campaigns |
| **Total** | **85.2 / 100** | **85% — Good** | |

---

## Actions — segmented by cascade state

### 🔍 Investigate first (blocking)

Nothing blocks in the usual sense — but one thing must be understood before any number here is acted on.

- **Confirm whether the +€42.20 conversion value rule applies to Search TOF.** If it does, every ROAS in this report drops ~29% and `rocker hoodies` (€715) joins the unprofitable set. **Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100, top finding: *"an enabled conversion value rule adds +€42.20 per conversion with no visible conditions, against €16.46 documented; Search TOF's value-per-conversion of €186.12 minus €42.20 equals €143.92, almost exactly the €143 clean AOV — which would mean even Search TOF carries this rule."* Re-run only for fresher data. → then `/tracking-specialist`

### 🔧 Structural fix needed — this is the real work

- **Repair landing page experience for the non-brand ad group.** Six of six scored keywords rate BELOW_AVERAGE; it caps Quality Score, which caps ad rank, which produces both the 64% rank-lost impression share and the sub-break-even economics. No LP audit exists → **run `/lp-auditor`**, scoped to the pages behind `STAN I BROAD I HOME`.
- **Review the offer on those pages.** business.md §15 documents "price-vs-quality perception" as an open blocker on exactly this traffic. No offer audit exists → **run `/offer-auditor`**.
- **Recalibrate the campaign target.** tROAS 5.19 against a 1.9 break-even labels genuinely profitable keywords (2.4–3.4 clean) as failures. Blocked until conversion goals are repaired. → `/strategy-specialist`, then `/bidding-optimizer`
- **Split the ad group.** All 17 non-brand keywords sit in one ad group spanning four subcultures and three product types. **Review the existing 2026-08-06 account audit** at `context/analysis/account/account-audit.md` — 75%, AUD-D20 flagged exactly this. Re-run only for fresher data.

### 🔄 Recover efficiency first

- **Add negatives for the off-brand PMax queries.** 27 of 80 overlapping terms are other brands or the wrong subculture — the "cyberpunk" cluster alone spans 15+ variants and is a completely different aesthetic from Stay Cold's. Zero negative coverage today. No search-term audit exists → **run `/search-term-auditor ngrams`** over 120–180 days to size the waste before excluding.
- **Then re-measure.** Only after LP, offer, target and negatives have been worked should keyword-level economics be re-judged.

### ✅ Act now (safe)

- **Nothing requires action today.** No duplicates to merge (the six flagged are geo-separated), no match conflicts to resolve (all 18 likewise), no zombies to remove (both are six days old), no disapproved or ineligible keywords, no below-first-page bids.
- Optional hygiene: `punk shop` [PHRASE] has produced zero impressions and zero cost across both periods. Removing it changes nothing but tidies the set.

### ⚠️ Do NOT pause — and this is the report's main instruction

| Keyword | Match | Spend | Clean ROAS | Why not |
|---|---|---|---|---|
| `t shirt metal` | BROAD | €1,006 | 1.50 | **Core term.** Largest non-brand keyword in the account and was HERO last period. LP experience BELOW_AVERAGE, QS 5 |
| `goth and punk clothing` | PHRASE | €457 | 1.41 | **Core term.** Literally names two of the four subcultures the brand sells to |
| `goth rock clothes` | PHRASE | €372 | 1.54 | **Core term.** LP experience BELOW_AVERAGE, QS 5 |
| `punk and rock outfit` | PHRASE | €79 | 1.82 | **Core term.** Marginally below break-even on trivial spend |
| `tattoo hoodies` | PHRASE | €47 | 0.21 | **Core term.** €47 total — not worth an intervention either way |

**B3 concentration is 100%.** These are the front door of a business whose stated proposition is "heavyweight apparel for metal / tattoo / hardcore / dark-streetwear culture." Pausing them would remove the category terms the brand exists to rank for, while leaving the actual defect — the landing page — untouched.

**Also never pause:** the 4 OVER_TARGET keywords (`rocker hoodies` €715, `punk hoodie` €562, `tattoo clothing` €173, `tattoo streetwear` €138). They clear break-even 1.9 at 2.42–3.39 clean and are only "over target" because the campaign target sits at 5.19. They are profitable.

---

## Module details

### Module 1 — Match Type Health (20/20)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| KW-D01 | Match type distribution | PASS | 5/5 | 37 keywords: 13 BROAD, 11 PHRASE, 13 EXACT. Non-brand set is 3 broad / 8 phrase / 6 exact — a reasonable modern mix on Smart Bidding |
| KW-D02 | Broad without Smart Bidding | PASS | 5/5 | Zero. Every campaign runs Target ROAS, Maximize Conversion Value or Target Impression Share; there is no manual CPC in the account |
| KW-D03 | Match type redundancy in ad group | PASS | 5/5 | **0 groups.** No keyword duplicated across match types within any single ad group |
| KW-D04 | Cross-campaign match conflicts | **PASS** (engine flagged 18) | 5/5 | **Overridden — false positive.** All 18 are brand terms appearing across the DE, FRA, SKANDI and USA brand campaigns in different match types. Today's geo-schedule audit verified from per-campaign LOCATION criteria that these campaigns target distinct markets, so they cannot compete in the same auction. The engine does not read geo targeting |

**Off-score note carried forward:** DE brand runs 5 of 5 enabled keywords on broad match and SKANDI 4 of 4, against a documented guardrail that forbids broad match on brand campaigns and a measured +278% result when it was removed from SKANDI in 2024. This is the account audit's AUD-D06 finding; it is a brand-campaign governance issue rather than a match-type-health defect, so it is not scored here.

### Module 2 — Performance Segmentation (17.6/30)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| KW-D05 | Hero keywords | PASS | 6/6 | 6 HEROes, all brand: `stay cold apparel` in four markets (ROAS 52–93), `stay cold clothing` SKANDI, `stay cold` FRA. Healthy and concentrated where you would want it |
| KW-D06 | Performance distribution | WARN | 3.6/6 | 9 INSUFFICIENT_DATA + 2 ZOMBIE + 1 LOW_PERFORMER = **12 of 37 (32%) producing nothing**. On a 37-keyword account that is thin, though the two "zombies" are new (see D08) |
| KW-D07 | Unprofitable keywords | **FAIL** | 0/8 | 5 keywords, **€1,961 = 42% of the non-brand campaign's €4,697**. Finding is real; the action is blocked by B3 at 100% core-term concentration. See "Do NOT pause" |
| KW-D08 | Zombies / low performers | **PASS** (engine flagged 2) | 5/5 | **Overridden.** `mens hoodies` and `sinner hoodie` were added **2026-07-31 via the API by `ads@jonas-makki.com`** — six days ago, and *after* Period A closed. Zero spend is expected, not a zombie signal. Source: `context/account-changelog.md`, pulled today. `punk shop` is genuinely dormant at €0 cost — zero waste |
| KW-D09 | Tier degradation | WARN | 3/5 | 6 keywords degraded, including both top non-brand spenders: `t shirt metal` **HERO → UNPROFITABLE**, `punk hoodie` **HERO → OVER_TARGET**, `tattoo streetwear` ACTIVE → OVER_TARGET, `tattoo hoodies` → UNPROFITABLE, `punk and rock outfit` → UNPROFITABLE, `punk shop` → LOW_PERFORMER. Zero upgrades. The non-brand set is deteriorating uniformly, which points at a shared cause rather than keyword-specific decay — consistent with H1 |

### Module 3 — Cannibalization & Duplicates (22.6/25)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| KW-D10 | Duplicate keywords | **PASS** (engine flagged 6) | 7/7 | **Overridden — same geo false positive as D04.** All 6 are `stay cold` variants across DE/SKANDI or USA/FRA brand campaigns |
| KW-D11 | Cannibalization | PASS | 6/6 | No cross-ad-group cannibalization is possible: the entire non-brand set lives in one ad group, and brand campaigns are geo-separated |
| KW-D12 | PMax overlap | WARN | 3.6/6 | 108 flags across **80 distinct PMax search terms**, **0 covered by negatives**. Some Search/PMax overlap is structurally unavoidable — but **27 of 80 (34%) are off-brand**, which is not |
| KW-D13 | Similar broad match | PASS | 6/6 | Only 3 broad keywords in the non-brand ad group (`t shirt metal`, `rocker hoodies`, `punk hoodie`) and they are semantically distinct |

**The off-brand PMax cluster, in full.** Fifteen-plus "cyberpunk" variants (`cyberpunk hoodie`, `cyberpunk hoodie sandevistan`, `samurai cyberpunk hoodie`, `adidas cyberpunk hoodie`, `h&m cyberpunk hoodie`, `youngla cyberpunk hoodie`, `lucy/rebecca/rtj/goni/realm/nonsense cyberpunk hoodie`, `cyberpunk shop`, …) plus `represent t shirt metallica`, `t shirt metallica`, `t shirt metallica original`, `t shirt metallica oversize`, `gildan t shirt metal`, `t shirt metal mulisha`, `t shirt metal carter`, `cm punk hoodie`.

Three distinct contamination types: a **sci-fi aesthetic** mistaken for punk subculture, **band merchandise** (Metallica) that Stay Cold does not sell, and **blank-apparel competitors** (Gildan). None is the brand's audience.

### Module 4 — Keyword Hygiene (10/10)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| KW-D14 | Below first-page bid | PASS | 5/5 | No keyword flagged. Expected — Smart Bidding manages bids everywhere |
| KW-D15 | Serving status | PASS | 5/5 | **All 37 keywords `system_serving_status = ELIGIBLE` and `approval_status = APPROVED`.** No disapprovals, no policy restrictions, no rare-search suppressions |

### Module 5 — Intent Alignment (15/15)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| KW-D17 | Informational intent | PASS | 8/8 | None. All 17 non-brand keywords are product or category queries with commercial intent — no "how to", "what is", "best", "vs", "review", or tutorial phrasings in any language |
| KW-D18 | Brand term coverage | PASS | 7/7 | Brand terms appear **only** in the five dedicated brand campaigns; zero brand terms in non-brand campaigns, confirmed today across all 1,022 keyword rows. Variants covered: `stay cold`, `staycold`, `stay cold apparel`, `stay cold clothing`, `stay cold hoodie`, `stay cold shirt`, `stay cold shop`. No competitor keywords exist — deliberate, per business.md §9: *"no active competitor campaign; do not auto-negate foreign brands"* |

---

## Peer report integration

| Peer | Report | Status | Used how |
|---|---|---|---|
| `/competitive-analyst` | `context/analysis/competitive/competitive-audit.md` | **FRESH — 2026-08-06**, 73/100 | Supplied the decisive H1 evidence: LP experience BELOW_AVERAGE on 6 of 6 scored non-brand keywords, ad relevance ABOVE_AVERAGE on 5 of 6. Its 64.2% rank-lost figure and this audit's sub-break-even ROAS are the same fault from two angles |
| `/bidding-auditor` | `context/analysis/bidding/bidding-audit.md` | **FRESH — 2026-08-06**, 54/100 | Established that Search TOF is the one campaign with inflation factor 1.00, making these keyword economics trustworthy. Also supplied the +€42.20 value-rule sensitivity |
| `/account-auditor` | `context/analysis/account/account-audit.md` | **FRESH — 2026-08-06**, 75% | AUD-D20 owns the single-ad-group split; AUD-D24 corroborated the clean goal config on Search TOF; AUD-D06 owns the brand broad-match issue |
| `/budget-auditor` | `context/analysis/budget/budget-audit.md` | **FRESH — 2026-08-06**, 47/100 | Search TOF is its one legitimate scale candidate — but gated on exactly the rank problem H1 describes |
| `/lp-auditor` | — | **Missing** | **Top handoff.** The fix lives here |
| `/offer-auditor` | — | Missing | Second handoff |
| `/search-term-auditor` | — | Missing | Owns the 27 off-brand PMax queries |
| `/quality-score-auditor` | — | Missing | Would extend the QS picture beyond the 6 keywords carrying a score |
| `/tracking-specialist`, `/strategy-specialist` | — | Missing | Value-rule resolution; target recalibration |

**No peer contradicts this audit's hypothesis.** Four fresh reports independently converge on the landing page as the constraint on non-brand performance.

---

## Data freshness

| Source | Rows | Status |
|---|---|---|
| `keyword/keywords-periodA.csv` / `periodB.csv` | 37 / 37 | Pulled fresh 2026-08-06 |
| `keyword/keywords-conv-by-action-periodA/B.csv` | 38 / 36 | Pulled fresh — 25 / 22 keywords with tracked conversions |
| `keyword/keywords-structural.csv` | 37 | Pulled fresh |
| `keyword/pmax-search-terms.csv` | **106,689** | Pulled fresh |
| `keyword/negatives-*.csv` | 21 campaign / 3,213 shared / 13 links / 1 ad group | Pulled fresh |
| `bidding-strategies.csv` | 0 | No portfolio strategies exist — all targets are campaign-inline |
| `evidence/keyword-tiers.csv` | 37 | Generated |
| `evidence/keyword-flags.csv` | 28 | Generated |
| `evidence/keyword-overlaps.csv` | 132 | Generated |

⚠️ **Data sufficiency.** 37 keywords is a small set, and 12 of them produced no meaningful data in the window. Per-keyword conclusions for anything under ~€100 of spend are indicative only. The five findings that drive this report all sit above €370 except `tattoo hoodies` (€47), which is explicitly flagged as immaterial.

**Tooling note:** `keyword-auditor/scripts/` had no installed dependencies; `csv-parse` was installed to make both analyzers executable.
