# Business Context — Stay Cold Apparel

*Last updated: 2026-08-03 · Currency: **EUR** · Google Ads customer 359-911-6618 · MCC 5591362086*

> **What this file is.** The context book for this account. It links the past (two years of measured change history), the present (current performance and economics), and the future (goals, calendar, risks). Every downstream skill reads this before acting. Numbers carry a confidence label; assumptions are labelled `[ASSUMPTION]`; unknowns live in **Gaps & Open Questions** at the end — never silently omitted.
>
> **Sources:** Google Ads API pull 2026-08-03 (window 2026-07-04 → 2026-08-02) · targeted API query on conversion-action segmentation 2026-08-03 · Airtable Product Catalogue / Order Base / Return Controlling / Drop Base (read 2026-08-03) · Notion Cheat Sheets (read 2026-08-03) · Slack public channels (read 2026-08-03) · change-impact analysis 2024–2026 (cutoff 2026-07-03) · `context/brand.md` · `context/pre-knowledgebase-nodes/`

---

## READ THIS FIRST — five things that change every decision

1. **Never steer on the reported account ROAS.** Since 2025-11-10 the account counts `purchase_gads_mable` **and** `Custom NewCustomerPurchase - Stay Cold Mable`. Verified 2026-08-03: reported €382,976 vs. real purchase €255,105 = **inflation ×1.50 account-wide, but ×1.28–1.94 per campaign**. Always use the purchase-only ("clean") series.
2. **Break-even clean ROAS is ~1.9.** Derived from a 75 % gross margin and a ~5 % return rate (both now sourced from Stay Cold's own systems). Anything below 1.9 destroys contribution margin.
3. **Two thirds of current spend produces roughly zero contribution.** Shopping FOKUSPRODUKTE (clean 1.73) and PMax PROSPECTING (clean 1.96) are 67 % of spend at a combined clean ROAS of 1.85 — below break-even. This is not a strategy; it is an arithmetic side-effect of setting tROAS targets in the inflated currency (see §6).
4. **We do not execute. We propose.** Martin has no execution mandate on this account; Jonas Makki makes all changes. Every skill output is a proposal for a human, never an action. Approval latency is unknown → **Gap G12**.
5. **The four brand search campaigns are do-not-touch.** 11.5 % of spend, 77 % of tracked purchase value. Measured swings from tiny interventions range −32 % to +396 %.

---

## 1. Business Model

- **Company:** Stay Cold Apparel (legal entity MASCANI GmbH), Berlin, founded 2015, no outside investors.
- **Model:** D2C e-commerce (Shopify Plus, `staycoldapparel.com`), heavyweight apparel for metal / tattoo / hardcore / dark-streetwear culture. Sells worldwide, EUR default, 90+ currencies, ships from a German warehouse.
- **Revenue:** ~€10M in 2024 (last documented figure). **2025 actual and 2026 target are not documented anywhere** → **Gap G3 (Critical)**.
- **Merchandising rhythm:** "Drops, not seasons." Weekly Friday drops ("Thunder Drop Weeks", ~1 week), daily drops (1 day), restocks, named collections. Catalogue: 495 products / 2,549 SKUs / 280 designs / 26 artists / 37 categories.
- **Strategic direction (Notion, Product + Offer Cheat Sheet):** "Growth. Scaling. International markets. **Higher prices. Fewer products.**" — explicitly not a sell-out/volume strategy.
- **Secondary revenue:** Wholesale (passive channel, `is_b2b_order` in Shopify). **Excluded from all revenue reporting — keep Google Ads discussions consistent with that.**
- **What Google Ads sells:** direct product purchases. No lead gen, no subscription.

### Markets

| Market | Role |
|---|---|
| DE / DACH | Home market, fastest shipping (2–3 days), strongest brand demand |
| USA | Growth market. Delivery 10–14 days. Brand IS lowest here (84 %) — the account's cheapest open opportunity |
| FRA | Strong brand efficiency (clean ROAS 88) |
| SKANDI | Smaller, weakest brand efficiency of the four (clean ROAS 26) |
| WW-EN | Catch-all for PMax/Shopping prospecting |

Community also strong in Japan (organic, not an ads market).

---

## 2. Unit Economics

| Input | Value | Confidence | Source |
|---|---|---|---|
| **Gross margin** | **~75 %** | **High** | Airtable `Function: Price Recommender` → "Buying price x4" on `Default Buying Price DDP incl. VAT`. A ×4 markup is mathematically exactly 75 % gross margin; VAT cancels out. |
| **Return rate** | **~4.6–5.1 %** (use **5 %**) | **Medium** | Airtable Return Controlling `apppNMIKbDaGtGHrD`, Weekly Snapshots 2026-07-20 (4.61 %) and 2026-07-27 (5.07 %). Trailing 60d, unit-based, B2B-excluded. |
| Payment fees | 2 % of gross | `[ASSUMPTION]` | → Gap G8 |
| Outbound shipping | €6 / order blended | `[ASSUMPTION]` | → Gap G8 |
| **AOV (as tracked by Google)** | **~€143** | **Medium** | Derived 2026-08-03: clean conversion value €255,105 ÷ clean conversions 1,788.53. Per-campaign range €124 (DE brand) – €181 (USA brand, Search TOF). Probably VAT-inclusive — unverified. |
| AOV (true, Shopify, B2B-excluded) | not available | — | → **Gap G1**. Needed as a cross-check and to settle gross-vs-net. |
| Repeat purchase rate / CLV | **Not available** | — | → **Gap G2 (High)**. Account bids for new customers with a +€16.46 value bonus that nothing currently validates. |

### Two corrections to prior documentation

- **The "0.6 % return rate" carried in the Notion KB is wrong.** It comes from the first Return Controlling snapshot (2026-07-18), which shows 25,395 units / 162 returns — while the run two days later shows 51,278 units / 2,364 returns. Units do not double in 48 hours; the first pull was incomplete. The two subsequent runs agree at ~5 %. Annotated at source in `context/pre-knowledgebase-nodes/01-notion-kb/Stay Cold - Produkte & Drops.md` on 2026-08-03. **Stay Cold's own Notion still carries the wrong figure — worth telling Jonas, since their Return-Rate Report feeds product decisions.**
- **Do not compute margin from raw PO buying prices.** Those (€10.70 median hoodie, `PO_Product.Buying Price per item (excl. VAT)`) exclude freight and duty and imply an implausible 78–89 % margin. The ×4 rule is based on **DDP incl. VAT** — landed cost — and yields the defensible 75 %.

### Break-even calculation

Per average tracked order of **€143**, assuming Google receives VAT-inclusive order values:

| Line | Amount |
|---|---|
| Tracked revenue (1 order) | €143.00 |
| VAT (19 %) | −€22.83 |
| COGS (25 % of net) | −€30.04 |
| Returns (5 %, net of recovered COGS/VAT + handling) | −€5.51 |
| Payment fees (2 %) | −€2.86 |
| Outbound shipping | −€6.00 |
| **Contribution before media** | **€75.76 = 53 % of tracked revenue** |

> ### Break-even clean ROAS ≈ **1.9**
> **~1.6** if Google receives net (ex-VAT) values instead of gross. This is a factor of 1.19 on the most important threshold in the account and is **not yet verified** → **Gap G1**. Use **1.9** (conservative) until resolved.

*Robustness: the same calculation run at a €119 order value also yields 1.9 (52 % contribution). The threshold is insensitive to AOV within the plausible range — it is driven by margin, VAT and returns. The gross-vs-net question is the only input that moves it materially.*

**Contribution per €1 of media at various clean ROAS levels:**

| Clean ROAS | Contribution per €1 spent |
|---|---|
| 1.73 (FOKUSPRODUKTE today) | **−€0.10** |
| 1.96 (PROSPECTING today) | **+€0.02** |
| 2.14 (all non-brand today) | +€0.11 |
| 2.50 | +€0.30 |
| 3.00 | +€0.56 |
| 8.26 (account today) | +€3.30 |
| 0.63 (June 2026 marginal) | **−€0.67** |

The June 2026 over-scaling was buying revenue at a **67-cent loss per marginal euro**. That is the price of steering on the reported number.

---

## 3. Business Goals & Performance Targets

> ⚠️ **No client-set goals exist.** Notion contains no 2026 revenue target, no H2 plan, and Google is still not defined as a channel (see §11). The targets below are **provisional, derived from unit economics, and require Jonas's sign-off** → **Gaps G3, G4, G5 (all Critical)**. Do not treat them as agreed.

**Primary KPI:** clean ROAS (purchase-only series)
**Mode:** **Cost Control**, transitioning to Balanced once non-brand clears its floor
*Rationale: 67 % of spend sits at or below break-even. Efficiency must be restored before any volume growth is defensible.*

### Provisional targets `[ASSUMPTION — needs Jonas confirmation]`

| Metric | Floor (hard) | Target | Basis |
|---|---|---|---|
| Account clean ROAS | 4.0 | **6.0** | 6.16 was the 90-day account anchor at 2026-07-03; 8.26 achieved now |
| **Non-brand clean ROAS** | **1.9** (break-even) | **2.5** | 2.5 yields +€0.30 contribution per media euro, enough to carry overhead |
| Brand clean ROAS | no floor | maintain | structural; harvests existing demand |
| Brand impression share | 90 % | **95–99 %** | gap is rank-lost, not budget-lost — fixable via bids/quality |
| Monthly spend | — | **€30–35k** while non-brand is under 2.5 | current level; re-scaling is conditional, not scheduled |

### Feasibility check (performed 2026-08-03, per domain rule 3)

- **Achievable:** non-brand clean 2.5 from today's 2.14 — the lever is target calibration, not new demand. Requires no budget increase.
- **Achievable:** brand IS 95–99 % — precedent exists (USA package 2026-03-13 measured +261 %).
- **NOT achievable simultaneously:** "grow spend" and "restore non-brand efficiency." Every measured attempt to scale non-brand past its saturation point in this account produced negative results (0 of 6 budget increases above +90 % were positive). If Jonas wants growth, it must come from brand IS, market expansion, and feed/structure work — not from raising budgets on the two saturated campaigns.

---

## 4. Current State vs Target

**Window: 2026-07-04 → 2026-08-02 (30 days)**

| Metric | Current | Target | Gap |
|---|---|---|---|
| Spend | €30,875 | €30–35k | ✅ in range |
| **Clean ROAS** | **8.26** | 6.0 | ✅ +38 % |
| Reported ROAS | 12.40 | — | (ignore — inflated ×1.50) |
| **Non-brand clean ROAS** | **2.14** | 2.5 | ❌ **−14 %** |
| Brand clean ROAS | 55.6 | maintain | ✅ |
| Brand IS (weakest = USA) | 84.4 % | 95–99 % | ❌ −11 pp |
| Clicks / Avg CPC | 42,145 / €0.73 | — | — |
| Conversion rate | 6.43 % (reported basis) | — | — |

**Recovery from the June saturation is real:** spend halved from €61,961 (June) and clean ROAS rose from 5.04 → 8.26. The account is back at its historical "efficiency plateau" level (9–14, Nov 2024 – Oct 2025).

**But the recovery is uneven.** The account average is carried by brand. The two campaigns holding 67 % of spend did not recover.

---

## 5. Account Structure — campaign roles and current economics

| Campaign | Type | Cost | Clean ROAS | vs BE 1.9 | Role |
|---|---|---|---|---|---|
| `EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING` | PMax | €10,900 | **1.96** | ⚠️ zero | Main prospecting engine |
| `EX I SHOPPING I FOKUSPRODUKTE` | Shopping | €9,908 | **1.73** | ❌ −€0.10/€ | Flagship spender, saturation-limited |
| `EX I EN I WW I TOF I BROAD ... Kollektionen + Types` | Search | €5,490 | 3.00 | ✅ | Only active non-brand search |
| `EX \| DE \| SEARCH \| BRAND` | Search | €1,730 | 57.2 | ✅ | **Protected** |
| `EX \| USA \| SEARCH \| BRAND` | Search | €820 | 60.3 | ✅ | **Protected** · IS 84.4 % = biggest opportunity |
| `EX \| SKANDI \| SEARCH \| BRAND` | Search | €625 | 25.8 | ✅ | **Protected** |
| `JM I DSA I FC'S I CAT'S` | DSA | €603 | 3.80 | ✅ | Dynamic search (Jonas) |
| `EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX + NEAR-INDEX` | PMax | €410 | 2.15 | ✅ thin | Scaled down from former flagship |
| `EX \| FRA \| SEARCH \| BRAND` | Search | €364 | 88.4 | ✅ | **Protected** |
| `EX I SHOPPING I PUR I T-ROAS I NEAR INDEX` | Shopping | €24 | 9.11 | ✅ | Near-dormant |

**Channel mix:** PMax 36.6 % · Shopping 32.2 % · Search 31.2 % · Video 0 % · Demand Gen 0 %
*Search share has risen from ~13 % to 31 % purely because Shopping was cut — not because Search grew.*

**Brand vs non-brand:** brand 11.5 % of spend / **77 % of tracked purchase value**.

### Structural observations requiring action

- **Video and Demand Gen are at €0.** `BS DEALS - DG_ CP+PDP_S+V` had an H1-2026 clean ROAS of **5.78** and was profiled as "fundamentally healthy." If it is off unintentionally, profitable volume is idle → **Gap G6 (High)**.
- **Budget utilisation is inconsistent.** FOKUSPRODUKTE (€1,150/day budget) spends ~€330/day; PROSPECTING (€1,250/day) spends ~€363/day — yet both report as budget-constrained. Either these are shared budgets or the daily caps were restored after the 2026-06-30 cut and the campaigns cannot fill them → **Gap G7 (High)**, resolvable via API without client input.
- 74 further campaigns exist at €0 cost (paused/removed). No campaign has >€1,000 spend with zero conversions (guardrail DON'T-6 clear).
- **There is a fifth brand campaign: `EX | ESP | SEARCH | BRAND`.** Prior documentation consistently says "the four brand search campaigns." ESP had €0 spend in this window but exists and is linked to the shared negative sets. It inherits do-not-touch protection. Whether Spain is a deliberately dormant market or an oversight is unknown → **Gap G22 (Low)**.

### Shared negative sets — verified 2026-08-03

The account contains exactly **two** shared negative sets (prior config named three that do not exist):

| Set | Keywords | Applied to |
|---|---|---|
| `EX I ALL` (id 9606244993) | 78 | Broadly — search, shopping, video, DSA |
| `EXCLUSIONS FOR BRAND` (id 11415316346) | **3,135** | All five brand campaigns **and** `EX I SHOPPING I FOKUSPRODUKTE` |

⚠️ **`EXCLUSIONS FOR BRAND` is still attached to FOKUSPRODUKTE.** Applying it there on 2025-02-20 measured **−23 %** (finding N7 in the change-impact analysis) because it pushed brand-driven purchases out of the Shopping campaign. The move is structurally defensible — brand traffic belongs in brand campaigns — but it was never re-evaluated after the negative measurement, and FOKUSPRODUKTE is now the campaign running below break-even. **Worth a deliberate decision rather than inheritance** → **Gap G23 (Medium)**.

---

## 6. Bidding — the target-currency problem

**This is the single most actionable finding in this file.**

Because NewCustomerPurchase inflates conversion value, every nominal tROAS target steers to a *lower* real target. The inflation factor differs per campaign, so nominal targets are **not comparable to each other**.

| Campaign | Nominal tROAS | Inflation | **Effective clean target** | To reach clean 2.5, set nominal to |
|---|---|---|---|---|
| FOKUSPRODUKTE | 3.53 | 1.81 | **1.95** | **~4.5** |
| PROSPECTING | 3.60 | 1.88 | **1.92** | **~4.7** |
| DSA | 2.50 | 1.93 | **1.29** ← worst calibrated | ~4.8 |
| OVER-INDEX | 3.50 | 1.45 | 2.42 | ~3.6 |
| NEAR INDEX | 4.00 | 1.28 | 3.13 | — |
| **Search TOF** | **5.19** | **1.00** | **5.19** | — |
| DE brand | 100 | 1.42 | 70.7 | — |
| USA brand | 42.64 | 1.53 | 27.8 | — |
| FRA / SKANDI brand | Target Impression Share | — | — | — |

**Nobody decided to run the two biggest campaigns at break-even.** The account is doing exactly what it was told; it was accidentally told "break-even."

**Note the anomaly:** the Search TOF campaign records **zero** NewCustomerPurchase conversions — its goal configuration excludes NCP, so its 5.19 means 5.19. Goal configuration is therefore inconsistent across campaigns → verify per campaign before comparing any two targets.

### Recommended sequence (proposals for Jonas, not actions)

1. **Preferred, structural:** remove NCP from the bidding goals so targets mean what they say. **This is an account-level change → guardrail DON'T-8: humans only, never autonomous, never evaluated by an agent.**
2. **If (1) is not wanted:** raise nominal tROAS on FOKUSPRODUKTE (3.53 → ~4.5) and PROSPECTING (3.60 → ~4.7). This is guardrail DO-1 (scarcity via target) — the account's only repeatedly proven lever. Respect DON'T-2 (14 days rest per campaign) and DON'T-9 (one campaign at a time, staggered 1–2 weeks).
3. **Cheapest win, independent of the above:** close the USA brand IS gap (84.4 % → 95 %+) via bids and ad quality. The gap is rank-lost, not budget-lost. Precedent: +261 %.

---

## 7. Conversion Tracking & Measurement Regimes

**Primary conversion:** `purchase_gads_mable` (PURCHASE, WEBPAGE, MANY_PER_CLICK, ENABLED)

### The three counting regimes — mandatory context for any historical number

| Regime | Period | What it counted | Rule |
|---|---|---|---|
| 1 | Aug 2023 – Apr 2024 | GA4 **+** Google Shopping App in parallel → purchases double-counted | Never use as absolute values |
| 2 | **May 2024 – Sep 2025** | only `purchase_gads_mable` | **The only clean raw window — use as baseline/YoY anchor** |
| 3 | since 2025-11-10 | + `Custom NewCustomerPurchase` | Reported ROAS inflated ×1.42–1.94 (per campaign); ×1.50 account-wide |

**Regime-3 event chain:** 2025-11-10 conversion restructuring → 2025-11-23 bidding goal changed to "Käufe + New Customers" (two days before Black Friday week) → 2025-12-11 NCP set back to secondary → 2026-02-18 account-level new-customer acquisition activated ("bid for new customers only" + €16.46 extra value per new customer) → 2026-03-13 campaign-level goal re-included it. **Verified still active 2026-08-03.** The NCA setup is deliberate strategy, not a bug — but it changes what the account measures.

### Tracking hygiene issues

- **`YouTube follow-on views` is `primary_for_goal = true` AND `ENABLED`** — alongside `purchase_gads_mable` the only active primary conversion. Harmless at €0 video spend; **will corrupt bidding signal the moment Video or Demand Gen restarts.** Fix before reactivating (§5).
- **10 further primary-for-goal actions are legacy Universal Analytics goals** with status `HIDDEN` (add-to-cart, checkout steps, "Intelligentes Zielvorhaben", Transactions). Inactive but should be cleaned up.
- 57 conversion actions exist in total; 45 are secondary. Multiple `(OLD)` duplicates and both GA4 and Mable purchase variants coexist.
- **Auto-apply:** keyword/asset auto-apply is **off and stays off** (8/8 historical clusters hit brand campaigns; hit rate ~38 %; worst case removed exact `[stay cold]` two days before BFCM week 2024). Bidding auto-apply paused 2026-07-03.
- **Third-party attribution: Tracify** (owner Jonas). Its view of Google is unknown → **Gap G9**. Expect divergence; agree which number governs *before* any ROAS debate.
- **Conversion lag:** `config/ads-context.config.json` sets 8 days. Unverified; apparel typically converts within 1–3 days, so 8 is likely conservative-but-safe → **Gap G13 (Low)**.
- **Attribution model / conversion window:** not present in the pulled data → **Gap G10 (Medium)**.

---

## 8. Budget & Spend

- **Current run rate:** ~€31k/month (down from €62k in June 2026)
- **Budget period:** calendar month
- **Reallocation authority:** **none — Martin proposes, Jonas executes** (§13)

### Budget guardrails (evidence-based, this account only)

| Rule | Threshold |
|---|---|
| Raise budget only against a real limit | budget-lost IS ≥ ~20 % (Search/Shopping). PMax has no lost-IS → proxy: marginal clean ROAS of last step ≥ 0.8× campaign average |
| Never raise budget | when budget-lost IS < 5 % |
| Step size (outside promo windows) | max ±30 % per step, ≥7 days apart |
| Inside documented promo windows | step-size and rest rules **suspended** — intraday scaling is a legitimate tactic here |
| Saturation response | cut immediately when marginal clean ROAS drops below break-even proxy |
| Zero-conversion alarm | any campaign >€1,000 cumulative spend without a purchase |

**Historical note:** 78 % of 95 non-promo budget steps exceeded ±30 %, and the net effect of all non-promo budget work over two years was ≈ 0. Budget is not this account's lever. **Targets and structure are.**

---

## 9. Strategic Priorities

### Campaign priorities (analyse in this order)

1. **FOKUSPRODUKTE + PROSPECTING** — 67 % of spend at zero contribution. Fix target calibration first. Highest euro impact in the account.
2. **USA brand search** — IS 84.4 % vs. 95 % target, rank-limited. Cheapest traffic available; measured precedent +261 %.
3. **Search TOF (non-brand)** — clean 3.00, budget-constrained at €240/day. The only non-brand unit clearly above target. Candidate for controlled expansion once §6 is settled.
4. **Video / Demand Gen** — determine whether the €0 is intentional (Gap G6) before anything else.
5. **DSA** — worst-calibrated target (effective clean 1.29). Small spend, quick fix.

### Keyword / theme priorities

1. Brand terms (all markets) — protected, highest value density
2. Core product-category terms (heavyweight hoodie, oversized tee, 400gsm, tattoo/dark apparel) — the scene core
3. Artist and design names (Reign of Blood, named tattoo artists) — high-intent, brand-adjacent
4. Competitor terms — **no active competitor campaign; do not auto-negate foreign brands** (scene shoppers with brand overlap convert)

---

## 10. Competitive Strategy

**Approach:** Defensive-Balanced — protect brand toward 95–99 % IS, no conquest campaigns.

**Priority competitors** (from Stay Cold's own Marketing Cheat Sheet): Killstar · DropDead · Disturbia · Sullen · Named Collective · Blackcraft Cult · Bad Monday

**Reference brands they benchmark against:** LFDY (DE D2C scale) · Glow25 (CRM) · Carhartt (durability) · Supreme/Palace (drop discipline)

**Win themes — verifiable claims only:**
- 400gsm heavyweight hoodies · 250gsm heavy tees · prints withstand 200 washes
- Real tattoo artists, credited by name (artist is a filterable facet on-site)
- Berlin 2015, no investors · 10+ years
- 4.6/5 from 6,473 REVIEWS.io reviews · 30-day returns · free shipping from €89

**Never in copy:** "Premium Quality" · "Community" · "Streetwear" · emojis · discount screaming · fake urgency. Full rules: `context/pre-knowledgebase-nodes/03-account-config/ad-copy-rules.md`.

⚠️ **Copy risk:** the site's "Worldwide Delivery within ~1–2 business days" is a **dispatch** claim, not delivery (USA is 10–14 days). Do not put a 1–2 day *delivery* promise in ads for non-DE geos — misleading-claim and CVR/return risk.

---

## 11. Google's Strategic Position — an open risk

**Google is still not defined as a channel in Stay Cold's own marketing strategy.**

- Marketing Cheat Sheet v0.1 (Active) lists 8 channels — Instagram, TikTok, Meta Ads, Email, Influencer, Wholesale, Word of Mouth, Website. **Google is not among them.**
- It appears only as **open question #1**: *"Is Google (Search/PMax) still an active acquisition channel, and what's its role?"*
- v0.2 has sat in **Draft since 2026-06-25**, unchanged. A "TEMP — Change Proposal" (2026-06-26) lists Google's role as **"Not ready."**
- Owner is now assigned: **Jonas Makki** (Head of Marketing/CMO), whose documented remit explicitly includes "Google ads."

**Meanwhile the operational layer moved without the strategy layer.** "Our Data Structure" (edited 2026-07-30) documents Google Ads as a **🟢 live data source**, ingested hourly into the Supabase "Class C" warehouse (16,056 rows from 2023), feeding `marts.mart_gads__weekly` / `__monthly` (spend / ROAS / impression share) and blended MER — and exposed to Stay Cold's own Slack **Marketing** and **Analyst** agents via `query_gads_history` and `gads_optimization_signals`.

**Two consequences:**

1. **Risk — a numbers conflict is loading.** If those marts read `metrics.conversions_value` from the API (the default), Stay Cold's internal dashboard shows **ROAS 12.4 where the truth is 8.26**, and an equally inflated MER. Someone will steer on that. **Verify the mart definition before it becomes a disagreement** → **Gap G11 (Critical)**.
2. **Opportunity.** Open question #1 is the only unanswered item in the sheet, the owner is named, and the change-impact analysis plus this file answer it factually. Frame the conversation as: *"here is the answer to open question #1 in your marketing sheet."*

---

## 12. Cross-Channel Context

| Channel | Role (per their Marketing Cheat Sheet) | Data available to us |
|---|---|---|
| Instagram | Primary awareness (reach, saves) | none |
| TikTok | Reach outside the bubble; "critical for building the USA" | none |
| **Meta Ads** | "Paid amplification of organic content that already works. An accelerator, not a replacement." KPIs: ROAS, CPA. **Treated internally as *the* paid channel.** | **none** → **Gap G4** |
| Email (Klaviyo) | Retention, drops, waitlists, early access | none |
| Influencer | Part of acquisition, weighting undefined | none |
| Wholesale | Passive new-customer channel | excluded from reporting |
| Word of Mouth | "the strongest channel we have" | — |
| Website | Conversion. KPIs: CVR, AOV, repeat purchase | Gap G1 |

- **Budget assumption:** 70 % acquisition / 30 % retention (Max1, explicitly "not yet validated")
- **Retention principle:** "identity, not incentives" — no discount winbacks, no voucher flows, no gamification
- **Why this matters for Google:** Meta is the politically established paid channel. Google's budget is defensible only with a documented role and a clean number. Total marketing budget and Meta's spend level are unknown → **Gap G4 (High)**.

---

## 13. Operating Model & Known Constraints

**Martin (external) analyses and proposes. Jonas Makki executes. No exceptions.**

| Constraint | Detail |
|---|---|
| **No execution mandate** | All skill output = proposals for a human. No autonomous pushes. |
| Approval latency | **Unknown** → **Gap G12 (High)**. This determines whether guardrail DO-3 ("cut saturation immediately") is even achievable. |
| Account-level changes | Conversion setup, NCA settings, access, tracking templates → **humans only**, never agent-evaluated or executed (DON'T-8) |
| Brand campaigns | Do-not-touch: no pausing, no keyword removals, no negatives, no broad match; bids upward only (DON'T-4) |
| Rollouts | Never same-day across all markets — stagger 1–2 weeks per market (DON'T-9) |
| Offer messaging | No discount framing outside Black Friday slow-mover scope (locked business rule) |
| Landing pages / feed | Ownership and lead time **unknown** → **Gap G14 (Medium)** |
| Working language | **English** for everything client-facing |
| PMax visibility | No search terms, no impression share available — saturation diagnosis via marginal clean ROAS proxy only |
| Search-terms agent scope | Search + Shopping (negatives only for Shopping); PMax out of reach; brand campaigns observe-only |

---

## 14. Seasonality & Promo Calendar

**Seasonal shape:** Q4 dominant (BFCM is the single biggest event). Q1 strong on efficiency, Q2–Q3 lower volume. Drop cadence, not seasons, drives week-to-week demand.

**Historical Q4:** BFCM 2025 = best month in account history — €33,877 spend at clean ROAS **19.38**, +62 % purchase revenue vs. BFCM 2024, measurement-clean. BFCM insights rest on **n=2 seasons under two different counting regimes** — not enough for seasonal thresholds.

### Promo windows

**Verified historical** (guardrail DO-4 requires these; inside them, step-size and rest rules are suspended):

| From | To | Promo |
|---|---|---|
| 2024-11-20 | 2024-12-02 | BFCM 2024 |
| 2025-11-20 | 2025-12-01 | BFCM 2025 |
| 2026-03-12 | 2026-03-20 | Black Spring Sale 2026 |

**Planned, from Airtable Drop Base (read 2026-08-03):**

| From | To | Activation | Status |
|---|---|---|---|
| 2026-10-02 | 2026-10-04 | VIP Sale Weekend | planned |
| 2026-11-23 | 2026-11-30 | Black Week Special Drops | **only "Proposed by Jonas" — not confirmed** |
| 2026-12-02 | 2026-12-17 | 3For2 Hoodies On Special Drop | planned |

Plus 113 routine weekly "New Product" / restock activations in the same window.

⚠️ **Unresolved conflict.** The locked offer rule (Max1, 2026-05-08) is *"no sitewide discounts; no discounts on new drops in the first 90 days; discounts only on Black Friday, and only on slow movers."* A **VIP Sale Weekend in October** does not fit that rule. **3For2** may qualify as an unlock/gift mechanic (like the recurring "Thunder Drop Deal — buy any 3, get 1 free") rather than a discount. The v0.2 Product + Offer draft flags the rule for reconciliation against a new "test different offer structures" purpose — so the rule may be softening in practice. **`promo_windows.csv` is deliberately not written yet** pending this answer → **Gap G5 (Critical)**.

⚠️ **BFCM 2026 is unconfirmed 16 weeks out** — for the channel whose best month ever was BFCM. Product side is moving (offer products selected, "Black Razor" hoodie in production per Slack, 2026-07-28); **no ad budget, channel plan, or discount scope exists.**

---

## 15. Business Risks with Direct Ads Impact

Non-advertising problems that will show up in the account:

| Risk | Status | Ads impact |
|---|---|---|
| **Global-e blocked** | Contract terms deviate from sales pitch; go-live on hold (Jonas check-in, July 2026) | Global-e was to carry cross-border checkout and non-EU returns. Threatens any international Q4 push and leaves the USA return rate unmeasured |
| **Price-vs-quality perception** | Open, documented blocker (Marketing Cheat Sheet v0.2) | Depresses CVR on non-brand traffic — the exact traffic running at break-even |
| **"PDP truth gap"** | Open — "shop photos vs. the real product. Close the gap; don't oversell in imagery" | Returns driver and LP-experience/Quality-Score driver |
| **Customs friction** | Open, unassigned | USA/non-EU conversion drop-off; compounds the Global-e issue |
| High sold-out rate | Structural (drop model) | Verify Shopping/PMax feed excludes out-of-stock and Search LPs are live |
| Sizing returns | Return report: sizing 54 %, style 30 % of reasons; 260gsm oversized jerseys named | Deprioritise those products in feed/product pushes |
| Stock demotion logic | Shop demotes products at <10 units or weighted size availability <25 % (nightly Collection Sorting Score) | Paid should mirror it — candidate for supplemental feed automation |
| Production → fulfilment handoff | Known risk: "if AIC isn't informed in time, stock problems hit on drop day" | Drop-day campaigns can point at unavailable stock |
| Shipping software outage | AIC, 2026-07-20, temporary | Dispatch delay; minor |

---

## 16. Historical Timeline — what this account has learned

| Phase | Period | Spend/mo | Clean ROAS | Core |
|---|---|---|---|---|
| Baseline | Jul–Sep 2024 | €24–32k | 5.2–5.6 | Broad PMax/Shopping setup |
| **Efficiency program** | Oct 2024 | €25k | **8.0** | Budgets cut + tROAS raised |
| Efficiency plateau | Nov 2024 – Oct 2025 | €16–33k | 9–14 | Discipline. Best: Aug/Sep 2025 (12.8 / 14.2) |
| **BFCM 2025** | Nov 2025 | €34k | **19.4** | +62 % YoY, measurement-clean |
| **Over-scaling** | Jan–Jun 2026 | €21k → **€62k** | 11.6 → **5.0** | Clean ROAS fell six months straight |
| **Correction** | Jul 2026 | **€31k** | **8.26** | Spend halved, efficiency restored at account level |

**YoY anchors (clean):** H2 2025 vs. H2 2024 — spend flat, purchase revenue **+66 %** (real improvement). H1 2026 vs. H1 2025 — spend **+92 %**, clean ROAS **−23 %**.

### What worked (evidence-backed)

- **Scarcity as the efficiency lever** — cut budget 20–40 % and/or raise tROAS, then 14 days of rest. *Every* high-confidence win in two years was a scarcity or correction package (2024-07-16 +45 %, 2024-10-04 +126 %, 2024-10-09 +246 %, 2025-04-15 +86 %).
- **Structure over budget** — FOKUSPRODUKTE ad-group restructuring 2026-01-23: +29 %.
- **Brand IS closing** — USA package 2026-03-13: +261 %.
- **Removing broad match from brand** — SKANDI 2024-09-23: +278 %.
- **Clearing expired sale assets** — SKANDI 2026-01-13: +396 %.
- **Targeted tracking-template cleanup** — 2026-03-06 across three brands: +66 / +25 / +17 %.
- **Disabling search partners** — FOKUSPRODUKTE 2025-09-18: +17 %.
- **Moderate budget steps in calm windows** — ≤ +44 % repeatedly positive.

### Historical failures — do not repeat

- **Budget increases above +90 %: 0 of 6 positive** (all outside promo windows). Worst: 2026-05-29 PROSPECTING €450 → €880 at ~0 % budget-lost IS → **−27 % on €17,435** — the most expensive single decision of H1 2026.
- **Headroom is necessary but not sufficient** — 2025-04-05: +77 % at 56 % budget-lost IS still measured −17 %.
- **Whipsaw costs in both directions** — 2025-04-17 panic reversal 12 days later: −22 %.
- **Pausing needs the same evidence bar as spending** — 2025-05-13 pausing profitable PROSPECTING BROAD: **−118 %**, the hardest negative verdict in two years.
- **Blanket rollouts act in opposite directions per market** — 2025-01-23 negative-list batch: FRA −32 % while two other markets +30 / +24 %. 2026-01-13 asset cleanup: USA −32 % while SKANDI +396 %.
- **Account-wide same-day tracking rollout** — 2024-10-23: 7 of 11 clusters negative, up to −47 %.
- **Target thrash** — OVER-INDEX tROAS 560 → 300 → 450 within Nov 2024: unmeasurable and destabilising.
- **Auto-apply** — removed exact `[stay cold]` from DE brand two days before BFCM week 2024.
- **Unmonitored launches** — "Video View DRAFT" ran four weeks unnoticed: **€4,750 for 2 purchases** (clean ROAS 0.04).

Full evidence: `context/pre-knowledgebase-nodes/04-historie/Jonas-Briefing_StayCold_2024-2026.md` and `02-gads-guardrails/`.

---

## 17. Data Sources & Systems

| Class | Content | System | Our access |
|---|---|---|---|
| A | Strategy, SOPs, brand guide | **Notion** | ✅ read |
| B | Operational tables | **Airtable** — Product Catalogue `app72sPNYvvMonkXg`, Drop Base `app9nQAQ5BiI6OpPY`, Order Base `appM65nblESBXYQ00`, Return Controlling `apppNMIKbDaGtGHrD` | ✅ read |
| C | Read-only big data: Shopify orders, Meta Ads, **Google Ads**, Klaviyo, Reviews.io | **Supabase** ("Class C warehouse", hourly ingest) | ❌ **requested** |
| — | Shop / inventory master | **Shopify Plus** (`rapid-4.myshopify.com`) | ❌ **requested** (`read_orders`) |
| — | Attribution | **Tracify** (owner Jonas) | ❌ not requested — one screenshot suffices |
| — | Communication | Slack `stay-cold-apparel.slack.com` | ✅ read (public) |

**Notes:** Shopify is master for inventory (no Airtable sync, decided 2026-07-04). Product numbers change per production run from 2026 — "the same" product changes ID in the feed. Google Shopping metafields are live (`mm-google-shopping.custom_label_0/1/2` plus analytics twins for design / artist / colour / GSM) → feed segmentation by design line, artist, or drop freshness is possible today. `custom.drop_date`, `early_access_start/end`, `last_restock_date`, `collection_sorting_score` are usable for campaign timing.

**Team:** Founder circle Max1 (Maximilian Abraham) · Vuven (Vivian Meurer) · Jonas Makki · Maxobert (Max Algermissen). Performance marketing: Jonas (internal), Martin (external, Google Ads), Valentin Hertweck (external, presumably Meta — unconfirmed). Tech: Shaun Kutsanzira (English only), Maxobert. Weekly rhythm: Monday team meeting, preceded by Net-Sales Dashboard and Return-Rate Report.

---

## 18. Gaps & Open Questions

*Every unanswered question, with priority and owner. Downstream skills must treat these as unknown — never fill them with plausible values.*

### Critical — blocks target setting and profitability judgement

| # | Gap | Why it matters | Unblocked by |
|---|---|---|---|
| **G1** | **Whether Google receives gross (incl. VAT) or net conversion values** | Moves break-even clean ROAS between **1.6 and 1.9** — the most important threshold in the account. Resolvable by reconciling Google's tracked purchase value against Shopify revenue for the same period: a ratio of ~1.19 means gross. *(The AOV half of this gap is now closed — ~€143 derived from the account itself.)* | Shopify `read_orders` (read-only) |
| **G3** | **2025 actual revenue and 2026 / H2-2026 revenue target** | No documented company goal exists. Channel goals cannot be derived from nothing | Jonas |
| **G4a** | **Google's intended role**: efficiency harvesting vs. active new-customer channel | These are opposite setups. Efficiency harvesting → clean ROAS target ~6. Prospecting growth → target ~2.5. Every recommendation depends on which | Jonas / Marketing Cheat Sheet v0.2 |
| **G5** | **Binding offer/promo rules**, and resolution of the VIP-Sale-Weekend conflict | `promo_windows.csv` is blocked on this. Guardrail DO-4 calls the promo calendar mandatory infrastructure. Also governs all ad copy | Jonas / Max1 |
| **G11** | **How `marts.mart_gads__*` computes ROAS** — inflated or clean series | If inflated, Stay Cold's own dashboard and MER are ~50 % overstated and someone will steer on it | Supabase `SELECT` on `marts`, or Shaun |

### High — materially changes recommendations

| # | Gap | Why it matters | Unblocked by |
|---|---|---|---|
| **G2** | Repeat-purchase rate / CLV | Account bids for new customers with a +€16.46 value bonus that nothing validates | Shopify `read_orders` |
| **G4b** | Meta Ads spend level and ROAS; total marketing budget | Google's budget is politically measured against Meta. No cross-channel view exists | Supabase `marts` (preferred) |
| **G6** | Is Video / Demand Gen at €0 intentional? | BS DEALS had clean ROAS 5.78 and was profiled "healthy". If off by accident, profitable volume is idle | Jonas |
| **G7** | Why do FOKUSPRODUKTE / PROSPECTING spend ~30 % of their daily budgets while reporting budget-constrained? | Determines whether budget or bidding is the actual limiter | **Resolvable via API without client input** |
| **G12** | Approval latency for proposals | Determines whether guardrail DO-3 ("cut saturation immediately") is achievable at all | Jonas |
| **G15** | What happened in the account in July 2026 (spend halved, Video/DG to zero) | Nothing about it appears in public Slack. Current state cannot be labelled intentional or accidental without this | Jonas (or private Slack search, with consent) |

### Medium

| # | Gap | Unblocked by |
|---|---|---|
| **G8** | Actual shipping cost per order (DE / EU / USA) and payment fee % | Jonas / accounting |
| **G9** | Tracify's attributed revenue for Google, last 30 days | One screenshot from Jonas |
| **G10** | Attribution model and conversion window settings | Targeted API pull |
| **G13** | Verified conversion lag (config says 8 days; apparel typically 1–3) | API analysis |
| **G14** | Landing-page and feed ownership + change lead time | Jonas |
| **G16** | Real non-EU return rate (Global-e returns sit outside Shopify) | Jonas / Global-e |
| **G17** | Role split with Valentin Hertweck | Jonas |
| **G18** | BFCM 2026: confirmation, dates, discount scope, ad budget | Jonas |

### Low

| # | Gap |
|---|---|
| **G19** | Legacy "Google Product Master Sheet" (Sebastian, inactive) tied to Shopify metafield `custom.internal_rolling_number` — still needed? |
| **G20** | The two n-gram shared negative lists do not exist in the account. Config sets them to `null` deliberately so a run fails loudly instead of writing into the wrong list. Jonas must create them before n-gram push is enabled. |
| **G21** | PMax asset-group deep dive — data pulled to 2026-07-03, never analysed |
| **G22** | `EX \| ESP \| SEARCH \| BRAND` — dormant by design or overlooked? |
| **G23** | *(Medium)* `EXCLUSIONS FOR BRAND` still applied to FOKUSPRODUKTE despite measuring −23 % there in Feb 2025. Re-decide deliberately. |

---

## 19. Change Log

*Most recent first.*

- **2026-08-03** — `business.md` rebuilt from scratch. Prior file was the unmodified lead-gen template (USD, form submits, €150/lead) and produced wrong recommendations for this EUR e-commerce account. Unit economics established from Airtable (gross margin 75 %, returns ~5 %); AOV ~€143 derived from the purchase-only series; break-even clean ROAS ~1.9 established; NCP inflation verified live per campaign (×1.28–1.94); two-thirds of spend identified as running at or below break-even; fifth brand campaign (ESP) and the two real shared negative sets discovered.
  Also corrected: the wrong ~0.6 % return rate annotated at source in `pre-knowledgebase-nodes/01-notion-kb/Stay Cold - Produkte & Drops.md`; `config/ads-context.config.json` template placeholders replaced with verified values (`conversionActions` → `purchase_gads_mable`, `brandedCampaigns` → the five real campaigns, `biddingStrategy` cpa → roas, `defaultAOV` 200 → 143, three invented shared-list names → the two that exist, brand terms added to `neverExclude`).
- **2026-07-31** — Shaun: Google Ads goes live as a Supabase Class C data source (hourly ingest, marts + Slack agent access).
- **2026-07-04 → 2026-08-02** — Spend at €30,875, clean ROAS 8.26. Video and Demand Gen at €0.
- **2026-07-03** — Jonas pauses bidding auto-apply. Change-impact analysis 2024–2026 completed (cutoff).
- **2026-06-30** — Budget cut on FOKUSPRODUKTE: €1,600 → €550/day (saturation correction, campaign was at weekly clean ROAS 0.77). Correct call, ~4 weeks late.
- **2026-06-25** — Cheat Sheet v0.2 round enters Draft; Google's role listed "Not ready". Unchanged since.
- **2026-05-29** — PROSPECTING budget €450 → €880 at ~0 % budget-lost IS → −27 % on €17,435. Most expensive single decision of H1 2026.
- **2026-05-08** — Offer rules locked by Max1: no sitewide discounts, no discounts on new drops <90 days, discounts only Black Friday on slow movers.
- **2026-03-13** — Campaign-level goal re-includes NewCustomerPurchase. Still active.
- **2026-02-18** — Account-level new-customer acquisition activated (+€16.46 value per new customer).
- **2025-11-10** — Conversion restructuring begins regime 3. Reported ROAS inflated from here on.
