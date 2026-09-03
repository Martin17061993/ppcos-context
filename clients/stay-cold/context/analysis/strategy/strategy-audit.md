# Strategy Audit — 2026-08-07

**Overall Score:** 81 / 105 — **77% · Good**
**Mode:** DIAGNOSE · both modules · 14 diagnostics (5 SKIP by vertical)
**Vertical:** D2C e-commerce (apparel) · EUR · **Viability verdict: GO — on fundamentals**
**Sources:** `business.md` (2026-08-03, 4 days old) · `campaigns.csv` · `account-changelog.md` (2026-08-06)

---

## Executive read

The unit economics are excellent and the goals are not agreed with anyone. That gap is the whole audit.

On the economics side this account scores a clean 100%. A 75% gross margin sourced from the client's own pricing system, a break-even clean ROAS of 1.9 derived line-by-line through VAT, COGS, returns, payment fees and shipping, and a documented robustness check showing the threshold barely moves across the plausible AOV range. Very few accounts have this. The fundamentals unambiguously support profitable advertising, and the verdict is **Go**.

**The goals layer is where it breaks, and business.md says so itself in bold:** *"No client-set goals exist… The targets below are provisional, derived from unit economics, and require Jonas's sign-off. Do not treat them as agreed."* Every target this account is being optimised against was derived by the analyst, not set by the business. Google is still not listed as a channel in Stay Cold's own marketing strategy — it appears only as open question #1, and the strategy document has sat in draft since June. Thirteen audits have now optimised toward numbers nobody has approved.

**Two priorities follow.** First, get the targets signed off — that single act converts twelve audits of provisional recommendations into an agreed plan. Second, **fix the campaign targets that contradict the documented goal.** Deflated to the clean series, three of six non-brand campaigns sit more than 30% below the 2.5 target, and the DSA campaign's effective target is **1.29 — below the 1.9 break-even**. That campaign is currently instructed to buy unprofitable volume.

**One genuine weakness in the targets themselves.** The non-brand target of 2.5 against a 1.9 break-even implies a profit-above-breakeven ratio of 76%, above the healthy 70% ceiling. It leaves only 24% headroom — about €0.30 of contribution per media euro. Defensible, but thin, and it means a small measurement error flips the campaign to loss-making.

**What is not a problem:** the guardrails. They are unusually good — floors grounded in break-even, budget step rules derived from 95 measured changes over two years, and an explicit acknowledgement that growth and efficiency cannot be pursued simultaneously. That last point is the mark of an honest plan.

Read the Viability verdict, then D14. Baseline run — no prior score.

---

## Viability verdict: **GO — on fundamentals**

| Contributing factor | Assessment |
|---|---|
| Gross margin 75% | ✅ Far above the 30% viability minimum |
| Break-even clean ROAS 1.9 (190%) | ✅ Far below the 333% ceiling |
| Documented derivation | ✅ Full line-item calculation, robustness-tested |
| Data freshness | ✅ 4 days old |

**This verdict is about unit economics, not current performance — and the distinction matters.** The fundamentals support profitable advertising comfortably. The account is nonetheless running roughly two-thirds of its spend at or below break-even, which is an execution problem the other twelve audits address, not a viability problem. A business with a 75% margin and a 1.9 break-even can absolutely make Google Ads work; this one currently is not.

### Risk factors that could change the verdict

| Risk | Impact | Source |
|---|---|---|
| **Gap G1 — gross vs net conversion values unverified** | Moves break-even between **1.6 and 1.9** — a factor of 1.19 on the most important number in the account | business.md §2 |
| **Gap G8 — payment fees (2%) and shipping (€6/order) are assumptions** | Both feed the break-even calculation directly | business.md §2 |
| **Gap G2 — repeat purchase rate / CLV unavailable** | The account bids with a **+€16.46 new-customer value bonus that nothing validates** | business.md §2 |
| Measurement inflation | Conversion value runs ×1.28–1.94 above the clean series, so reported performance overstates reality | 2026-08-06 bidding audit |

---

## Module 1 — Unit Economics: 50/50 (100%)

