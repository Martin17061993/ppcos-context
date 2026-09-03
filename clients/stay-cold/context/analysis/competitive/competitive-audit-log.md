# Competitive Audit Log

## 2026-08-06 — Score: 73/100 (Good)

- Period: 90d (lag 8, 2026-04-30 → 2026-07-28) | Campaigns with IS data: 8 | 701 campaign-days, 35 keyword rows, 151 Shopping ad-group days | 31 flags
- **Verdict: Selective competition** — with landing page experience as the shared lever
- **Top finding: the rank loss is landing-page-driven, not bid-driven.** Of the 6 non-brand keywords carrying a Quality Score, **6 of 6 show `post_click_quality_score = BELOW_AVERAGE`**, while ad relevance is ABOVE_AVERAGE on 5 of 6 and expected CTR is ABOVE_AVERAGE/AVERAGE on all 6. QS lands at 4–7, capped by the LP component. Brand keywords score 10 with all three components ABOVE_AVERAGE. This is the only lever that recovers impression share without additional spend
- **Second finding — a reframe of the other audits: there is no competitive pressure.** Zero campaigns declined over 90 days; FOKUSPRODUKTE *gained* 11.7pp of IS while its CPC rose 47%. That is an advertiser bidding deeper, not a competitor bidding harder. The bidding audit's CPC-rise finding is real for profitability but is **not** a competitive event
- Verdicts: D01 PASS 15/15 · **D02 FAIL 0/15** · D05 PASS 15/15 · **D08 FAIL 0/12** · D09 PASS 8/8 · D11 PASS 15/15 · D13 PASS 20/20 → 73/100
- Standing IS loss (not deteriorating): Search TOF 92.6% (budget 28.4 / rank 64.2), DSA 90.0% (rank 90.0, budget 0), NEAR INDEX 56.5%, FOKUSPRODUKTE 50.9% (budget 19.8 / rank 31.1). **Rank dominates budget on every campaign**
- Economics gate: Search TOF clean 4.31 ✅, DSA clean 5.51 ✅, USA brand clean 64.3 ✅ → compete. FOKUSPRODUKTE clean 2.06 over 90d but **1.72 over the recent 30d, below break-even** → excluded, reduce candidate
- USA brand is the one place a bid increase is correct: 15.8% rank-lost with QS 10 on all components → genuinely bid-driven, and "bids upward only" is guardrail-permitted. Precedent +261%
- Fresh peer reports integrated: `/bidding-auditor` 2026-08-06 (54/100) — inflation factors + corroborating rank-lost figures; `/budget-auditor` 2026-08-06 (47/100) — explains the FOKUSPRODUKTE CPC/IS rise via the +109% budget raise, supplies reduce-not-raise; `/account-auditor` 2026-08-06 (75%) — AUD-D20 loose ad group is the entire CA-D08 flag set
- Routing: `/lp-auditor` (**top**, hard evidence) → `/quality-score-auditor` → review existing budget + bidding reports (no re-run) → USA brand bid proposal for Jonas
- 6 of 13 diagnostics permanently SKIP (Auction Insights not API-exposed) — competitor-level visibility requires manual UI review; the 7 competitor domains remain unverified so `/competitor-scraper` cannot run

| Module | Score | Key finding |
|---|---|---|
| IS Health & Trends | 15/30 (50%) | No campaign declining (D01 PASS) but four carry severe standing IS loss (D02 FAIL) |
| Competitive Position | 23/35 (66%) | Top-of-page stable, Shopping ad groups healthy, but every non-brand keyword under heavy rank pressure (D08 FAIL) |
| Competitive Impact | 35/35 (100%) | No CPC-competition signature, no attributable competitive KPI loss |

**Window caveat:** this 90-day window ends 2026-07-28, before the August spend ramp. Competitive conditions during the current high-spend period are not covered — re-run after it resolves.

**Tooling:** `competitive-analyst/scripts/` had no `node_modules`; `csv-parse` installed via npm during this run.
