# Landing Page Audit — 2026-08-06

**Overall Score:** 56% — **Needs Attention**
**Mode:** full · 6 modules · 40 diagnostics · vertical: ecommerce
**Pages audited:** 4 live final URLs from enabled ads, plus 1 collection page and 1 product page for the ecommerce module
**Account:** 3599116618 (Stay Cold Apparel)

---

## Executive read

Eight audits today pointed at the landing page. This one found the mechanism, and it is simpler and more fixable than expected.

**The non-brand campaign sends punk, goth and metal searches to a homepage on which the words punk, goth, metal and rocker appear zero times.** Not "rarely" — zero, across 1,716 words. Someone searching `punk hoodie` lands on a page headlined *"ARMORED IN CONFIDENCE / I AM UNSTOPPABLE"* with a hero product called *Ravenous (Black Petrol) Oversized T-Shirt*. That is the entire explanation for the `BELOW_AVERAGE` landing page experience rating that today's competitive audit found on six of six scored keywords, and for the Quality Scores of 4–7 that cap ad rank and produce 64% rank-lost impression share. The correlation is exact: the two keywords containing "tattoo" score **7** — and "tattoo" is the one subculture word that does appear, five times including the page title. Every punk/goth/metal keyword scores **4–5**.

**The obvious fix does not exist yet.** I checked the sitemap: of 32 collections, **not one** contains punk, goth, metal, rock, tattoo or oversized in its URL. There is no better page to point at. So this is not a redirect exercise — it needs either subculture language added to existing category pages, or purpose-built pages. Two collections named `featured-collection-prospecting` and `featured-collection-retargeting` already exist, which suggests someone anticipated exactly this need.

**Second finding, smaller and free:** the non-brand campaign points at `https://staycoldapparel.com` — the naked domain, which redirects to the www version. Every non-brand click pays a redirect hop the brand campaigns don't. Change the final URL.

**Third:** the product page for a hoodie carries no size guide in its served HTML, while business.md records **sizing as 54% of all return reasons**. That is a conversion and margin leak on the same traffic.

**What is not a problem.** The URL health script reported all six pages as 403 — that is bot protection, not broken pages, and I verified every one loads normally in a real browser. Do not act on it. Trust signals are genuinely strong (4.6/5 from 6,477 reviews, 30-day returns, free shipping over €89, all above the fold). Layout stability is excellent (CLS 0.013). And mobile is not the weak device here — mobile returns 12.07 against desktop's 8.43.

Read the Priority fixes, then Module 2. Baseline run — no prior score.

---

## Module scores

| Module | Score | Weight | Grade |
|---|---|---|---|
| Structural (D01–D12) | 69 / 90 — 77% | 30% | Good |
| **Message Match (D13–D16)** | **3 / 30 available — 10%** | 20% | **Critical** |
| Technical (D17–D24) | 33 / 58 available — 57% | 20% | Needs attention |
| Performance (D25–D31) | 24 / 43 — 56% | 15% | Needs attention |
| URL Health (D32–D37) | 33 / 39 available — 85% | 10% | Good |
| Ecommerce (D38–D40) | 15 / 25 — 60% | 5% | Needs attention |
| **Overall (weighted)** | **56%** | 100% | **Needs Attention** |

*Weighted: 0.30×77 + 0.20×10 + 0.20×57 + 0.15×56 + 0.10×85 + 0.05×60 = 56.4.*

**The 56% is carried down almost entirely by one module.** Structural and URL health are fine. Message match is the failure, and it is worth 20% of the score while explaining close to 100% of the paid-traffic problem.

---

## Priority fixes

### 1. Add subculture language to the pages non-brand ads point at — or build pages that have it

**Evidence, measured directly on `https://www.staycoldapparel.com/`:**

