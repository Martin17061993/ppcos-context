# PMax Audit — 2026-08-06

**Run:** full · all applicable modules per campaign
**Window:** 60 days (2026-06-07 → 2026-08-06) · **Active Roster:** 7 of 12 campaigns scored · 5 excluded as dormant · 0 experiments
**Vertical:** ecommerce (from business.md) · **Setup split:** 2 Feed-Only / 5 Full Assets
**Account:** 3599116618 (Stay Cold Apparel) · EUR · 24,703 evidence rows

> ⚠️ **Read the scores with the serving column next to them.** The mechanical scorer returned 94–97/100 ("strong") for all seven campaigns. For five of them that number is measuring the configuration quality of campaigns **that cannot serve at all**. See "Where the scorer is blind" below before quoting any figure from this report.

---

## Executive read

The scorer says this is a strong PMax setup. On the two campaigns that actually run, it is right — feed integration is clean, brand exclusion is on, URL expansion is off, and channel allocation sits inside the expected ecommerce range. On the other five it is measuring an empty room.

**The headline finding closes a question three earlier audits left open.** The five enabled PMax campaigns that have served zero impressions for 30 days do so because **every one of their asset groups is paused** — 14, 9, 7, 9 and 13 asset groups respectively, without a single enabled one between them. A Performance Max campaign whose asset groups are all paused cannot serve, regardless of budget, bid strategy or feed health. This also corrects the hypothesis I put in the feed note earlier today: the listing groups are *not* missing (98–122 filter rows per campaign, all feed-connected), so this was never a product-coverage problem. It is five enabled shells with the lights switched off.

**Their asset group names say when it happened.** "BFCM I", "BFCM II (342H)", "Black Week", "Black Weekend", "BFCM'25 RoB Purple CP MIXED", "Grey Dye", "Intra Day 342" — these are Black Friday 2025 and Reign-of-Blood drop assets, paused when those promos ended and never cleaned up. The campaigns have been sitting enabled ever since, holding €359/day of budget allocation that cannot be spent and distorting every allocation figure in the account.

**Two things to act on this week.** First, decide per campaign: enable one asset group or pause the campaign. Leaving them enabled-but-empty is the only genuinely wrong option, and it is the current state. Second, before anything gets re-enabled, clear the **104 policy-restricted assets** sitting in those five campaigns — 61 are still live and 24 are live *disapproved*, concentrated in `WW PROSPECTING BROAD` (17 live disapproved) and `SCALING I BROAD` (7). They cause no harm while nothing serves; they become an immediate problem the moment someone flips a switch. The account changelog shows a Demand Gen and Video rebuild underway right now, which makes that switch-flip plausible within days.

**Two open questions from earlier audits are now answered.** Brand exclusion is **ON across all seven campaigns** (one negative BRAND_LIST criterion, shared set `10982324974`) — the account audit's AUD-D02 could not verify PMax brand separation and rated it WARN; the setting is active. And URL expansion returned **zero rows** for every campaign, so the account audit's AUD-D19 concern that the €10,900/month campaign might be running default-ON expansion is unfounded — it is off.

Read the serving-adjusted scorecard, then the two blind spots. The per-module tables are reference.

---

## Serving-adjusted scorecard

| Campaign | Setup | Mech. score | **Serving** | **Real verdict** |
|---|---|---|---|---|
| `EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING` | feed-only | **96/100** | €10,873 · 4.06M impr | ✅ **Genuinely healthy setup.** The score means what it says |
| `EX I WW I PMAX … OVER-INDEX + INDEX + NEAR-INDEX` | feed-only | **94/100** | €399 · 489k impr | ⚠️ Setup fine, but reaches only **13 products** — starved by its listing group, not by configuration |
| `EX I WW I PMAX I SCALING I BROAD` | full | 97/100 | **0** | ❌ **Non-serving.** 14/14 asset groups PAUSED |
| `EX I SKANDI I PMAX I TESTING I PROSPECTING` | full | 97/100 | **0** | ❌ **Non-serving.** 9/9 asset groups PAUSED |
| `EX I FRA I PMAX I TESTING I BROAD` | full | 97/100 | **0** | ❌ **Non-serving.** 7/7 asset groups PAUSED |
| `EX I USA I PMAX I TESTING I BROAD` | full | 96/100 | **0** | ❌ **Non-serving.** 9/9 asset groups PAUSED |
| `EX I WW I PMAX I PROSPECTING I BROAD` | full | 95/100 | **0** | ❌ **Non-serving.** 13/13 asset groups PAUSED |

