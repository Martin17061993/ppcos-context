# Placement Audit — 2026-08-06

**Overall Score:** 48% — **Critical**
**Mode:** full · 10 diagnostics · 3 modules · 2 SKIP, 1 INFO
**Window:** 90 days · **Account:** 3599116618 (Stay Cold Apparel) · EUR · vertical: D2C e-commerce (apparel)
**Data volume:** 260,516 placements analysed · 63,904 group · 176,217 detail · 20,395 PMax

---

## Executive read

Read this score as an exposure finding, not a spend finding. **No money is being wasted on placements — €117.73 of flagged spend across 1,793 flags, and every euro of it is historical.** It all belongs to one paused campaign, `Video View DRAFT`, which business.md already documents as a known failure ("ran four weeks unnoticed: €4,750 for 2 purchases"). Every Video, Display and Demand Gen campaign in this account is paused or removed. There is no live placement spend to cut.

What earns the Critical grade is that **brand safety has been built and then disconnected**. The account contains a serious, deliberately-assembled exclusion list — `BROAD Ausschlüsse + Konkurrenz`, 38,208 members: 24,553 mobile applications, 7,759 YouTube channels, 5,757 placements and 139 mobile app categories. Someone did real work here. It is attached to exactly three campaigns, and all three are removed or paused YouTube tests. **Zero of the seven campaigns currently serving placements are covered by it.** Meanwhile Performance Max is putting **3.0 million impressions across 20,395 placements**, including 3,301 mobile applications, with no exclusion list, no account-level app-category exclusions, no account-level placement exclusions, and exactly one content label excluded account-wide (parked domains).

**One nuance that changes the fix.** Performance Max does not accept shared negative placement lists the way Display and Video campaigns do. So "attach the list to the PMax campaigns" is not the action. The list's contents need promoting to **account-level exclusions**, which do apply to PMax — and account-level placement exclusions currently sit at zero.

**Second priority is timing.** The account changelog shows a Demand Gen and Video rebuild in progress right now — 113 editor changes on 5 August, 38 more on 6 August. Demand Gen is the channel most exposed to placement quality, and today it scores SKIP only because nothing is running. Connect the exclusions before that work goes live, not after.

**What is not a problem:** the 996 flagged PMax "bad domains" carry €0.00 spend, because Google does not attribute cost at PMax placement level — they are impression exposure, not waste. And of 300 placements reviewed for content, only 36 were flagged, mostly passive music channels.

Read Critical Issues, then Module 2. Baseline run — no prior score.

---

## Module scores

| Module | Score | Grade | Key finding |
|---|---|---|---|
| Performance & App Audit (PL-D01–D04) | 15 / 25 available | **60% — Needs attention** | All flagged spend is historical, from one paused campaign |
| **Brand Safety & Coverage (PL-D05–D07)** | **6 / 20** | **30% — Critical** | A 38,208-member exclusion list protects nothing that serves |
| Hygiene & Monitoring (PL-D08–D10) | 1.8 / 3 available | 60% — Needs attention | List contents are clean; Demand Gen unscoreable while paused |
| **Overall** | **22.8 / 48 available** | **48% — Critical** | Exposure risk, not spend waste |

*28 of 76 nominal points removed: PL-D02 SKIP (10 — no Display placements exist), PL-D08 SKIP (15 — every Demand Gen campaign is paused), PL-D10 INFO (3 — spot-check carries no points by design).*

---

## Critical issues

### 1. PL-D05 — FAIL — The exclusion list is attached to nothing that runs

| Shared set | `BROAD Ausschlüsse + Konkurrenz` (id `11001087871`) |
|---|---|
| Status | ENABLED · type `NEGATIVE_PLACEMENTS` |
| **Members** | **38,208** |
| — Mobile applications | 24,553 |
| — YouTube channels | 7,759 |
| — Placements | 5,757 |
| — Mobile app categories | 139 (of 140 that exist) |
| **Campaigns attached** | **3 — all dead** |

The three linked campaigns:

| Campaign | Channel | Status |
|---|---|---|
| `EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C.` | VIDEO | **REMOVED** |
| `EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C. #2` | DEMAND_GEN | **PAUSED** |
| `EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C. #3` | DEMAND_GEN | **PAUSED** |

Coverage analysis across the seven campaigns that actually serve placements: **0 full, 0 partial, 7 uncovered.**

