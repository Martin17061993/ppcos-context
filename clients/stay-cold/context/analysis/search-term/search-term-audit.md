# Search Term Audit — 2026-08-06

**Score:** 73 / 92 available — **79% · Good**
**Scope:** full · 26 diagnostics · 5 modules · branded campaigns excluded · experiments excluded
**Periods:** main 60d (lag 8) · n-grams 120d · **678,033 terms Period A** / 596,945 Period B / 242,927 PMax terms
**Account:** 3599116618 (Stay Cold Apparel) · EUR · target ROAS **2.5** (non-brand), break-even **1.9**

---

## Executive read

The script's headline says 31.7% of spend is irrelevant. **That number is right arithmetically and wrong strategically, and correcting it is the main job of this report.**

Of the €18,236 flagged as non-converting, **€10,425 (57%) sits on core product terms** — hoodie, shirt, tattoo, punk, goth, metal. Another **€2,141 is competitor brand names**, which business.md §9 explicitly forbids negating: *"do not auto-negate foreign brands (scene shoppers with brand overlap convert)."* And **€479 is your own brand leaking into non-brand campaigns**, which the account's hard rule says must be routed, never negated. What is actually left as a genuine negation candidate is **€5,191 — roughly 9% of spend, not 31.7%.** Acting on the headline number would have negated the front door of the business.

**The single largest n-gram finding closes the loop on the whole session.** `goth clothing` — 26,380 impressions, 254 clicks, **€345, zero conversions** across 357 distinct queries. "Goth" is a core product token. And today's landing page audit found the word "goth" appears **zero times** on the page that traffic lands on. This is not a bad n-gram; it is a good n-gram pointed at a page that never mentions what the searcher asked for. Negating it would delete demand instead of fixing the page.

**One documented guardrail is now confirmed with hard data.** business.md says competitor terms convert. They do: `killstar` returns **10 conversions at ROAS 8.11** on €133, and `civil regime` **11 conversions at ROAS 14.58**. Killstar is on the account's own named-competitor list. Do not touch these.

**Two things genuinely worth doing.** First, €5,191 of real waste is negatable — `tracksuit`, `techwear`, `zalando`, `uniqlo`, `zumiez`, `pump cover`, `badehose`, plus band-merch queries for other artists. Second, **PMax brand query share is 0%**, which finally resolves the account audit's open AUD-D02 warning: PMax is not cannibalising brand.

Read the Diagnosis, then the "Do NOT negate" table — it is longer than the "act now" one, and that is the finding.

---

## Diagnosis

**The problem is not at the Traffic layer.** The account's search terms are broadly well-matched to what it sells; the waste concentrates on core-category queries that arrive and then fail to convert. Of the 1,800 non-converting terms, 1,102 contain a core product token and account for 57% of the flagged spend — and the largest single n-gram, `goth clothing`, is a term the business would obviously want to win. Today's landing page audit established why they fail: the page receiving this traffic contains zero occurrences of punk, goth, metal or rocker, so a searcher arriving on a category query sees a brand slogan and a single hero product. That is a conversion problem wearing a traffic problem's clothes. The correct sequence is to fix the destination, re-measure, and only then revisit which terms genuinely do not belong — of which there are about €5,191 worth, concentrated in adjacent-but-wrong categories (activewear, techwear, swimwear) and general retailers (Zalando, Uniqlo, Zumiez). Two structural items are safe to do immediately and independently: route the €479 of brand queries leaking into non-brand campaigns back to the brand campaigns, and close the negative-keyword gap on the two serving Performance Max campaigns.

---

## Portfolio notice

No portfolio bid strategies exist in this account — `bidding-strategies.csv` returned 0 rows. Every flagged record carries `target_source = campaign_inline`, so all targets are campaign-level and directly attributable. **No record fell back to a missing target**, which means the B0 target-source gate is clean and no campaign is unconstrained.

---

## Evidence ladder

### Measurement layer — H1 (active, but narrower than usual)