Only the top two rows describe a running campaign. The bottom five describe well-formed campaigns that are switched off at the asset-group level while switched on at the campaign level.

---

## Where the scorer is blind — and why I am not restating its numbers as health

This matters more than any individual module result, so it gets its own section rather than a footnote.

**The `asset-groups` module scored `SCALING I BROAD` 100/100** while all 14 of its asset groups carry `status = PAUSED`, `primary_status = PAUSED`, `primary_status_reasons = ASSET_GROUP_PAUSED`. Its own output reads *"14 eligible asset group(s)… 0 zero-impression (serving)"* — it counted paused groups as eligible and then found no zero-impression *serving* groups because nothing was serving to begin with.

Meanwhile the three modules that would have caught the problem all returned **n/a**:

| Module | Returned | Why |
|---|---|---|
| `asset-performance` | n/a | *"No live asset cleared the 100-impression floor"* — because nothing served |
| `channel-allocation` | n/a | *"No channel rows… it had no spend/serving"* |
| `url-expansion` | 100 | *"No expansion rows — OFF or did not serve"* — scored as intentional-off |

So the absence of serving was interpreted three times as "not applicable" and never once as "broken." Configuration modules passed, evidence modules abstained, and the campaign came out at 97.

I have **not** rewritten the mechanical scores — they are the skill's deterministic output and overwriting them would hide the issue rather than surface it. Instead every score above carries its serving status next to it, and the five non-serving campaigns are excluded from any positive claim about account health.

---

## The five non-serving campaigns — full evidence

| Campaign | Asset groups | Enabled | Listing-group rows | Feed-connected |
|---|---|---|---|---|
| `SCALING I BROAD` | 14 | **0** | 122 | 14/14 |
| `WW PROSPECTING BROAD` | 13 | **0** | 113 | 13/13 |
| `SKANDI TESTING PROSPECTING` | 9 | **0** | 119 | 9/9 |
| `USA TESTING BROAD` | 9 | **0** | 98 | 9/9 |
| `FRA TESTING BROAD` | 7 | **0** | 105 | 7/7 |

Every asset group reports `ASSET_GROUP_PAUSED`. Product targeting is intact everywhere — this is not a feed or listing-group failure.

**Sample asset group names** (`SCALING I BROAD`): *EX I BROAD ASSETS I ALL PRODUCTS · Asset-Gruppe 1 · EX Video Rotation II · EX I NEW VID + STATIC ROTATION · Black Week · BROAD I ALL P I AI CREATIVES TESTING · Best performing + Vid Testing · BFCM I · BFCM II (342H) · INTRA DAY 342 · BFCM'25 RoB Purple CP MIXED · BFCM '25 - Special Drops #2 Beige · RoB Grey Dye CP · Grey Dye*

Eleven of fourteen are seasonal: Black Week, BFCM 2025, the Reign-of-Blood drop, an intra-day offer. The pattern repeats across all five campaigns. These were paused when the promos ended and the campaigns were never turned off with them.

### Cross-audit reconciliation

| Audit | What it said | Now resolved |
|---|---|---|
| Account (AUD-D08) | "5 enabled PMax campaigns, 0 impressions, cause unknown — check asset groups, then feed" | ✅ **Asset groups. All paused.** |
| Budget (BUD-D16) | "5 active campaigns with zero spend — likely policy/approval/targeting block" | ✅ Not policy, not approval, not targeting — paused asset groups |
| Bidding (BID-D01/D03) | "7 campaigns below the smart-bidding volume floor" | ✅ 5 of those 7 are these shells. Structural, not a bidding decision |
| Feed note (mine, today) | "Likely no asset group with a populated listing group" | ❌ **Wrong on mechanism.** Listing groups are populated and feed-connected; the asset groups are paused |

---

## Policy-restricted assets — a dormant landmine

| Campaign | Total restricted | Live | **Live & disapproved** |
|---|---|---|---|
| `WW PROSPECTING BROAD` | 20 | 18 | **17** |
| `SCALING I BROAD` | 50 | 11 | **7** |
| `USA TESTING BROAD` | 18 | 18 | 0 |
| `SKANDI TESTING PROSPECTING` | 13 | 11 | 0 |
| `FRA TESTING BROAD` | 3 | 3 | 0 |
| `OVER-INDEX` (live) | **0** | — | — |
| `FEED ONLY PROSPECTING` (live) | **0** | — | — |
| **Total** | **104** | **61** | **24** |

