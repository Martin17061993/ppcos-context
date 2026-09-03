# Competitive Position Audit — 2026-08-06

**Score:** 73/100 (Good)
**Verdict:** **Selective competition** — with landing page experience as the shared lever
**Window:** 90 days, lag-offset 8 (2026-04-30 → 2026-07-28) | 7 active diagnostics, 6 permanently skipped
**Account:** 3599116618 (Stay Cold Apparel) · EUR · 8 campaigns with IS data · 701 campaign-days
**Run by:** /competitive-analyst at 2026-08-06

---

## Executive read

73 is the highest score of the four audits run on this account today, and that is the finding, not a consolation. **Competitively, Stay Cold is not under attack.** Over 90 days not a single campaign lost impression share — FOKUSPRODUKTE actually gained 11.7 points, brand impression share is stable at 84–96%, and no campaign shows the CPC-up-plus-share-down signature of a competitor pushing into the auction. The other three audits scored Critical because of self-inflicted configuration problems. This one says the market is not the reason.

What the audit does find is a **standing** weakness rather than a deteriorating one, and it has a single cause. The non-brand Search campaign loses 92.6% of available impressions and the DSA campaign loses 90.0% — almost entirely to rank, not budget. The Quality Score data explains why with unusual clarity: of the six non-brand keywords carrying a Quality Score, **all six show landing page experience as BELOW AVERAGE.** Ad relevance is ABOVE AVERAGE on five of six and expected CTR is ABOVE AVERAGE or AVERAGE on all six. The ads are good. The keywords are relevant. The landing pages are what is capping the score at 4–7 and keeping the campaigns off the page. For contrast, every brand keyword scores a perfect 10 with all three components ABOVE AVERAGE.

Two priorities follow. **First, fix the landing page experience** — it is the only lever that gains impression share without spending more, and it constrains every non-brand keyword at once. business.md already predicted this: it lists the "PDP truth gap" as an open risk and names it, verbatim, an "LP-experience/Quality-Score driver." This audit is the API confirmation. **Second, do not raise bids on FOKUSPRODUKTE to chase its 31.1% rank loss** — at a clean return of 1.72 against a 1.9 break-even it cannot afford more traffic, and its CPC has already risen 47% while its share rose, meaning it is buying deeper into the auction on its own initiative.

Not a problem: brand position is healthy and stable; FRA and SKANDI brand CPCs actually fell 37% and 16%. And no competitor entry is detectable anywhere in the data.

Read the diagnosis, then the economics table. Everything else is reference.

---

## Score summary

| Module | Score | Grade | Key finding |
|---|---|---|---|
| IS Health & Trends | 15/30 | **50% — Needs attention** | No campaign is declining (D01 PASS), but four carry severe standing IS loss (D02 FAIL) |
| Competitive Position | 23/35 | **66% — Needs attention** | Top-of-page stable and Shopping ad groups healthy, but every non-brand keyword is under heavy rank pressure (D08 FAIL) |
| Competitive Impact | 35/35 | **100% — Excellent** | No CPC-competition signature, no attributable competitive KPI loss |
| **Total** | **73/100** | **Good** | Position is stable; the weakness is standing and self-correctable |

**Baseline run — no prior score to compare against.**

---

## Diagnosis

**Verdict: Selective competition.** Three campaigns can profitably fight for more visibility and one cannot, and the winning move in all three cases is the same and it is not bidding.

The competitive picture is stable — that is the first thing to internalise. Across 90 days every campaign held or improved its impression share, brand sits between 84% and 96%, and the one campaign whose cost-per-click rose sharply (FOKUSPRODUKTE, +47%) simultaneously *gained* 11.7 points of share, which is the signature of an advertiser buying deeper into an auction rather than being pushed out of one. There is no competitor-entry event in this data. That reframes the CPC findings the bidding audit raised the same day: the 2026-08-06 bidding audit (54/100) flagged FOKUSPRODUKTE for a +30% CPC spike and a three-period rising trend, and the budget audit (47/100) traced a +109% single-day budget increase on the same campaign. Read together, the rising CPC is **self-inflicted, not competitive** — the account raised its own budget and bid deeper. That is a materially different conclusion than "competitors got more expensive," and it changes the response from defensive to corrective.

