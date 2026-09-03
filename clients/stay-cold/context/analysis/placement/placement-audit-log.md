# Placement Audit Log

## 2026-08-06 — Score: 48% (Critical)

- **Mode:** full · 10 diagnostics · 90-day window · 260,516 placements analysed · 2 SKIP + 1 INFO · 22.8 / 48 available points
- **Read the score correctly: this is an EXPOSURE finding, not a spend finding.** Total flagged spend across 1,793 flags is **€117.73**, and all of it is historical — every flag belongs to `Video View DRAFT`, which is PAUSED and which business.md already documents as a known failure ("ran four weeks unnoticed: €4,750 for 2 purchases"). Every Video, Display and Demand Gen campaign in the account is paused or removed. There is no live placement spend to cut.

| Module | Score | Key finding |
|---|---|---|
| Performance & App Audit | 15/25 avail (60%) | All flagged spend historical, one paused campaign. D02 SKIP — no Display placements exist at all |
| **Brand Safety & Coverage** | **6/20 (30%)** | **A 38,208-member exclusion list protects nothing that serves** |
| Hygiene & Monitoring | 1.8/3 avail (60%) | List contents clean (0 overlaps); D08 SKIP — every Demand Gen campaign paused |

**TOP FINDING — PL-D05 FAIL: brand safety was built, then disconnected.** Shared set `BROAD Ausschlüsse + Konkurrenz` (id `11001087871`), ENABLED, **38,208 members** — 24,553 mobile applications, 7,759 YouTube channels, 5,757 placements, 139 of 140 mobile app categories. Attached to exactly **3 campaigns, all dead** (1 REMOVED, 2 PAUSED YouTube/DG tests). Coverage across the 7 campaigns actually serving placements: **0 full, 0 partial, 7 uncovered.**

**Crucial fix nuance — do not recommend "attach the list."** PMax is the only channel serving placements today, and it does not consume shared negative placement lists the way Display/Video do. The contents must be promoted to **account-level exclusions**, which do apply to PMax. Those currently stand at: mobile app categories **0**, placements **0**, content labels **1** (`PARKED_DOMAIN` only). The material already exists — this is a promotion exercise, not authoring.

**Live exposure being measured:** PMax serves **20,395 placements / 3,011,823 impressions**, of which 3,301 are MOBILE_APPLICATION and 16,941 WEBSITE. **996 tripped the bad-domain pattern check — all at €0.00**, because Google does not attribute cost at PMax placement level. Impression exposure, not waste. For an aesthetics-driven brand that still matters.

**Timing is the second priority.** PL-D08 scores SKIP only because Demand Gen is paused — and the changelog shows 113 Editor changes on 2026-08-05 plus 38 on 2026-08-06 concentrated on paused DG/Video campaigns. Connect the exclusions *before* that relaunch, not after. This account already has the scar.

**Content review (sub-agent, 300 placements sampled):** 36 flagged (12%) — 3 KIDS_CONTENT (SML, Family Friendly, Preston), 2 BRAND_UNSAFE (Lingerie Fighting Championships, Domovinski rat war content), 28 MUSIC_PASSIVE, 3 LANGUAGE_MISMATCH. Reviewer correctly rejected false positives (left *Ink Master* unflagged as on-brand).

⚠️ **One reviewer call NOT applied verbatim:** MUSIC_PASSIVE includes **KoRn, Judas Priest, Electric Callboy** — defensible as passive consumption, but those audiences are precisely Stay Cold's target market. Exclude VEVO and auto-generated "Topic" channels; keep the metal bands. Two separate decisions, recorded so a future run doesn't blanket-exclude them.

**Other notes:** all 65 view-through conversion rows resolved to **secondary** conversion actions — zero to `purchase_gads_mable`. Placement type breakdown is 100% YOUTUBE_CHANNEL: €2,918.66 / 625 clicks / 406,730 impressions / CTR 0.15% / **0 conversions**.

**Config:** `placementAudit` section written from business.md rather than defaults — `extremeCpaMultiplier` 2.0 (Cost Control, 67% of spend at/below break-even, Gap G2 LTV unvalidated), `minClicks` 30 (Content spend ≈€1,969/mo), `minWasteSpend` 30 (implied break-even CPA €75 = AOV 143 ÷ 1.9), `vtcDiscountFactor` 0.2 (short apparel consideration cycle).

**Fresh peers integrated (no re-runs):** `/pmax-auditor`, `/budget-auditor` 47/100, `/bidding-auditor` 54/100 — all 2026-08-06.

**Routing:** `/placement-optimizer lists` + `/placement-optimizer apps` (promote to account level) → `/placement-optimizer safety` (content-label policy, deliberate not blanket) → Jonas (timing vs DG relaunch; whether to remove `Video View DRAFT` rather than leave it paused) → `/tracking-specialist` (disable `YouTube follow-on views` as primary before DG restarts).
