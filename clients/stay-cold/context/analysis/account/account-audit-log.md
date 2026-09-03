# Account Audit Log

## 2026-08-06 — Score: 75% (Good)

- **Mode:** full (all 5 modules, 24 diagnostics)
- **Account:** 3599116618 (Stay Cold Apparel)
- **Top finding:** 5 enabled PMax campaigns served 0 impressions for 30 days while reporting `serving_status = SERVING`, holding €359/day of nominal budget
- **Fresh peer reports integrated:** none — no peer audits exist in `context/analysis/`; this is the baseline run
- **Critical issues:** 2 FAIL (AUD-D05, AUD-D08) | **Routing:** pmax-auditor, search-term-auditor, keyword-auditor, budget-auditor, tracking-specialist, feed-auditor, bidding-auditor, geo-schedule-auditor, ad-copy-specialist, account-changelog

| Module | Score | Key Findings |
|--------|-------|-------------|
| Structure | 57% (43/75) | D08 FAIL: 5 zero-impression PMax campaigns. D05 FAIL: two fragmentation groups. D02 WARN: PMax brand separation unverifiable. Off-score: brand broad-match drift on DE/SKANDI reverses a documented +278% win and breaches DON'T-4 |
| Naming | 80% (8/10) | D09 WARN: two incompatible delimiters (`I` ×11 vs `\|` ×4) break tooling that parses on pipe; one campaign name states `T-CPA` but runs MAXIMIZE_CONVERSION_VALUE |
| Settings | 89% (47/53) | Clean on Display Network, geo targeting/exclusion, ad rotation, tracking templates (100% identical). WARN: search partners inconsistent despite a measured +17% win on FOKUSPRODUKTE; SKANDI covers 4 languages in 1 ad group; TEXT_ASSET_AUTOMATION opted in on USA brand |
| Ad Groups | 92% (23/25) | D20 WARN: `STAN I BROAD I HOME` holds 17 keywords across 4 subcultures × 3 product types — the entire non-brand search program in one loose ad group. No SKAGs, no missing RSAs |
| Defaults | 100% (5/5) | 14 of 15 enabled campaigns override the account default with custom goal `6446192748`; only Search TOF uses `CUSTOMER`. The account default is the clean config — the 14 overrides are what break tROAS comparability (business.md §6). DON'T-8 humans-only |
