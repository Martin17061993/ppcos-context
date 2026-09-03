# Budget Audit — 2026-08-06

**Score:** 47/100 (Critical)
**Window:** 30 days, lag-offset 8 | **Module scope:** full (19 diagnostics, 5 modules)
**Account:** 3599116618 (Stay Cold Apparel) · EUR · 15 campaigns, 50 budgets, 0 portfolios
**Monthly target:** €32,500 | **Posture:** growth (PAR 1.2) | **Break-even:** clean ROAS 1.9
**Run by:** /budget-auditor at 2026-08-06

> ℹ️ Experiment campaigns INCLUDED (skill default). No active experiment variants were found in the serving roster.
> ✅ `account-changelog.md` was missing at the start of this run and was **pulled during it** (2026-07-08 → 2026-08-06, 67 attributable + 266 Editor changes). Every finding below is changelog-informed.

---

## Executive read

47 is the lowest of the three audits run on this account today, and unlike the other two it is not describing a latent problem. **Spend is ramping right now.** The account spent ~€650/day in mid-July, €1,476 on 31 July, then €2,378 → €2,948 → €3,160 → €3,274 → €2,530 across the first five days of August. That is €14,290 month-to-date and a month-end projection of **€78,000–93,000 against a €32,500 target**. For reference, the June 2026 over-scaling that business.md calls the most expensive decision period of the half-year peaked at €62,000/month. The current run rate is higher.

One thing matters this week and it is not subtle: **find out whether this ramp is intended, and if not, stop it.** The changelog shows why it is happening — FOKUSPRODUKTE was raised **€550 → €1,150/day (+109%) in a single day, in two steps three minutes apart** on 24 July, Search TOF went €120 → €240 (+100%) over seven days, and PROSPECTING went €880 → €1,250 (+42%). business.md's own guardrails cap steps at ±30% every 7 days and record that increases above +90% are **0 for 6 positive**, with the worst single case being a PROSPECTING raise that cost −27% on €17,435. PROSPECTING has now been raised again on top of that exact decision. August is not a promo month under the configured seasonality profile, so there is no seasonal justification on file.

Second: **the biggest spender is losing money and the engines cannot see it.** FOKUSPRODUKTE sits at clean ROAS 1.72 against a 1.9 break-even. Because the API returns inflated conversion value, the scoring engine classified it as *profitable with 0.64 margin* and would have recommended raising its budget further. I overrode three verdicts on that basis — details below. This is the same measurement fault the bidding audit (54/100, today) named as its blocking layer, and the account audit (75%, today) traced to 14 of 15 campaigns overriding the clean account-default conversion goal.

What is not a problem: there are no shared budgets, so that entire module is N/A rather than failing. The five zero-spend campaigns are the same non-serving PMax shells both other audits already flagged — a structural fault, not a budget one. And two campaigns are 13 days into a 14-day learning window that clears tomorrow, so "do nothing today" is a legitimate answer for those two specifically.

Read the diagnosis, then the risks. Everything else is reference.

---

## Diagnosis (technical)

The problem is at the **Struct layer — an uncontrolled budget ramp produced by guardrail-breaking raises — sitting on top of a blocking M layer that makes the ramp's damage invisible.** Between 17 and 24 July, three campaigns received budget increases of +42%, +100% and +109%, all executed via the web UI by a single operator, all outside any documented promo window, and two of them stacked with simultaneous bid-target changes. The 30-day performance window mostly predates those raises, which is why the window totals look calm; the daily series does not. Spend has tripled in six days and is now above the June 2026 crisis level. Underneath, the measurement fault means reported ROAS overstates profitability by roughly 50%, so the campaign absorbing the largest share of the new spend — FOKUSPRODUKTE at €12,316 and clean ROAS 1.72 — reads as profitable to every automated check while actually sitting below break-even. The correct first action is not a budget mutation in either direction: it is to establish whether the ramp was authorised, because that single answer determines whether this is a scaling decision to be measured or an incident to be reversed.

---

## Top hypothesis

