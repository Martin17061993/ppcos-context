# Brand Colour Palette - Stay Cold Apparel

Extracted from: https://www.staycoldapparel.com
Generated: 2026-08-03

---

## Colour Palette

| Hex | RGB | Usage Contexts | Frequency |
|-----|-----|----------------|-----------|
| `#ffffff` | rgb(255, 255, 255) | body-bg, h1-text, nav-text, cta-text, section-bg, hero panel | 18 |
| `#000000` | rgb(0, 0, 0) | announcement-bar-bg, header/nav-bg, footer-bg, body-text, h2-text, ADD TO CART bg | 17 |
| `#e52321` | rgb(229, 35, 33) | cta-bg — primary hero button "START RIOT" | 2 |
| `#f2a900` | rgb(242, 169, 0) | cta-bg — promo button "SHUT UP AND TAKE ME TO THE SHIRT" (Thunder Drop Deal) | 2 |
| `rgba(255,255,255,0.1)` | rgba(255, 255, 255, 0.1) | cta-bg — "Subscribe" button on black footer (ghost/outline style) | 1 |

> **Note on filtering:** the standard extraction filter drops pure black and pure white. That filter is wrong for this brand — black and white *are* the palette. Stay Cold runs a hard monochrome system (black chrome, white canvas) with two saturated accents used only on action elements. Both are retained deliberately.

## Typography

| Role | Font Family |
|------|-------------|
| Headings | `"StayCold Cond Medium", sans-serif` |
| Body | `"StayCold Cond Medium", sans-serif` |

Custom proprietary condensed display face used for *both* headings and body — heavy, condensed, all-caps-leaning. Not available as a webfont outside the site. For ad creative and landing pages, the nearest free substitutes are **Oswald**, **Barlow Condensed Semi Bold**, or **Anton** (display only).

## Suggested Colour Roles

| Role | Hex | Rationale |
|------|-----|-----------|
| Primary | `#000000` | Announcement bar, header/nav wrapper, footer inner, and ADD TO CART are all pure black — verified via `elementFromPoint` sampling and computed style, not just frequency. This is the brand's structural colour. |
| Accent | `#e52321` | Hero CTA "START RIOT" background. The only red on the page and the single highest-priority action element. |
| Accent 2 | `#f2a900` | Thunder Drop Deal promo CTA. Reserved for offer/promo messaging, never for standard navigation. |
| Background | `#ffffff` | `body` background-color; all content sections render white. |
| Text | `#000000` | `body` colour on white; inverts to `#ffffff` on black chrome. |
| Link | `#000000` | Inline links inherit body black, underline-on-hover; no distinct link colour. |

**Verification:** script output was cross-checked against a homepage screenshot after dismissing the cookie consent banner. The raw script reported header background as transparent — the black actually comes from the inner `div.header__wrapper`, confirmed by targeted extraction. Role assignments below reflect the visually-confirmed values, not the raw script output.

## Usage Recommendations

### Google Ads
- **Display / demand-gen ad background:** black `#000000` with white `#ffffff` type — matches the site chrome and the product photography, which is shot on dark/neutral grounds.
- **CTA buttons in display:** `#e52321` with white text. Reserve `#f2a900` exclusively for promo/offer creatives (Thunder Drop Deal, free-gift, sale) so the two accents stay semantically separate.
- **Text overlays on product imagery:** white on the dark half, black on the light half — the site's hero uses exactly this split (image left on dark grey, copy right on white).
- **Avoid:** introducing any additional hue. This brand has no tertiary palette; product colourways (beige, sand, purple, camo, petrol) come from the garments, not the brand system.

### Landing Pages
- **Hero:** black band or full-bleed product image, white condensed all-caps headline, `#e52321` CTA.
- **CTA buttons:** `#e52321` / white text for "buy" intent; black / white text for secondary ("ADD TO CART" on-site is black, so black reads as native).
- **Body sections:** white background, black text — high contrast, no grey mid-tones in the system.
- **Promo bars / urgency strips:** `#f2a900` with black text (matches the on-site Thunder Drop Deal treatment and gives WCAG-safe contrast).
- **Section dividers:** black rules at full opacity; the brand does not use soft/tinted dividers.

### Contrast Notes (WCAG)
- `#ffffff` on `#000000` — 21:1. Passes everything.
- `#ffffff` on `#e52321` — ~4.6:1. Passes AA for normal text, fails AAA. Fine for buttons; avoid for small body copy.
- `#000000` on `#f2a900` — ~10.3:1. Passes AAA. This is why the site pairs amber with black, not white.
- Never put white text on `#f2a900` (~2.0:1, fails).

### Brand Consistency Notes
- The palette is deliberately austere: two neutrals + two action colours. Ad creative that adds gradients, pastels, or a third accent will read as off-brand immediately.
- Red is the "shop now" colour; amber is the "there's a deal" colour. Keeping that split consistent between site and ads gives free message-match.
- The custom condensed typeface is the strongest brand asset after the logo — condensed all-caps headlines matter more to recognition than exact hex matching in ad creative.

---
*Extracted by /ads-context-gatherer colour analysis (Chrome DevTools MCP)*
*Source: https://www.staycoldapparel.com*