**The fix is not "attach the list."** Performance Max — which is the only channel serving placements today — does not consume shared negative placement lists the way Display and Video do. The correct action is to promote the list's contents to **account-level exclusions**, which do apply to PMax. Those currently stand at:

| Account-level exclusion type | Count |
|---|---|
| Mobile app categories | **0** |
| Placements | **0** |
| Content labels | **1** (`PARKED_DOMAIN` only) |

The material already exists inside the shared set. This is a promotion exercise, not an authoring one.

**Routing:** `/placement-optimizer lists`, then `/placement-optimizer apps`. PMax-side settings route to `/pmax-optimizer`.

### 2. PL-D07 / PL-D01 — WARN — 3.0 million uncovered PMax impressions, 3,301 of them in mobile apps

| PMax placement type | Placements | Cost |
|---|---|---|
| WEBSITE | 16,941 | €0.00 |
| **MOBILE_APPLICATION** | **3,301** | €0.00 |
| YOUTUBE_VIDEO | 150 | €0.00 |
| GOOGLE_PRODUCTS | 3 | €0.00 |
| **Total** | **20,395** | **€0.00 · 3,011,823 impressions** |

996 of these tripped the known-bad-domain pattern check. **All at €0.00**, because the PMax placement view reports impressions without cost attribution — Google does not break out spend at this level. So this is not measurable waste; it is three million brand impressions on surfaces nobody has vetted, including 3,301 mobile apps on an account with zero app-category exclusions.

For a brand whose entire proposition is aesthetic, that matters more than the euro figure suggests.

### 3. Timing — connect exclusions before the Demand Gen rebuild goes live

PL-D08 scores SKIP because every Demand Gen campaign is paused. That is temporary. The account changelog pulled today records **113 Google Ads Editor changes on 2026-08-05 and 38 more on 2026-08-06**, concentrated on paused Demand Gen and Video campaigns — including `BS DEALS - DG_ CP+PDP_S+V`, which business.md Gap G6 flags as clean ROAS 5.78 and idle.

Demand Gen is the channel where placement quality does the most damage fastest, and this account already has the scar: business.md's Historical Failures list records *"Unmonitored launches — 'Video View DRAFT' ran four weeks unnoticed: €4,750 for 2 purchases (clean ROAS 0.04)."* Every placement flag in this audit comes from that campaign.

**Do the exclusion work now, while nothing is running.** It is free to do today and expensive to do after launch.

---

## Placement type breakdown

**All measured placement spend is YouTube channels, and all of it is historical.**

| Type | Placements | Spend | Clicks | Impressions | CTR | **Conversions** |
|---|---|---|---|---|---|---|
| YOUTUBE_CHANNEL | 63,904 | €2,918.66 | 625 | 406,730 | 0.15% | **0** |

€2,918.66 over 90 days for **zero conversions**. Every row belongs to `Video View DRAFT`, status PAUSED.

### Top flagged placements — all in the paused campaign

| Spend | Flag | Placement | Channel |
|---|---|---|---|
| €79.21 | ZERO_CLICK | `UCRXeotOurT4O18UecCmyvRw` | Viraltek |
| €23.13 | (reviewed) | `UCYXIviXPAaaaU_AOotpXTAw` | Revive Music |
| €14.86 | (reviewed) | `UC-4Tzd5lIRU7lcv7_5OO01Q` | unsympathischTV |
| €13.73 | (reviewed) | `UC7Tmdxj18fdu4tTtxVUhoCA` | Jocuri Horror |
| €11.44 | (reviewed) | `UCoMdktPbSTixAyNGwb-UYkQ` | Sky News |
| €5.81 | ZERO_CLICK | `UCwWhs_6x42TyRM4Wstoq8HA` | — |
| €5.38 | ZERO_CLICK | `UC9r9HYFxEQOBXSopFS61ZWg` | — |

### Flags by type and spend

| Flag | Count | Spend |
|---|---|---|
| ZERO_CLICK | 3 | €90.40 |
| VIDEO_CTR_ANOMALY | 448 | €12.76 |
| HIGH_CTR_ACCIDENTAL | 199 | €7.74 |
| SPAM_CONTENT | 60 | €3.48 |
| KIDS_CONTENT | 47 | €2.14 |
| MUSIC_PASSIVE | 40 | €1.21 |
| PMAX_BAD_DOMAIN | 996 | **€0.00** |
| **Total** | **1,793** | **€117.73** |

---

## Content review (300 placements sampled)

