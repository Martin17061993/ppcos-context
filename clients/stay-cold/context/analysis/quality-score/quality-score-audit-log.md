# Quality Score Audit Log

## 2026-08-07 — Score: 61% (Needs Attention)

- **Top finding:** Landing Page Experience is BELOW AVERAGE on **9/9 non-brand** keywords and ABOVE AVERAGE on **19/19 brand** keywords — **and both groups point at the same homepage URL.** Ad Relevance and Expected CTR are below average on **zero** keywords account-wide.
- **Fresh peer reports integrated:** lp 2026-08-06 (56%) · competitive 2026-08-06 (73) · keyword 2026-08-06 (85%) · search-term 2026-08-06 (79%) · offer 2026-08-06 (97%) · budget 2026-08-06 (47) · tracking 2026-08-07 (66%) · strategy 2026-08-07 (77%)
- Period: 90d (2026-04-30→07-29) | History: 180d | Keywords: 37 (28 scored, 9 flagged)
- Top hypothesis: Creative-LP — homepage is not a relevant destination for subculture product queries (confidence very_high, explains ~100%)
- Module scores: M1 14.6/20 · M2 29/45 · M3 9/9 avail · M4 4.8/20 → **57.4/94**
- Classifier: 20 BRANDED, 0 COMPETITOR, 0 INFORMATIONAL, 17 GENERIC

### The account ran a controlled experiment by accident

All 7 RSAs — 4 brand, 3 non-brand — send traffic to the Stay Cold homepage. Google scores that page ABOVE AVERAGE for brand queries and BELOW AVERAGE for non-brand queries. **Same page, opposite verdicts, no exceptions in either direction.** That isolates the cause as message-match, not page quality (speed, mobile, structure would penalise both equally).

| | Brand (19 kw) | Non-brand (9 kw) |
|---|---|---|
| Weighted QS | **10.00** | **4.90** |
| Ad Relevance | 19 above avg | 8 above, 1 avg, **0 below** |
| Expected CTR | 19 above avg | 4 above, 5 avg, **0 below** |
| Landing Page | **19 above avg** | **9 below avg** |
| Spend (90d) | €10,534 | €4,244 |

Account weighted QS **8.85** — arithmetically true, strategically misleading; carried entirely by brand.

### Key rulings

- **AR queue EMPTY, ECTR queue EMPTY.** Do not route to `/rsa-maker`. `t shirt metal` proves the copy lever was already pulled successfully: QS **1 → 5** over 27 weeks driven purely by AR improving AVG → ABOVE AVG, while LP stayed pinned at below average and capped the result
- **LP has never been above average on a non-brand keyword in 27 weeks.** A permanent floor, not a decline — D12 PASS on trend, D09 FAIL on level
- **D15 FAIL:** Search TOF 69.0% lost IS (rank) on weighted QS 3.09, IS 10.0%. Engine flagged High. Correctly did NOT flag USA Brand (16.2% rank loss on healthy QS 8.96 — competitive, not quality)
- **DSA loses 90.0% to rank** but has no keywords → no QS → undiagnosable here. Pairs with strategy audit's finding that DSA's effective clean target is 1.29, below break-even
- **D16 WARN, not FAIL:** within non-brand, QS 4–5 pays €1.25/click vs €1.14 at QS 6–7 (+10%). The €0.19 vs €1.25 brand/non-brand gap is **auction difference, not QS** — attributing that 6.6× spread to Quality Score would be wrong
- **D10 scored WARN not FAIL** to avoid double-penalising D09; a single clean cause is the most actionable diagnosis available
- **D13 SKIP:** 42 changelog events, but 22 register "near" almost every keyword — account-wide budget changes, not keyword optimisations. Correlation would be spurious
- **Headline Test FAILS** on `STAN I BROAD I HOME`: 17 keywords spanning punk / goth / metal / tattoo / generic / one product name. Restructure brief written with 5 proposed splits — **but pages come first**; splitting without new destinations relabels the problem

### Cross-audit finding surfaced here first

**Search TOF lost 25.1% of impression share to budget** over 90 days, alongside the 69% to rank. business.md's guardrail permits a raise at budget-lost IS ≥20%, and the tracking audit confirms Search TOF carries **zero conversion-value inflation** (factor 1.00), so its 3.74 return is real. **Recommended to hold anyway:** the account is already ~2.7× over its monthly target, and raising budget behind a QS-3.09 ceiling buys expensive impressions. Fix the pages, then raise.

### Config

First run — wrote `qualityScoreAudit` to `config/ads-context.config.json` under auto-mode. **Ruling: 90d evaluation window instead of the 30d default** — with only 37 keywords, 30d would tag most as UNSTABLE_QS and gut the M2 denominators. `competitorCampaigns: []` per business.md L276; 7 competitor brand names configured for keyword-text classification (none matched — competitor traffic arrives as search terms, not keywords).

### Data notes

- No ad customizers exist anywhere (all 5 scopes returned 0 rows) — Headline Test ran in STANDARD mode
- No keyword-level final URLs — all inherit from the RSA, so the LP queue collapses to one URL
- No portfolio bid strategies (0 rows) — all targets inline
- 24.3% of keywords carry no QS at all (€2,688 spend, led by `rocker hoodies` at 7,977 impressions / €977) — under the 30% threshold, standard cause for phrase/broad terms
- 40% INSUFFICIENT_DATA in M3 — under the 50% re-prompt threshold, default kept

### Routing

1. Build subculture landing pages (punk / goth / metal / tattoo) and repoint the keywords — **review the existing 2026-08-06 LP audit**, no re-run
2. Take page copy from `brand.md` — **review the existing 2026-08-06 offer audit** (97%); transfer job, not a writing job
3. Fix `punk hoodie` first within that work — QS 4, €1,173, only HIGH_SPEND_LOW_QS flag, only declining keyword, only non-above-average AR
4. Then reconsider the Search TOF budget raise

**Report:** `context/analysis/quality-score/quality-score-audit.md`