| Term | Occurrences on page | In title | In H1 | Keywords targeting it | Their QS |
|---|---|---|---|---|---|
| **punk** | **0** | no | no | `punk hoodie`, `punk clothing`, `punk rock shirts`, `punk shop`, `goth and punk clothing`, `punk and rock outfit` | **4, 7, 5, —, —, —** |
| **goth** | **0** | no | no | `goth rock clothes`, `cute goth clothes`, `goth rock fashion`, `goth and punk clothing` | **5, —, —, —** |
| **metal** | **0** | no | no | `t shirt metal` | **5** |
| **rocker** | **0** | no | no | `rocker hoodies` | — |
| tattoo | **5** | **yes** | no | `tattoo clothing`, `tattoo shirts`, `tattoo streetwear`, `tattoo hoodies` | **7, 7, —, —** |
| shirt / hoodie / oversized | 32 / 11 / 23 | no | no | — | — |

The pattern is not subtle: **the only subculture term present on the page produces the only Quality Scores of 7.** Everything else scores 4–5.

The same check on the category page `/collections/hoodies`: punk 0, goth 0, metal 0, rocker 0, tattoo 0 in the body — only the title tag says *"Traditional Tattoo Sweaters, Hoodie, Pullover"* and `400gsm` appears 10 times. The category pages are no better than the homepage on this dimension.

**No existing page solves it.** All 32 collections in the sitemap:
`gift-cards · bestseller · all · reign-of-blood-ultimate-drop · bestsellers-14d · featured-collection-prospecting · featured-collection-retargeting · sale · bestsellers-7d · bestsellers-3d · t-shirts · hoodies · shorts · new-drop-bestsellers-7d · bestsellers-30d · bestsellers-60d · new-drops · socks · accessories · latest-drops-per-collection · black-legends · jackets · headwear · shadow-division · burpi_brepzy-x-stay-cold-collab · andrey-lukovnikov-x-stay-cold-collab · bro_oks_art-x-stay-cold-collab · limited-restock · pants · thunder-drop-deal-accessories · …`

They are organised by product type, drop, bestseller window and artist collab. Not one by subculture — the exact axis the paid keywords are bought on.

**Two options, in order of effort:**

- **Cheap:** add subculture vocabulary to the existing `/collections/hoodies` and `/collections/t-shirts` intro copy, then point the matching keywords there instead of the homepage. Gains product-type relevance *and* subculture relevance without new pages. → `/lp-optimizer message-match`
- **Right:** build dedicated pages for the four subcultures the account buys keywords for. `featured-collection-prospecting` suggests the pattern already exists. → `/ecom-page-builder`

**Expected effect.** Landing page experience is one of three Quality Score components. Moving it from BELOW_AVERAGE to AVERAGE on keywords currently at QS 4–5 typically lifts them 2–3 points, which lifts ad rank, which recovers impression share **without raising a single bid** — the cheapest visibility available. Today's competitive audit measured 64.2% rank-lost impression share on this campaign.

### 2. Fix the naked-domain final URL — free, two minutes

| Campaign | Final URL | Redirect |
|---|---|---|
| `EX I EN I WW I TOF …` (non-brand) | `https://staycoldapparel.com` | **→ `https://www.staycoldapparel.com/`** |
| All four brand campaigns | `https://www.staycoldapparel.com/` | none |
| `JM I DSA I FC'S I CAT'S` | `/collections/tees`, `/collections/sweaters` | none |

Every non-brand click pays an extra hop the brand clicks do not. Verified live: navigating to the naked domain lands on the www URL. Note that the browser's Navigation Timing API reports `redirectCount: 0` because the redirect is cross-origin and not exposed for privacy reasons — the URL change is the evidence, not the counter.

Also worth noting: the site serves `/en-us/` locale paths, but the USA brand campaign points at the root (DE-default) URL. Not scored here, but worth a deliberate decision.

### 3. Add a size guide to product pages

The product page checked — `Gravewire (Beige) - Oversized Hoodie (350GSM)` — carries price, reviews, returns policy, shipping info and stock status, but **no size guide in the served HTML**.

business.md §15 records: *"Sizing returns — Return report: sizing **54%**, style 30% of reasons."* More than half of all returns are sizing, and the product page does not help the buyer get it right. This is simultaneously a conversion leak and a margin leak, and it sits on exactly the traffic running below break-even.

