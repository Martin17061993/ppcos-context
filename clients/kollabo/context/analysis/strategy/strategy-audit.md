# Strategy Audit — Kollabo

**Datum:** 2026-08-10 · **Modus:** full (Unit Economics + Goals & KPIs) · **Vertical:** Lead Gen
**Account:** 1487707588 · **Währung:** CHF

---

## Executive read

55 % heißt hier nicht „die Wirtschaftlichkeit ist schlecht" — es heißt „die Wirtschaftlichkeit ist zur Hälfte ungeprüft und die Ziele sind nicht abgestimmt". Der Unterschied ist wichtig, weil er die Handlung bestimmt. Die Trichterquoten dieses Kontos konnte ich aus 13 Monaten API-Daten selbst messen, und sie sind gesund: 19,2 % der Bewerbungen werden qualifiziert, **18,1 % der qualifizierten Leads werden vermittelt**. Damit liegt die Lead-to-Sale-Rate über der 15-Prozent-Schwelle, ab der Google Ads im Lead-Gen konkurrenzfähig bietbar ist. Das ist die gute Nachricht, und sie war bisher nirgends dokumentiert.

Die Konsequenz daraus ist die wichtigste Zahl dieses Audits: bei aktuellem Spend kostet eine Vermittlung **rund 278 CHF**. Nicht 572,60 — dieser Wert aus `business.md` §2.3 ist durch das 90-Tage-Klickfenster verzerrt, weil die Abschlüsse eines Monats aus Klicks von bis zu einem Vierteljahr stammen. Die offene Frage an Kollabo schrumpft damit von „was ist ein Lead wert?" auf eine einzige binäre Entscheidung: **ist eine Vermittlung mehr als 278 CHF Deckungsbeitrag wert?** Bei Ja ist das Konto profitabel und die 15k-Skalierung wirtschaftlich gedeckt. Bei Nein muss der CPA runter, bevor irgendetwas skaliert wird. Ohne diese eine Zahl bleibt D04 und damit das Gesamturteil unentscheidbar.

Die Punktverluste kommen fast vollständig aus dem Ziel-Modul. Es existiert kein kundenseitig freigegebenes Ziel (D12 FAIL), es gibt keinen dokumentierten Stakeholder und keinen Reporting-Rhythmus (D14 FAIL), und — operativ am schwersten — **30 von 30 Kampagnen laufen Max Conversions ohne jede Zielvorgabe**, obwohl der Primär-KPI CPA-Steuerung ist (D13 FAIL). Eine Strategie, die das Budget unabhängig vom CPA ausgibt, ist mit einem CPA-Ziel nicht vereinbar. Die einzige Ausnahme, UMLAND mit tCPA 11, ist aus der falschen Conversion-Stufe abgeleitet.

Kein Problem sind: die Trichterqualität selbst, die Definition des Primär-KPI (`business.md` §2.1 trennt sauber zwischen Gebotsziel und Geschäftserfolg), und die Aktualität der Daten.

Der frische `/tracking-specialist`-Report von heute (48 %) **validiert** diese Befunde in einem entscheidenden Punkt: der Live-Gebotspfad ist sauber, in allen 30 Kampagnen ist ausschließlich `QUALIFIED_LEAD` gebotswirksam. Die Quoten oben stehen also auf einem intakten Messpfad. Der offene Vorbehalt bleibt der Salesforce-Import (`SF: New Lead` seit 01.07. bei null) — die Quote von 18,1 % ist über 13 Monate gemittelt und dadurch robust gegen diesen Ausfall, die Monatswerte ab Juli sind es nicht.

Kein Score-Trend — erster Lauf.

---

## Score

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| Unit Economics (D03, D04, D08, D09) | 20 / 20 | 100 % | *siehe Vorbehalt* |
| Goals & KPIs (D10–D14) | 21 / 55 | 38 % | Critical |
| **Gesamt** | **41 / 75** | **55 %** | **Needs Attention** |

