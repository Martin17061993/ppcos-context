# Geo-Schedule Audit Log

## 2026-08-06 — Score: 75% (Good)

- **Mode:** full · 14 diagnostics · 3 SKIPped (GS-D04, GS-D09, GS-D14) · 57 / 76 available points
- **Account:** 3599116618 · windows: geo/device/schedule 30d, demographics 90d
- **Governing fact:** every enabled campaign runs Smart Bidding (tROAS / MaxConvValue / tIS). No manual CPC anywhere. Smart Bidding ignores location, device and demographic bid modifiers — only −100% exclusions still work. Most of this skill's normal levers are unavailable by construction

| Module | Score | Key finding |
|---|---|---|
| Geographic (D01–D05) | 22/30 (73%) | Targeting method and exclusion coverage clean. €3,727 (10.8% of 30d spend) below deflated break-even across 9 markets — but "sells worldwide" is documented strategy, so this is a Jonas decision not a hygiene fix |
| Schedule & Device (D06–D09) | 23/23 (**100%**) | Zero dead windows across 168 hour×day slots. No ad-schedule criteria exist at all — everything runs 24/7. Desktop −26% but deflates to ~5.6 vs 1.9 break-even, so profitable — do not exclude |
| Demographics & Advanced (D10–D14) | 12/23 (52%) | Carried entirely by the GS-D11 FAIL. Demographics themselves are healthy |

**Top finding — GS-D11 FAIL: 11 location bid modifiers at +15% on a Smart Bidding campaign, aimed at the account's weakest markets.** `EX I EN I WW I TOF …` runs MAXIMIZE_CONVERSION_VALUE. Boosted geos include **Denmark (reported ROAS 0.47 — worst in account)**, **Czechia (0.92)**, **Estonia (0 conversions on 114 clicks)**, plus Canada, Italy, Switzerland and Australia — 9 of 11 at or below deflated break-even. Only Finland (15.06) and Slovakia (10.32) are strong. Inert today because Smart Bidding ignores them; they would activate on any move to manual or portfolio bidding. Remove: zero risk.

**Other findings:**
- GS-D02 WARN — 9 markets below deflated break-even: Canada €1,378, Netherlands €797, Denmark €503, Spain €351, Czechia €325, Ireland €156, Hungary €96, Ukraine €68, Estonia €53. Structural pattern worth naming: **markets with a dedicated brand campaign all perform strongly; markets served only by the worldwide non-brand campaigns are the ones below break-even**
- GS-D03 WARN — Ukraine (301 clicks, €68) and Estonia (114 clicks, €53), zero conversions. €121 total. Safe, cheap exclusion; location exclusions DO work under Smart Bidding
- GS-D12 WARN — **the YoY geo comparison is unusable.** It spans the 2025-11-10 conversion-regime change, comparing a clean prior year against an inflated current one. Distortion runs counter-intuitively: inflation lowers current CPA, so where the file shows CPA rising (Germany +77%) the real deterioration is worse (~+152% deflated). Budget rose +42–109% inside the window too. Fix measurement, then re-run
- GS-D10 / GS-D13 PASS — **the apparent demographic outliers are a comparison artefact.** Every known segment looked 17–50% below average, but that average is inflated by the untargetable UNDETERMINED bucket (22,981 clicks at ROAS 68.91). Recomputed against a known-segments-only baseline of 17.64, only 65+ exceeds −30%, on €309 spend, still ~4× break-even. No exclusion candidates
- GS-D07 PASS — **Friday is the standout day** (ROAS 16.40 vs 9.72 worst) and the five best hour-slots in the account are all Friday. Matches business.md's documented "Thunder Drop Weeks" Friday cadence. Confirmation, not a to-do — Smart Bidding already exploits it

**Cross-audit resolutions:**
- Account **AUD-D17** (ad schedule SKIPped, routed here) → ✅ **resolved**: no schedule criteria exist, zero dead windows
- Account **AUD-D06** (geo separation of brand campaigns assumed, unverified) → ✅ **confirmed**: per-campaign LOCATION criteria show genuinely distinct market targeting
- Account **AUD-D13/D14** → ✅ confirmed independently
- Bidding **BID-D19/D20/D21** (adjustments PASS, modifiers noted inert) → ⬆️ **escalated to FAIL** — not merely inert, aimed at the weakest markets

**Fresh peer reports integrated (no re-runs):** `/bidding-auditor` 54/100, `/budget-auditor` 47/100, `/competitive-analyst` 73/100, `/account-auditor` 75%, `/pmax-auditor` — all 2026-08-06.

**Routing:** `/geo-schedule-optimizer` (remove 11 modifiers, exclude UA + EE) → Jonas (9 below-break-even markets = strategy call) → re-run `demo` after conversion goals are repaired.

**Tooling:** `geo-schedule-auditor/scripts/` had no `node_modules`; junctioned from `gads-context/scripts/`.
