# Account Changelog — Stay Cold Apparel

*Last updated: 2026-08-06 · Window: 2026-07-08 → 2026-08-06 (30 days) · Customer 359-911-6618*
*Source: `change_event` (67 attributable changes) + `change_status` (266 API-invisible, typically Google Ads Editor)*
*Raw: `context/account-changelog.csv`, `context/account-changelog-invisible.csv`*

---

## READ THIS FIRST — three things this changelog changes

1. **The July budget work broke the account's own guardrails.** FOKUSPRODUKTE went **€550 → €1,150/day (+109%) in a single day, in two steps three minutes apart.** Search TOF went €120 → €240/day (+100%) across seven days. business.md records that budget increases above +90% are **0 for 6 positive** and that step size outside promo windows should be capped at ±30%, ≥7 days apart. July was not a promo window.
2. **Two campaigns are 13 days into a 14-day learning window.** FOKUSPRODUKTE and Search TOF both had budget *and* target changed on 2026-07-24. Any further change resets learning. The correct action this week is to wait one day, then evaluate.
3. **Someone is rebuilding the Demand Gen / Video stack right now.** 113 Editor changes on 2026-08-05 and 38 more on 2026-08-06, concentrated on paused DG/YouTube campaigns including `BS DEALS - DG_ CP+PDP_S+V` — the campaign business.md Gap G6 flags as "clean ROAS 5.78, fundamentally healthy, idle." A relaunch appears to be in preparation.

---

## 1. Budget changes

| Date | Campaign | Old → New (daily) | Step | Who | Via |
|---|---|---|---|---|---|
| 2026-07-17 12:46 | `EX I WW I PMAX … FEED ONLY I PROSPECTING` | €880 → **€1,250** | **+42%** | exmachina.agency@gmail.com | Web UI |
| 2026-07-17 12:46 | `EX I EN I WW I TOF … Kollektionen + Types` | €120 → **€185.01** | **+54%** | exmachina.agency@gmail.com | Web UI |
| 2026-07-24 13:43 | `EX I SHOPPING I FOKUSPRODUKTE` | €550 → **€850** | **+55%** | exmachina.agency@gmail.com | Web UI |
| 2026-07-24 13:46 | `EX I SHOPPING I FOKUSPRODUKTE` | €850 → **€1,150** | **+35%** | exmachina.agency@gmail.com | Web UI |
| 2026-07-24 13:47 | `EX I EN I WW I TOF … Kollektionen + Types` | €185.01 → **€240** | **+30%** | exmachina.agency@gmail.com | Web UI |

**Net effect over 7 days:**

| Campaign | Start | End | Total step | vs guardrail (±30%/step, ≥7d apart) |
|---|---|---|---|---|
| FOKUSPRODUKTE | €550 | €1,150 | **+109% in one day** | ❌ Two steps 3 minutes apart |
| Search TOF | €120 | €240 | **+100% in 7 days** | ❌ Both steps exceeded 30% |
| PROSPECTING | €880 | €1,250 | **+42%** | ❌ Single step over 30% |

⚠️ **PROSPECTING was raised on top of a raise that already failed.** business.md logs 2026-05-29: PROSPECTING €450 → €880 at ~0% budget-lost IS → **−27% on €17,435**, described as "the most expensive single decision of H1 2026." The €880 baseline in the table above *is* that decision. It has now been increased a further 42%.

### This resolves Gap G7

business.md asks why FOKUSPRODUKTE and PROSPECTING report budget-constrained while spending ~30% of their daily budgets. Answer: **the budgets were raised late in the measurement window.**

- FOKUSPRODUKTE's 25.6% budget-lost impression share was earned while the budget was €550/day. The €1,150 budget existed for only the final ~9 days of the 30-day window. The "36% utilisation" figure compares full-window spend against an end-of-window budget — the two are not comparable.
- PROSPECTING is a different case: its budget-lost IS is **0%**. It was never budget-limited. Its constraint is rank (48.2% rank-lost IS). The +42% raise addressed a limit that did not exist.

---

## 2. Bid target changes

| Date | Campaign | Field | Old → New | Note |
|---|---|---|---|---|
| 2026-07-24 13:45 | `EX I EN I WW I TOF …` | `maximize_conversion_value.target_roas` | 3.5 → **5.1915** | **+48%** |
| 2026-07-24 13:45 | `EX I SHOPPING I FOKUSPRODUKTE` | `target_roas.target_roas` | 3.5 → **3.5301** | +0.86%, immaterial |
| 2026-07-24 13:45 | `EX I EN I WW I TOF …` | `maximize_conversion_value.target_roas` | 5.1915 → 5.191502863646795 | Float precision artifact, not a real change |