- No tracking audit exists → the account-wide conversion-value inflation (×1.28–1.94) remains unresolved → **H1**
- **Crucial per-campaign nuance:** the non-brand Search campaign has inflation factor **1.00** — it is the one campaign on the clean account-default conversion goal (business.md §6; account audit AUD-D24). Its term-level economics are already clean → **H1 downgraded for Search TOF**
- Shopping and PMax terms **are** inflated (FOKUSPRODUKTE 1.81, PMax PROSPECTING 1.88, NEAR INDEX 1.28). Since 90% of flagged spend sits in those two campaigns, their ROAS figures are optimistic — deflating makes the waste case *stronger*, not weaker → **H1**

### Business layer — H2 (active, blocks most negations)

- **B2 relevant-but-underperforming: 1,102 of 1,800 non-converting terms (€10,425, 57%) match core product tokens** → **H2 — do not negate**
- **business.md §9 hard rule:** *"Competitor terms — no active competitor campaign; do not auto-negate foreign brands (scene shoppers with brand overlap convert)."* 119 terms / €2,141 → **H2**
- **Validated with data:** `killstar` 10 conv @ ROAS 8.11 (€133); `civil regime` 11 conv @ ROAS 14.58 (€169). Both are competitor brands and both clear the 2.5 target comfortably → **H2 confirmed**
- **business.md protectedTerms hard rule:** *"no term matching 'stay ?cold' is ever proposed as a negative, in any campaign or list… Brand+product queries route to brand campaigns, they are never negated outright."* 38 terms / €479 → **H2**
- The n-gram engine independently respected this: **1,766 safe-list conflicts** were caught and suppressed before any candidate was proposed → **H2, guardrail working**

### Traffic layer — H3 (the residual, and it is small)

- After removing core, competitor and brand terms: **541 terms / €5,191 = 9.0% of spend** are genuine negation candidates → **H3**
- Concentrated in adjacent-but-wrong categories: activewear (`pump cover`, `gymshark`-adjacent), techwear, swimwear (`badehose`), general retail (`zalando`, `uniqlo`, `zumiez`), and other artists' band merch (`bad omens merch`) → **H3**
- Coverage gap: 2 serving PMax campaigns carry no campaign-level negative keywords → **H3**

---

## Module scores

| Module | Score | Grade | Key finding |
|---|---|---|---|
| Search Term Quality | 18 / 25 | **72% — Good** | 1,800 non-converting terms, but 57% are core-product and must not be negated |
| Negative Keyword Coverage | 20.2 / 25 | **81% — Good** | Zero conflicts, zero duplicates, zero legacy syntax. Gaps are almost entirely PMax and dormant campaigns |
| N-gram Analysis | 9.6 / 12 available | **80% — Good** | Only one candidate — and it is a core term whose fix is upstream |
| Close Variant Monitoring | 15 / 15 | **100% — Excellent** | No drift, no disproportionate variant spend |
| Promotion & PMax | 10.2 / 15 | **68% — Needs attention** | 863 promotion candidates, 0% coverage. **PMax brand query share 0%** |
| **Overall** | **73 / 92 available** | **79% — Good** | |

*8 points removed as SKIP: ST-D15 (list staleness — no data returned) and ST-D16 (volume concentration — not computed by the engine). ST-D23 and ST-D24 are removed by design.*

---

## Actions — segmented by cascade state

### 🔍 Investigate first

- **Resolve the conversion-value inflation before trusting any Shopping or PMax term economics.** 90% of flagged spend sits in FOKUSPRODUKTE (€11,207) and PMax PROSPECTING (€5,228), both on inflated series. **Review the existing 2026-08-06 bidding audit** at `context/analysis/bidding/bidding-audit.md` — 54/100, top finding: *"an enabled conversion value rule adds +€42.20 per conversion against €16.46 documented, and 14 of 15 campaigns override the clean account-default conversion goal."* Deflating makes this audit's waste case stronger, not weaker. **No re-run needed** → then `/tracking-specialist`

### 🔧 Structural fix needed — this is where the money is