What is genuinely weak is the *standing* non-brand position, and the Quality Score data pins the cause precisely. Search TOF loses 64.2% of impressions to rank and DSA loses 90.0%, with budget contributing 28.4% and 0% respectively. Of the six non-brand keywords with a Quality Score reading, **six of six show `post_click_quality_score = BELOW_AVERAGE`** — landing page experience — while ad relevance is ABOVE AVERAGE on five of six and expected CTR is ABOVE AVERAGE or AVERAGE on all six. Scores land at 4, 5, 5, 7, 7, 7, capped by the one weak component. Brand keywords, pointed at different pages, score a clean 10 with all three components ABOVE AVERAGE. The rank problem is therefore **landing-page-driven, not bid-driven**, which means it can be fixed without spending an additional euro — and conversely that raising bids would buy traffic at a worse price while leaving the underlying rank deficit intact.

The economics then sort the campaigns. Deflated to the clean series, Search TOF runs at 4.31 and DSA at 5.51 against a 1.9 break-even — both have wide headroom and both deserve the investment. FOKUSPRODUKTE runs at 2.06 across 90 days but has fallen to **1.72 in the most recent 30 days, below break-even** — it must not be given more traffic at any price until that reverses. USA brand carries a 15.8% rank gap, but its keywords score a perfect 10, so that gap really *is* bid-driven, and it is the one place where a bid increase is both justified and permitted by the account's own brand guardrail ("bids upward only"). Hence: selective. Compete on Search TOF, DSA and USA brand. Hold FOKUSPRODUKTE.

---

## Business economics context

Deflated using the per-campaign inflation factors verified 2026-08-03 (business.md §6). Break-even is clean ROAS **1.9**; target under the growth posture (PAR 1.2) is **2.28**.

| Campaign | 90d cost | Reported ROAS | Factor | **Clean ROAS** | vs BE 1.9 | Headroom | **Can afford more IS?** |
|---|---|---|---|---|---|---|---|
| `EX \| FRA \| SEARCH \| BRAND` | €1,400 | 113.88 | — | ~114 | ✅ | vast | Protected — already 96% IS |
| `EX \| USA \| SEARCH \| BRAND` | €2,329 | 98.42 | 1.53 | **64.3** | ✅ | vast | **Yes — and rank gap is bid-driven (QS 10)** |
| `EX \| DE \| SEARCH \| BRAND` | €4,992 | 90.01 | 1.42 | **63.4** | ✅ | vast | Protected — already 94% IS |
| `EX \| SKANDI \| SEARCH \| BRAND` | €2,006 | 40.67 | — | ~41 | ✅ | vast | Protected — CPC cap €2.50 may bind |
| `EX I SHOPPING I PUR … NEAR INDEX` | €132 | 7.90 | 1.28 | **6.17** | ✅ | wide | Volume too small to matter — consolidate |
| `JM I DSA I FC'S I CAT'S` | €1,093 | 10.63 | 1.93 | **5.51** | ✅ | wide | **Yes — best efficiency-to-volume gap in the account** |
| `EX I EN I WW I TOF …` (Search TOF) | €10,273 | 4.31 | 1.00 | **4.31** | ✅ | wide | **Yes — the primary competitive opportunity** |
| `EX I SHOPPING I FOKUSPRODUKTE` | €66,107 | 3.72 | 1.81 | **2.06** (90d) → **1.72** (30d) | ⚠️ → ❌ | none | **No — below break-even and falling** |

⚠️ **FOKUSPRODUKTE is the whole story in one row.** It is 74% of the 90-day cost in this table, it was marginally profitable over the window and is now below break-even, and it is the campaign whose budget was doubled on 2026-07-24. Its 31.1% rank-lost impression share is real but must not be pursued.

### Keyword-level economics — the non-brand set

Ranked by 90-day spend. All sit in one ad group (`STAN I BROAD I HOME`).

