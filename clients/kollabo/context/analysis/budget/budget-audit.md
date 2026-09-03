# Budget Audit — Kollabo

**Datum:** 2026-08-18 · **Modus:** full (19 Diagnostiken, 5 Module) · **Account:** 1487707588 · **Währung:** CHF
**Fenster:** 30 Tage · **Conversion-Lag:** 14 T · **Monatsziel:** 8.500 CHF (seit 11.08. kundenseitig freigegeben)

> ℹ️ Audit schliesst aktive Experiment-Kampagnen ein (Default). 30 aktive Kampagnen, 30 Budget-Konsumenten nach Gruppierung, 12 Shared Budgets.
> ⚠️ `account-changelog.md` ist 7 Tage alt (Schwelle 24 h). Budget-Änderungen der letzten Woche sind darin nicht erfasst.

---

## Executive read

**80 % — und die wichtigste Zahl dieses Audits ist eine, die das Skript selbst nicht sieht.** Die Engine meldet 29 budget-limitierte Kampagnen und legt 16 Erhöhungs-Chancen auf den Tisch. Rechnet man Budget- gegen Rang-Verlust, kippt das Bild vollständig: **bei 29 von 30 Kampagnen dominiert weiterhin der Rang.** Elektroinstallateur verliert 36 % ans Budget — aber 43,6 % an den Rang. Compeditor 33 % gegen 58 %. Schweisser 20 % gegen 61 %. **Alle acht Kampagnen in der Opportunity-Liste sind rang-dominiert.** Wer dort Budget nachlegt, kauft genau das, wovor deine eigene Guardrail #2 warnt: teurere Klicks, keine besseren.

Die einzige Kampagne mit echter Budget-Dominanz ist **Trockenbauer** (32,9 % Budget vs. 16,4 % Rang) — bei 85 CHF Spend und einer Conversion die kleinste Position im Konto.

**Und dann ist da UMLAND, das dieses Audit strukturell nicht finden kann.** Im 30-Tage-Fenster steht UMLAND bei 1,3 % Budget-Verlust und 78,2 % Rang-Verlust — also klar rang-limitiert, keine Opportunity. Das Fenster mittelt aber über den Stichtag 11.08., an dem der tCPA-Throttle entfernt wurde. Misst man die 7 Tage davor gegen die 7 Tage danach, hat die Kampagne die Limitierung **gewechselt**: Rang-Verlust 79,9 → 47,1 %, Budget-Verlust 3,4 → 31,5 %. UMLAND ist heute die einzige Kampagne, bei der eine Erhöhung durch Daten gedeckt ist — und sie steht in keiner Opportunity-Zeile.

Zwei Kaskaden-Ebenen blockieren ausserdem alles, was mit Rentabilität zu tun hat. `/strategy-specialist` (10.08., 55 %) führt D04 und D08 als **ASK**: der Erlös je Vermittlung ist unbekannt. Der hier verwendete `breakEvenCPA` von 75 CHF ist laut Config ausdrücklich **nicht margenbasiert**, sondern 1,5 × Konto-Ø. Jedes „profitabel/unprofitabel" in diesem Report misst gegen eine operative Schwelle, nicht gegen echte Marge — deshalb habe ich BUD-D03, D04, D13, D14 und D15 auf INFO gesetzt und aus der Wertung genommen. Konkret: BUD-D04 stuft Gipser bei CPA 75,12 als „unprofitabel" ein — **0,16 % über einer selbstgesetzten Linie.**

Kein Problem sind: Pacing (MTD 4.877 vs. 4.935 Soll, Monatsende projiziert 8.893 = +4,6 %), Shared Budgets (alle drei Diagnostiken PASS), und Budget-Sufficiency gegen tCPA. Kein Zero-Spend.

**Trend: 86 % (10.08.) → 80 %.** Der Rückgang ist überwiegend Methodik — ich gate die rentabilitätsabhängigen Diagnostiken jetzt am Business-Layer. Der Budget-Verlust selbst ist nur leicht gestiegen.

---

## Diagnose

**Das Konto ist nicht budget-limitiert, es ist rang-limitiert — und die einzige Ausnahme ist acht Tage jung und im 30-Tage-Fenster unsichtbar.** Der Engpass sitzt weiterhin dort, wo ihn `/quality-score-auditor` und `/lp-auditor` lokalisiert haben: bei der Landing-Page-Erfahrung, die den Ad Rank drückt. Solange 29 von 30 Kampagnen mehr Impressionen an den Rang als ans Budget verlieren, ist eine Budgeterhöhung die teuerste verfügbare Antwort. Die richtige Reihenfolge lautet: **Ad Rank heben, dann Budget.** Einzige heute begründbare Ausnahme ist UMLAND, wo die Rang-Limitierung durch das Entfernen des Throttles bereits gefallen ist.