A content-review sub-agent examined the top 300 placements by spend against the brand's context — deliberately dark/tattoo/metal aesthetic is on-brand and must not be flagged; kids content, mobile games, spam, passive music, adult and political content are not.

**36 of 300 flagged (12%):**

| Flag | Severity | Count | Examples |
|---|---|---|---|
| MUSIC_PASSIVE | Medium | 28 | VEVO channels, YouTube "Topic" auto-channels, artist channels, Boiler Room, Lyrical Lemonade |
| **KIDS_CONTENT** | **Critical** | **3** | SML (puppet pranks), Family Friendly, Preston (Minecraft) |
| **BRAND_UNSAFE** | **Critical** | **2** | Lingerie Fighting Championships (adult), Domovinski rat (war/political) |
| LANGUAGE_MISMATCH | Medium | 3 | Новий канал (Ukrainian), 戰爭劇場 (Chinese drama) |

The reviewer correctly rejected false positives — *Ink Master* was left unflagged as genuinely on-brand for a tattoo apparel advertiser.

> ⚠️ **One reviewer call I would not apply verbatim.** The MUSIC_PASSIVE list includes **KoRn, Judas Priest and Electric Callboy**. The classification is defensible on its own terms — people watching music videos are in passive consumption mode and convert poorly — but those three channels are watched by *precisely* Stay Cold's target audience: metal and hardcore listeners. Excluding VEVO and auto-generated "Topic" channels is sound. Blanket-excluding the metal bands whose fans are the customer base would be a mistake for any future Video or Demand Gen campaign. Treat the music cluster as two separate decisions.

---

## Module details

### Module 1 — Performance & App Audit (15/25 available, 60%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| PL-D01 | Mobile app category audit | WARN | 3/5 | **0 of 140 app categories excluded at account level.** But app spend is **€0.00 of €2,918.66 (0.0%) with 0 conversions**, so there is no current waste. The gap is exposure-side: PMax serves 3,301 mobile-application placements uncovered. Mitigating: 139 app categories already sit inside the shared list — the content exists, the placement is wrong |
| PL-D02 | Display placement performance | **SKIP** | —/10 | **No Display placements exist.** Every DISPLAY campaign is removed or paused; the entire placement dataset is YOUTUBE_CHANNEL. Nothing to evaluate — 10 points removed from the denominator |
| PL-D03 | Video placement quality | WARN | 9/15 | 448 CTR anomalies, 47 kids-content, 60 spam, 40 passive-music, 3 zero-click flags — **€2,918.66 spend, 0 conversions, CTR 0.15%** across 90 days. All in `Video View DRAFT`, **status PAUSED**. Real findings with zero live exposure; not a FAIL because nothing serves, not a PASS because the campaign is only paused and a Video rebuild is underway |
| PL-D04 | Known-bad domains | WARN | 3/5 | 996 PMAX_BAD_DOMAIN flags — **all at €0.00**, impression exposure only. Plus 2 BRAND_UNSAFE and 3 KIDS_CONTENT confirmed by content review in the paused video campaign |

### Module 2 — Brand Safety & Coverage (6/20, 30%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| PL-D05 | Exclusion list coverage | **FAIL** | **0/10** | **0 of 7 serving campaigns covered.** 38,208-member list attached to 3 dead campaigns. See Critical issue 1 |
| PL-D06 | Brand safety configuration | WARN | 3/5 | Account-level content label exclusions: **1** (`PARKED_DOMAIN`). Campaign-level brand safety settings: **0 rows**. Google exposes several further content labels (tragedy and conflict, sensitive social issues, profanity, sexually suggestive, among others), none of which is excluded. *Judgement note: for a deliberately edgy brand, some labels are legitimately worth allowing — this needs a deliberate decision rather than a blanket sweep* |
| PL-D07 | PMax placement review | WARN | 3/5 | 20,395 placements, 3,011,823 impressions, **€0.00 attributed cost**, zero exclusion coverage. 996 bad-domain pattern hits. Impression exposure without vetting |

### Module 3 — Hygiene & Monitoring (1.8/3 available, 60%)

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| PL-D08 | Demand Gen channel controls | **SKIP** | —/15 | **Every Demand Gen campaign is paused** — 9 of them, all at €0 spend. Nothing to score. ⚠️ This is temporary: the changelog shows an active rebuild. 15 points removed from the denominator |
| PL-D09 | Exclusion list hygiene | WARN | 1.8/3 | 1 list, 38,208 members, **0 cross-list overlaps** — the contents are clean and well-maintained. The fault is linkage (`reference_count = 3`, all to dead campaigns), which PL-D05 owns |
| PL-D10 | Top placement spot-check | **INFO** | — | 300 placements reviewed, 36 flagged (12%). Carries no points by design. Findings summarised above |