| Keyword | Match | Spend | Conv | **QS** | Ad relevance | **LP experience** | Expected CTR | IS | Rank-lost |
|---|---|---|---|---|---|---|---|---|---|
| `t shirt metal` | BROAD | €1,871 | 20.1 | **5** | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | AVERAGE | <10% | 67.5% |
| `punk hoodie` | BROAD | €1,164 | 23.3 | **4** | AVERAGE | ❌ **BELOW_AVERAGE** | AVERAGE | <10% | 65.9% |
| `rocker hoodies` | BROAD | €950 | 17.6 | — | — | — | — | <10% | 52.4% |
| `goth and punk clothing` | PHRASE | €897 | 6.5 | — | — | — | — | <10% | 66.3% |
| `goth rock clothes` | PHRASE | €688 | 5.5 | **5** | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | AVERAGE | <10% | 65.0% |
| `tattoo clothing` | PHRASE | €248 | 5.1 | **7** | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | ABOVE_AVERAGE | 11.6% | 63.0% |
| `tattoo streetwear` | PHRASE | €209 | 5.8 | — | — | — | — | <10% | 67.8% |
| `cute goth clothes` | PHRASE | €124 | 0.0 | — | — | — | — | <10% | 67.8% |
| `punk clothing` | EXACT | €123 | 0.0 | **7** | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | ABOVE_AVERAGE | <10% | 70.3% |
| `tattoo shirts` | EXACT | €61 | 0.0 | 7 | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | ABOVE_AVERAGE | — | — |
| `punk rock shirts` | EXACT | €21 | 0.0 | 5 | ABOVE_AVERAGE | ❌ **BELOW_AVERAGE** | AVERAGE | — | — |

**Six of six keywords with a Quality Score show BELOW_AVERAGE landing page experience. Zero exceptions.** Five of six show ABOVE_AVERAGE ad relevance. The pattern is unambiguous.

**Brand keywords, for contrast:** `stay cold apparel`, `stay cold`, `stay cold clothing`, `stay cold shirt`, `staycold` — all **QS 10**, all three components ABOVE_AVERAGE. The difference is the destination page, not the account's advertising craft.

*Note: keywords showing "—" for QS have too few impressions for Google to report one. `IS <10%` is Google's reporting floor, not a precise value.*

---

## Evidence ladder

### Layer 1 — Data validation

| Check | Result |
|---|---|
| DV1 — campaign maturity | All 8 campaigns have ≥71 days of data; 7 have the full 90. No maturity caveat. |
| DV2 — bidding strategy context | Every campaign runs Target ROAS, Maximize Conversion Value or Target Impression Share. **Under value-based bidding, low IS on low-margin queries is partly intentional** — the algorithm declines auctions it judges unprofitable. This tempers, but does not explain away, a 90% rank loss. |
| DV3 — conversion sufficiency | Non-brand keyword conversions range 0–23 per keyword over 90 days. Below the 10-conversion reliability bar on 6 of 11 keywords — per-keyword efficiency figures are indicative only. Campaign-level figures are sound. |

### Layer 2 — Business economics

| Check | Result |
|---|---|
| BE1 — efficiency headroom | Search TOF (4.31), DSA (5.51) and USA brand (64.3) all clear break-even 1.9 with room. **FOKUSPRODUKTE at 1.72 over the recent 30 days does not.** |
| BE2 — implied efficiency floor | Not structurally unviable. Even at the wide end of rank recovery, Search TOF and DSA would remain above break-even at current auction prices. This is not a market the account cannot afford to be in. |
| BE3 — budget headroom | Cross-referenced with the fresh budget audit: Search TOF carries 28.4% budget-lost IS over 90 days — genuinely budget-constrained. DSA carries **0%** — funding it would change nothing. |
| BE4 — IS recovery ROI | The cheapest recovery path costs nothing in media: raising landing page experience from BELOW_AVERAGE to AVERAGE lifts Quality Score, which lifts ad rank, which recovers impression share at the *same* bid. This is why LP outranks bids in the action list. |

### Layer 3 — QS & rank diagnosis

**This is the decisive layer.** Read from live Quality Score data, not a proxy.