---

## Top-Hypothese

| | |
|---|---|
| **Layer** | Competitive (Comp) — mit blockierendem M und B darüber |
| **Label** | Rang-Limitierung durch LP-Erfahrung, nicht Budget-Knappheit |
| **Evidenz** | BUD-D01/D02 flaggen Budget-Verlust; Gegenrechnung zeigt Rang-Dominanz bei 29/30. Alle 16 Opportunities betroffen. |
| **Konfidenz** | hoch |
| **Blockiert Raise?** | ja — ausser UMLAND |

---

## Module Scores

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| 1 · Limitation (D01–D04) | 3,75 / 12,5 | 30 % | Critical |
| 2 · Sufficiency (D05–D08) | 8,25 / 11,25 | 73 % | Needs Attention |
| 3 · Pacing (D09–D12) | 11,25 / 11,25 | 100 % | Excellent |
| 4 · Allocation (D13–D16) | 7,5 / 7,5 | 100 % | *nur 1 von 4 gewertet* |
| 5 · Shared Budgets (D17–D19) | 15 / 15 | 100 % | Excellent |
| **GESAMT** | **45,75 / 57,5** | **80 %** | **Good** |

> **Nenner-Reduktionen (B-Layer):** D03, D04, D13, D14, D15 auf INFO — alle fünf hängen an einem Break-even, den es nicht gibt (GAP-1 offen, `/strategy-specialist` D04/D08 = ASK). D07 und D12 sind konstruktionsbedingt INFO.
> **Modul 4 trägt nur BUD-D16.** Die 100 % sind kein Gütesiegel für die Allokation, sondern das Ergebnis dreier ausgeblendeter Diagnostiken.

---

## Risiken

### 🔍 Investigate first — blockierend

| Was | Warum | Wohin |
|---|---|---|
| **Erlös je Vermittlung fehlt (GAP-1)** | Ohne ihn ist „profitabel" in diesem Report eine Konvention, keine Messung. Fünf Diagnostiken hängen daran. | **Bestehenden Report lesen:** `context/analysis/strategy/strategy-audit.md` (10.08., 55 %) — *„Conditional Go — Bedingung: Deckungsbeitrag je Vermittlung > 278 CHF."* Frage an Kollabo, kein Re-Run. |
| **Messpfad (M-Layer)** | `SF: New Lead` seit 01.07. bei null, Gebotssignal −63 %. Jede CPA-basierte Budgetentscheidung steht darauf. | **Bestehenden Report lesen:** `context/analysis/tracking/tracking-audit.md` (10.08., 48 %, Completeness 34 %). |

### 🔧 Bidding-seitiger Fix — vor jeder Budgetänderung

| Was | Warum | Wohin |
|---|---|---|
| **BUD-D08: 30 von 30 Kampagnen unter dem Conversion-Floor** | Smart Bidding braucht ~30 Conv/Monat je Kampagne. Ist-Werte: Brand 23, UMLAND 16, Automatiker 8, Montage-Elektriker **1,9**. Mehr Budget auf eine Kampagne, die nicht lernen kann, verstärkt nur die Streuung. | `/bidding-auditor` — Report ist 8 Tage alt (Fenster 7 T), **Re-Run empfohlen** |

### 🔄 Effizienz zuerst — der eigentliche Hebel

| Was | Warum | Wohin |
|---|---|---|
| **Rang-Verlust 34–78 % bei 29 Kampagnen** | Das ist der Deckel, nicht das Budget. Ursache ist lokalisiert. | **Bestehende Reports:** `lp/lp-audit.md` (11.08., 60 %) — *„keine Landingpage, sondern eine Website-Seite: 114 Links, jeder ein Ausgang"* · `competitive/competitive-audit.md` (11.08., 41 %) — *„aggressiv konkurrieren, aber über Quality Score, nicht über Gebote"* |
| **QS-Report ist abgelaufen** | 44 % am 10.08., 123 Keywords mit LP als allein limitierender Komponente. 8 Tage alt bei 7-Tage-Fenster. | `/quality-score-auditor` **Re-Run**, um die Wirkung von LP-Fixes zu messen |

### ✅ Act now (safe)

