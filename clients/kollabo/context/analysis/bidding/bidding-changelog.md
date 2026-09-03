# Bidding Changelog — Kollabo

## 2026-08-11 — UMLAND: Ziel-CPA entfernt

**Kampagne:** `EX | DE | DACH | SEARCH | LEAD | UMLAND TEST` (ID 20685916051)
**Änderung:** `maximize_conversions.target_cpa` = 11,00 CHF → **entfernt** (kein Ziel)
**Strategie:** MAXIMIZE_CONVERSIONS (unverändert) · **Budget:** 26,00 CHF/Tag (unverändert)
**Ausgeführt von:** Martin, manuell im Google-Ads-UI
**Verifiziert:** 2026-08-11 gegen `campaign-bid-strategy.gaql` — Ziel-CPA-Feld leer

### Weg
`/bidding-optimizer setup` wurde aufgerufen und hat in **Phase 0.5 hart blockiert**:
- **Measurement:** `/tracking-specialist` (2026-08-10) Score 48 %, Modul Completeness 34 % = Critical
- **Business:** `/strategy-specialist` (2026-08-10) D04/D08 = ASK, Break-even unbestimmt

Für den M/B-Block existiert kein Override-Flag. Die Änderung wurde deshalb manuell im UI
ausgeführt und hier nachdokumentiert. **Keine `operations.json`, kein Dry-Run, kein `mutate.js`.**

### Begründung
Der Wert 11,00 wurde am 24.07.2026 um 13:41:29 im Zuge der Experiment-Promotion gesetzt
(belegt im `account-changelog.md`). Er stammt aus der **Bewerbungs-Stufe** (UMLAND lag dort bei
~9,5 × 1,15 = 11), während die Kampagne gegen **Qualified** optimiert — realer CPA 35–38.

Drei unabhängige Messungen: PAR 0,33 · 259 % Zielabweichung (14 T) · 77,7 % Rangverlust bei
nur 1,4 % Budgetverlust. Budgetausnutzung 76 % — die einzige der 30 aktiven Kampagnen unter 90 %.

**Warum entfernt statt auf 43 angehoben:** Die 43 wären aus dem CPA einer **gedrosselten**
Kampagne abgeleitet gewesen und damit systematisch zu niedrig — eine gedrosselte Kampagne
gewinnt nur die billigste Traffic-Scheibe. Zusätzlich hat die Kriterienänderung vom 01.07. die
Bezugsgröße verschoben. Ein belastbares Ziel lässt sich erst aus 14 Tagen ungedrosselter
Messung ableiten.

### Ausgangswerte für die Nachkontrolle (Stand 2026-08-11)

| Kennzahl | Wert |
|---|---|
| Budgetausnutzung | 76 % (19,9 von 26,0 CHF/Tag) |
| Lost IS Budget | 1,4 % (Juli) / 2,9 % (August) |
| Lost IS Rang | 77,7 % (Juli) / 79,6 % (August) |
| Qualified/Monat | 15 (Juli) · 20 (Juni) · 13 (Mai) |
| Qualified-CPA | 35,40 (Juli) / 37,83 (August) — **gedrosselt gemessen** |

**Nachkontrolle:** 2026-08-25 → `tmp/bidding-optimizer/follow-ups-UMLAND-2026-08-11.md`
## 2026-08-18 — Bidding Optimizer

**Mode:** live | **Customer:** 1487707588
**Result:** 5/5 applied

| # | Resource | Type | Target | Rationale |
|---|----------|------|--------|-----------|
| 1 | bidding_strategy | remove | `—` | ENABLED, non_removed_campaign_count = 0. Traegt einen aktiven CPC-Cap. Altlast des 2025er-Portfolio-Experiments. |
| 2 | bidding_strategy | remove | `—` | ENABLED, 0 Kampagnen. CPC-Cap 0,50 CHF liegt weit unter dem Konto-CPC von ~1,30-1,56 — wuerde jede angebundene Kampagne sofort ersticken. |
| 3 | bidding_strategy | remove | `—` | ENABLED, 0 Kampagnen. Namenszusatz '(old)' weist sie selbst als abgeloest aus. |
| 4 | bidding_strategy | remove | `—` | ENABLED, 0 Kampagnen. MAXIMIZE_CONVERSION_VALUE ist fuer dieses Konto ohnehin unbrauchbar — alle conversionActionValues stehen auf 0 (GAP-1). |
| 5 | bidding_strategy | remove | `—` | ENABLED, 0 Kampagnen. Gleiche Begruendung wie DE Push. |