| Campaign | Rank-lost IS | QS range | Weak component | **Diagnosis** |
|---|---|---|---|---|
| Search TOF | 64.2% | 4–7 | `post_click_quality_score` BELOW_AVERAGE on 6/6 | **QS-driven — landing page.** Not bids. |
| DSA | 90.0% | n/a (dynamic) | — | Presumed same cause; DSA has no keywords, so relevance and LP are inferred from the same site. |
| FOKUSPRODUKTE | 31.1% | n/a (Shopping) | — | Shopping has no QS. Rank driven by feed quality and bid. **Irrelevant — the campaign cannot afford more traffic.** |
| NEAR INDEX | 56.5% | n/a (Shopping) | — | €132 over 90 days. Too small to act on. |
| **USA brand** | 15.8% | **10** | none — all ABOVE_AVERAGE | **Bid-driven.** QS is perfect; the gap is purely ad rank from bidding. The one place a bid increase is the correct instrument. |
| DE brand | 6.0% | 10 | none | Near-saturation. Nothing to fix. |
| SKANDI brand | 8.5% | 10 | none | Bid-driven; the €2.50 CPC ceiling is a candidate constraint (see bidding audit BID-D15). |

**Peer cross-check.** No `/quality-score-auditor` report exists, so this diagnosis is built from the raw `keywords.csv` pull rather than a peer report — which for this specific question is the better source, since it carries the three component scores directly. The fresh **bidding audit (2026-08-06, 54/100)** independently measured 58.7% rank-lost on Search TOF and 90.0% on DSA over its 30-day window; this audit's 90-day figures of 64.2% and 90.0% confirm the pattern is persistent rather than a recent shift.

### Layer 4 — Strategic assessment

| Check | Result |
|---|---|
| SA1 — campaign prioritisation by IS recovery ROI | 1. **Search TOF** — largest addressable loss (92.6%) on a campaign at 4.31 clean. 2. **DSA** — highest efficiency (5.51) and the widest rank gap (90%), but small absolute volume. 3. **USA brand** — smallest gap (15.8%) but cheapest traffic in the account and a measured +261% precedent. 4. **FOKUSPRODUKTE** — excluded on economics. |
| SA2 — branded competitive entry response | **No branded CPC pressure detected.** FRA brand CPC fell 37%, SKANDI fell 16%, DE was flat, USA rose 10% while its IS also rose. No defensive action needed. |
| SA3 — market position verdict | **Selective competition.** Three campaigns viable, one excluded on economics, brand healthy and stable. |

---

## IS trend dashboard (90 days, first third vs last third)

| Campaign | Days | IS start | IS end | Δ | Top-IS start | Top-IS end | CPC start | CPC end | CPC Δ |
|---|---|---|---|---|---|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | 90 | 42.5% | **54.1%** | **+11.7** | — | — | €0.85 | €1.25 | **+47%** |
| `EX \| FRA \| SEARCH \| BRAND` | 90 | 94.4% | 96.0% | +1.5 | 92.5% | 93.9% | €0.17 | €0.11 | **−37%** |
| `EX \| USA \| SEARCH \| BRAND` | 90 | 83.3% | 84.3% | +1.0 | 78.4% | 78.4% | €0.20 | €0.22 | +10% |
| `EX I SHOPPING I PUR … NEAR INDEX` | 71 | 41.5% | 45.7% | +4.2 | — | — | €4.61 | €3.22 | −30% |
| `EX I EN I WW I TOF …` (Search TOF) | 90 | 10.0% | 10.3% | +0.3 | 10.0% | 10.0% | €0.98 | €1.20 | **+23%** |
| `JM I DSA I FC'S I CAT'S` | 90 | 10.0% | 10.0% | +0.1 | 10.0% | 10.0% | €0.97 | €0.91 | −6% |
| `EX \| DE \| SEARCH \| BRAND` | 90 | 94.0% | 94.1% | +0.1 | 89.8% | 89.9% | €0.19 | €0.19 | 0% |
| `EX \| SKANDI \| SEARCH \| BRAND` | 90 | 92.2% | 91.9% | −0.3 | 86.9% | 87.4% | €0.45 | €0.38 | −16% |

**Nothing is declining.** The single −0.3pp movement (SKANDI) is noise. Search TOF and DSA sit pinned at Google's `<10%` reporting floor — persistently low, but not falling.

---

## IS loss decomposition (CA-D02)

