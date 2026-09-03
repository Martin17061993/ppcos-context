# Budget Audit Log

## 2026-08-06 — Score: 47/100 (Critical)

- Period: 30d (lag 8) | Campaigns: 15 | Budgets: 50 | Portfolios: 0 | Experiments: included (none active)
- Top hypothesis: **Struct — uncontrolled spend ramp from guardrail-breaking budget raises**, with **M (Measurement) active-blocking** beneath it. Confidence high
- Active blocking: M (conversion-value inflation), Bid (BUD-D08 `blocking: ['bidding']`)
- **Top finding: spend is projected at €78–93k for August against a €32,500 target (+140% to +185%).** MTD €14,290 in 5 days. Daily series went €650/day (mid-July) → €3,274/day (4 Aug). Last 7 days €2,360/day vs prior 7 days €719/day = **+228%**. This exceeds the June 2026 over-scaling (€62k/mo) that business.md calls the most expensive decision period of H1
- Cause identified from the changelog pulled during this run: FOKUSPRODUKTE **€550 → €1,150/day (+109%) in one day, two steps 3 minutes apart** (2026-07-24); Search TOF €120 → €240 (+100% over 7 days); PROSPECTING €880 → €1,250 (+42%). All via web UI by `exmachina.agency@gmail.com`, all outside any documented promo window, two stacked with simultaneous target changes
- Engine overrides (all from the same cause — engines compare clean break-even 1.9 against the inflated value series): **BUD-D04 PASS→FAIL**, **BUD-D14 PASS→FAIL**, **BUD-D15 PASS→WARN**. BUD-D03 kept WARN but FOKUSPRODUKTE removed from its "profitable" list. BUD-D05 PASS→SKIP (no tCPA campaign exists; vacuous check)
- Fresh peer reports integrated: `/bidding-auditor` 2026-08-06 (54/100) supplied the inflation factors and the rank-vs-budget split; `/account-auditor` 2026-08-06 (75%) owns the 5 zero-spend shells and the goal-override mechanism
- Routing: Jonas today (is the ramp authorised? who has budget authority?) → `/tracking-specialist` (blocking) → review existing bidding + account reports → `/quality-score-auditor` → `/pmax-auditor` + `/feed-auditor` → `/budget-optimizer` (reduce FOKUSPRODUKTE, no raises approved)

| Module | Score | Key finding |
|---|---|---|
| Allocation | 12/30 (40%) | FOKUSPRODUKTE holds 40% of spend at clean ROAS 1.72, below the 1.9 break-even, and was just raised +109% — a reduce candidate, not a hold. 6 profitable campaigns under 5% share |
| Limitation | 12/25 (48%) | Search TOF 31.7% and FOKUSPRODUKTE 25.6% IS Lost (Budget). Only Search TOF is genuinely profitable+limited once deflated |
| Pacing | 6.4/12 avail (53%) | BUD-D10 FAIL at +172.6% projected overspend. August is not a highlight month — no seasonal justification on file |
| Sufficiency | 5.4/9 avail (60%) | 8 campaigns below the 50-conv floor. All 50 budgets on STANDARD delivery → up to 2× daily spend possible, which is what makes the ramp mechanically possible |
| Shared budgets | N/A | No shared budgets exist — 15 pts redistributed |

**Two campaigns in learning until 2026-08-07:** FOKUSPRODUKTE and Search TOF (both had budget AND target changed on 2026-07-24, 13 days ago). Touching either today resets a window one day from completing.

**Governance flag:** every budget and target change this window came from `exmachina.agency@gmail.com` via web UI, plus 266 unattributed Editor changes. business.md §13 documents "Martin proposes, Jonas executes, no exceptions." Worth resolving before proposals are submitted.

**Time-sensitive side finding:** a Demand Gen / Video relaunch appears to be in preparation (113 Editor changes 2026-08-05, 38 on 2026-08-06, concentrated on `BS DEALS - DG_ CP+PDP_S+V` — business.md Gap G6). Needs budget not in the €32,500 plan, and the `YouTube follow-on views` primary conversion must be disabled before launch or it corrupts bidding signal.