The two campaigns that actually serve are completely clean. All 104 restricted assets sit in the five dormant shells, so **nothing is being harmed today**.

The risk is sequencing. The account changelog records 113 Google Ads Editor changes on 2026-08-05 and 38 more on 2026-08-06, concentrated on paused Demand Gen and Video campaigns — a creative rebuild is in progress. If any of these five PMax shells is re-enabled as part of that work, 24 disapproved assets go live with it. **Clear them before, not after.**

*Note: compliance routing (`/compliance-guardian`) is not yet built. Until it is, review these in the Google Ads UI under each asset group's policy status.*

---

## Module results

### feed-integration — 100/100 on all 7 (weight 20)

Every asset group across every campaign is feed-connected and carries listing-group filters. No group serves zero products by exclusion.

**Advisory, not scored:** 6 asset groups in `SCALING I BROAD` exclude the root catch-all (`BFCM II (342H)`, `INTRA DAY 342`, `BFCM'25 RoB Purple CP MIXED`, and others). That is a deliberate pattern for promo-scoped groups and appropriate for what those groups were.

**Feed quality is explicitly out of scope here and was not re-derived.** A canonical `/feed-auditor` report does not exist — today's attempt was **blocked at the Merchant API preflight** (`context/analysis/feed/feed-preflight-blocked.md`, OAuth lacks Merchant scopes). What that note *did* establish from Ads-side data is directly relevant and worth carrying: **zero of 1,817 products are fully eligible** (45% serve restricted, 55% cannot serve), with colour missing on 55% and age-group/gender on 37%. That is a live constraint on the two serving campaigns even though feed *connection* scores 100.

### asset-groups — 95–100 on the 5 full-assets campaigns · n/a on the 2 feed-only (weight 18)

Composition is genuinely good where it was measured: all groups meet ecom minimums (3 headlines, 1 long headline, 2 descriptions, 1 marketing image, 1 square image), all carry the recommended portrait image and YouTube video, none is generically named apart from one "Asset-Gruppe 1", and auto-generated creative sits at 4% of live creative (585 live assets) — well inside the norm.

**But see "Where the scorer is blind."** These scores describe paused groups. Treat them as "the creative that exists is well-formed," not "the campaign is healthy."

### brand-defense — 95–100 on all 7 (weight 15)

**Brand exclusion is ON for every campaign** — one negative `ENABLED` BRAND_LIST criterion pointing at shared set `10982324974`, corroborated by `brand_guidelines_enabled = true`.

This is a direct upgrade to an open finding: the account audit rated **AUD-D02 (brand/non-brand separation) as WARN** specifically because PMax brand separation could not be verified without served search-term data. The exclusion *setting* is now confirmed active across all seven PMax campaigns. That is strong evidence, not proof — the setting being on does not prove zero brand queries were served. `/search-term-auditor` (ST-D25) still owns the served-query question, and no such report exists yet.

Disapproved-asset detail is in the section above.

### nca-lifecycle — 80–85 "watch" on all 7 (weight 12)

**Resolved from business.md without asking** (Phase 0.5 ladder, step 1): NCA is deliberate. business.md §7 records account-level new-customer acquisition activated 2026-02-18 with a +€16.46 value bonus, re-included at campaign level 2026-03-13, and verified still active 2026-08-03 — described there as "deliberate strategy, not a bug." No writeback was needed; nothing new was learned.

**PMX-D22 value-premium check: SKIPPED, not scored 0.** New-vs-existing LTV is genuinely unavailable — business.md Gap G2 (High) states it plainly: *"Account bids for new customers with a +€16.46 value bonus that nothing currently validates."* Per the ladder's step 4 this routes to `/strategy-specialist`, and the 80–85 band is provisional as a result.

**One finding the modules don't surface: the NCA mode is inconsistent across campaigns.**

| Mode | Campaigns |
|---|---|
| `TARGET_NEW_CUSTOMER` (bid **only** for new customers) | FEED ONLY PROSPECTING, OVER-INDEX, WW PROSPECTING BROAD, FRA TESTING |
| `BID_HIGHER_FOR_NEW_CUSTOMER` (premium, still serves existing) | SCALING I BROAD, SKANDI TESTING, USA TESTING |
| `TARGET_ALL_EQUALLY` | SCALING I RE/HOT *(dormant)* |

