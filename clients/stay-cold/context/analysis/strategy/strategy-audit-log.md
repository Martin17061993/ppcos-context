# Strategy Audit Log

## 2026-08-07 — Score: 81/105 (77% · Good) · Verdict: GO (on fundamentals)

- **Mode:** DIAGNOSE, both modules · 14 diagnostics, 5 SKIP by vertical (ecommerce → D01/D02/D08/D09 + D10–D14)
- **Sources:** `business.md` 2026-08-03 (4d) · `campaigns.csv` + `account-changelog.md` 2026-08-06 (1d)

| Module | Score | Verdict |
|---|---|---|
| Unit Economics | **50/50 (100%)** | D01 PASS · D02 PASS · D08 PASS · D09 PASS |
| Goals & KPIs | 31/55 (56%) | D10 PASS · D11 PASS · **D12 WARN** · **D13 FAIL** · **D14 FAIL** |

**The audit in one line: the unit economics are excellent and the goals are not agreed with anyone.**

**D08 Viability = GO — but on fundamentals only.** 75% gross margin (Airtable ×4 markup on DDP incl. VAT), break-even clean ROAS 1.9 (190% vs a 333% ceiling), full line-item derivation, robustness-tested across the plausible AOV range. The account is nonetheless running ~2/3 of spend at or below break-even — that is an execution problem, not a viability problem, and the distinction matters.

**D14 FAIL — no client-set goals exist.** business.md says it in bold: *"The targets below are provisional, derived from unit economics, and require Jonas's sign-off. Do not treat them as agreed."* Google is **absent from the client's own 8-channel marketing strategy** — it appears only as open question #1, and v0.2 has sat in Draft since 2026-06-25 with Google's role listed "Not ready." No 2025 actual or 2026 target documented (Gap G3, Critical). No agreed review cadence. **Thirteen audits have now optimised toward numbers nobody approved.** Getting sign-off is the highest-leverage action available — it costs no campaign change.

**D13 FAIL — campaign targets contradict the documented goal.** Deflated to clean, 3 of 6 non-brand campaigns deviate >30% from the 2.5 target, and **DSA's effective target is 1.29 — below the 1.9 break-even**, i.e. instructed to buy unprofitable volume:

| Campaign | Nominal | Factor | Effective clean | vs 2.5 |
|---|---|---|---|---|
| DSA | 2.50 | 1.93 | **1.29** | **−48%, below break-even** |
| PMax PROSPECTING | 3.60 | 1.88 | 1.92 | −23% |
| FOKUSPRODUKTE | 3.53 | 1.81 | 1.95 | −22% |

Bid *mechanisms* are sound — all 15 campaigns on Smart Bidding with inline targets, brand on conservative settings. The numbers fed into them are not. Root cause is the conversion-goal override (account-audit AUD-D24), so this routes to tracking before bidding.

**D12 WARN — the non-brand target is defensible but thin.** PAR = 1.9/2.5 = **76%**, above the 70% healthy ceiling; only 24% headroom, ≈ +€0.30 contribution per media euro. Account-level targets are fine (6.0 → PAR 32%; floor 4.0 → 48%). Reasoning is documented, which is why WARN not FAIL. **But viability rests on Gap G1**: if Google receives net values, break-even is 1.6 and PAR improves to 64% (healthy); if inflation is worse than measured, the target is loss-making.

**D11 PASS — guardrails are unusually strong.** Floors grounded in break-even (non-brand floor *is* 1.9), budget step rules derived from **95 measured changes over two years** (raise only at budget-lost IS ≥20%, never below 5%, max ±30% per step ≥7d apart, zero-conv alarm >€1,000), and an explicit acknowledgement that growth and efficiency are incompatible here. Better than most accounts manage.

**A peer contradicts a PASS, stated plainly:** D11 rates the €30–35k monthly spend guardrail as excellent. The 2026-08-06 budget audit projects **€78–93k for August**. The guardrail passes as a *definition* and is failing as a *control* — breached by ~2.5×.

**Open risks carried into the verdict:** Gap G1 (gross vs net — moves break-even 1.6↔1.9), Gap G8 (payment fee 2% and shipping €6 are assumptions feeding break-even directly), Gap G2 (repeat purchase / CLV unavailable while the account pays a +€16.46 new-customer bonus nothing validates — routed here by the PMax audit's nca-lifecycle module).

**Governance flag carried from the changelog:** business.md §13 states "Martin proposes, Jonas executes, no exceptions," but every budget and target change in the last 30 days came from `exmachina.agency@gmail.com`, plus 266 unattributed Editor changes. Proposals routed to the wrong person do not land.

**Fresh peers integrated (all 2026-08-06, no re-runs):** bidding 54, budget 47, LP 56%, offer 97%, keyword 85%, search-term 79%, account 75%, competitive 73, geo-schedule 75%, placement 48%, pmax. **`/tracking-specialist` is the one missing peer** — and it is the one that would validate every economics input.

**Routing:** Jonas sign-off on targets (**top**) → resolve Gap G1 (Shopify reconciliation) → clarify budget authority → `/tracking-specialist` → then `/bidding-optimizer adjust-targets` for DSA → close G2 and G8. **Do NOT lower targets to match current performance** — business.md's feasibility check found 2.5 reachable from today's 2.14 through calibration alone, with no budget increase.

**Timing:** the FOKUSPRODUKTE and Search TOF learning windows recorded on 2026-08-06 as clearing on 2026-08-07 **have now cleared**. Both are available for change today, subject to the tracking fix landing first.