*Ecommerce vertical: D01, D02, D08, D09 active. D03–D07 SKIP (Lead Gen / SaaS only).*

| ID | Diagnostic | Status | Pts | Details |
|---|---|---|---|---|
| **STR-D01** | Gross margin adequacy | **PASS** | 15/15 | **~75%**, High confidence. Sourced from Airtable `Function: Price Recommender` — "Buying price ×4" on `Default Buying Price DDP incl. VAT`. A ×4 markup is mathematically exactly 75% gross margin, and VAT cancels out. Threshold is ≥30%; this clears it by 45 points. Implied break-even ROAS 190% against a 333% ceiling |
| **STR-D02** | Break-even ROAS calculation | **PASS** | 15/15 | **1.9 (190%)**, explicitly documented with a full line-item derivation — see table below. Non-brand target 2.5 sits above it; account target 6.0 far above. Documented reasoning links target to economics directly |
| **STR-D03–D07** | Lead Gen / SaaS diagnostics | **SKIP** | — | Not applicable to ecommerce |
| **STR-D08** | Viability verdict | **PASS** | 15/15 | **Go.** All active vertical diagnostics pass. Risk factors listed above, none of them blocking |
| **STR-D09** | Unit economics staleness | **PASS** | 5/5 | Last updated **2026-08-03 — 4 days ago**. Threshold is 30 days |

### The break-even derivation (per average tracked order of €143)

| Line | Amount |
|---|---|
| Tracked revenue | €143.00 |
| VAT (19%) | −€22.83 |
| COGS (25% of net) | −€30.04 |
| Returns (5%, net of recovered COGS/VAT + handling) | −€5.51 |
| Payment fees (2%) *[assumption]* | −€2.86 |
| Outbound shipping *[assumption]* | −€6.00 |
| **Contribution before media** | **€75.76 = 53% of tracked revenue** |
| **Break-even clean ROAS** | **≈ 1.9** |

**Robustness noted in business.md:** the same calculation at a €119 order value also yields 1.9. The threshold is insensitive to AOV across the plausible range — it is driven by margin, VAT and returns. **The only input that moves it materially is the gross-vs-net question (Gap G1), which would take it to 1.6.**

### Contribution per €1 of media, at various clean ROAS levels

| Clean ROAS | Contribution per €1 spent |
|---|---|
| 1.72 (FOKUSPRODUKTE today) | **−€0.10** |
| 1.90 (break-even) | €0.00 |
| 2.24 (PMax PROSPECTING today) | +€0.16 |
| **2.50 (non-brand target)** | **+€0.30** |
| 3.74 (Search TOF today) | +€0.63 |
| 8.26 (account, July) | +€3.30 |

---

## Module 2 — Goals & KPIs: 31/55 (56%)

| ID | Diagnostic | Status | Pts | Details |
|---|---|---|---|---|
| **STR-D10** | Primary KPI definition | **PASS** | 15/15 | All four conditions met. KPI explicitly named (**clean ROAS**, purchase-only series), numeric targets set (account floor 4.0 / target 6.0; non-brand floor 1.9 / target 2.5), goal type stated (**Cost Control**, transitioning to Balanced), and ROAS is the correct Tier-1 KPI for ecommerce. *The approval question belongs to D14, not here* |
| **STR-D11** | Guardrail KPI definition | **PASS** | 10/10 | **Unusually strong.** See below |
| **STR-D12** | Target feasibility | **WARN** | 6/15 | **Implied PAR 76% on the non-brand target — above the 70% healthy ceiling.** See below |
| **STR-D13** | Goal-to-bid-strategy alignment | **FAIL** | 0/10 | Three of six non-brand campaigns deviate >30% from the documented target once deflated, and one is instructed to bid **below break-even**. See below |
| **STR-D14** | Stakeholder alignment | **FAIL** | 0/5 | **No client-set goals exist.** See below |

### D11 — why the guardrails pass so comfortably