Three different stances in one account. Both live spenders run the most aggressive setting — `TARGET_NEW_CUSTOMER` excludes existing customers from PMax entirely. business.md describes the account-level intent as "bid for new customers only," so the two live campaigns match intent; the three `BID_HIGHER` shells do not. Worth a deliberate decision rather than inheritance, especially before any of them is re-enabled.

### audience-signals — 92–100 on the 5 full-assets campaigns · n/a on feed-only (weight 10)

Signal quality is strong: 12 of 14 groups in `SCALING I BROAD` use first-party lists (purchaser / cart / visitor), 1 uses a custom segment, none is broad-only. All 7 serving first-party lists clear their size floors. 72 of 72 signal rows resolved against the audience resource.

One gap: `EX I BROAD ASSETS I ALL PRODUCTS` has **no audience signal and no search theme** — PMax has no steer for it. Immaterial while paused; fix before re-enabling.

*Customer-match upload freshness was SKIPPED — no upload-recency field is selectable in API v24.1 (probed live), so it cannot be judged.*

### channel-allocation — 100 and 87 on the 2 serving campaigns · n/a on the 5 dormant (weight 8)

Account-wide PMax network mix over 60 days:

| Network | Serving | Cost | Share | Conv | Value |
|---|---|---|---|---|---|
| SEARCH | feed/Shopping | €27,893 | **86.3%** | 626.0 | €94,415 |
| CONTENT | feed/Shopping | €3,938 | 12.2% | 127.0 | €20,743 |
| GMAIL | text/non-feed | €345 | 1.1% | 15.0 | €2,146 |
| GMAIL | feed/Shopping | €108 | 0.3% | 5.0 | €704 |
| CONTENT | text/non-feed | €48 | 0.1% | 0.8 | €118 |
| YOUTUBE | feed/Shopping | €3.72 | 0.01% | **0** | €0 |

Shopping-share is 98.8% of spend. For a Feed-Only ecommerce PMax that is the expected shape, and channel skew is a **symptom routed upstream**, not a PMax-side lever — there is no control to change it. `OVER-INDEX` scores 87 rather than 100 on mix, consistent with its tiny 13-product reach.

The audit window starts 2026-06-07, after the 2025-06-01 channel data floor, so channel evidence is complete.

### url-expansion — 100/100 on all 7 (weight 5)

`final_url_expansion_asset_view` returned **0 rows** for every campaign across 60 days. URL expansion is off, or served nothing.

**This resolves an open account-audit concern.** AUD-D19 flagged that the €10,900/month `FEED ONLY PROSPECTING` campaign carried no explicit URL-expansion setting and that PMax defaults to ON — while stating the reading was inferred rather than confirmed. Over a 60-day window a campaign spending €10,873 would produce expansion rows if expansion were on and serving. It is off. **AUD-D19's PMax half is a false alarm; its `TEXT_ASSET_AUTOMATION` half on the USA brand Search campaign stands unchanged.**

### conversion-signal — n/a on all 7 (weight 18)

Lead-gen only by design. Every campaign classified ecommerce, so this module is excluded from the denominator (never scored 0). One paused campaign, `PMAX I NC DEALS PUSH I SPLIT`, classified `leadgen (?)` on conflicting evidence — it is dormant and outside the Active Roster, and business.md is unambiguous that this account has *"no lead gen, no subscription."* Resolved as ecommerce; no user question required.

### asset-performance — n/a on all 7 (weight 12)

No live asset cleared the 100-impression floor. On the five dormant campaigns that is because nothing served. On the two Feed-Only campaigns it is by design — serving runs through the feed, where individual creative assets do not accumulate impressions.

**Consequence worth stating:** creative quality in this account is currently **unmeasured**. 585 live creative assets exist in the dormant campaigns and none has performance data. If the rebuild proceeds, there is no historical asset-level signal to select from.

---

## Top hypothesis

- **Layer:** Structural (above the module cascade — it invalidates the modules rather than sitting inside them)
- **Name:** Five enabled PMax campaigns are BFCM-2025 shells with every asset group paused
- **Confidence:** **high** — direct API evidence, no inference
- **Evidence:** 52 asset groups across 5 campaigns, 0 enabled. All carry `ASSET_GROUP_PAUSED`. Listing groups intact (98–122 rows each, all feed-connected). Asset-group names are Black Week / BFCM '25 / Reign-of-Blood drop assets. Zero impressions across the full 60-day window.
- **Blocks downstream:** yes — `asset-performance` and `channel-allocation` cannot be judged on these campaigns until something serves, and the 94–97 mechanical scores must not be read as health.

