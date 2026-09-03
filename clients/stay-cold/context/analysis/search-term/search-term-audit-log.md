# Search Term Audit Log

## 2026-08-06 — Score: 79% (Good)

- **Scope:** full · 26 diagnostics · 5 modules · branded campaigns excluded · experiments excluded · 73/92 available points
- **Periods:** main 60d (lag 8) · n-grams 120d · **678,033 terms Period A**, 596,945 Period B, 242,927 PMax
- **Top hypothesis: Business layer (B2) — relevant-but-underperforming. The traffic is right; the destination is wrong.**

**THE HEADLINE NUMBER IS MISLEADING AND CORRECTING IT IS THE MAIN JOB OF THIS REPORT.** The engine reports 31.7% irrelevant spend (€18,236 of €57,515). Decomposed:

| Category | Terms | Spend | Verdict |
|---|---|---|---|
| **Core product terms** | 1,102 | **€10,425 (57%)** | **DO NOT NEGATE** — B2 relevant-but-underperforming |
| **Competitor brands** | 119 | €2,141 | **DO NOT NEGATE** — business.md §9 hard rule |
| **Own brand leakage** | 38 | €479 | **DO NOT NEGATE** — route to brand campaigns (protectedTerms hard rule) |
| **Genuine waste** | 541 | **€5,191 = 9.0%** | ✅ Negatable |

Acting on the 31.7% headline would have negated the front door of the business.

| Module | Score | Key finding |
|---|---|---|
| Search Term Quality | 18/25 (72%) | ST-D02 FAIL — 1,800 non-converting terms, €18,236. 90% of it in FOKUSPRODUKTE (€11,207) + PMax PROSPECTING (€5,228) |
| Negative Coverage | 20.2/25 (81%) | **Zero conflicts, zero duplicates, zero legacy syntax.** The 15 "campaigns without negatives" are 11 PMax + 4 dormant — **no serving Search/Shopping campaign lacks negatives** |
| N-gram Analysis | 9.6/12 avail (80%) | Exactly one candidate, and it's a core term (see below). D15/D16 SKIP — engine returned no data |
| Close Variants | 15/15 (**100%**) | No drift, no disproportionate spend. Narrow surface (17 non-brand keywords) |
| Promotion & PMax | 10.2/15 (68%) | 863 candidates, 0% coverage. **PMax brand query share 0%** |

**THE N-GRAM THAT CLOSES THE SESSION'S LOOP:** `goth clothing` (2-gram) — 26,380 impressions, 254 clicks, **€344.83, ZERO conversions**, 357 distinct terms. "Goth" is a core token, and today's LP audit found the word appears **zero times** on the destination page. Same root cause, third independent angle. Negating it would delete a subculture from the account while the broken page stays broken.

**A DOCUMENTED GUARDRAIL CONFIRMED WITH HARD DATA FOR THE FIRST TIME.** business.md §9 says *"do not auto-negate foreign brands (scene shoppers with brand overlap convert)."* Proven: **`killstar` 10 conversions @ ROAS 8.11** (€133) and **`civil regime` 11 conversions @ ROAS 14.58** (€169), both against a 2.5 target. Killstar is on the account's own named-competitor list.

**CROSS-AUDIT RESOLUTION — AUD-D02 CLOSED.** ST-D25 measures **0% brand queries across 242,927 PMax terms**. The account audit rated brand/non-brand separation WARN precisely because this couldn't be verified. Combined with the PMax audit's finding that brand exclusion is ON across all 7 campaigns (shared set `10982324974`), setting and outcome now both confirm it. AUD-D02 can move to PASS.

**Brand leakage worth routing (not negating), €479 / 38 terms:** `staycold apparel discount code` €67 (Search TOF), `stay cold apparel hoodie` €54 (FOKUSPRODUKTE), `stay cold apparel sale` €24, plus **reputation queries** — `is staycoldapparel legit` ×2 (€27) and `staycoldapparel review` / `staycold apparel review` (€31). High intent, currently landing nowhere useful.

**Genuine negation candidates (€5,191):** adjacent-but-wrong categories and general retailers — `tracksuit` €50, `bad omens merch` €48 (another band), `techwear` €44, `vlone` €37, `chrome hearts` €37, `teddy fresh` €33, `zalando` €31, `badehose` €31, `zumiez` €30, `uniqlo` €29, `pump cover` €28. **`staycool` €46 needs a human glance** — one letter from the brand.

**Guardrail that worked:** the n-gram engine evaluated 1,048,603 rows, generated 495,644 raw candidates, then caught and suppressed **1,766 safe-list conflicts** against `protectedTerms.neverExclude` before proposing anything. The `stay cold` protection held.

**Catalog gap that explains the residual waste:** 3,135 of the 3,213 shared negatives sit in `EXCLUSIONS FOR BRAND`, leaving only 78 in the general-purpose `EX I ALL` list. Generic waste patterns are thinly covered — exactly where the €5,191 got through.

**Data note:** the Period B pull failed at the file-rename step with a Windows `EBUSY` lock (OneDrive) after writing 599,438 rows. The partial was verified well-formed (20 header cols, 20 in the final row) and moved into place. Period B feeds only ST-D05 trending, so residual risk is confined there.

**Config written:** `targetROAS = 2.5` (non-brand target per business.md §3 — not the account-wide 6.0, since branded campaigns are out of scope); `brandTerms` (12 variants incl. typos, generic dictionary words deliberately excluded to avoid substring misclassification); `targetCPA` left null (no tCPA campaign exists).

**Fresh peers integrated (no re-runs):** `/lp-auditor` 56%, `/offer-auditor` 97%, `/keyword-auditor` 85%, `/pmax-auditor`, `/bidding-auditor` 54/100, `/account-auditor` 75%. **None contradicts** — five converge on "traffic is right, destination is wrong."

**Routing:** `/lp-optimizer message-match` (**top**) → `/offer-maker angles` → route the €479 brand leakage to brand campaigns → `/search-term-optimizer negate` for the €5,191 → add campaign-level negatives to the 2 serving PMax campaigns → `/tracking-specialist`. **Do NOT run a blanket negation cycle** — 69% of the flagged spend is protected by documented rules.