| Guardrail | Threshold | Grounded in |
|---|---|---|
| Non-brand clean ROAS floor | **1.9** | Literally the break-even figure |
| Account clean ROAS floor | 4.0 | 90-day account anchor |
| Brand impression share floor | 90% | Measured precedent |
| Monthly spend ceiling | €30–35k | Volume protection under an efficiency-primary goal |
| Budget raise permitted only when | budget-lost IS ≥ ~20% | 95 measured budget steps over two years |
| Never raise budget when | budget-lost IS < 5% | Same evidence base |
| Step size outside promo windows | max ±30%, ≥7 days apart | Same |
| Saturation response | Cut when marginal clean ROAS < break-even proxy | Same |
| Zero-conversion alarm | Any campaign >€1,000 cumulative without a purchase | Same |

The guardrails are the opposite type from the primary goal (efficiency primary → volume-protective guardrails via the spend range and brand IS floor), every threshold is numeric, and none is arbitrary — the budget rules are derived from two years of measured change history rather than convention. **This is better than most accounts manage.**

### D12 — the target is defensible but thin

| Target | Break-even | Implied PAR | Range |
|---|---|---|---|
| **Non-brand clean ROAS 2.5** | 1.9 | **76%** | ⚠️ Above the 70% ceiling |
| Account clean ROAS 6.0 | 1.9 | 32% | ✅ Healthy |
| Account floor 4.0 | 1.9 | 48% | ✅ Healthy |

The account-level targets sit comfortably in the healthy band. The **non-brand target does not** — 2.5 against a 1.9 break-even leaves only 24% headroom, worth about €0.30 of contribution per media euro.

That is a real profit, and business.md derives it explicitly ("2.5 yields +€0.30 contribution per media euro, enough to carry overhead") — the reasoning is documented, which is why this is a WARN and not a FAIL. But the thin margin has a consequence worth naming: **a modest measurement error flips it.** If Gap G1 resolves to net values, break-even drops to 1.6 and the PAR improves to 64% (healthy). If the conversion inflation is worse than measured, the campaign is loss-making. The target's viability currently depends on an unverified number.

### D13 — campaign targets contradict the documented goal

Comparing each non-brand campaign's **effective clean target** (nominal target ÷ its verified inflation factor, per business.md §6) against the documented non-brand target of 2.5:

| Campaign | Nominal tROAS | Inflation | **Effective clean target** | vs target 2.5 | vs break-even 1.9 |
|---|---|---|---|---|---|
| **`JM I DSA I FC'S I CAT'S`** | 2.50 | 1.93 | **1.29** | **−48%** | ❌ **BELOW BREAK-EVEN** |
| `EX I WW I PMAX … PROSPECTING` | 3.60 | 1.88 | **1.92** | −23% | ⚠️ At break-even |
| `EX I SHOPPING I FOKUSPRODUKTE` | 3.53 | 1.81 | **1.95** | −22% | ⚠️ At break-even |
| `EX I WW I PMAX … OVER-INDEX` | 3.50 | 1.45 | 2.42 | −3% | ✅ |
| `EX I SHOPPING I PUR … NEAR INDEX` | 4.00 | 1.28 | 3.13 | +25% | ✅ |
| `EX I EN I WW I TOF …` (Search TOF) | 5.19 | 1.00 | 5.19 | +108% | ✅ |

**Three of six exceed the 30% deviation tolerance, and the DSA campaign's effective target sits below the break-even floor** — the D12 FAIL condition ("Target ROAS < break-even ROAS") manifesting at campaign level. That campaign is instructed to buy volume the business loses money on.

Bid strategies themselves are sound: all 15 enabled campaigns use Smart Bidding with inline targets, none is on Maximize Conversions without a target, and brand campaigns run conservative settings (DE tROAS 100, USA 42.64, FRA/SKANDI on Target Impression Share). **The mechanism is right; the numbers fed into it are not.** The root cause is the conversion-goal misconfiguration — nominal targets do not mean what they say — which is why this routes to tracking before bidding.

### D14 — there are no agreed goals

business.md states it in bold, and it is the most important sentence in this audit:

> *"⚠️ **No client-set goals exist.** Notion contains no 2026 revenue target, no H2 plan, and Google is still not defined as a channel. The targets below are **provisional, derived from unit economics, and require Jonas's sign-off** → Gaps G3, G4, G5 (all Critical). **Do not treat them as agreed.**"*

Supporting evidence:

- **Google is absent from the client's own marketing strategy.** The Marketing Cheat Sheet v0.1 lists eight channels — Instagram, TikTok, Meta Ads, Email, Influencer, Wholesale, Word of Mouth, Website. Google is not among them. It appears only as **open question #1**: *"Is Google (Search/PMax) still an active acquisition channel, and what's its role?"*
- **v0.2 has sat in Draft since 2026-06-25**, unchanged. A change proposal from 2026-06-26 lists Google's role as **"Not ready."**
- **No 2025 actual revenue or 2026 target is documented anywhere** (Gap G3, Critical). Channel goals cannot be derived from nothing.
- **No agreed review cadence with the analyst.** The client runs a Monday team meeting internally, but no goal-review rhythm is documented between Martin and Jonas.
- **The documented operating model does not match reality.** business.md §13 states *"Martin analyses and proposes. Jonas Makki executes. No exceptions."* The account changelog pulled 2026-08-06 shows every budget and bid-target change in the last 30 days came from a third party — `exmachina.agency@gmail.com` — plus 266 unattributed changes via Editor.

**What saves this from being worse:** business.md explicitly acknowledges the growth-versus-efficiency trade-off rather than papering over it — *"NOT achievable simultaneously: 'grow spend' and 'restore non-brand efficiency.'"* That is the mark of an honest plan, and it is the reason D14 fails on approval rather than on internal contradiction.

---

## Critical issues

### 1. Thirteen audits have optimised toward unapproved numbers

Every target used across this session — break-even 1.9, non-brand target 2.5, PAR 1.2, the €32,500 monthly budget — traces back to figures the analyst derived, not figures the business agreed. They are well-derived and defensible. They are not signed off.

**Getting sign-off is the single highest-leverage action available**, because it converts a session's worth of provisional analysis into an agreed plan without changing a single campaign setting. Frame it, as business.md suggests, as answering open question #1 in the client's own marketing sheet: *"here is the answer to the question your strategy document has been carrying since June."*

### 2. The DSA campaign is instructed to lose money

Effective clean target **1.29 against a 1.9 break-even**. This is not a performance problem — the campaign actually returns clean ~5.9 — it is an instruction problem: the algorithm is told to accept far worse, and only rank limitations are preventing it from doing so. It is also the account's most efficient non-brand unit, so the misconfiguration is suppressing something that works.

**Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100, top finding: *"an enabled conversion value rule adds +€42.20 per conversion against €16.46 documented, and 14 of 15 campaigns override the clean account-default conversion goal."* That override is why nominal 2.50 becomes effective 1.29. **No re-run needed.**

### 3. The non-brand target's viability rests on an unverified number

PAR 76% means 24% headroom. Gap G1 — whether Google receives gross or net order values — moves break-even between 1.6 and 1.9, which moves the PAR between 64% (healthy) and 76% (thin). Resolving it requires reconciling tracked purchase value against Shopify revenue for the same period: a ratio near 1.19 means gross.

**This is a one-afternoon job that determines whether the account's central target is comfortable or marginal.**

---

## Recommendations

### Act now

1. **Get the targets signed off by Jonas.** Non-brand clean ROAS 2.5 (floor 1.9), account 6.0 (floor 4.0), brand IS 95–99%, monthly spend €30–35k. Present as the answer to open question #1 in the Marketing Cheat Sheet. → `/strategy-specialist --execute goals` once approved, to record the agreement
2. **Resolve Gap G1** — reconcile Google's tracked purchase value against Shopify revenue for the same window. Needs Shopify `read_orders`. Determines whether break-even is 1.6 or 1.9
3. **Clarify who holds budget authority.** The documented model says Jonas executes; the changelog says otherwise. Proposals routed to the wrong person do not land

### Sequenced