---

## Sequenced handoffs

Peer reports were checked per Phase 2.5. Four are fresh and quoted inline rather than re-run.

1. **Decide per campaign: enable one asset group, or pause the campaign.** Five campaigns, ~2 minutes each in the UI. Leaving them enabled-but-empty is the only wrong answer and it is the status quo. → **Jonas** (Martin has no execution mandate; `/pmax-optimizer` exists but every change here is a human judgement about intent, not a mechanical fix)
2. **Clear 24 live-disapproved assets before anything is re-enabled** — 17 in `WW PROSPECTING BROAD`, 7 in `SCALING I BROAD`. Time-sensitive given the creative rebuild visible in the changelog. → Google Ads UI (compliance-guardian not yet built)
3. **Review the existing 2026-08-06 budget audit** at `context/analysis/budget/budget-audit.md` — 47/100, top finding: *projected August spend of €78–93k against a €32,500 target*. Its BUD-D16 zero-spend finding is fully explained by this audit; the €359/day these five hold should be released as part of the decision in step 1. **No re-run needed.**
4. **Review the existing 2026-08-06 account audit** at `context/analysis/account/account-audit.md` — 75%, Good. Two of its findings are updated here: **AUD-D08 is now root-caused**, and **AUD-D19's PMax half is a false alarm** (URL expansion is off). Its AUD-D02 WARN is substantially improved by brand exclusion being ON, though not fully closed. **No re-run needed.**
5. **Review the existing 2026-08-06 competitive audit** at `context/analysis/competitive/competitive-audit.md` — 73/100, top finding: *landing page experience is BELOW_AVERAGE on 6 of 6 scored non-brand keywords*. Relevant here because the same site backs every PMax asset group's final URL. **No re-run needed.**
6. **Run `/merchant-auth "Stay Cold Apparel"`, then `/feed-auditor full`** — feed *quality* is out of scope for this audit and the canonical feed report does not exist. The Ads-side evidence already shows zero of 1,817 products fully eligible, which constrains the two serving PMax campaigns directly. Merchant account `116274940` is already saved in config; the blocker is a two-minute browser sign-in.
7. **Run `/search-term-auditor`** — the only remaining way to close AUD-D02 properly. Brand exclusion being ON is strong evidence; ST-D25 measures what was actually served.
8. **Run `/strategy-specialist`** — owns the unresolved NCA question: the +€16.46 new-customer premium that Gap G2 says nothing validates, plus the three-way NCA mode inconsistency.

---

## Methodology

- **Excluded from scoring and narrative:** 5 dormant campaigns (paused with 0 impressions in the window) — `SCALING I RE/HOT`, `ESP TESTING BROAD`, `WW PROSPECTING RoB`, `SMART VS ST SHOPPING TOF I HOODIE TEST`, `PMAX I NC DEALS PUSH I SPLIT`. Pulled and listed in the inventory for completeness. 0 experiment arms excluded (none exist).
- **Non-applicable modules are `null`, never 0.** Feed-Only campaigns exclude asset-groups, asset-performance, audience-signals and conversion-signal; all ecommerce campaigns exclude conversion-signal. Denominators renormalize per campaign (Σ weights 80 for full-assets, 60 for feed-only).
- **Learning status:** all 7 stable. `account-changelog.md` was present (pulled earlier today) and shows no PMax bid-strategy or budget change inside the learning window.
- **No prior `pmax-decisions.json`** — nothing to re-confirm.
- Classification questions were resolved from business.md rather than asked, per the ladder: vertical = ecommerce (unambiguous), NCA intent = ON/deliberate (§7), LTV = unavailable → SKIP (Gap G2).

### Data freshness

| Source | Rows | Status |
|---|---|---|
| `pmax/` (22 queries) | 24,703 | Pulled fresh 2026-08-06, 60-day window |
| `campaign-inventory.{md,json}` | 12 campaigns | Generated 2026-08-06 |
| `module-scores/` | 7 campaigns × 9 modules | Generated 2026-08-06 |
| `{module}-flags.json` | 8 files | Written for `/pmax-optimizer` |
| `account-changelog.md` | 67 + 266 changes | Pulled 2026-08-06 |