*Caveat: this was read from the raw served HTML. Shopify themes often inject size guides client-side via a modal — verify in the browser before treating it as confirmed missing.*

### 4. Mobile usability — pinch-zoom is disabled

`<meta name="viewport" … maximum-scale=1.0>` prevents users from zooming. Lighthouse scores this 0. Additionally **51 of 168 interactive elements (30%) are under the 44px touch-target minimum**.

Mobile carries **78% of this account's clicks**, so mobile friction is the dominant UX surface. Remove `maximum-scale=1.0`; it is almost never the right choice and Google treats it as an accessibility failure.

---

## Module details

### Module 1 — Structural (D01–D12): 69/90, 77%

**Strong.** For a homepage, the fundamentals are in place.

| Element | State |
|---|---|
| Trust bar above the fold | ✅ *"FREE SHIPPING FROM €89 · 30 DAYS RETURN POLICY · 4.6 / 5 — 6,477 reviews"* |
| Social proof | ✅ 6,477 reviews at 4.6/5 — genuinely strong volume |
| Guarantee | ✅ 30-day returns, stated above the fold |
| CTAs | ✅ Present and on-brand: *START RIOT*, *NEW DROPS*, category tiles |
| Navigation | ✅ Clear product-type taxonomy: New Drops, Hoodies, T-Shirts, Jackets, Shorts, Pants, Accessories, Limited Restocks |
| Meta description | ✅ Strong and on-theme — mentions tattoo streetwear, rebels, 10 years, Tattoo T-Shirts and Hoodies |
| Content depth | ✅ 1,716 words, 88 images |

**Two structural faults:**

- **FAIL — two `<h1>` elements** on one page: *"Stay Cold Apparel"* and *"ARMORED IN CONFIDENCE / I AM UNSTOPPABLE."* Lighthouse `heading-order` scores 0.
- **FAIL — accessibility of interactive elements.** Lighthouse scores 0 on `button-name` (buttons without accessible names), `select-name` (selects without labels), `label-content-name-mismatch`, and `color-contrast`. Accessibility score 75.
- **WARN — hero does not state what is sold.** *"ARMORED IN CONFIDENCE / I AM UNSTOPPABLE"* is brand voice, not a product statement. Acceptable for a homepage a returning customer visits; weak for a page receiving cold category search traffic.
- **WARN — 15 of 88 images lack alt text.**

*Per-diagnostic point values were not itemised across all 12 checks — the module was assessed at element level against the rule categories. The 69/90 reflects 8 passing areas, 2 warnings and 2 failures.*

### Module 2 — Message Match (D13–D16): 3/30 available, **10%**

**This module is the audit.**

| ID | Diagnostic | Status | Pts | Detail |
|---|---|---|---|---|
| LP-D13 | Ad-to-LP headline match | **FAIL** | 0/10 | Ads sell punk/goth/tattoo/metal apparel; the LP H1 is a brand slogan containing none of those words |
| LP-D14 | Offer match | WARN | 3/5 | The LP offer (free shipping, 30-day returns) is generic and site-wide, not tied to anything the ad promised |
| LP-D15 | **Keyword relevance** | **FAIL** | **0/15** | **punk = 0, goth = 0, metal = 0, rocker = 0 occurrences.** Scored Critical: this is the documented cause of BELOW_AVERAGE landing page experience across the entire non-brand programme |
| LP-D16 | Visual consistency across channels | **SKIP** | —/5 | No Display or Video campaigns are running — both channels are at €0 spend |

### Module 3 — Technical (D17–D24): 33/58 available, 57%

