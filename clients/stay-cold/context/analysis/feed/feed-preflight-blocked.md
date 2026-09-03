# Feed Audit — BLOCKED at preflight

**Date:** 2026-08-06
**Requested mode:** `full` (auto-mode selection — all 5 modules)
**Status:** ❌ **Not run.** The Merchant API preflight gate could not be cleared.
**Account:** Google Ads 3599116618 · Merchant Center **116274940** (discovered, see below)

> This is **not a feed audit** and carries no feed score. It documents why the audit could not run, and reports the feed evidence that *was* obtainable from the Google Ads side without Merchant API access. Do not cite it as feed coverage.

---

## Why it is blocked

The skill's shared preflight requires `merchantCenter.enabled === true` and a valid `merchantCenter.accountId`. Neither existed in config. Two things happened:

1. **The Merchant account ID was recoverable without asking.** Every row in the existing Google Ads pull carries it inside the resource name — `customers/3599116618/shoppingProducts/116274940~ONLINE~en~DE~shopify_DE_…` — consistent across all 1,817 products. Merchant account is **116274940**, feed label **DE**, channel ONLINE, content language **en**.
2. **The OAuth token is the real blocker.** With the account ID provisionally configured, `pull-data.js` validated Google Ads access successfully and then failed:

   ```
   Error [oauth-failed]: Could not exchange GOOGLE_ADS_REFRESH_TOKEN for an access token.
   Route: /merchant-auth Stay Cold Apparel
   ```

   The stored refresh token carries Ads scopes but not Merchant scopes. This cannot be fixed from here — regenerating it requires an interactive browser sign-in.

**To unblock:** run `/merchant-auth "Stay Cold Apparel"`. It regenerates a refresh token with both Ads and Merchant scopes and validates each API. The account ID is already saved in config, so that step is pre-answered. Then re-run `/feed-auditor full`.

`merchantCenter.enabled` has been left at **false** deliberately — claiming otherwise would make future runs fail confusingly.

---

## What could still be established from Google Ads data

`shopping-products.csv` (1,817 products) and `shopping-performance.csv` carry product status and Merchant issue payloads as surfaced through Google Ads. That is a fraction of what a real feed audit reads — no titles/descriptions at length, no image data, no attribute completeness beyond what Ads echoes — but it answers three questions left open by the audits run earlier today.

### 1. Not a single product is fully eligible

| Status | Products | Share |
|---|---|---|
| `ELIGIBLE_LIMITED` | 817 | 45.0% |
| `NOT_ELIGIBLE` | 1,000 | 55.0% |
| `ELIGIBLE` (unrestricted) | **0** | **0%** |

| Availability | Products | Share |
|---|---|---|
| `IN_STOCK` | 1,095 | 60.3% |
| `OUT_OF_STOCK` | 722 | 39.7% |

**The actionable cell is 278 products that are IN_STOCK but NOT_ELIGIBLE** — sellable inventory that cannot serve. The 722 out-of-stock products are structural: business.md documents the drop model and a high sold-out rate as an accepted business characteristic, not a feed defect.

### 2. Which issues actually matter — three of the loudest are irrelevant here

Every issue carries `affected_regions`. Reading the counts without that field produces a badly wrong conclusion, so the split matters:

| Issue | Products | Affects DE? | Verdict |
|---|---|---|---|
| **Missing `color`** | **1,009 (55.5%)** | ✅ **Yes** (BR, DE, FR, GB, JP, US) | **Real — the largest DE-relevant defect** |
| **Missing `age group`** | **674 (37.1%)** | ✅ **Yes** | **Real** |
| **Missing `gender`** | **674 (37.1%)** | ✅ **Yes** | **Real** |
| `landing_page_error` — "Product page unavailable" | 6 (0.3%) | ✅ Yes | **Real, small, and easy** |
| `invalid_currency_for_country` | 1,817 (100%) | ❌ No — **KR only** | Noise for a DE feed |
| `missing_shipping_no_shipping_service_defined_for_country` | 1,817 (100%) | ❌ No — **BR, KR only** | Noise for a DE feed |
| `missing_business_registration_number` | 1,817 (100%) | ❌ No — literally *"Missing Korean business registration number"* | Noise for a DE feed |
| `not_eligible_out_of_stock` | 722 (39.7%) | region-agnostic | Structural (drop model) |
| `not_eligible_in_any_campaign` | 432 (23.8%) | region-agnostic | **Targeting gap — see below** |

⚠️ **Do not report "100% of products have three critical errors."** Those three affect Korea and Brazil. This feed serves Germany only. The DE-relevant story is apparel attributes.

**Why the apparel attributes matter here specifically.** Colour, size, age group and gender are *required* attributes for Apparel & Accessories in DE, FR, GB, US, JP and BR. Products missing them get demoted or excluded rather than hard-disapproved — which matches the data exactly: 376 of the colour-missing products are `ELIGIBLE_LIMITED` (serving, restricted) and 633 are `NOT_ELIGIBLE`. This is a plausible contributor to the **31.1% rank-lost impression share** the competitive audit measured on FOKUSPRODUKTE, and to the fact that no product in the feed is unrestricted.

