# LP Audit Log

## 2026-08-06 — Score: 56% (Needs Attention)

- **Mode:** full · 6 modules · 40 diagnostics · vertical ecommerce · 4 live final URLs + 1 collection page + 1 product page
- **Top finding — the mechanism eight prior audits pointed at:** the non-brand campaign sends punk/goth/metal searches to a homepage where **punk = 0, goth = 0, metal = 0, rocker = 0** occurrences across 1,716 words. The one subculture word present is "tattoo" (5×, incl. title) — and the two tattoo keywords are the only ones scoring **QS 7**; every punk/goth/metal keyword scores **4–5**. Exact correlation.

| Module | Score | Weight | Key finding |
|---|---|---|---|
| Structural | 69/90 (77%) | 30% | Trust bar strong (4.6/5, 6,477 reviews, 30-day returns, free shipping €89). Faults: 2× `<h1>`, Lighthouse accessibility 75 (button-name, select-name, colour-contrast all 0), 15/88 images without alt |
| **Message Match** | **3/30 avail (10%)** | 20% | **The audit.** D13 FAIL, D15 FAIL (Critical), D14 WARN, D16 SKIP (no Display/Video) |
| Technical | 33/58 avail (57%) | 20% | CLS 0.013 excellent, HTTPS ✅, mobile CVR *better* than desktop. FAIL: `maximum-scale=1.0` disables pinch-zoom + 51/168 tap targets under 44px |
| Performance | 24/43 (56%) | 15% | D29 FAIL — non-brand points at homepage while DSA correctly points at category pages. 2.04% CVR is in-band |
| URL Health | 33/39 avail (85%) | 10% | All 200 in a real browser. One avoidable redirect: non-brand uses the naked domain |
| Ecommerce | 15/25 (60%) | 5% | PDP has price/reviews/returns/shipping/stock but **no size guide** — and sizing is 54% of returns |

**Critical false positive caught and NOT reported as a finding:** `url-health-check.js` returned **403 on all 6 URLs**. That is bot protection against the script's user agent. Verified every URL loads normally in Chrome. An account producing 1,700+ monthly conversions cannot be serving 403s. Recorded so a future run does not re-raise it.

**The obvious fix does not exist:** of 32 collections in the sitemap, **not one** contains punk, goth, metal, rock, tattoo or oversized in its URL. They are organised by product type, drop, bestseller window and artist collab — never by subculture, which is the axis the keywords are bought on. `/collections/hoodies` body copy also has zero subculture terms (only `400gsm` ×10; the title tag alone says "Traditional Tattoo Sweaters"). Two collections named `featured-collection-prospecting` / `featured-collection-retargeting` already exist, suggesting the pattern was anticipated.

**Other findings:**
- Non-brand final URL is `https://staycoldapparel.com` (naked domain → redirects to www); all 4 brand campaigns use the correct www URL. Free fix
- Site serves `/en-us/` locale paths but USA brand points at the DE-default root
- Claim-vs-product mismatch for ad copy: business.md §10 claims "400gsm hoodies · 250gsm tees"; audited hoodie is **350GSM**, homepage hero tee is **200GSM**. 400gsm products do exist (10 mentions on the hoodies collection) — but generic claims should not outrun the flagship products
- Lighthouse mobile: Accessibility 75 · Best Practices 54 · SEO 92 · Agentic Browsing 75. 13 audits failed
- LCP and INP **not measured** — the Lighthouse mode used excludes the performance category

**Fresh peer reports integrated (no re-runs):** `/competitive-analyst` 73/100 (supplied the BELOW_AVERAGE finding this audit explains), `/keyword-auditor` 85% (routed here for the fix; this is the answer), `/bidding-auditor` 54/100, `/budget-auditor` 47/100, `/account-auditor` 75%, `/pmax-auditor`.

**Routing:** `/lp-optimizer message-match` (**top** — subculture language on category pages, then repoint) → `/ecom-page-builder` if that proves insufficient → `/lp-optimizer urls` (naked domain) → size guide (dev work) → `/lp-optimizer mobile` → `/offer-auditor`. **Rebuild not recommended** — 56% is above the sub-40% threshold and the page is a competent ecommerce homepage being misused as a paid landing page.