- **Fix the landing page, then re-measure the core-term waste.** €10,425 of non-converting spend sits on core product terms, and the largest n-gram (`goth clothing`, €345, 0 conversions, 357 distinct queries) is a word that appears **zero times** on the destination page. **Review the existing 2026-08-06 landing page audit** at `context/analysis/lp/lp-audit.md` — 56%, top finding: *"punk, goth, metal and rocker appear zero times across 1,716 words; the only subculture word present is 'tattoo', and the two tattoo keywords are the only ones scoring QS 7."* **No re-run needed** → `/lp-optimizer message-match`
- **Deploy the offer language that already exists.** **Review the existing 2026-08-06 offer audit** at `context/analysis/offer/offer-audit.md` — 97%, top finding: *"the offer scores 97 with zero failures; the material needed to fix the landing page is already documented in brand.md."* → `/offer-maker angles`
- **Route the €479 of brand leakage to brand campaigns — do not negate it.** business.md's hard rule is explicit. The largest are `staycold apparel discount code` (€67, Search TOF), `stay cold apparel hoodie` (€54, FOKUSPRODUKTE), `stay cold apparel sale` (€24). Also present: `is staycoldapparel legit` (×2, €27 combined) and `staycoldapparel review` / `staycold apparel review` (€31 combined) — **reputation queries**, high-intent and currently landing nowhere useful

### ✅ Act now (safe)

