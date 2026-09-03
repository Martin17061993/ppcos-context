# Keyword Audit Log

## 2026-08-06 — Score: 85% (Good)

- **Scope:** full · 17 diagnostics · 37 keywords across 5 campaigns · Period A 30d lag 8 (≈2026-06-29 → 2026-07-28) vs prior 30d
- **Top finding:** €1,961 — **42% of the non-brand search budget** — runs below the 1.9 clean break-even across 5 keywords, and **B3 core-term concentration is 100%**, so pausing is prohibited. The cause is the landing page, verified independently.
- **Diagnosis: Conversion layer.** LP experience is `BELOW_AVERAGE` on 6 of 6 scored non-brand keywords while ad relevance is `ABOVE_AVERAGE` on 5 of 6. QS capped at 4–7 by that single component; brand keywords on other pages score 10. Same fault the competitive audit measured as 64.2% rank-lost impression share.

| Module | Score | Key finding |
|---|---|---|
| Match Type Health | 20/20 (100%) | No redundancy; all broad on Smart Bidding; 18 flagged cross-campaign conflicts are geo-separated false positives |
| Performance Segmentation | 17.6/30 (59%) | KW-D07 FAIL — €1,961 below break-even. 6 tier degradations, zero upgrades |
| Cannibalization & Duplicates | 22.6/25 (90%) | 6 "duplicates" are geo-separated brand terms. Real finding: 80 distinct PMax terms overlap, 0 negatived, **27 off-brand** |
| Keyword Hygiene | 10/10 (100%) | All 37 ELIGIBLE + APPROVED. No below-first-page bids |
| Intent Alignment | 15/15 (100%) | No informational keywords. Brand terms cleanly confined to brand campaigns |

**Three engine verdicts overridden:**
- **KW-D04 FAIL→PASS** — 18 cross-campaign match conflicts are all brand terms across geo-separated DE/FRA/SKANDI/USA campaigns. Today's geo audit verified the separation from per-campaign LOCATION criteria. The engine does not read geo targeting
- **KW-D10 FAIL→PASS** — same false positive, 6 duplicate groups
- **KW-D08 WARN→PASS** — `mens hoodies` and `sinner hoodie` flagged ZOMBIE at €0, but the changelog shows they were **added 2026-07-31 via API, after Period A closed**. New, not dead. The skill's edge case notes the dataset lacks a created date; the changelog supplied it

**Unusual measurement note:** account-wide inflation (×1.28–1.94) normally blocks all pause recommendations — but Search TOF, which holds every non-brand keyword, is **the one campaign with factor 1.00** (business.md §6; corroborated by AUD-D24's finding that it alone uses the clean account-default goal). So these keyword economics are already clean and more trustworthy than anything else in the account. **Residual risk:** if the bidding audit's +€42.20 value rule applies here too, all ROAS drop ~29% and `rocker hoodies` (€715) flips from above-target to below break-even.

**Do NOT pause (recorded so a future run does not relitigate it):** `t shirt metal` €1,006 / 1.50 (was HERO), `goth and punk clothing` €457 / 1.41, `goth rock clothes` €372 / 1.54, `punk and rock outfit` €79 / 1.82, `tattoo hoodies` €47 / 0.21 — all core terms. Plus the 4 OVER_TARGET keywords (`rocker hoodies`, `punk hoodie`, `tattoo clothing`, `tattoo streetwear`) which clear break-even at 2.42–3.39 and are only "over target" because the campaign target is 5.19 against a 1.9 floor.

**Off-brand PMax contamination (new finding):** 27 of 80 distinct overlapping terms are other brands or the wrong subculture — 15+ `cyberpunk hoodie` variants (sci-fi aesthetic, not punk subculture), plus `t shirt metallica` / `represent t shirt metallica`, `gildan t shirt metal`, `t shirt metal mulisha`, `cm punk hoodie`. Zero negative coverage.

**Fresh peer reports integrated (no re-runs):** `/competitive-analyst` 73/100 (supplied the decisive LP evidence), `/bidding-auditor` 54/100 (inflation factor 1.00 + value-rule sensitivity), `/account-auditor` 75% (AUD-D20 ad-group split, AUD-D24 goal config, AUD-D06 brand broad match), `/budget-auditor` 47/100. **No peer contradicts the hypothesis — four independently converge on the landing page.**

**Routing (sequenced, pause is last resort and currently unreachable):** `/lp-auditor` (**top**) → `/offer-auditor` → `/search-term-auditor ngrams` 120–180d for the off-brand PMax cluster → `/strategy-specialist` + `/bidding-optimizer` for the 5.19-vs-1.9 target gap → account-audit AUD-D20 ad-group split. **No `/keyword-optimizer pause` offered** — B3 at 100%.