- **Layer:** Struct (with M active-blocking beneath it)
- **Name:** Uncontrolled spend ramp from guardrail-breaking budget raises, invisible because conversion value is inflated
- **Confidence:** **high**
- **Evidence:** BUD-D10 FAIL (projected +172.6% overspend). Changelog: five budget increases 17–24 July of +42% / +54% / +55% / +35% / +30%, netting +109% on FOKUSPRODUKTE in one day. Daily spend series €650/day → €3,274/day in six days. BUD-D14 and BUD-D15 both had to be overridden because the largest spender is below break-even on the clean series while the engine scored it profitable.

**Active blocking layers:** M (Measurement) — blocks every raise. Bid — BUD-D08 carries `blocking: ['bidding']`.

---

## Module scores

| Module | Score | Status |
|---|---|---|
| Allocation | 12/30 | **40% — Critical** |
| Limitation | 12/25 | **48% — Critical** |
| Pacing | 6.4/12 available (15 nominal — D12 INFO) | 53% — Critical |
| Sufficiency | 5.4/9 available (15 nominal — D05 SKIP) | 60% — Needs attention |
| Shared budgets | N/A — no shared budgets exist | 15 pts redistributed |
| **Total** | **35.8 / 76 available** | **47/100 — Critical** |

*24 of 100 nominal points removed: Shared module (15, no shared budgets), BUD-D05 (6, no tCPA campaign exists in the account), BUD-D12 (3, INFO). Formula: 35.8 / (100 − 24) × 100 = 47.1 → 47.*

### Three engine verdicts I overrode, and why

All three have the same cause: the engines resolve break-even from `biddingAudit.breakEvenROAS = 1.9`, which is a **clean** threshold, but compare it against `metrics.conversions_value`, which is the **inflated** series. FOKUSPRODUKTE's factor is 1.81, so reported ROAS 3.12 deflates to **1.72 — below break-even**.

| Diagnostic | Engine | Reported here | Reason |
|---|---|---|---|
| BUD-D04 — unprofitable + budget-limited | PASS (5/5) | **FAIL (0/5)** | The engine found no unprofitable campaign that is budget-limited. FOKUSPRODUKTE is exactly that: clean 1.72 against 1.9, with 25.6% IS Lost (Budget) — and its budget was just raised +109%. This is the "active harm" case the module is built to catch. |
| BUD-D14 — underperformer over-allocated | PASS (10/10) | **FAIL (0/10)** | FOKUSPRODUKTE is the single largest line in the account at €12,316 (40% of window spend), below break-even, and freshly doubled. That is an underperforming campaign being over-allocated, by the plainest reading. |
| BUD-D15 — profitable share of spend | PASS (5/5) | **WARN (3/5)** | Engine: "profitable share = 100%". Deflated, FOKUSPRODUKTE's €12,316 is unprofitable, putting the real profitable share at roughly **60%** (€18,558 of €30,874). |

BUD-D03 keeps its WARN but its campaign list is corrected: only **Search TOF** is genuinely a profitable budget-limited campaign. FOKUSPRODUKTE was removed from that list — recommending a raise there would have been actively wrong.

---

## Risks (segmented by cascade state)

### 🔍 Investigate first (blocking)

- **Is the August spend ramp authorised?** €14,290 MTD, projecting €78–93k against a €32,500 target. No promo window is configured for August, and business.md Gap G5 records that `promo_windows.csv` is deliberately unwritten pending an unresolved offer-rule conflict — so an approved promo cannot be ruled out from the files alone. **This one question determines whether everything below is a scaling programme to be measured or an incident to be reversed.** → Jonas, today
- **Who is authorised to change budgets?** All five budget changes and all three target changes came from `exmachina.agency@gmail.com` via the web UI. business.md §13 states "Martin proposes, Jonas executes. No exceptions." A further 266 changes via Editor carry no attribution. Proposals routed to Jonas may not reach whoever is actually making these decisions. → Jonas, as a question not an accusation
- **Conversion-value integrity.** Until the 14 campaign-level goal overrides and the +€42.20 value rule are resolved, no profitability-based budget decision is trustworthy — as the three overrides above demonstrate concretely. → `/tracking-specialist`

### 🔧 Bidding-side fix (sequence before budget)

