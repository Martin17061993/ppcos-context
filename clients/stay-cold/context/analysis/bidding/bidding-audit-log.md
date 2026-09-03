# Bidding Audit Log

## 2026-08-06 — Score: 54/100 (Critical)

- Period: 30d (lag 8, ≈ 2026-06-29 → 2026-07-28) | Campaigns: 15 in Active Roster (82 pulled) | Experiments excluded
- Top hypothesis: **M (Measurement)** — Conversion-value integrity failure; targets denominated in an unknown currency. Confidence high
- Active blocking layers: **M** (BID-D26 FAIL; conversion value rule `35918909` ADD +€42.20 ENABLED vs €16.46 documented in business.md §7; plus NCP double-count ×1.28–1.94). B layer clear but Gap G1 keeps a ±19% band on break-even
- Unclearable layers: Eff and Conv — no search-term / keyword / QS / LP / offer audit exists
- Top finding: Deflated to the clean series, FOKUSPRODUKTE runs at ROAS 1.72 against a 1.9 break-even while its CPC rose 36% across three windows — and DSA's *effective clean target* is 1.29, below break-even, so the algorithm is being told to buy unprofitable volume
- Engine overrides: BID-D06 PASS→WARN (engine compared nominal targets, not effective clean); BID-D26 INFO→FAIL (it owns the M layer)
- Unscored: Learning Phase module entirely (15 pts) — `account-changelog.md` missing, learning state unknown not clean
- Fresh peer reports integrated: `/account-auditor` 2026-08-06 (75%, Good) — supplied the mechanism (AUD-D24: 14 of 15 campaigns override the clean account-default conversion goal) and reclassified 5 of 7 strategy failures as structural (AUD-D08)
- Routing: `/account-changelog` (unblocks Learning + the FOKUSPRODUKTE budget contradiction), `/tracking-specialist` (blocking), `/pmax-auditor` + `/feed-auditor` (5 zero-traffic campaigns), `/quality-score-auditor` (DSA 90% + Search TOF 58.7% rank-lost), `/budget-auditor` (Search TOF 31.7% budget-lost), `/strategy-specialist` (Gap G1)

| Module | Score | Key finding |
|---|---|---|
| Target Validation | 8.4/14 avail (60%) | D06 passes only on nominal targets; effective clean targets for DSA (1.29), FOKUSPRODUKTE (1.95), PROSPECTING (1.92) sit at or below break-even 1.9. D05/D07 SKIP — no tCPA campaign exists |
| Strategy Selection | 5/20 (25%) | 7 of 15 campaigns run smart bidding below the 30-conv floor — but 5 are the zero-traffic PMax campaigns from AUD-D08, structural not bidding |
| Learning Phase | N/A (unscored) | All 4 diagnostics degraded to INFO — changelog missing, no change dates available |
| Portfolio Health | 5.8/7 avail (83%) | Zero portfolio strategies in the account. CPC ceiling €2.50 on SKANDI brand (92.0% IS vs 95–99% target) is a candidate constraint — and raising it is DON'T-4-compliant |
| CPC & Cost Health | 7.2/10 (72%) | FOKUSPRODUKTE spike +30% AND rising 3 periods (€1.31→€1.78); PROSPECTING rising +27%. 67% of spend getting more expensive at/below break-even |
| Conversion Value Rules | 5/10 (50%) | Undocumented +€42.20 ADD rule, enabled, no visible conditions |
| Bid Adjustments | 3/3 avail (100%) | Only adjustments in the account are 11 location modifiers at +15% on Search TOF — inert under Smart Bidding |

**Gap G7 partially resolved:** PROSPECTING is **not** budget-limited (0% budget-lost IS, 48.2% rank-lost) — business.md's framing is wrong for that campaign. FOKUSPRODUKTE reports 25.6% budget-lost at 36% utilisation, which is arithmetically contradictory and points to a mid-window budget change; needs the changelog to confirm.
