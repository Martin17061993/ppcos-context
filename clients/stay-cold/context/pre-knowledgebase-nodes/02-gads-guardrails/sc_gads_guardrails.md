# Stay Cold Google Ads — operating guardrails (derived from 2024–2026 evidence)

Scope note: all thresholds were measured on this one account (Stay Cold,
Google Ads customer 359-911-6618). They are Stay-Cold-specific operating
rules, not generic e-commerce truths.

## Do (positive rules)

### Guardrail DO-1: use scarcity as the efficiency lever

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
When a campaign underperforms its target on this account, the proven first
move is scarcity: cut budget 20–40 % and/or raise the tROAS target, then
leave the campaign alone for 14 days. Mechanism: with loose budgets/targets,
smart bidding buys unprofitable marginal auctions; scarcity forces it to drop
the weakest first. Evidence: every high-confidence win of 2024–2026 was a
scarcity or correction package (2024-07-16 +45 %, 2024-10-04 +126 %,
2024-10-09 +246 %, 2025-04-15 +86 % vs. account trend). Apply selectively per
campaign — two blanket cuts inside the Oct 2024 program measured negative on
other campaigns (−27 %, −38 %).

### Guardrail DO-2: raise budget only against a real budget limit, and only in steps

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Before any budget increase, check budget-lost impression share
(Search/Shopping): it must be at least ~20 %. For PMax, where lost-IS is not
available, use the marginal clean ROAS of the last budget step as proxy — it
must stay above 0.8× the campaign average, else no increase. A real limit is
necessary but NOT sufficient: step size stays capped (see DON'T-1). Evidence:
Fokusprodukte scaled acceptably in steps at 52–67 % budget-lost IS (Feb–Apr
2026), yet a single +77 % step at 56 % lost-IS still measured −17 %
(2025-04-05); with lost-IS ≈ 0 the June 2026 push produced marginal clean
ROAS 0.63.

### Guardrail DO-3: when saturation shows, cut immediately

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
If a budget increase produces marginal clean ROAS below the campaign's
break-even proxy, step back at once — every week of waiting buys revenue at
0.6 EUR per 1 EUR spent. Evidence: the 2026-06-30 budget cut on
"EX I SHOPPING I FOKUSPRODUKTE" (1,600 → 550 EUR/day, campaign at weekly
clean ROAS 0.77) was correct but came roughly four weeks after the June
saturation was measurable.

### Guardrail DO-4: maintain a promo calendar; inside promo windows, intraday scaling is a legitimate tactic

[Stay Cold · Google Ads · guardrail · as of 2026-07-10]
Stay Cold runs sales/promos as a core tactic, including deliberate intraday
scaling (fast, large budget and bid moves within a sale). Therefore a promo
calendar (promo_windows.csv: BFCM 2024, BFCM 2025, Black Spring Sale 2026;
to be verified and extended by the account operator) is mandatory
infrastructure. Inside a documented promo window the step-size and
rest-window rules are suspended; outside them they apply strictly. Promo
performance is evaluated as a package — promo versus the previous year's
promo on the purchase-only series — never as per-change verdicts. Evidence
that package evaluation works: BFCM 2025 measured +62 % purchase revenue vs.
BFCM 2024, measurement-clean. Roughly half of all budget steps of 2024–2026
(94 of 189 parsed steps) occurred inside promo windows — treating them as
individual mistakes was the main error of the first analysis version
(corrected after operator review 2026-07-10).

### Guardrail DO-5: evaluate every change trend-corrected on the purchase-only series

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Judge any change on this account by comparing 28 days after vs. 28 days
before, minus the account-wide change in the same window (DiD), computed on
purchase-only revenue (purchase_gads_mable). Otherwise the evaluation
measures season, the account trend, or the counting-regime inflation instead
of the change. Evidence: November/December 2025 looks like a steering success
on the account surface; the apparent lift is NewCustomerPurchase double
counting plus BFCM season.

### Guardrail DO-6: build brand impression share toward 95–99 % via bids and quality

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
The brand campaigns' visibility gap is rank-lost, not budget-lost (USA brand:
82.8 % impression share, 15.6 % rank-lost). Closing it via bid and ad-quality
work is the cheapest traffic in the account. Evidence: the 2026-03-13 USA
brand package measured +261 % vs. account trend. Do not expect the average
brand ROAS (24–64) on the increment — brand harvests existing demand; the
marginal return is lower but still the best available.

## Don't (hard limits)

### Guardrail DON'T-1: outside documented promo windows, never change budget more than ±30 % per step or twice within 7 days