### 3. The five dead PMax campaigns have no products at all

`shopping-performance.csv` contains only **four** campaigns:

| Campaign | Products served | Cost | Impressions |
|---|---|---|---|
| `EX I WW I PMAX … FEED ONLY I PROSPECTING` | 840 | €10,873 | 4,056,989 |
| `EX I SHOPPING I FOKUSPRODUKTE` | 850 | €9,908 | 999,196 |
| `EX I WW I PMAX … OVER-INDEX + INDEX + NEAR-INDEX` | **13** | €399 | 489,237 |
| `EX I SHOPPING I PUR I T-ROAS I NEAR INDEX` | **1** | €24 | 544 |

The five zero-impression PMax campaigns — `SCALING I BROAD`, `SKANDI I TESTING I PROSPECTING`, `FRA I TESTING I BROAD`, `USA I TESTING I BROAD`, `WW I PROSPECTING I BROAD` — **appear nowhere.** Zero products. Combined with the account audit's finding that they have no ad groups in the data, the most likely explanation is that they have no asset group with a populated listing group, so there is no inventory for them to serve.

This narrows AUD-D08 considerably: the cause is **product coverage, not budget, bid strategy or approval status**. Fixing bids or budgets on them would change nothing.

**Two more campaigns are explained the same way.** `OVER-INDEX` reaches 13 products and `NEAR INDEX` reaches exactly 1. Three audits flagged these for running smart bidding below the conversion floor and treated them as consolidation candidates on volume grounds. The real reason is upstream: **they cannot generate volume because they are pointed at almost no inventory.** That is a sharper diagnosis than "sub-scale," and it argues for fixing or retiring the product-group definitions rather than merging the campaigns on bidding grounds alone.

### 4. Attribute basics that are fine

| Attribute | Missing |
|---|---|
| `brand` | 0 — all 1,817 are "stay cold apparel" |
| `category_level1` | 0 |
| `title` | 0 |
| `price` | 0 (none zero) |

Feed plumbing is intact. The gaps are specific apparel attributes, not wholesale data loss.

---

## What a real feed audit would still add

Everything above comes from Ads-side echoes. The five modules would additionally cover:

| Module | What is still unknown |
|---|---|
| `errors` | Merchant-side account health, disapproval reasons, policy issues, and the destination-level breakdown |
| `completeness` | Real attribute coverage across the full schema — `size`, `material`, `pattern`, GTIN/MPN, shipping weight |
| `attributes` | `product_type` depth, Google taxonomy accuracy, custom-label usage (business.md notes `custom_label_0/1/2` metafields are live and usable for design/artist/GSM segmentation — entirely unexamined) |
| `title-desc` | Title and description structure, keyword coverage, boilerplate, truncation |
| `images` | Image quality, promotional overlays, whitespace, resolution — and business.md's documented **"PDP truth gap"** ("shop photos vs. the real product") is an *image* problem the competitive audit already tied to below-average landing page experience |

That last row is the one worth chasing. Today's competitive audit found landing page experience rated BELOW AVERAGE on six of six scored non-brand keywords, and business.md independently names the PDP truth gap as an open risk. The images module is the direct test of whether feed imagery is part of that.

---

## Sequenced next steps

1. **`/merchant-auth "Stay Cold Apparel"`** — interactive, ~2 minutes, needs a browser sign-in. Account ID `116274940` is already in config. Then set `merchantCenter.enabled: true`.
2. **`/feed-auditor full`** — re-run. Single feed label DE, so no main-market question will be asked.
3. **Independent of the above,** two findings are already actionable:
   - **Add `color`, `age group` and `gender` to the feed.** 1,009 / 674 / 674 products respectively, all DE-relevant, all required attributes for apparel. This is source-feed work (Shopify → Merchant), not something the ads layer can patch — though business.md notes Google Shopping metafields are already live, which may make it a mapping change rather than a data-entry project.
   - **Fix 6 products with `landing_page_error`** — "Product page unavailable." Small, unambiguous, and it also feeds the landing-page-experience problem.
4. **Investigate the 5 empty PMax campaigns as a product-coverage problem** — `/pmax-auditor` owns asset groups and listing groups. This report narrows the hypothesis for it.

---

## Data used

| Source | Rows | Date |
|---|---|---|
| `context/google-ads/data/shopping-products.csv` | 1,817 | 2026-08-03 (gads-context) |
| `context/google-ads/data/shopping-performance.csv` | 1,704 | 2026-08-03 |
| `context/google-ads/data/product-groups.csv` | 11 | 2026-08-03 |

No Merchant API data was retrieved. `context/feed/cache/` was not created. No module scores, no queue CSVs, no evidence summary — those require the pull that could not run.