4. **Fix the conversion goal configuration before touching any campaign target.** 14 of 15 campaigns override the clean account default. Until that is repaired, nominal targets are uninterpretable and D13 cannot be fixed. → `/tracking-specialist`
5. **Then re-set the DSA target.** Effective 1.29 must clear 1.9 at minimum, 2.5 to match the documented goal. Blocked until step 4. → `/bidding-optimizer adjust-targets`
6. **Close Gap G2** — repeat purchase rate and CLV are unavailable, yet the account pays a +€16.46 new-customer bonus. Either validate it or remove it. Needs Shopify `read_orders`. **Review the existing 2026-08-06 PMax audit** at `context/analysis/pmax/pmax-audit.md` — its `nca-lifecycle` module skipped the value-premium check for exactly this reason and routed it here. **No re-run needed**
7. **Close Gap G8** — replace the assumed 2% payment fee and €6 shipping with actuals. Both feed break-even directly

### Do not

8. **Do not revise the targets downward to match current performance.** Two-thirds of spend sitting below break-even is an execution failure, not evidence that 2.5 is unrealistic. business.md's feasibility check found 2.5 achievable from today's 2.14 through target calibration alone, requiring no budget increase
9. **Do not pursue growth and efficiency simultaneously.** business.md is explicit that they are incompatible here, and the evidence backs it: 0 of 6 budget increases above +90% were positive

---

## Peer report integration

All twelve peer reports are from 2026-08-06 — one day old, fresh within every window. None is re-run.

| Peer | Score | How it informs this audit |
|---|---|---|
| `/bidding-auditor` | 54/100 | **Explains D13.** The conversion-goal override is why nominal targets deflate below break-even. Its measurement block is the reason target fixes are sequenced behind tracking |
| `/budget-auditor` | 47/100 | Top finding: *projected August spend €78–93k against a €32,500 target.* Directly contradicts the documented spend guardrail — a live breach of a D11 guardrail this audit rated PASS |
| `/lp-auditor` | 56% | Establishes that non-brand underperformance is a destination problem, which supports recommendation 8 — do not lower targets to match a fixable execution gap |
| `/offer-auditor` | 97% | Confirms the value proposition supports the pricing that produces the 75% margin behind D01 |
| `/keyword-auditor` | 85% | Independently found core-term spend below break-even, consistent with the D13 misalignment |
| `/search-term-auditor` | 79% | Confirmed the competitor-term guardrail with data, validating business.md's evidence-based rule-making that D11 rewards |
| `/pmax-auditor` | — | Routed the NCA value-premium question here (Gap G2, recommendation 6) |
| `/account-auditor` | 75% | AUD-D24 located the goal-override mechanism behind D13 |
| `/competitive-analyst` | 73/100 | No competitive pressure — supports the view that targets are achievable |
| `/geo-schedule-auditor` | 75% | No contradiction |
| `/placement-auditor` | 48% | No contradiction |
| `/tracking-specialist` | — | **Missing.** The one peer that would validate every economics input. Its absence is why the measurement risk stays open across all thirteen audits |

**One peer contradicts a PASS in this audit, and it should be said plainly.** D11 rates the guardrails as excellent, including the €30–35k monthly spend ceiling. The 2026-08-06 budget audit projects **€78–93k for August** — the guardrail is well-designed and currently being breached by a factor of about 2.5. The guardrail passes as a *definition*; it is failing as a *control*.

---

## Data freshness

| Source | Date | Status |
|---|---|---|
| `context/business.md` | 2026-08-03 | 4 days — fresh. Rebuilt from scratch that day |
| `context/google-ads/data/campaigns.csv` | 2026-08-06 | 1 day — fresh |
| `context/account-changelog.md` | 2026-08-06 | 1 day — fresh |
| All 12 peer audit reports | 2026-08-06 | 1 day — fresh |

**Timing note:** the learning windows on FOKUSPRODUKTE and Search TOF, which the 2026-08-06 bidding and budget audits recorded as clearing on 2026-08-07, **have now cleared**. Both campaigns are available for change as of today — subject to the tracking fix in recommendation 4 landing first.