[Stay Cold · Google Ads · guardrail · as of 2026-07-10]
Per campaign and only OUTSIDE documented promo windows (inside promos,
intraday scaling is a legitimate tactic — promo-calendar rule): budget steps
stay within ±30 %, with at least 7 days between changes. Mechanism: every
large jump resets smart-bidding learning. Evidence, computed excluding promo
windows: increases above +90 % per step were never positive (0 of 6; e.g.
+143 % → −23 % on 2025-04-04, +204 % → −18 % on 2025-10-11, +96 % → −27 % on
2026-05-29 — all outside promos), while moderate steps up to ~+44 % were
repeatedly positive in calm windows. Outside promo windows, 78 % of 95
parsed budget steps still exceeded ±30 % and 28 % of follow-up changes came
within 7 days — and the net effect of all non-promo budget work was ≈ 0.

### Guardrail DON'T-2: outside promo windows, never change tROAS targets twice within 14 days on the same campaign

[Stay Cold · Google Ads · guardrail · as of 2026-07-10]
This rule applies outside documented promo windows only — inside a promo,
target moves are part of legitimate intraday scaling. Target-ROAS is the
strongest bidding input; without a 14-day rest neither
learning nor measurement is possible. Evidence: the target thrash on
"EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX" (560 → 300 → 450 within
November 2024) was unmeasurable and destabilizing, while the account's only
two high-confidence target successes (2024-10-04, 2025-04-15) both had 14+
days of rest afterwards.

### Guardrail DON'T-3: never raise budget when budget-lost impression share is below 5 %

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Below ~5 % budget-lost impression share the campaign already wins every
auction it wants at its bid level; extra budget only raises the marginal
click price. Evidence: 2026-05-29 increase on the feed-only prospecting PMax
at ≈ 0 % lost-IS → −27 % vs. trend on ~17,400 EUR; June 2026 Fokusprodukte
increments at 0–1 % lost-IS → marginal clean ROAS 0.63.

### Guardrail DON'T-4: do not touch protected brand campaigns

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Campaigns with clean ROAS ≥ 1.25× account average AND ≥ 3 purchases (in
practice: all four brand search campaigns) are do-not-touch: no pausing, no
keyword removals, no broad match added, bids only upward. Mechanism: highest
value density in the account — small interventions, largest swings (−32 % to
+396 % measured from similar same-day actions). Evidence: 2024-11-21
auto-apply removal of [stay cold]; 2025-01-23 exclusion-list batch (FRA
−32 %); 2026-01-13 asset cleanup (USA −32 %).

### Guardrail DON'T-5: keep keyword/asset auto-apply off

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Google's auto-apply recommendations for keywords/assets are disabled on this
account and stay off. Evidence: in two years, all 8 auto-apply clusters
touched brand campaigns, hit rate ~38 % positive, worst case the removal of
exact keyword [stay cold] from the DE brand campaign two days before BFCM
week 2024. Bidding-related auto-apply was paused by the account operator on
2026-07-03.

### Guardrail DON'T-6: never let a campaign pass 1,000 EUR cumulative spend without a purchase

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Alert and review any campaign that crosses 1,000 EUR cumulative spend with
zero purchases; do not let it keep running unexamined. Evidence: "Video View
DRAFT" spent 4,750 EUR for 2 purchases over four unnoticed weeks
(2026-04-27 to 2026-05-24), presumably an unintended launch.

### Guardrail DON'T-7: never steer on the reported account ROAS

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Since 2025-11-10 the reported account ROAS measures purchase +
NewCustomerPurchase and is inflated ~1.49–1.57× vs. real purchase revenue.
All decisions use the purchase-only series or trend-corrected deltas.
Evidence: June 2026 reads 7.85 on the surface and 5.04 real; every
budget/target decision steered on the surface since December 2025 was based
on ~50 % phantom revenue.

### Guardrail DON'T-8: account-level changes are never evaluated or executed autonomously

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
Conversion-setup changes, new-customer-acquisition settings, access changes
and tracking-template rollouts move the whole account and cannot be isolated
against the account trend — an agent that forces a verdict or executes them
autonomously fabricates causality. In the 2024–2026 analysis, 45 such
clusters were deliberately marked "manual review" instead of receiving a
verdict. These decisions belong to humans.

### Guardrail DON'T-9: no same-day batch rollouts across all markets or campaigns

[Stay Cold · Google Ads · guardrail · as of 2026-07-03]
The same change acts differently per market: the 2025-01-23 exclusion-list
batch measured −32 % (FRA brand) alongside +30 %/+24 % on other brands; the
2026-01-13 asset cleanup measured −32 % (USA) alongside +396 % (SKANDI); the
2024-10-23 account-wide tracking rollout hit 7 of 11 campaigns negatively.
Roll changes out one market/campaign at a time, staggered by 1–2 weeks, so
effects stay attributable and errors stay contained.