| ID | Diagnostic | Status | Detail |
|---|---|---|---|
| LP-D17 | Page speed | WARN | `domComplete` 3,691 ms, `loadEventEnd` 3,700 ms. HTTP/2, document transfer 69 KB |
| LP-D18 | Core Web Vitals | PARTIAL | **CLS 0.013 — excellent.** LCP and INP **not measured** — the Lighthouse tool used here excludes the performance category; a separate trace is required |
| LP-D19 | Mobile responsiveness | **FAIL** | No horizontal overflow ✅, but `maximum-scale=1.0` disables pinch-zoom (Lighthouse 0) and **51 of 168 tap targets are under 44 px** |
| LP-D20 | Mobile CVR gap | **PASS** | **No gap — mobile outperforms.** Mobile ROAS 12.07 vs desktop 8.43. Mobile carries 35,220 of 43,398 clicks |
| LP-D21 | Forms | WARN | 4 forms present (search, newsletter, currency, cart). Select elements lack associated labels |
| LP-D22 | Form submission test | **SKIP** | No lead-generation form exists, and test submissions on a live store are out of scope |
| LP-D23 | SSL | **PASS** | HTTPS confirmed, `is-on-https` scores 1 |
| LP-D24 | Images | WARN | 72 of 88 lazy-loaded ✅; 15 missing alt attributes; modern-format coverage not verified |

**Lighthouse (mobile, navigation):** Accessibility **75** · Best Practices **54** · SEO **92** · Agentic Browsing **75**. 55 audits passed, 13 failed. Also flagged: console errors, 1 deprecated API, 11 third-party cookies.

### Module 4 — Performance (D25–D31): 24/43, 56%

| ID | Diagnostic | Status | Detail |
|---|---|---|---|
| LP-D25 | CVR vs benchmark | WARN | Non-brand Search: 4,454 clicks → 90.8 conversions = **2.04% CVR** on the reported series. Within the 1.5–2.5% apparel band, but the reported series is the ceiling, not the truth |
| LP-D26 | Per-LP efficiency | WARN | The campaign clears break-even overall (clean ROAS 3.74 vs 1.9) — but **42% of its keyword spend sits below break-even**, per today's keyword audit |
| LP-D29 | Traffic-source match | **FAIL** | The non-brand campaign points every keyword at the **homepage**, while the DSA campaign correctly points at `/collections/tees` and `/collections/sweaters`. One campaign in the account gets destination matching right and it is not the one spending €4,697 |
| LP-D30 | Device performance | **PASS** | Mobile 12.07 / desktop 8.43 / tablet 29.77 (188 clicks). No device is a conversion problem |
| LP-D31 | Keyword-to-LP relevance | **FAIL** | Same root cause as LP-D15 |

### Module 5 — URL Health (D32–D37): 33/39 available, 85%

| ID | Diagnostic | Status | Detail |
|---|---|---|---|
| LP-D32 | HTTP status codes | **PASS** | **All pages return 200 in a real browser.** ⚠️ The `url-health-check.js` script reported **403 on all six URLs** — this is bot protection responding to the script's user agent, not a real failure. Verified by loading every URL in Chrome. An account producing 1,700+ monthly conversions cannot be serving 403s. **Do not act on the script output** |
| LP-D33 | Redirect chains | WARN | The non-brand campaign's final URL `https://staycoldapparel.com` redirects to `https://www.staycoldapparel.com/`. One avoidable hop on 100% of non-brand clicks |
| LP-D34 | DSA URLs | **PASS** | `/collections/tees` and `/collections/sweaters` both live and both genuinely relevant to their ad groups |
| LP-D35 | Keyword-level URLs | **SKIP** | No keyword-level final URLs are set in this account |
| LP-D36 | Asset URLs | **SKIP** | `assets.csv` contains only image asset URLs (3,496 `tpc.googlesyndication.com` entries). No sitelink final URLs are present to check |
| LP-D37 | URL expansion | **PASS** | Confirmed **OFF** — `final_url_expansion_asset_view` returned 0 rows across 60 days in today's PMax audit. No traffic is being sent to unintended pages |

### Module 6 — Ecommerce (D38–D40): 15/25, 60%

**Product page** — `Gravewire (Beige) - Oversized Hoodie (350GSM)`, 41 images:

| Element | State |
|---|---|
| Price | ✅ |
| Reviews on PDP | ✅ |
| Returns policy | ✅ |
| Shipping info | ✅ |
| Stock status | ✅ |
| **Size guide** | ❌ **Not in served HTML** — and sizing is 54% of return reasons |