| Campaign | Combined loss | Budget-lost | Rank-lost | Dominant | Can afford more IS? |
|---|---|---|---|---|---|
| `EX I EN I WW I TOF …` | **92.6%** | 28.4% | **64.2%** | RANK | ✅ Yes — clean 4.31 |
| `JM I DSA I FC'S I CAT'S` | **90.0%** | 0.0% | **90.0%** | RANK | ✅ Yes — clean 5.51 |
| `EX I SHOPPING I PUR … NEAR INDEX` | 56.5% | 0.0% | 56.5% | RANK | ⚠️ Yes on efficiency, but €132/90d — immaterial |
| `EX I SHOPPING I FOKUSPRODUKTE` | 50.9% | 19.8% | 31.1% | RANK | ❌ **No — clean 1.72, below break-even** |
| `EX \| USA \| SEARCH \| BRAND` | 15.8% | 0.0% | 15.8% | RANK | ✅ Yes — and QS is 10, so bids are the right lever |
| `EX \| SKANDI \| SEARCH \| BRAND` | 8.5% | 0.0% | 8.5% | RANK | ✅ Protected; CPC ceiling may bind |
| `EX \| DE \| SEARCH \| BRAND` | 6.0% | 0.0% | 6.0% | RANK | ✅ Near-saturated |

Rank dominates budget on **every single campaign**. Only two campaigns lose any share to budget at all.

---

## Top-of-page position analysis (CA-D05) — PASS

| Campaign | Top-IS start → end | Abs-top trend | Verdict |
|---|---|---|---|
| FRA brand | 92.5% → 93.9% | improving | Healthy |
| DE brand | 89.8% → 89.9% | flat | Healthy |
| SKANDI brand | 86.9% → 87.4% | improving | Healthy |
| USA brand | 78.4% → 78.4% | flat | Stable, with room |
| Search TOF | 10.0% → 10.0% | at reporting floor | Persistently low, not declining |
| DSA | 10.0% → 10.0% | at reporting floor | Persistently low, not declining |

No declining trend anywhere. The two non-brand campaigns sit at the `<10%` floor — a level problem, which CA-D02 and CA-D08 own, not a trend problem.

---

## Shopping ad group breakdown (CA-D09) — PASS

Ran because FOKUSPRODUKTE carries 3 ad groups (`Sommer Fokus`, `SHIRTS + FOKUSMÄRKTE`, `Hoodies Push`). 151 ad-group-days analysed across both Shopping campaigns. **No isolated or severe ad-group-level IS decline detected** — the campaign-level picture is not masking a single failing product group.

---

## CPC–competition correlation (CA-D11) — PASS

Zero campaigns show the competitive-pressure signature (CPC rising *while* IS falls).

The two notable CPC movements both run the other way:

- **FOKUSPRODUKTE: CPC +47% with IS +11.7pp.** Rising cost bought rising share. That is an advertiser bidding deeper, not a competitor bidding harder. Corroborated by the 2026-08-06 budget audit, which found the budget was raised **€550 → €1,150/day (+109%) on 2026-07-24**.
- **Search TOF: CPC +23% with IS flat.** Coincides with the bid target being raised 3.5 → 5.19 on 2026-07-24. Self-inflicted rather than auction-driven.

**This reframes a finding from the other audits.** The bidding audit flagged rising CPC on both campaigns as a risk (BID-D22/D23). It is real and it matters for profitability — but it is **not evidence of competitive pressure**. Treating it as competitor entry would point at the wrong response.

---

## KPI impact estimate (CA-D13) — PASS

No campaign lost impression share over 90 days, so there is **no attributable KPI loss from competitive erosion**. Nothing has been taken from this account.

That is different from saying there is no opportunity. The standing 92.6% and 90.0% losses on Search TOF and DSA are real unclaimed volume — but they are unclaimed because of an internal quality constraint, not because a competitor won them. The recovery path is the landing page, and its cost is development time rather than media spend, which is why it does not appear as a media-cost trade-off here.

---

## Skipped diagnostics

CA-D03, CA-D04, CA-D06, CA-D07, CA-D10, CA-D12 are **permanently skipped** in this track — all six require Auction Insights, which the Google Ads API does not expose. Their points are excluded from the denominator.

Consequence: this audit can see *that* rank is lost and *why* on the account's own side (Quality Score), but it cannot name which competitors are winning those auctions or how their impression share is trending. To close that gap, Auction Insights must be read manually in the Google Ads UI (Campaigns → the campaign → Insights → Auction insights).