> ⚠️ **Die 100 % bei Unit Economics sind irreführend.** 2 der 4 Diagnostiken (D04 Deal Value,
> D08 Viability Verdict) konnten mangels Erlösdaten **nicht bewertet** werden und sind aus dem
> Nenner genommen. Bewertet wurden nur D03 und D09.

---

## Viability-Urteil: **Conditional Go — abhängig von einer Zahl**

| | |
|---|---|
| **Verdikt** | Conditional Go |
| **Bedingung** | Deckungsbeitrag je Vermittlung > **278 CHF** |
| **Getragen von** | D03 PASS — Lead-to-Sale 18,1 % liegt über der 15-%-Viabilitätsschwelle |
| **Offen** | D04 ASK — Erlös je Vermittlung unbekannt |
| **Risikofaktor** | Sinkt die Vermittlungsquote beim Skalieren, steigt die Schwelle: bei 15 % → 335 CHF, bei 13 % → 387 CHF |

### Die Break-even-Tabelle für das Gespräch mit Kollabo

| Vermittlungsquote | Kosten je Vermittlung | Nötiger Deckungsbeitrag |
|---|---|---|
| 25 % | 201 CHF | > 201 CHF |
| 22 % | 229 CHF | > 229 CHF |
| **18,1 % (gemessen)** | **278 CHF** | **> 278 CHF** |
| 15 % | 335 CHF | > 335 CHF |
| 13 % (Mai-Tief) | 387 CHF | > 387 CHF |

---

## Unit Economics — Ergebnisse

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D01 | Gross Margin | SKIP | — | Ecommerce-only |
| D02 | Break-even ROAS | SKIP | — | Ecommerce-only |
| **D03** | **Lead-to-Sale-Rate** | **PASS** | **15/15** | **18,1 %** (1.094,8 Qualified → 198,0 Vermittlungen, 13 Monate). Über der 15-%-Schwelle. Trichter vollständig: Bewerbung → Qualified 19,2 % → Vermittlung 18,1 %; Bewerbung → Vermittlung 3,6 %. |
| **D04** | **Deal Value Adequacy** | **ASK** | — | Max CPL = Deal Value × Marge × 18,1 %. **Deal Value unbekannt** → nicht berechenbar. Umkehrung: der aktuelle Betrieb entspricht 278 CHF je Vermittlung. |
| D05–D07 | SaaS-Metriken | SKIP | — | SaaS-only |
| **D08** | **Viability Verdict** | **ASK** | — | Composite. Mit offenem D04: „Incomplete". Materiell: **Conditional Go**, siehe oben. |
| D09 | Staleness | PASS | 5/5 | `business.md` heute erstellt (2026-08-10). Frisch. |

### Was hier neu gemessen wurde

Diese Werte standen in **keiner** Quelle — weder `business.md` (Platzhalter), noch
`account-info.md` (Felder leer), noch der Pre-Knowledgebase. Sie sind aus
`conv-monthly.csv` (13 Monate Conversion-Verlauf je Aktion) abgeleitet:

| Kennzahl | Wert | Fenster | Datenbasis |
|---|---|---|---|
| Bewerbung → Qualified | 19,2 % | 2025-10 – 2026-08 (11 Mon) | 4.578 → 878 |
| Qualified → Vermittlung | **18,1 %** | 2025-08 – 2026-08 (13 Mon) | 1.094,8 → 198,0 |
| Bewerbung → Vermittlung | 3,6 % | 11 Mon | 4.578 → 166 |
| Kosten je Vermittlung | 278 CHF | Fenster-Spend / erwartete Vermittlungen | 7.977,05 / 28,7 |

