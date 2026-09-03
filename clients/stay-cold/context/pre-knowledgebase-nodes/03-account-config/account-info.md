---
id: stay-cold.account-info
layer: customer
client: stay-cold
status: draft
triggers: [search-terms, keyword-optimization, ad-copy]
topics: [account, tracking, guardrails]
language: en
last_reviewed: 2026-07-21
---
# Client: Stay Cold Apparel

> DRAFT v2 (2026-07-21). Sources: change-impact analysis 2024–2026 + campaign index (as of 2026-07-03) + Stay Cold Notion Knowledge Base (full crawl 2026-07-21).
> Items marked `TODO(Martin)` must be verified before the first production run.
> **Working language for this client is ENGLISH** — all agent chat output, reports, sheet entries and proposals for Stay Cold are written in English.

## Account Identification
- **Google Ads Customer ID:** 3599116618 (359-911-6618)
- **MCC:** 5591362086 (Jonas Makki)
- **Website:** https://staycoldapparel.com (Shopify Plus; internal shop handle `rapid-4.myshopify.com`)
- **Legal entity:** MASCANI GMBH
- **Stakeholders:** Founder circle Max1 (Maximilian Abraham), Vuven (Vivian Meurer), Jonas Makki, Maxobert (Max Algermissen). Performance Marketing area: Jonas (internal), Martin (external, Google Ads), Valentin Hertweck (external — role split TODO(Martin): clarify, presumably Meta).

## Business Context
- **Industry:** D2C e-commerce — heavyweight apparel (metal / tattoo / dark streetwear culture). Founded Berlin 2015, no investors, ~€10M revenue 2024.
- **Brand core:** "Built Without Permission." / "Defeat Conformity. Stay Cold." Communication targets ONLY the core audience (70%: metal, tattoo, hardcore, dark streetwear); the culture-adjacent 25% follow on their own and are never addressed directly.
- **What Google Ads promotes:** direct product sales (Purchase). Core: Shopping (Fokusprodukte), PMax, brand search. Sales/promos (BFCM, Black Spring Sale) are a core tactic.
- **Product model:** "Drops, not seasons." Thunder Drop Weeks = Friday drops with a deal product (~1 week); daily drops last one day. Drop planning lives in the Airtable **Drop Base** (Planned Activations: early-access + public go-live windows, AIC dates, drop dates).
- **Offer rules (LOCKED by Max1, 2026-05-08):** no sitewide discounts; no discounts on new drops in the first 90 days; discounts only on Black Friday and only on slow movers. → No sale messaging in ads outside these rules.
- **Markets:** DACH/DE, USA, FRA, SKANDI, WW-EN. Community across Europe, USA, Japan.
- **Spend level:** ~€40–62k/month (H1 2026); ~€50k after the 2026-06-30 saturation correction.
- **Clean ROAS June 2026:** 5.04 (account surface shows 7.85 — see Tracking).
- **DB1 margin:** not available in the account → profitability of non-brand activity (clean ROAS ~2.4, 90-day view) cannot be judged without margin input.
- **Competitors (per Marketing Cheat Sheet):** Killstar, DropDead, Disturbia, Sullen, Named Collective, Blackcraft Cult, Bad Monday.
- **Strategic note:** Stay Cold's active Marketing Cheat Sheet v0.1 does NOT define Google as a channel — it is listed as open question #1 ("Is Google (Search/PMax) still an active acquisition channel, and what's its role?"). Until that role is defined, treat channel positioning as an open strategic thread with Jonas.

## Account Tier (Brain reference)

Monthly budget > €50k (H1-2026 level) → **Tier 3** → 14-day lookback.
Note: search is only ~13% of spend (~€6–7k/month). If search-terms data volume is too thin in a 14-day window, extend lookback to 30 days (deliberate deviation — document it here).

**This account's tier:** 3

## Channel Mix (spend since 2026-04-01, from perf_campaign_daily)

| Channel | Spend | Share | Search-terms agent? |
|---|---|---|---|
| Shopping | ~€75k | 48% | Yes — in scope since 2026-07-22 (negatives only) |
| Performance Max | ~€53k | 34% | No (PMax search terms not in search_term_view) |
| Search | ~€21k | 13% | Yes — core scope |
| Video / Demand Gen | ~€7k | 5% | No |

## Exceptions vs. Brain

```markdown
## Exceptions vs. Brain
- Evaluation basis: judge EVERY number on the purchase-only series, never on the
  reported account ROAS. Since 2025-11-10 the account double-counts purchase +
  NewCustomerPurchase (inflation ×1.49–1.57). (Guardrail DON'T-7)
- Promo calendar: inside documented promo windows (promo_windows.csv) step-size
  and rest rules do NOT apply — intraday scaling is a legitimate tactic there.
  Outside them they apply strictly. (Guardrail DO-4)
- Brand campaign protection: the 4 brand search campaigns (FRA/DE/USA/SKANDI)
  are do-not-touch — no keyword removals, no negatives, no broad match, bids
  upward only. Stricter than the generic Brain top-performer protection.
  (Guardrail DON'T-4)
- No same-day batch rollouts across all markets — stagger changes per market
  (1–2 weeks). Also applies to large negative-keyword batches. (Guardrail DON'T-9)
- Offer rules override generic promo heuristics: no discount framing outside
  Black Friday slow-mover scope (locked business rule, source: 03 Product +
  Offer Cheat Sheet v0.1).
```

Full evidence-based guardrails: `system-prompts/agents/change-impact-agent/reporting/stay-cold/rag/sc_gads_guardrails.md` — mandatory reading for every agent on this account.

## Tracking Setup

- **Primary conversion:** Purchase (`purchase_gads_mable`)
- **Known issue:** since 2025-11-10 NewCustomerPurchase counts additionally → reported ROAS/conv. value inflated ×1.49–1.57. Decisions ONLY on the purchase-only series.
- **Third-party attribution:** Stay Cold uses **Tracify** (owner: Jonas). Expect diverging channel numbers; align on which number governs before any ROAS debate. TODO(Martin): get Tracify's view of Google.
- **Auto-apply:** keyword/asset auto-apply is disabled and stays off (Guardrail DON'T-5); bidding auto-apply paused since 2026-07-03.
- **B2B:** wholesale orders exist (`is_b2b_order` in Shopify) and are excluded from Stay Cold's internal revenue reporting — keep GAds revenue discussions consistent with that.

## Notes / History

- 2026-06-30: Budget cut Fokusprodukte 1,600 → 550 EUR/day (saturation correction)
- 2026-07-03: Change-impact analysis 2024–2026 completed
- 2026-07-21: Full Notion KB crawl; file rewritten in English (business language), enriched with brand/offer/ops facts