---

## Competitor ad copy insights

**Not available.** `context/competitor-ads/` does not exist and `config → competitors.domains` is deliberately empty — business.md records that the competitor brands are documented (Killstar, DropDead, Disturbia, Sullen, Named Collective, Blackcraft Cult, Bad Monday) but their exact domains are unverified, and guessing them would make `/competitor-scraper` fetch the wrong advertisers.

Resolving those seven domains would unlock competitor ad-copy analysis. Given this audit found **no** competitive pressure, it is a low priority right now.

---

## Actions — segmented by cascade state

### 🔍 Investigate first

- **Landing page experience is BELOW_AVERAGE on 6 of 6 scored non-brand keywords.** This is the binding constraint on the account's entire non-brand programme and the only lever that recovers impression share without additional spend. No LP audit exists → **run `/lp-auditor`**, focused on the pages behind `STAN I BROAD I HOME`.
  *business.md §15 already names this: the "PDP truth gap" is listed as an open risk and described verbatim as a "Returns driver and LP-experience/Quality-Score driver." This audit is the API confirmation of a risk the business had already written down.*
- **Quality Score has never been audited on this account** → **run `/quality-score-auditor`** to get the full distribution, per-campaign trends and the component breakdown across all keywords rather than the 6 with readings here.

### 🔧 Fix economics first

- **FOKUSPRODUKTE — do not pursue its 31.1% rank-lost share.** Clean ROAS 1.72 over the last 30 days against a 1.9 break-even. It is the account's largest spender and its budget was doubled nine days before this window closed. **Review the existing 2026-08-06 budget audit at `context/analysis/budget/budget-audit.md`** — top finding: projected August spend of €78–93k against a €32,500 target, with FOKUSPRODUKTE named as a reduce candidate, not a hold. Re-run only if you want fresher data.
- **Resolve the conversion-value inflation before acting on any efficiency number here.** Every clean figure in this report is a manual deflation, not a measured value. **Review the existing 2026-08-06 bidding audit at `context/analysis/bidding/bidding-audit.md`** — top finding: an enabled conversion value rule adds +€42.20 per conversion against €16.46 documented, and 14 of 15 campaigns override the clean account-default goal. Blocking for all target work.

### ✅ Compete where viable

- **Search TOF — the primary opportunity.** 92.6% combined IS loss, clean 4.31, wide headroom. Split the recovery: 64.2% is rank (→ landing page, see above) and 28.4% is budget (→ **review the existing budget audit**, which projects +43.9 conversions from budget recovery but gates it on exactly this rank/budget split). Do not fund it before the LP work — most of the missing share is not buyable.
- **DSA — best efficiency-to-volume gap in the account.** Clean 5.51, 90.0% rank-lost, **0% budget-lost**. Budget will do nothing here. Dynamic ad relevance and landing page quality are the levers. Its bid target is also mis-calibrated (effective clean target 1.29, below break-even) — but that fix is blocked until the conversion goals are repaired.
- **USA brand — the one place a bid increase is the right instrument.** 15.8% rank-lost, QS 10 with all three components ABOVE_AVERAGE, 0% budget-lost. The gap is purely bid-driven, business.md targets 95–99% brand IS, and the brand guardrail explicitly permits "bids upward only." Measured precedent: +261% (2026-03-13). **Proposal for Jonas** — Martin has no execution mandate.

### 💬 Strategic discussion

- **Auction Insights is the visible gap in this analysis.** Six of thirteen diagnostics are permanently unavailable via API. If competitor-level visibility matters for Q4 planning, someone needs to read Auction Insights manually and the seven competitor domains need verifying to enable `/competitor-scraper`.
- **SKANDI brand's €2.50 CPC ceiling** sits under a Target Impression Share strategy at 91.9% actual against a 95–99% goal. Raising the ceiling is guardrail-compliant, but SKANDI is also the market with the weakest brand efficiency and an all-broad match-type problem (account audit AUD-D06). Sequence the match-type fix first.

### 👁 Monitor