> **Methodischer Hinweis:** Der in `business.md` §2.3 geführte Wert von 572,60 CHF je Abschluss
> ist **lag-verzerrt**. Bei 90 Tagen Klickfenster stammen die Abschlüsse eines Monats aus Klicks
> von bis zu einem Quartal zuvor — Fenster-Closed-Won gegen Fenster-Spend zu rechnen unterschätzt
> die Ausbeute systematisch. Die Kohorten-Rechnung über 13 Monate umgeht das.
> **`business.md` wurde entsprechend korrigiert.**

> **Vorbehalt:** Alle Quoten sind aus Google-Ads-Conversion-Daten abgeleitet, nicht aus
> Salesforce direkt. Sie messen, was importiert wurde. Steht [GAP-4] (möglicher Mapping-Fehler
> New Lead → Qualified) im Raum, verschiebt ein Fix die Quote. Die 13-Monats-Mittelung macht sie
> robust gegen den Ausfall ab Juli, aber nicht gegen einen systematischen Mapping-Fehler.

---

## Goals & KPIs — Ergebnisse

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D10 | Primär-KPI-Definition | PASS | 15/15 | `business.md` §2.1 definiert `SF: Qualified (2)` als Gebotsziel und trennt es explizit vom Geschäftserfolg (`Closed Won`). Diese Trennung ist ausdrücklich dokumentiert und begründet. |
| D11 | Guardrail-KPIs | WARN | 6/10 | Guardrails existieren und sind ungewöhnlich gut fundiert — §8 enthält 10 empirisch aus 149 bewerteten Änderungen abgeleitete Leitplanken plus operative Schwellen (WASTED > 30 CHF, INEFFICIENT > 2× Konto-Ø, Pause ≥ 1,5× Ø, Top-Performer-Schutz ≤ 0,8× Ø). **Aber:** die zentrale Effizienzgrenze ist eine Spanne (55–138 CHF Qualified-CPA), kein festgelegter Wert — weil [GAP-1] offen ist. |
| **D12** | **Ziel-Feasibility** | **FAIL** | **0/15** | **Kein kundenseitig freigegebenes Ziel.** Alle Zielwerte sind `[ASSUMPTION]`. Das interne Ziel (Testing-Roadmap: 15k bei ≤ 18 CHF/Bewerbung bis Okt) ist **im Verzug** (Ist 8,3k statt 9,5k) und sein Mechanismus ist **widerlegt** — die Roadmap setzt Budget-Limitierung voraus, tatsächlich sind 29/30 Kampagnen rang-limitiert. |
| **D13** | **Ziel-zu-Gebotsstrategie** | **FAIL** | **0/10** | **30 von 30 Kampagnen auf `MAXIMIZE_CONVERSIONS` ohne Zielvorgabe** bei CPA als Primär-KPI. Max Conversions gibt das Budget unabhängig vom CPA aus — das ist mit CPA-Steuerung strukturell unvereinbar. Einzige tCPA im Konto (UMLAND, 11,00 CHF) ist aus der Bewerbungs-Stufe abgeleitet, während die Kampagne gegen Qualified optimiert (realer CPA 37,23). |
| **D14** | **Stakeholder-Alignment** | **FAIL** | **0/5** | Kein Ansprechpartner, kein Reporting-Rhythmus, kein Eskalationsweg, keine Freigabemarker dokumentiert. `business.md` [GAP-11]. |

---

## Kritische Befunde

### 1. D13 — Gebotsstrategie widerspricht dem Primär-KPI (FAIL)
CPA ist der Steuerungs-KPI, aber keine einzige Kampagne hat ein CPA-Ziel. Max Conversions
maximiert Menge im Rahmen des Budgets, ohne Effizienzgrenze. Bei 30 fragmentierten Kampagnen
mit je 0–24 Conversions/Monat (siehe `/account-auditor` D04) kommt hinzu, dass keine davon
genug Signal für ein stabiles tCPA hätte — **das ist kein reines Bidding-Problem, sondern eine
Folge der Struktur.**

**Reihenfolge:** erst konsolidieren (Signal je Kampagne über 30 Conv/Monat bringen),
dann tCPA setzen. Nicht umgekehrt.

