---
id: stay-cold.search-terms-rules
layer: customer
client: stay-cold
status: draft
triggers: [search-terms, keyword-optimization]
topics: [search-terms, negatives, brand-protection]
language: en
last_reviewed: 2026-07-21
---
# Stay Cold — Search Terms Rules

> DRAFT v2 (2026-07-21), English (client business language). Verify all `TODO(Martin)` items
> (especially shared negative list names and thresholds) in the account before the first run —
> `pull_search_terms` aborts without this file, but wrong list names fail silently downstream.
> **All agent output for this client (chat reports, sheet entries, reasoning) is written in English.**

## Account Context
- **Customer ID:** 359-911-6618 · **MCC:** 5591362086
- **Budget:** ~€50k/month total; search share ~€6–7k/month (~13%)
- **Match types:** non-brand search campaign is Broad Match (TOF campaign); brand campaigns exact/phrase
- **Industry:** D2C e-commerce, heavyweight apparel (metal/tattoo/dark streetwear)
- **Audience:** core scene audience (metal, tattoo, hardcore, dark streetwear), markets DE/DACH, USA, FRA, SKANDI, WW-EN
- **Primary conversion:** Purchase — ALWAYS evaluate on the purchase-only series (reported values inflated ×1.49–1.57 since 2025-11-10)

---

## Agent Scope on This Account

**Scope confirmed 2026-07-22 (Martin):** Shopping IS in scope. `get_search_terms_raw` returns Search AND Shopping terms (verified: ~80% of cost-bearing terms sit in Shopping). The agent analyzes and proposes **negatives only** for Shopping campaigns — ADD_KEYWORD is impossible there (no keywords; enforced in the rule engine). PMax (34% of spend) remains out of reach via `search_term_view` — known limitation.

### Campaigns in scope (ENABLED, as of 2026-07-03)

| Campaign | Type | Role | Agent behavior |
|---|---|---|---|
| `EX I EN I WW I TOF I BROAD I PUR I T-CPA II BROAD I NO PROMO I Kollektionen + Types` | Search, Broad | Only active non-brand search (~€8.5k/quarter) | **Core scope**: ADD_NEGATIVE + ADD_KEYWORD |
| `JM I DSA I FC'S I CAT'S` | DSA | Dynamic Search (Jonas) | ADD_NEGATIVE allowed; no ADD_KEYWORD (DSA has no keywords) |
| `EX I SHOPPING I FOKUSPRODUKTE` | Shopping | Main spender (~48% of account spend with NEAR INDEX) | **In scope since 2026-07-22**: ADD_NEGATIVE only |
| `EX I SHOPPING I PUR I T-ROAS I NEAR INDEX` | Shopping | Secondary shopping | **In scope since 2026-07-22**: ADD_NEGATIVE only |
| `EX \| DE \| SEARCH \| BRAND` | Search | Brand DE | **PROTECTED — observe only** |
| `EX \| USA \| SEARCH \| BRAND` | Search | Brand USA | **PROTECTED — observe only** |
| `EX \| FRA \| SEARCH \| BRAND` | Search | Brand FRA | **PROTECTED — observe only** |
| `EX \| SKANDI \| SEARCH \| BRAND` | Search | Brand SKANDI | **PROTECTED — observe only** |

---

## Negative Keyword Lists (Shared Sets)

TODO(Martin): verify in the account which shared sets actually exist and correct this table.
Do NOT copy the Kollabo names blindly — the rule engine writes into exactly the lists named here.

| Shared set | Applied to | Content | Status |
|---|---|---|---|
| `TODO_NKL_Generic` | Account-wide (excluding brand campaigns) | Irrelevant terms without purchase intent | TODO: exists? name? |
| `TODO_NKW_Brand` | Non-brand campaigns only | Stay Cold brand variants → route traffic to brand campaigns | TODO: exists? name? |
| `TODO_NKW_Competitor` | TODO | Other apparel brands | TODO: wanted at all? There is NO active competitor campaign — foreign brand terms are NOT automatically relevant here |

### Classification rules (draft — adapt to real lists)