---

## Recommended actions

Peer reports were checked. All are fresh from today and quoted rather than re-run.

### Act now — free, and the window is closing

1. **Promote the shared list's contents to account-level exclusions.** 24,553 mobile applications, 7,759 YouTube channels, 5,757 placements and 139 app categories already exist inside `BROAD Ausschlüsse + Konkurrenz`. Account-level exclusions apply to Performance Max, which shared placement lists do not. → `/placement-optimizer lists` then `/placement-optimizer apps`
2. **Do it before the Demand Gen rebuild launches.** 113 editor changes on 5 August and 38 on 6 August are concentrated on paused Demand Gen and Video campaigns. → **Jonas**, timing decision
3. **Decide the content-label policy deliberately.** Only parked domains are excluded today. For an intentionally dark brand, a blanket sweep would be wrong — but one label out of many is unlikely to be the considered position either. → `/placement-optimizer safety`

### Investigate

4. **Split the music-channel decision.** Exclude VEVO and auto-generated "Topic" channels; **keep** KoRn, Judas Priest and Electric Callboy, whose audiences are the target market. → manual, before any Video relaunch
5. **Decide `Video View DRAFT`'s fate.** It is paused, not removed, and it is the source of every flag in this audit — €2,918.66 for zero conversions over 90 days. Removing it eliminates the risk of an accidental restart. → **Jonas**

### Peer context — no re-runs needed

6. **Review the existing 2026-08-06 PMax audit** at `context/analysis/pmax/pmax-audit.md` — top finding: *"five enabled PMax campaigns are BFCM-2025 shells with every asset group paused."* Its channel-allocation module measured the live PMax mix at **98.8% Shopping-share**, with CONTENT at 12.2% and YouTube at €3.72 — which is why placement exposure is high on impressions and near-zero on cost.
7. **Review the existing 2026-08-06 budget audit** at `context/analysis/budget/budget-audit.md` — 47/100, top finding: *projected August spend of €78–93k against a €32,500 target.* Relevant here as a caution: any Demand Gen relaunch adds spend to an account already running well over plan.
8. **Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100. Its measurement finding caps how far any placement conversion figure can be trusted; note that **all 65 view-through conversion rows in this audit resolved to secondary conversion actions, none to `purchase_gads_mable`**.
9. **Run `/tracking-specialist`** — before Demand Gen restarts, `YouTube follow-on views` must be removed as a primary conversion action. business.md §7: *"harmless at €0 video spend; will corrupt bidding signal the moment Video or Demand Gen restarts."*

---

## Data summary

| Source | Rows | Note |
|---|---|---|
| `placement/placement-performance.csv` | 63,904 | 90-day group view |
| `placement/placement-detail.csv` | 176,217 | Video granularity |
| `placement/pmax-placements.csv` | 20,395 | €0.00 cost attribution by design |
| `placement/placement-vtc-by-action.csv` | 65 | **All 65 resolved to secondary actions — 0 primary** |
| `placement/exclusion-list-items.csv` | 38,208 | The list in question |
| `placement/exclusion-lists.csv` | 1 | `BROAD Ausschlüsse + Konkurrenz` |
| `placement/exclusion-list-links.csv` | 3 | All to dead campaigns |
| `placement/account-exclusions-apps.csv` | **0** | — |
| `placement/account-exclusions-placements.csv` | **0** | — |
| `placement/account-exclusions-labels.csv` | 1 | `PARKED_DOMAIN` |
| `placement/campaign-brand-safety.csv` | **0** | No campaign-level settings |
| `evidence/placement-flags.csv` | 1,793 | €117.73 total flagged spend |
| `evidence/placement-content-flags.csv` | 36 | From 300 reviewed |

⚠️ **Two measurement caveats.** The performance script logged *"placement-vtc-primary.csv not found — falling back to raw view_through_conversions"* even though the file was written with zero rows; since every VTC row resolved to a secondary action, any view-through credit in the flags is on secondary conversions, not purchases. And PMax placement cost is **structurally €0.00** — absence of attributed spend is not evidence of absence of cost.