⚠️ **Budget and target were changed on the same campaigns within four minutes on 2026-07-24.** Search TOF received +30% budget *and* +48% target at 13:45–13:47. FOKUSPRODUKTE received +35% budget and a target nudge at 13:45–13:46. Stacking two levers on one campaign makes the outcome unattributable — neither change can be evaluated on its own. business.md's guardrails call for one lever at a time.

---

## 3. Learning-window status (derived)

Smart bidding learning runs ~14 days from the last material change. As of **2026-08-06**:

| Campaign | Last material change | Days since | Status |
|---|---|---|---|
| `EX I SHOPPING I FOKUSPRODUKTE` | 2026-07-24 (budget +35%, target) | **13** | ⚠️ **In learning — clears 2026-08-07** |
| `EX I EN I WW I TOF … Kollektionen + Types` | 2026-07-24 (budget +30%, target +48%) | **13** | ⚠️ **In learning — clears 2026-08-07** |
| `EX I WW I PMAX … FEED ONLY I PROSPECTING` | 2026-07-17 (budget +42%) | 20 | ✅ Out of learning |
| All other enabled campaigns | none in window | — | ✅ No recent change |

**Consequence:** the two campaigns most likely to be discussed this week are the two that must not be touched until 2026-08-07. Any change today resets a learning period that is one day from completing.

---

## 4. Tracking template rollout — 2026-07-23

**57 ad-group-level `tracking_url_template` updates across ~25 campaigns in a single day**, all by exmachina.agency@gmail.com via the web UI. Touched every brand campaign (DE, USA, FRA, SKANDI, ESP), both Shopping campaigns, the DSA campaign, Search TOF, and a long tail of paused Demand Gen / YouTube / BFCM campaigns.

⚠️ business.md historical failures records: *"Account-wide same-day tracking rollout — 2024-10-23: 7 of 11 clusters negative, up to −47%."* The same pattern was repeated on 2026-07-23. It also contradicts guardrail DON'T-9 (never roll out same-day across all markets; stagger 1–2 weeks).

Offsetting note: the 2026-08-06 account audit found tracking templates **byte-identical across all 15 enabled campaigns** (AUD-D18, PASS). Whatever the rollout risk, the end state is consistent — and business.md separately records a *positive* tracking-template cleanup (2026-03-06, +66/+25/+17%). Worth measuring rather than assuming harm.

---

## 5. Keyword changes

| Date | Campaign | Change | Who | Via |
|---|---|---|---|---|
| 2026-07-31 14:35 | `EX I EN I WW I TOF …` | Added `mens hoodies` [EXACT] | ads@jonas-makki.com | **API** |
| 2026-07-31 14:40 | `EX I EN I WW I TOF …` | Added `sinner hoodie` [EXACT] | ads@jonas-makki.com | **API** |

Both landed in ad group `STAN I BROAD I HOME`. These are the two keywords the 2026-08-06 account audit flagged as thematic outliers in that ad group (AUD-D20) — `mens hoodies` is a generic head term sitting among niche subculture keywords. They are six days old, so no performance verdict is possible yet.

---

## 6. API-invisible changes (Google Ads Editor)

266 changes visible only via `change_status` — no user attribution available.

| Resource type | Count |
|---|---|
| `AD_GROUP_AD` | 194 |
| `AD_GROUP_CRITERION` | 41 |
| `CAMPAIGN` | 28 |
| `CAMPAIGN_BUDGET` | 3 |

**By date — note the concentration at the end:**

| Date | Changes |
|---|---|
| 2026-07-08 → 2026-08-02 | 113 spread over 10 days |
| **2026-08-05** | **113 in one day** |
| **2026-08-06** | **38 (today, ongoing)** |

### What is being edited — Gap G6 is moving

The recent burst is concentrated on **paused Demand Gen, YouTube and BFCM campaigns**:

| Campaign | Changes | Status |
|---|---|---|
| `BS DEALS - DG_ CP+PDP_S+V` | 34 | PAUSED |
| `JM I DG I TOF I MBP I VID` | 33 | PAUSED |
| `EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C. #3` | 28 | PAUSED |
| `BFCM '25 - DG SPECIAL DROPS _ CP+PDP_MIXED` | 19 | PAUSED |
| `BFCM '25 - DG SPECIAL DROPS _ CP+PDP_ TOF` | 19 | PAUSED |
| `EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C. #2` | 17 | PAUSED |
| `BFCM '25 - DG SPECIAL DROPS _ CP+PDP_MIXED #2` | 15 | PAUSED |
| `EX \| EN \| WW \| DEMAND GEN \| TEST` | 9 | PAUSED |
| `BFCM '25 - DG SPECIAL DROPS _ CP+PDP_MIXED #4` | 8 | PAUSED |

**`BS DEALS - DG_ CP+PDP_S+V` is the single most-edited campaign in the account right now** — and it is exactly the campaign business.md Gap G6 (High) asks about: *"had an H1-2026 clean ROAS of 5.78 and was profiled as 'fundamentally healthy'. If it is off by accident, profitable volume is idle."*

**Three consequences, all time-sensitive:**

1. **Gap G6 has a directional answer.** The €0 in Video/Demand Gen is not being ignored — a rebuild is underway. Confirm intent with Jonas rather than treating the channel as dormant.
2. **A tracking landmine must be defused before relaunch.** business.md §7: *"`YouTube follow-on views` is `primary_for_goal = true` AND `ENABLED` — harmless at €0 video spend; **will corrupt bidding signal the moment Video or Demand Gen restarts.** Fix before reactivating."* This is now urgent, not theoretical.
3. **Budget planning is stale before it is written.** Any Video/DG relaunch needs budget that is not in the current €30–35k/month plan, and business.md logs the precedent: *"Unmonitored launches — 'Video View DRAFT' ran four weeks unnoticed: €4,750 for 2 purchases (clean ROAS 0.04)."*

BFCM '25 campaigns being edited in August also intersects Gap G18 (BFCM 2026 unconfirmed, 16 weeks out) — the campaign shells may be getting prepared ahead of a plan.

---

## 7. Who is changing what

| Actor | Changes | Channel | What |
|---|---|---|---|
| **exmachina.agency@gmail.com** | 62 | Google Ads Web UI | **All 5 budget changes, all 3 target changes**, the 57-ad-group tracking rollout |
| **ads@jonas-makki.com** | 2 | Google Ads API | 2 keyword additions |
| *(unattributed)* | 266 | Google Ads Editor | DG/Video/BFCM rebuild |

⚠️ **This does not match the documented operating model.** business.md §13 states: *"Martin (external) analyses and proposes. Jonas Makki executes. No exceptions."* In this window, every budget and bid-target change came from **exmachina.agency@gmail.com**, not from Jonas's account, and 266 further changes have no attribution at all.

Either business.md's operating model is out of date, or there is a third party making material budget decisions outside the documented chain. **Worth resolving before any proposal is submitted** — a recommendation routed to Jonas may not reach whoever is actually making these changes. Raise it as a question, not an accusation; agency-managed sub-accounts commonly have multiple legitimate operators.

---

## 8. What this means for the open audits

| Audit | Finding affected | Update |
|---|---|---|
| **Bidding** (54/100, 2026-08-06) | Learning Phase module was unscored (15 pts) for lack of change history | **Now scoreable.** Two campaigns in learning until 2026-08-07 |
| **Bidding** | FOKUSPRODUKTE 25.6% budget-lost at 36% utilisation flagged as "arithmetically contradictory" | **Resolved** — budget was raised +109% nine days before window end |
| **Bidding** | "PROSPECTING is not budget-limited" | **Reinforced** — it was raised +42% anyway, on top of a raise that measured −27% |
| **Account** (75%, 2026-08-06) | AUD-D20: `mens hoodies` / `sinner hoodie` flagged as thematic outliers | **Dated** — added 2026-07-31 via API, 6 days old |
| **Account** | AUD-D18: tracking templates consistent (PASS) | **Contextualised** — consistency is the result of a same-day 57-ad-group rollout on 2026-07-23 |
| **Budget** (this run) | All pacing and allocation math | **Budgets are 9–20 days old and rose 42–109%.** Full-window spend understates the current run rate |

---

## Data notes

- `change_event` retains a maximum of 30 days. Anything before 2026-07-08 is unavailable via this API and must come from business.md's change-impact analysis (cutoff 2026-07-03).
- `change_status` reports *that* a resource changed, not *what* changed or *who* changed it. The 266 invisible rows are almost certainly Google Ads Editor pushes.
- Timestamps are account timezone as returned by the API.