| Was | Umfang | Wohin |
|---|---|---|
| **UMLAND-Budget +20 % (26,00 → 31,20 CHF/Tag)** | Einzige Kampagne mit belegtem Limitierungs-Wechsel. Budget-Verlust 31,5 % (7 T nach Throttle-Entfernung), Sättigungsdeckel laut Guardrail #1 bei ~85 CHF/Tag. Guardrail #8 (≥7 Tage Ruhe) ist erfüllt. | `/budget-optimizer raise` oder manuell im UI |

### ⚠️ Hold — nicht erhöhen

| Was | Umfang | Begründung |
|---|---|---|
| **Alle 16 Opportunities der Engine** | Brand, Automatiker, Schweisser, Elektroinstallateur, Bauarbeiter, Grundbauer, Maurer, Compeditor | Sämtlich **rang-dominiert**. Guardrail #2: „Budget-Headroom ist kein Freibrief — vor jeder Erhöhung Budget- vs. Rank-Lost-IS prüfen." Die Prüfung fällt hier negativ aus. |
| **BUD-D04 „Gipser + Heizungsinstallateur reduzieren oder pausieren"** | 2 Kampagnen, 1.005 CHF | Gipser liegt bei CPA 75,12 gegen eine **nicht margenbasierte** 75er-Linie. Ausserdem Guardrail #10: „Keine Profession pausieren (Kundenwunsch)" — schwache Gewerke auf 3–4 CHF/Tag statt Pause. |
| **Batch-Erhöhungen** | — | Guardrail #3: „Keine Batch-Budget-Pushes." 15.08.2024: 4 Kampagnen gleichzeitig hoch → mehrfach negativ. |

### ℹ️ Confirm intent

| Was | Befund |
|---|---|
| **Zwei stille UMLAND-Kampagnen** | `UMLAND TEST Keyword Test` und `UMLAND TEST Testzeitraum 263` sind ENABLED mit je **65,99 CHF/Tag** Budget, hatten aber in 14 Tagen null Impressionen. Kein realer Spend, aber sie verfälschen jede Tagesbudget-Summe. Experiment-Reste (`business.md` §7.4). |
| **BUD-D06: 28 Kampagnen erreichen ihr Tagesbudget an ≥50 % der Tage** | Echtes Erschöpfungssignal — Budget wirkt als sekundäre Bremse. Ändert nichts an der Rang-Dominanz, erklärt aber, warum die Engine so viele Kampagnen flaggt. |

---

## Opportunities

| Typ | Kampagnen | Engine-Projektion | Urteil nach Kaskade |
|---|---|---|---|
| `profitable_limited_recovery` | 8 | IS-Lost-Budget-Recovery | **verworfen** — alle rang-dominiert |
| `winner_underfunded` | 8 | dieselben 8 Kampagnen | **verworfen** — identische Grundlage |
| *(nicht von der Engine gefunden)* | **UMLAND TEST** | +20 % Tagesbudget | **gültig** — Limitierungs-Wechsel belegt |

> Die Engine bewertet Budget-Verlust absolut und nicht relativ zum Rang-Verlust. Auf einem rang-limitierten Konto erzeugt das systematisch falsch-positive Erhöhungs-Chancen. Für Kollabo ist das kein Einzelfall, sondern der Normalzustand.

---

## Pacing-Snapshot

| Kennzahl | Wert |
|---|---|
| MTD-Spend (Stand 18.08.) | 4.877 CHF |
| Proportionales Soll | 4.935 CHF (−0,7 pp) |
| Projiziertes Monatsende | **8.893 CHF** |
| Monatsziel | 8.500 CHF (**+4,6 %**) |
| Saisonalitäts-Modus | `none` (GAP-8 — Kollabos Geschäfts-Saisonalität undokumentiert) |

Pacing ist gesund. Die +4,6 % Überschreitung liegt im Toleranzband. **Achtung:** August ist laut `business.md` §11 historisch der teuerste Monat (2025-08 CPA 25,19 bei höchstem Spend). Ein UMLAND-Uplift von +5,20 CHF/Tag entspricht ~158 CHF/Monat und hebt die Projektion auf ~9.050 CHF — das sind +6,5 % über Ziel.

---

## Sequenzierte Handoffs