- **Negate the €5,191 of genuine non-core, non-competitor waste** — 541 terms. Highest-spend examples: `tracksuit` €50, `techwear` €44, `badehose` €31, `zalando` €31, `zumiez` €30, `uniqlo` €29, `pump cover` €28, `bad omens merch` €48 (another band's merch), `vlone` €37, `chrome hearts` €37, `teddy fresh` €33. → `/search-term-optimizer negate`
- **Add campaign-level negative keywords to the two serving PMax campaigns** — `EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING` and `OVER-INDEX`. Both currently have none. → `/search-term-optimizer negate`
- **`staycool` (€46) needs a human glance before negating** — one letter from the brand name. Almost certainly a different advertiser's brand, but worth confirming rather than auto-negating given the protected-terms rule.

### ⚠️ Do NOT negate — and this list is longer than the one above

| Category | Terms | Spend | Why not |
|---|---|---|---|
| **Core product terms** | 1,102 | **€10,425** | Match business.md's documented scene core (hoodie, shirt, tattoo, punk, goth, metal, streetwear). These are the categories the business exists to rank for. The failure is the destination page, not the query |
| **Competitor brands** | 119 | €2,141 | business.md §9 hard rule. **Proven with data this run:** `killstar` 10 conv @ ROAS 8.11, `civil regime` 11 conv @ ROAS 14.58 — both clear the 2.5 target |
| **Own brand queries** | 38 | €479 | business.md protectedTerms hard rule — route to brand campaigns, never negate |
| **`goth clothing` n-gram** | 357 queries | €345 | Core token. Negating it removes an entire subculture from the account while the page that fails them stays broken |

---

## Module details

### Module 1 — Search Term Quality (18/25)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| ST-D01 | Irrelevant spend % | WARN | 3/5 | Engine reports **31.7%** (€18,236 of €57,515). **Genuine irrelevance is 9.0% (€5,191)** once core, competitor and brand terms are removed. The headline overstates by a factor of 3.5 |
| ST-D02 | Non-converting terms | **FAIL** | 0/5 | 1,800 terms, €18,236. By campaign: FOKUSPRODUKTE 1,109 terms / €11,207 · PMax PROSPECTING 502 / €5,228 · Search TOF 151 / €1,495 · DSA 19 / €144 · OVER-INDEX 11 / €83 · NC DEALS PUSH 7 / €67 · NEAR INDEX 1 / €13. Material regardless of how it decomposes |
| ST-D03 | Underperforming terms | **PASS** | 5/5 | Only **25 terms** clear the ≥€50 / ≥3-click threshold while missing the 2.5 target. Notably small for an account this size |
| ST-D04 | Foreign language | **PASS** | 5/5 | German terms appear (`badehose`, `motorrad hoodie`, `rabattcode`) but **Germany is the primary market** — not foreign-language waste. No genuinely out-of-market language found in the high-cost sample |
| ST-D05 | Trending terms | **PASS** | 5/5 | 1,226 terms trending Period A vs B. Informational; no action |

### Module 2 — Negative Keyword Coverage (20.2/25)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| ST-D06 | Campaigns without negatives | WARN | 2.4/4 | 15 flagged — **but the composition matters**: 11 are Performance Max, 3 are paused Search TOF variants (DACH, UK), 1 is the paused ESP brand campaign. **Zero actively-serving Search or Shopping campaigns lack negatives.** The real gap is the 2 serving PMax campaigns |
| ST-D07 | Campaigns without shared lists | WARN | 2.4/4 | 16 flagged, same composition |
| ST-D08 | Negative conflicts | **PASS** | 4/4 | **Zero.** No negative blocks a keyword it shouldn't |
| ST-D09 | Repeated ad-group negatives | **PASS** | 3/3 | Zero |
| ST-D10 | Repeated campaign negatives | **PASS** | 3/3 | Zero |
| ST-D11 | Legacy +modified +broad syntax | **PASS** | 3/3 | Zero. Clean, modern syntax throughout |
| ST-D12 | Catalog completeness | WARN | 2.4/4 | 3,213 shared negatives + 21 campaign + 1 ad group. **But the distribution is lopsided:** 3,135 of the 3,213 belong to `EXCLUSIONS FOR BRAND`, leaving only 78 in the general-purpose `EX I ALL` list. Generic waste patterns (adjacent categories, general retailers, other artists' merch) are thinly covered — which is exactly where the €5,191 of genuine waste got through |

### Module 3 — N-gram Analysis (9.6/12 available)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| ST-D13 | Non-converting n-grams | WARN | 3.6/6 | **Exactly one candidate: `goth clothing`** (2-gram) — 26,380 impressions, 254 clicks, **€344.83, 0 conversions**, 357 distinct terms. Correctly identified. But "goth" is a core product token, so the action is upstream, not a negation |
| ST-D14 | Inefficient n-grams | **PASS** | 6/6 | Zero. No n-gram is converting inefficiently |
| ST-D15 | Shared list staleness | **SKIP** | —/4 | Engine returned an empty object — no staleness data computed |
| ST-D16 | Volume concentration | **SKIP** | —/4 | Not computed by the engine on this run |

**The safe-list guardrail worked.** The engine evaluated 1,048,603 eligible n-gram rows and generated 495,644 raw candidates, then caught **1,766 safe-list conflicts** — candidates that collided with `protectedTerms.neverExclude` — and suppressed them before proposing anything. The `stay cold` protection held.

### Module 4 — Close Variant Monitoring (15/15)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| ST-D17 | Variant performance drift | **PASS** | 5/5 | Zero drift candidates |
| ST-D18 | Variant spend share | **PASS** | 5/5 | Zero variants taking disproportionate spend |
| ST-D19 | Unintended expansion | **PASS** | 5/5 | No semantic drift detected in the variant set. *Note: the account runs only 17 non-brand keywords, so close-variant exposure is structurally small — this PASS reflects a narrow surface, not a large one well-managed* |

### Module 5 — Promotion & PMax (10.2/15)

| ID | Diagnostic | Verdict | Pts | Detail |
|---|---|---|---|---|
| ST-D20 | High performers not keywords | WARN | 1.8/3 | 863 candidates from 936 converting terms. Genuine non-brand opportunities: **`streetwear`** 14 conv @ ROAS 7.87 (€214), **`civil regime`** 11 conv @ 14.58 (€169), **`killstar`** 10 conv @ 8.11 (€133). The rest are brand variants already covered by brand campaigns |
| ST-D21 | Duplicates across campaigns | WARN | 1.8/3 | Brand variants (`staycoldapparel`, `stay cold apparel`, `stay cold`) surface as promotion candidates across **four** non-brand campaigns — Search TOF, PMAX NC DEALS PUSH, DSA. Promoting them would cannibalise the brand campaigns, which are do-not-touch under guardrail DON'T-4 |
| ST-D22 | Coverage ratio | WARN | 1.8/3 | **0%** — 936 converting terms, none exists as a keyword. Partly structural (Shopping and PMax have no keywords by design), but Search TOF genuinely has none of its converting terms promoted |
| ST-D25 | **PMax brand query %** | **PASS** | **3/3** | **0%.** Zero brand queries served by the active PMax roster across 242,927 terms |
| ST-D26 | PMax search overlap | WARN | 1.8/3 | 15,479 overlaps between PMax terms and Search keywords. Large, but Search/PMax overlap is structurally unavoidable; the actionable part is the off-brand subset the keyword audit already isolated |

---

## Cross-audit resolutions

| Prior finding | Status after this audit |
|---|---|
| **Account audit AUD-D02** — brand/non-brand separation rated **WARN** because PMax brand share could not be verified without served search-term data | ✅ **RESOLVED.** ST-D25 measures **0% brand queries** across 242,927 PMax terms. Combined with the PMax audit's finding that brand exclusion is ON across all 7 campaigns (shared set `10982324974`), the setting and the outcome now both confirm it. AUD-D02 can move to PASS |
| **Keyword audit KW-D12** — 27 of 80 overlapping PMax terms were off-brand (cyberpunk, Metallica, Gildan, CM Punk) | ✅ **Corroborated and extended.** This run finds the same pattern at scale: `bad omens merch`, `vlone`, `chrome hearts`, `teddy fresh` — other artists' and brands' merch absorbed by PMax |
| **Keyword audit B3** — 100% of unprofitable keyword spend is core terms, pausing prohibited | ✅ **Same conclusion from the search-term side.** 57% of non-converting *term* spend is core product language |
| **business.md §9** — "do not auto-negate foreign brands (scene shoppers with brand overlap convert)" | ✅ **Confirmed with hard data for the first time.** `killstar` ROAS 8.11, `civil regime` ROAS 14.58 |

---

## Peer report integration

| Peer | Report | Status | Used how |
|---|---|---|---|
| `/lp-auditor` | `context/analysis/lp/lp-audit.md` | **FRESH — 2026-08-06**, 56% | Explains why core-term traffic converts at zero. The `goth clothing` n-gram and the "zero occurrences of goth on the page" finding are the same fact |
| `/offer-auditor` | `context/analysis/offer/offer-audit.md` | **FRESH — 2026-08-06**, 97% | The language needed to fix the destination already exists in brand.md |
| `/keyword-auditor` | `context/analysis/keyword/keyword-audit.md` | **FRESH — 2026-08-06**, 85% | Same core-term protection logic, reached independently from the keyword side |
| `/pmax-auditor` | `context/analysis/pmax/pmax-audit.md` | **FRESH — 2026-08-06** | Brand exclusion ON across all 7 PMax campaigns — the mechanism behind ST-D25's 0% |
| `/bidding-auditor` | `context/analysis/bidding/bidding-audit.md` | **FRESH — 2026-08-06**, 54/100 | Caps confidence in Shopping/PMax term economics |
| `/account-auditor` | `context/analysis/account/account-audit.md` | **FRESH — 2026-08-06**, 75% | AUD-D02 resolved by this run |
| `/tracking-specialist`, `/strategy-specialist` | — | Missing | Measurement and target handoffs |

**No peer contradicts this audit.** Five fresh reports converge on the same conclusion: the traffic is right, the destination is wrong.

---

## Data notes

| Source | Rows | Status |
|---|---|---|
| `search-term/search-terms-periodA.csv` | 680,648 | Pulled fresh |
| `search-term/search-terms-periodB.csv` | 599,438 | ⚠️ See note below |
| `search-term/search-terms-ngram.csv` | 1,049,758 | Pulled fresh, 120d |
| `search-term/pmax-search-terms.csv` | 242,927 | Pulled fresh |
| `negative-keywords-shared.csv` | 3,213 | 3,135 in `EXCLUSIONS FOR BRAND`, 78 in `EX I ALL` |
| `negative-keywords-campaign.csv` / `-adgroup.csv` | 21 / 1 | — |
| `bidding-strategies.csv` | **0** | No portfolios — all targets campaign-inline |
| `keywords-active.csv` | 37 | — |

⚠️ **Period B recovery.** The Period B pull failed at the final file-rename step with a Windows `EBUSY` lock (OneDrive sync), after the query had already written 599,438 rows. The partial file was verified before use — 20 columns in the header, 20 in the final row, well-formed — and moved into place. The write had completed; only the rename failed. Period B is used solely for ST-D05 trend comparison, so any residual truncation risk affects trending terms only, not the core findings.

**Config written this run:** `searchTermAnalysis.targetROAS = 2.5` (non-brand target from business.md §3, not the account-wide 6.0, because branded campaigns are out of scope) and `searchTermAnalysis.brandTerms` (12 variants incl. typos, deliberately excluding generic dictionary words that would misclassify via substring matching). `targetCPA` left null on purpose — no campaign in this account runs tCPA.