- **BUD-D08 — 8 campaigns below the 50-conversion smart-bidding floor**, carrying `blocking: ['bidding']`. **A fresh bidding audit already exists** (2026-08-06, 54/100 Critical): it found the same 8 campaigns, established that 5 of them are the non-serving PMax shells, and identified the two genuine cases as `OVER-INDEX` (18.2 conv) and `NEAR INDEX` (5 conv). Its recommendation — consolidate rather than fund — stands. **Review `context/analysis/bidding/bidding-audit.md`; no need to re-run.**
- **PROSPECTING was raised +42% against a limit that does not exist.** Its IS Lost (Budget) is **0%**; its constraint is rank at 48.2%. The bidding audit reached the same conclusion independently. Budget cannot buy rank-lost impression share.

### 🔄 Recover efficiency first

Neither the Eff nor Conv layer can be cleared — no search-term, keyword, quality-score, LP or offer audit exists.

- Search TOF is the one legitimate raise candidate (clean 3.74, 31.7% IS Lost (Budget)) — but it also carries 58.7% rank-lost IS per the bidding audit, meaning most of its missing impression share is **not** budget-recoverable. Establish the split before funding it → `/quality-score-auditor`
- business.md §15 flags two open CVR blockers ("price-vs-quality perception", "PDP truth gap") on exactly the non-brand traffic now absorbing the extra spend → `/lp-auditor`, `/offer-auditor`

### ⚖️ Allocation

- **BUD-D13 — 6 profitable campaigns under 5% spend share**: DSA (1.6%, clean 5.90), FRA brand (1.3%), USA brand (2.5%), SKANDI brand (2.0%), OVER-INDEX (1.7%), NEAR INDEX (0.1%). The three brand campaigns are `protect` by guardrail and should not be scaled on this signal alone. DSA is the genuine case — highest clean ROAS of any non-brand unit, smallest budget consumption, 90% rank-lost.
- **BUD-D14 (overridden to FAIL) — FOKUSPRODUKTE holds 40% of spend below break-even.** On the clean series it is a **reduce** candidate, not a hold. The +109% raise moved it in the wrong direction.

### ✅ Act now (safe)

- **Nothing that changes a budget.** Every raise is blocked by the M layer; every reduction on FOKUSPRODUKTE and Search TOF is blocked until tomorrow by the learning window.
- The one genuinely safe action — pulling the account changelog — **was completed during this run.**

### ⚠️ Hold (in learning)

| Campaign | Last material change | Days | Clears |
|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | 2026-07-24 — budget +35% **and** target change | 13 | **2026-08-07** |
| `EX I EN I WW I TOF … Kollektionen + Types` | 2026-07-24 — budget +30% **and** target +48% | 13 | **2026-08-07** |

Both had two levers moved within four minutes, which makes the outcome unattributable regardless. Touching either today resets a learning period one day from completing. `PROSPECTING` (last changed 2026-07-17, 20 days) is out of learning.

### ℹ️ Confirm intent

- **BUD-D07 — all 50 budgets are on STANDARD delivery**, so Google may spend up to **2× the daily budget** on any given day. Normally a footnote; with €4,415/day of nominal daily budget now configured across enabled campaigns, the theoretical ceiling is far above the €32,500 monthly target. This is what makes the current ramp possible.
- **A Demand Gen / Video relaunch appears to be in preparation.** 113 Editor changes on 2026-08-05 and 38 more today, concentrated on paused DG/YouTube campaigns — `BS DEALS - DG_ CP+PDP_S+V` is the single most-edited campaign in the account. business.md Gap G6 flags it as clean ROAS 5.78 and "fundamentally healthy" but idle. **Two budget consequences:** any relaunch needs money not in the €32,500 plan, and business.md §7 warns that `YouTube follow-on views` is still an enabled primary conversion that "will corrupt bidding signal the moment Video or Demand Gen restarts." Defuse before launch. Precedent: "Video View DRAFT ran four weeks unnoticed — €4,750 for 2 purchases, clean ROAS 0.04."

---

## Opportunities