- **Brand position across all four markets is healthy and needs nothing.** 84–96% IS, QS 10 everywhere, CPCs flat or falling. FRA −37% and SKANDI −16% CPC are genuine efficiency gains.
- **No competitor entry anywhere in 90 days.** Re-check after any Q4 competitive shift — BFCM is the account's biggest event and the auction will look different in November.
- **Shopping ad groups are internally healthy** — no single product group is dragging FOKUSPRODUKTE's campaign-level numbers.

---

## Peer report integration (Phase 2.5)

| Peer | Report | Status | Used how |
|---|---|---|---|
| `/bidding-auditor` | `context/analysis/bidding/bidding-audit.md` | **FRESH — 2026-08-06**, 54/100 | Supplied the inflation factors for every clean-ROAS figure here. Its 30-day rank-lost measurements (58.7% Search TOF, 90.0% DSA) corroborate this audit's 90-day figures. Its CPC-rise findings are **reframed** by this audit as self-inflicted rather than competitive. |
| `/budget-auditor` | `context/analysis/budget/budget-audit.md` | **FRESH — 2026-08-06**, 47/100 | Explains the FOKUSPRODUKTE CPC/IS rise (+109% budget on 2026-07-24) and supplies the reduce-not-raise verdict this audit adopts. Gates the Search TOF budget half of the opportunity. |
| `/account-auditor` | `context/analysis/account/account-audit.md` | **FRESH — 2026-08-06**, 75% | Its AUD-D20 flagged the single loose non-brand ad group whose keywords are the entire CA-D08 flag set. Its AUD-D06 brand match-type finding sequences ahead of the SKANDI CPC-cap discussion. |
| `/quality-score-auditor` | — | Missing | **Top handoff.** This audit read raw QS from `keywords.csv` — better for the component question, but it covers only the 6 keywords with readings. |
| `/lp-auditor` | — | Missing | **Top handoff.** The single highest-leverage action in this report. |
| `/offer-auditor`, `/search-term-auditor`, `/keyword-auditor`, `/tracking-specialist`, `/strategy-specialist` | — | Missing | Standard handoffs |

**Where this audit contradicts a peer — stated explicitly.** The bidding audit treated rising CPC on FOKUSPRODUKTE and PROSPECTING as a competitive-pressure signal worth routing to `/competitive-analyst`. Having run it: **there is no competitive pressure.** FOKUSPRODUKTE's CPC rose 47% while its impression share rose 11.7 points, which is the opposite of the competitor-entry signature. The cost increase is real and it does damage profitability, but the cause is the account's own budget and bid changes of 17–24 July. Responding to it as a competitive event would be wrong.

**Skills referenced that do not exist yet:** `/ad-copy-specialist`, `/product-optimizer`, `/performance-reviewer` are named in this skill's handoff matrix but are not built. None is needed here — ad relevance is already ABOVE_AVERAGE, so there is no ad-copy work to route, and no Shopping ad group is failing.

---

## Configuration snapshot

- **Primary KPI:** roas | **Break-even:** clean ROAS 1.9 (Gap G1 open — 1.6 if net values)
- **Conversion lag:** 8 days | **Window:** 90 days, 2026-04-30 → 2026-07-28
- **Config block:** `competitiveAnalyst` written 2026-08-06 with values **inherited** from `biddingAudit` and `searchTermAnalysis` — no new assumptions introduced, no interview run (auto-mode)

### Data freshness

| Source | Rows | Status |
|---|---|---|
| `competitive/campaign-is-timeseries.csv` | 701 | Pulled fresh 2026-08-06 |
| `competitive/keyword-is.csv` | 35 | Pulled fresh 2026-08-06 |
| `competitive/shopping-adgroup-is-timeseries.csv` | 151 | Pulled fresh 2026-08-06 |
| `keywords.csv` (Quality Score) | 36 | Pulled fresh 2026-08-06, 90-day window |
| `competitive/evidence/competitive-flags.csv` | 31 flags | Generated 2026-08-06 |

⚠️ **Window note.** This 90-day window (2026-04-30 → 2026-07-28) ends before the August spend ramp the budget audit identified. Competitive conditions during the current high-spend period are **not** covered here. Re-run after the ramp resolves.

**Tooling note:** `competitive-analyst/scripts/` had no installed dependencies — `csv-parse` was installed during this run to make the analysis engine executable.