1. **Erlös je Vermittlung klären** → Frage an Kollabo. Report liegt: `strategy/strategy-audit.md` (10.08.)
2. **Salesforce-Import klären** → Frage an Kollabo. Report liegt: `tracking/tracking-audit.md` (10.08.)
3. **`/bidding-auditor`** → Re-Run (8 T alt). BUD-D08 blockiert bidding-seitig: 30/30 unter Conversion-Floor
4. **`/quality-score-auditor`** → Re-Run (8 T alt). Misst die Wirkung der LP-Fixes auf den Ad Rank
5. **LP-Fixes umsetzen** → `lp/lp-audit.md` Prio 1: „Facebook Rating 0" + abgebrochener Satz, 14+ Vorlagenseiten
6. **`/budget-optimizer raise`** → **nur UMLAND**, ein Schritt +20 %, Nachkontrolle 25.08.

---

## Modul-Details

### Modul 1 — Limitation (3,75 / 12,5)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BUD-D01 | WARN | 3,75/6,25 | 29 Kampagnen mit Budget-Verlust ≥10 %. Real, aber bei 29 davon dominiert der Rang. |
| BUD-D02 | FAIL | 0/6,25 | 24 Kampagnen mit Budget-Verlust ≥25 %. Höchste Werte: Elektroinstallateur 36,0 %, Montage-Elektriker 35,5 %, Kranführer 35,4 %. |
| BUD-D03 | INFO | — | „8 profitable Kampagnen budget-beschränkt" — B-Layer blockiert, zusätzlich alle acht rang-dominiert. |
| BUD-D04 | INFO | — | „2 unprofitable Kampagnen" — Gipser CPA 75,12 vs. willkürlicher 75er-Linie. Nicht wertbar. |

### Modul 2 — Sufficiency (8,25 / 11,25)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BUD-D05 | PASS | 3,75 | Alle Search-Kampagnen mit Tagesbudget ≥ 2× tCPA. |
| BUD-D06 | WARN | 2,25 | 28 Kampagnen erreichen ihr Tagesbudget an ≥50 % der Tage — mögliche Mittags-Erschöpfung. |
| BUD-D07 | INFO | — | 314 von 314 Budgets auf STANDARD delivery; Google darf bis 2× Tagesbudget ausgeben. |
| BUD-D08 | WARN | 2,25 | **30 von 30** Smart-Bidding-Kampagnen unter dem Conversion-Floor von 30/Monat. Blockiert bidding-seitig. |

### Modul 3 — Pacing (11,25 / 11,25)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BUD-D09 | PASS | 3,75 | MTD 4.877 vs. 4.935 Soll (−0,7 pp). |
| BUD-D10 | PASS | 3,75 | Monatsende projiziert 8.893 vs. 8.500 (+4,6 %). |
| BUD-D11 | PASS | 3,75 | Innerhalb des 10-%-Bandes. |
| BUD-D12 | INFO | — | Saisonalität `none`, aktueller Monat August. |

### Modul 4 — Allocation (7,5 / 7,5)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BUD-D13 | INFO | — | „5 profitable Kampagnen unter 5 % Spend-Anteil" (Brand 4,7 %, Maurer 1,8 %). B-Layer blockiert. |
| BUD-D14 | INFO | — | „2 unprofitable Kampagnen ≥5 % Spend" (Gipser 5,9 %, Heizungsinstallateur 6,3 %). B-Layer blockiert. |
| BUD-D15 | INFO | — | Profitabler Anteil am klassifizierten Spend 79 %. Gegen eine Konvention gemessen. |
| BUD-D16 | PASS | 7,5 | Keine aktive Kampagne mit Null-Spend. |

### Modul 5 — Shared Budgets (15 / 15)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BUD-D17 | PASS | 5 | 12 Shared Budgets, ausgewogen über die Mitglieder. |
| BUD-D18 | PASS | 5 | Konsistente Zielsetzungen innerhalb der Gruppen. |
| BUD-D19 | PASS | 5 | Kein Konflikt mit Portfolio-Gebotsstrategien — im aktiven Bestand ist kein Portfolio-Bidding im Einsatz. |

---

## Konfigurations-Snapshot

| Feld | Wert |
|---|---|
| `monthlyBudgetTotal` | 8.500 CHF — seit 11.08. kundenseitig freigegeben (`business.md` §5.3) |
| `accountCurrency` | CHF |
| `breakEvenCPA` | 75 — **nicht margenbasiert**, 1,5 × Konto-Ø |
| `primaryKPI` | cpa |
| `seasonalityProfile.mode` | `none` (GAP-8) |
| `includeExperiments` | true |
| `businessMdHash` | `3fd67857455b6b63` (aktualisiert 2026-08-18) |
| `lastConfirmed` | 2026-08-18 |