| # | Type | Campaign | Projected impact | Action |
|---|---|---|---|---|
| 1 | profitable_limited_recovery | Search TOF | +1,810 clicks, +43.9 conv, +€2,181 cost, +€8,165 value at projected ROAS 3.74 (clean — this campaign's inflation factor is 1.00, so the projection is trustworthy) | **Genuine, but gated.** 58.7% of its lost IS is rank, not budget. Confirm the split via `/quality-score-auditor` before funding. Max +30% per step. |
| 2 | winner_underfunded | `JM I DSA I FC'S I CAT'S` | 1.6% of spend at clean ROAS 5.90 — best non-brand efficiency in the account | Rank-limited at 90%, not budget-limited. Budget will not fix it; ad quality might. Not a raise. |
| 3 | reduce_candidate | `EX I SHOPPING I FOKUSPRODUKTE` | 40% of spend at clean 1.72 vs 1.9 break-even. At business.md's contribution table, clean 1.72 ≈ **−€0.10 contribution per euro spent** | **The largest euro lever in the account, and it points down, not up.** Blocked until 2026-08-07 by learning; blocked further by the M layer for the exact size of the cut. |
| 4 | underspend_redeploy | — | None. The account is overspending, not underspending. | — |

---

## Pacing snapshot

| Metric | Value |
|---|---|
| Month-to-date spend (1–5 Aug) | **€14,290** |
| Proportional target at day 6 | €6,290 |
| Deviation | **+24.6pp** |
| Engine projection (5-day mean × 31) | **€88,595** |
| Conservative projection (hold at 5 Aug's €2,530/day) | ~€80,100 |
| Aggressive projection (last 3-day mean €2,988/day) | ~€92,600 |
| **Monthly target** | **€32,500** |
| Overshoot | **+140% to +185%** |
| August a highlight month? | **No** — configured highlights are October, November, December |

**Daily series — the finding in one column:**

| Date | Spend | |
|---|---|---|
| 2026-07-10 → 07-30 | €462–893/day | trough |
| 2026-07-31 | €1,476 | ramp begins |
| 2026-08-01 | €2,378 | |
| 2026-08-02 | €2,948 | |
| 2026-08-03 | €3,160 | |
| 2026-08-04 | **€3,274** | peak |
| 2026-08-05 | €2,530 | |

Last 7 days average **€2,360/day** vs prior 7 days **€719/day** — **+228%**.

**Historical calibration.** June 2026 ran €61,961/month (~€2,065/day) and business.md records clean ROAS falling to 5.04 with marginal clean ROAS at 0.63 — "buying revenue at a 67-cent loss per marginal euro… the most expensive single decision of H1 2026." The current daily rate exceeds that period. July 2026 totalled €30,829, almost exactly on target; the correction business.md celebrates lasted about four weeks.

⚠️ **Caveats, stated plainly.** Five days is a short base for a month-end projection, and 5 August came down from 4 August. A linear extrapolation is crude. And because Gap G5 leaves `promo_windows.csv` unwritten, an approved early-August promo cannot be excluded from the files alone. None of this changes the recommendation — the ramp is large enough that confirming intent is worth doing today regardless of which projection is right.

---

## Sequenced handoffs

**Top hypothesis:** Struct — uncontrolled budget ramp, with M blocking beneath it.

1. **Confirm intent on the August ramp** — is €78–93k authorised? → **Jonas, today.** Nothing below is safe to act on until this is answered.
2. **Confirm budget-change authority** — `exmachina.agency@gmail.com` made every budget and target change this window; business.md documents a different operating model → **Jonas**
3. **Repair conversion-goal configuration** — 14 campaign-level overrides + the +€42.20 value rule. Blocking for every profitability-based budget decision → `/tracking-specialist`
4. **Bidding side** — already done. **Review `context/analysis/bidding/bidding-audit.md` (2026-08-06, 54/100)**; its top finding is the same measurement block, and it independently confirms PROSPECTING is rank- not budget-limited. Re-run only if you want fresher data.
5. **Structure side** — already done. **Review `context/analysis/account/account-audit.md` (2026-08-06, 75%)**; its AUD-D08 owns the 5 zero-spend campaigns behind BUD-D16, and AUD-D05 owns the OVER-INDEX / NEAR-INDEX consolidation behind BUD-D08.
6. **Efficiency layer** — needed before funding Search TOF → `/quality-score-auditor`, then `/search-term-auditor`
7. **PMax structural** — the 5 non-serving shells → `/pmax-auditor`, `/feed-auditor`
8. **Budget mutations — `/budget-optimizer`, not before the above:**
   - Reduce: FOKUSPRODUKTE (clean 1.72, 40% of spend) — after 2026-08-07 and after step 3
   - Reallocate: away from the 5 zero-spend shells
   - Raise: **none approved.** Search TOF is the only candidate and it is gated on step 6

---

## Module details

### Allocation (12/30 — Critical)

| ID | Verdict | Pts | Evidence |
|---|---|---|---|
| BUD-D13 | WARN | 6/10 | 6 profitable campaigns under 5% spend share: DSA 1.6%, USA brand 2.5%, SKANDI brand 2.0%, OVER-INDEX 1.7%, FRA brand 1.3%, NEAR INDEX 0.1%. Three are `protect`-priority brand campaigns and should not be scaled on this signal alone. |
| BUD-D14 | **FAIL** (overridden from PASS) | 0/10 | FOKUSPRODUKTE: €12,316 = 40% of window spend, clean ROAS 1.72 vs 1.9 break-even, budget raised +109% on 2026-07-24. Largest allocation in the account pointed at the least profitable non-trivial campaign. |
| BUD-D15 | **WARN** (overridden from PASS) | 3/5 | Real profitable share ≈ 60% of classified spend, not 100%. |
| BUD-D16 | WARN | 3/5 | 5 active campaigns, zero spend across 30 days: the PMax shells. Same set as account audit AUD-D08 and bidding BID-D01/D03. |

### Limitation (12/25 — Critical)

| ID | Verdict | Pts | Evidence |
|---|---|---|---|
| BUD-D01 | WARN | 3/5 | 2 campaigns with IS Lost (Budget) ≥ 10%: Search TOF 31.7%, FOKUSPRODUKTE 25.6%. |
| BUD-D02 | WARN | 3/5 | Both exceed the 25% severe threshold. |
| BUD-D03 | WARN (list corrected) | 6/10 | Engine listed 2 profitable+limited campaigns. Deflated, only **Search TOF** qualifies (clean 3.74, factor 1.00). FOKUSPRODUKTE removed — it is unprofitable. |
| BUD-D04 | **FAIL** (overridden from PASS) | 0/5 | FOKUSPRODUKTE is unprofitable (clean 1.72) **and** budget-limited (25.6%) **and** was just raised +109%. The module's "active harm" case. |

### Pacing (6.4/12 available — Critical)

| ID | Verdict | Pts | Evidence |
|---|---|---|---|
| BUD-D09 | WARN | 2.4/4 | MTD €14,290 vs €6,290 proportional target — **+24.6pp**. |
| BUD-D10 | **FAIL** | 0/4 | Projected €88,595 vs €32,500 — **+172.6%**. |
| BUD-D11 | PASS | 4/4 | Not underspending. Vacuously true given D10 — recorded for completeness, carries no positive signal. |
| BUD-D12 | INFO | — | August is not a highlight month; September isn't either. **No seasonal justification exists for the overspend.** 3 pts removed. |

### Sufficiency (5.4/9 available — Needs attention)

| ID | Verdict | Pts | Evidence |
|---|---|---|---|
| BUD-D05 | **SKIP** | —/6 | Engine returned PASS, but the account contains **no tCPA campaign at all** (every campaign is Target ROAS, Maximize Conversion Value, or Target Impression Share — verified in the bidding audit). The check is vacuous here; SKIPped per the skill's all-PMax edge case rather than banked as a free pass. 6 pts removed. |
| BUD-D06 | WARN | 1.8/3 | 2 campaigns hit their daily budget on 8 of 14 days (57%): Search TOF (€240/day) and OVER-INDEX (€45/day). Possible mid-day exhaustion. |
| BUD-D07 | INFO | — | All 50 budgets on STANDARD delivery → up to 2× daily spend possible. Material context for the current ramp. |
| BUD-D08 | WARN | 3.6/6 | 8 campaigns below the 50-conv floor. `blocking: ['bidding']`. Covered by the fresh bidding audit. |

### Shared budgets (N/A)

| ID | Verdict | Evidence |
|---|---|---|
| BUD-D17 / D18 / D19 | SKIP | No shared budgets exist — all 50 budgets have `explicitly_shared = false`. Module N/A; 15 points redistributed. Independently confirmed by the bidding audit (BID-D17 PASS). |

---

## Peer report integration (Phase 3.5)

| Peer | Report | Status | Used how |
|---|---|---|---|
| `/bidding-auditor` | `context/analysis/bidding/bidding-audit.md` | **FRESH — 2026-08-06**, 54/100 Critical | Supplied the per-campaign inflation factors used for all three verdict overrides. Independently confirmed PROSPECTING is rank- not budget-limited (0% budget-lost, 48.2% rank-lost), and that Search TOF carries 58.7% rank-lost — which caps how much of its 31.7% budget-lost IS is actually recoverable. Its BUD-D08 equivalent (BID-D01/D03) identified the same 8 campaigns. |
| `/account-auditor` | `context/analysis/account/account-audit.md` | **FRESH — 2026-08-06**, 75% Good | AUD-D08 owns the 5 zero-spend campaigns behind BUD-D16. AUD-D05 owns the OVER-INDEX / NEAR-INDEX consolidation. AUD-D24 located the conversion-goal mechanism behind the M block. |
| `/tracking-specialist` | — | Missing | Blocking handoff |
| `/quality-score-auditor` | — | Missing | Gates the Search TOF opportunity |
| `/search-term-auditor`, `/keyword-auditor` | — | Missing | Eff layer uncleared |
| `/lp-auditor`, `/offer-auditor` | — | Missing | Conv layer uncleared |
| `/competitive-analyst` | — | Missing | Would contextualise the rank-lost share on PROSPECTING and DSA |
| `/strategy-specialist` | — | Missing | Gap G1 (gross vs net) still moves break-even between 1.6 and 1.9 |

**Where the fresh peers agree:** all three audits today converge on the same measurement fault from three different directions — structure found the mechanism, bidding found the consequence for targets, budget found the consequence for allocation. That convergence is why the M-layer block is rated high confidence rather than medium.

---

## Configuration snapshot

- **Monthly target:** €32,500 — midpoint of business.md §3's documented €30–35k range (Martin's ruling 2026-08-06)
- **Currency:** EUR
- **Posture:** growth, PAR 1.2 (inherited from `biddingAudit`)
- **Break-even:** clean ROAS 1.9 — Gap G1 open (1.6 if net values)
- **Per-campaign targets:** 15 campaigns mapped; 3 `protect`, 2 `scale`, 10 `hold`. The 5 non-serving PMax shells set to €0 so they receive no allocation share
- **Seasonality:** `highlight_months` = October, November, December (derived from business.md §14). ⚠️ Gap G5 unresolved — `promo_windows.csv` deliberately unwritten
- **Experiments:** included (skill default)
- **Static defaults:** all unchanged
- **Last confirmed:** 2026-08-06 | **business.md hash:** `7bbedf9130b8a944`

### Data freshness

| Source | Date | Status |
|---|---|---|
| `budget/campaign-budgets.csv` | 2026-08-06 | Pulled fresh (50 rows) |
| `budget/campaigns-budget-perf.csv` | 2026-08-06 | Pulled fresh (15 rows) |
| `budget/campaigns-pacing-daily.csv` | 2026-08-06 | Pulled fresh (554 rows) |
| `budget/account-budget.csv` | 2026-08-06 | Pulled fresh (1 row) |
| `bidding-strategies.csv` | 2026-08-06 | Pulled fresh (0 rows — no portfolios) |
| `context/account-changelog.md` | 2026-08-06 | **Pulled during this run** — 67 attributable + 266 Editor changes |

⚠️ **The 30-day performance window largely predates the budget raises of 17–24 July.** Window totals therefore understate the current run rate by a wide margin. Where this report cites current state it uses the daily series, not the window aggregate.