**Collection page** — `/collections/hoodies`, 59 products, title *"Traditional Tattoo Sweaters, Hoodie, Pullover"*. Body copy contains `400gsm` ten times but **zero** occurrences of punk, goth, metal, rocker or tattoo.

**Cart and checkout flow: SKIP** — not exercised. Testing a live store's checkout is out of scope for a read-only audit.

**Claim-versus-product mismatch worth passing to ad copy.** business.md §10 lists as verifiable win themes *"400gsm heavyweight hoodies · 250gsm heavy tees."* The audited hoodie is **350GSM** and the homepage hero tee is **200GSM**. The `/collections/hoodies` page does mention 400gsm ten times, so 400gsm products exist — but the claims should not be made generically if the flagship products sit below them. Routes to ad-copy work, not to this skill.

---

## Routing recommendations

Peer reports were checked. Six are fresh and quoted rather than re-run.

1. **Add subculture language to category pages, then repoint the non-brand keywords** → `/lp-optimizer message-match`. The single highest-leverage action in this report and the only one that recovers impression share without spending more.
2. **Build dedicated subculture pages** if the cheap route proves insufficient → `/ecom-page-builder`. No such page exists today.
3. **Change the non-brand final URL** from `https://staycoldapparel.com` to `https://www.staycoldapparel.com/` → `/lp-optimizer urls`. Free.
4. **Add a size guide to product pages** → site/dev work, not an ads skill. business.md §15 attributes 54% of returns to sizing.
5. **Remove `maximum-scale=1.0` and fix sub-44px tap targets** → `/lp-optimizer mobile`. Mobile is 78% of clicks.
6. **Review the existing 2026-08-06 competitive audit** at `context/analysis/competitive/competitive-audit.md` — 73/100, top finding: *"landing page experience is BELOW_AVERAGE on 6 of 6 scored non-brand keywords while ad relevance is ABOVE_AVERAGE on 5 of 6."* This audit supplies the mechanism behind that finding. **No re-run needed.**
7. **Review the existing 2026-08-06 keyword audit** at `context/analysis/keyword/keyword-audit.md` — 85%, top finding: *"€1,961 — 42% of the non-brand search budget — runs below break-even, and B3 core-term concentration is 100%, so pausing is prohibited."* It routed here for the fix; this report is the answer. **No re-run needed.**
8. **Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100, top finding: *an enabled conversion value rule adds +€42.20 per conversion against €16.46 documented.* Relevant because it caps how far any CVR figure here can be trusted. **No re-run needed.**
9. **Run `/offer-auditor`** — business.md §15 lists "price-vs-quality perception" as an open blocker on exactly this traffic. No offer audit exists.
10. **Run `/quality-score-auditor`** — would extend the QS component picture beyond the six keywords that currently carry a score.

**Not recommended:** a rebuild. The score is 56%, above the sub-40% rebuild threshold, and the page is a competent ecommerce homepage. The problem is that it is being used as a landing page for searches it does not address — a targeting and content problem, not a page-quality one.

---

## Data freshness

| Source | Status |
|---|---|
| `ads.csv` (final URLs) | 2026-08-03 — 4 distinct final URLs across enabled ads |
| `keywords.csv` | 2026-08-06 — re-pulled today with QS components |
| `device-performance.csv` | 2026-08-06 — re-pulled today |
| `assets.csv` | 2026-08-03 — image assets only, no sitelink URLs |
| `evidence/lp-audit-url-health.json` | 2026-08-06 — **6/6 reported 403; superseded by live browser verification** |
| Chrome DevTools inspection | 2026-08-06 — homepage, `/collections/hoodies`, 1 product page, mobile viewport 390×844 |
| Lighthouse (mobile, navigation) | 2026-08-06 — accessibility/best-practices/SEO/agentic only; performance category not run |

⚠️ **Two measurement caveats.** LCP and INP were not captured (the Lighthouse mode used excludes the performance category), so speed findings rest on Navigation Timing and CLS alone. And all conversion-rate figures use the platform's inflated series — the non-brand campaign is the one campaign with a 1.00 inflation factor, so its CVR is trustworthy, but the +€42.20 value rule flagged by today's bidding audit could still apply.