**Generic/irrelevant** — belongs here:
- Queries without purchase intent: "diy", "how to make", "tutorial", "meaning", "wiki", "history of"
- Free/fake/replica queries: "free", "fake", "replica", "knockoff", "cheap alternative"
- Job/career queries ("stay cold jobs" → note brand protection: never negative without human review)
- B2B/wholesale queries ("wholesale", "b2b", "reseller", "bulk") — wholesale exists as a separate passive channel; paid search should not buy it. TODO(Martin): confirm with Jonas.
- Product categories Stay Cold does not carry. Catalogue (Airtable, 37 categories) covers apparel + accessories: hoodies, tees/jerseys, jackets, pants/joggers, shorts, caps, socks, accessories, women's line. NOT carried (examples): shoes/sneakers, jewelry, perfume. TODO(Martin): confirm boundary list.

**Brand variants** (→ brand routing list, applied to non-brand campaigns ONLY):
- stay cold, staycold, stay cold apparel, staycold apparel, stay cold apparell, stay-cold, staycoldapparel + typo variants
- Brand+product queries ("stay cold hoodie") also belong to brand campaigns, not non-brand

**Foreign brands:**
- Known direct competitors (from Stay Cold's own Marketing Cheat Sheet): **Killstar, DropDead, Disturbia, Sullen, Named Collective, Blackcraft Cult, Bad Monday** — plus other streetwear/metal brands.
- Default for foreign-brand terms in non-brand search: **IGNORE** (do not auto-negate — scene shoppers with brand overlap can convert). Only propose ADD_NEGATIVE at measurable spend without purchase above threshold.

---

## Hard Rules (agent must NOT override)

1. **Absolute brand protection:** no term matching `stay ?cold` is ever proposed as a negative — in any campaign, in any list.
2. **Brand campaigns are do-not-touch** (Guardrail DON'T-4; measured swings −32% to +396% from smallest interventions): the agent writes NO proposals for the 4 brand campaigns — neither negatives nor keywords. Escalate observations (e.g. irrelevant terms with spend) as notes in the final report; a human decides.
3. **No same-day batches across all markets** (Guardrail DON'T-9): stagger large negative packages per market/campaign.
4. **Purchase-only evaluation** (Guardrail DON'T-7): CPA/ROAS arguments in proposals reference the purchase-only series; never cite reported conversions after 2025-11-10 as evidence.
5. **ADD_KEYWORD only into the non-brand TOF campaign**, exact match only. Never propose new campaigns/ad groups.
6. **No discount/sale framing in any proposal reasoning or keyword suggestion** outside documented Black Friday slow-mover scope (locked offer rule, 03 Product + Offer Cheat Sheet).

---

## Language Rules

- Non-brand scope is the **EN/WW campaign**: English terms are the norm.
- German/French/Scandinavian **brand** terms run through the respective brand campaigns (protected, no agent action).
- Non-English non-brand terms in the WW campaign: no automatic negative (WW targeting), but treat normally as WASTED at spend without purchase above threshold.

---

## Thresholds (draft — TODO(Martin) verify)

Reference: search spend ~€6–7k/month, 14-day lookback (Tier 3). Extend to 30 days if data is thin.

| Metric | Threshold | Action |
|---|---|---|
| Spend without purchase | > €50 | Flag as WASTED |
| Clearly irrelevant term with spend | > €10 | Propose ADD_NEGATIVE immediately |
| Min. clicks for a decision | 20+ | Below 20 clicks = MONITOR/IGNORE |
| ADD_KEYWORD candidate | ≥ 2 purchases AND ROAS ≥ campaign average (purchase-only) | Exact-match proposal into TOF campaign |

## Competitor Patterns (master registry column K)

No active competitor campaign in the account → column K stays **empty**.
(Historic "Kampagne 1.0 Konkurrenz" is REMOVED.)

## Notes / History

- 2026-07-21 v2: rewritten in English; enriched with locked offer rules, competitor list, assortment boundaries, wholesale exclusion (source: Notion KB crawl 2026-07-21)
- 2026-07-21 v1: initial draft from campaign index + change-impact guardrails