### 2. D12 — Ziel ist nicht freigegeben und sein Weg ist widerlegt (FAIL)
Zwei getrennte Probleme:
- **Freigabe:** Kollabo hat kein Ziel bestätigt. Alles ist Ableitung.
- **Mechanismus:** Die Roadmap will über Budget auf 15k. 29/30 Kampagnen sind rang-limitiert
  (Lost IS Rank 39–78 %, Lost IS Budget meist < 35 %). Mehr Budget kauft dort teurere Klicks.

**Die Auktionsreserve ist aber real:** Impression Share liegt bei 10–34 %. Es sind also
66–90 % des Marktes unbesetzt. Der Weg dorthin führt über Ad Rank, nicht über Budget.
Das Ziel ist **nicht widerlegt** — nur der geplante Weg.

### 3. D04/D08 — Eine Zahl blockiert das Gesamturteil (ASK)
Nach diesem Audit ist die Frage an Kollabo nicht mehr „was ist ein Lead wert?", sondern:
**„Bringt eine Vermittlung mehr als 278 CHF Deckungsbeitrag?"**

Das ist eine Ja/Nein-Frage, die jeder im Unternehmen in einem Satz beantworten kann.

---

## Empfehlungen

| # | Aktion | Warum jetzt | Wer |
|---|---|---|---|
| 1 | **Deckungsbeitrag je Vermittlung erfragen** — binäre Frage: über oder unter 278 CHF? | Löst D04, D08 und den Hard-Block von `/bidding-auditor` auf einen Schlag | Kollabo |
| 2 | **Ziel formell freigeben lassen** (Menge + Effizienzgrenze + Zeitachse) | D12; ohne Freigabe rechnen 15 Audits gegen Annahmen | Kollabo |
| 3 | **Kampagnen konsolidieren, bevor tCPA gesetzt wird** | D13; tCPA braucht ≥ 30 Conv/Monat je Kampagne, aktuell hat keine das | `/bidding-auditor`, `/budget-auditor` |
| 4 | **UMLAND-tCPA korrigieren** (11 → ~43 oder raus) | Einzige tCPA im Konto, auf falscher Stufe abgeleitet, drosselt den besten Performer | Google Ads UI |
| 5 | **Stakeholder + Reporting-Rhythmus dokumentieren** | D14 | Martin/Kollabo |
| 6 | **Vermittlungsquote monatlich mitschreiben** | Guardrail: fällt sie beim Skalieren unter 15 %, steigt die Break-even-Schwelle auf 335 CHF | Martin |

### Peer-Reports

| Peer | Stand | Integration |
|---|---|---|
| `/tracking-specialist` | **2026-08-10 (frisch)**, 48 % | Bestätigt den Messpfad: „Live-Gebotspfad sauber, nur QUALIFIED_LEAD biddable in allen 30 Kampagnen." Die Trichterquoten stehen damit auf intakter Messung. Offener Vorbehalt: SF-Import-Zerfall. → `context/analysis/tracking/tracking-audit.md` |
| `/account-auditor` | **2026-08-10 (frisch)**, 77 % | Liefert die strukturelle Ursache für D13: „30 Kampagnen, keine mit ≥ 30 Conv" — deshalb ist tCPA aktuell gar nicht setzbar. → `context/analysis/account/account-audit.md` |
| `/bidding-auditor` | **blockiert** | Hard-Block auf Unit Economics. Nach Empfehlung 1 lauffähig. |
| übrige | fehlen | Laufen in diesem Durchgang noch |

---

## Datenfrische

| Quelle | Stand |
|---|---|
| `context/business.md` | 2026-08-10 (heute erstellt) |
| `context/google-ads/data/campaigns.csv` | 2026-08-10 |
| `context/google-ads/data/history/conv-monthly.csv` | 2026-08-10 (13 Monate) |
| `context/account-changelog.md` | **fehlt** |
