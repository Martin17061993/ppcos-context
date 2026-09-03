# Quality Score Audit — Kollabo

**Datum:** 2026-08-18 · **Fenster:** 30 Tage · **Historie:** 180 Tage · **Lag:** 14 T · **Modus:** full (16 Diagnostiken, 4 Module)
**Account:** 1487707588 · **Währung:** CHF · **Keywords im Scope:** 389 (223 mit QS)
**Klassifikation:** 353 GENERIC · 19 BRANDED · 17 COMPETITOR · 0 INFORMATIONAL

> ⚠️ **Alle 389 Keywords laufen auf Smart Bidding.** QS speist weiterhin den Ad Rank — die CPC-Wirkung ist gedämpft, nicht aufgehoben. Alle Schweregrade unten sind entsprechend annotiert.

---

## Executive read

**44 % — exakt derselbe Wert wie am 10.08. In acht Tagen hat sich nichts bewegt, und das ist die eigentliche Nachricht.** Die Landing-Page-Erfahrung steht bei **176 von 223 bewerteten Keywords auf BELOW_AVERAGE — 78,9 %**, praktisch unverändert gegenüber den 78,4 % aus `business.md`. Bei 125 Keywords ist LP die **allein** limitierende Komponente; bei weiteren 51 eine von mehreren. Zum Vergleich: Ad Relevance liegt bei 8,9 % (ohne Conquesting-Keywords), Expected CTR bei 17,0 %. Es gibt in diesem Konto nicht drei QS-Probleme, es gibt eines.

**Zwei Befunde sind neu und ändern, wohin die Arbeit gehen muss.** Erstens: die teuersten LP-Below-URLs sind **nicht** die Gewerke-Vorlagen, sondern `https://kollabo.com/de-ch/jobs/` (570 CHF, 9 Keywords) und die Startseite `https://kollabo.com/de-ch/` (362 CHF, 4 Keywords). Zusammen 932 CHF — mehr als jede einzelne Gewerkeseite. `/lp-auditor` (11.08., 60 %) hat die Vorlage `/de-ch/jobs/gipser-jobs/` geprüft und für inhaltlich gut befunden: *„kein schlechtes Stück Arbeit… die Inhalte sind gut"* — der Engpass sei *„Ausgangsdichte und Technik"* (114 Links, 41 Fusszeilen-Links). **Diese beiden Hub-Seiten hat noch niemand geprüft.** Zweitens: 20 Keywords fallen scharf ab, darunter `elektroinstallateur jobs` von QS 7 auf 3 und `strassenbauer jobs` von 8 auf 5.

Was **kein** Problem ist: Ad Relevance (8,9 % — die RSAs treffen), die Brand-Kampagne (kein einziges BRANDED-Keyword unter QS 7), Ad Customizer (keine im Konto, also auch keine defekten), und die Komponenten-Trends — LP steht bei 111 von 132 auswertbaren Keywords auf STABLE. Die schlechte LP-Erfahrung ist chronisch, nicht frisch verschlechtert.

**Drei von fünf High-Spend/Low-QS-Keywords sind Competitor-Terms** (`Job24`, `Adecco`, `Jop.ch`) — dort ist AR Below Avg strukturell erwartbar und **kein** Fixkandidat. Übrig bleiben `polymechaniker schweiz` (QS 4, 359 CHF, nur LP limitiert) und `gipser job` (QS 3).

**So liest du den Rest:** Die LP-Queue unten ist nach effektiver URL gruppiert und nach Spend sortiert — das ist die Arbeitsliste. AR- und ECTR-Queues sind kurz und nachrangig. **Trend: 44 % (10.08.) → 44 %.**

---

## Diagnosis

**In einer Zeile:** Der Ad Rank dieses Kontos wird von einer einzigen Komponente gedrückt, und die liegt ausserhalb von Google Ads.

**Was passiert:** 78,9 % der bewerteten Keywords haben eine unterdurchschnittliche Landing-Page-Erfahrung, während Anzeigenrelevanz und erwartete CTR weitgehend in Ordnung sind. Google bewertet damit nicht die Kampagnenarbeit als schwach, sondern das Ziel, auf das sie verweist. Das erklärt mechanisch, warum `/competitive-analyst` (11.08., 41 %) 37–73 % Rang-Verlust misst und `/budget-auditor` (heute, 80 %) bei 29 von 30 Kampagnen Rang- statt Budget-Dominanz findet.

**Wo es am meisten weh tut:** 3.585 CHF Spend im 30-Tage-Fenster laufen über Keywords mit LP Below Avg — das sind 29.015 Impressionen. Der Löwenanteil verteilt sich auf 29 URLs, angeführt von zwei generischen Hub-Seiten, die bisher in keinem Audit geprüft wurden.

**Was zuerst zu tun ist:** Die beiden Hub-URLs prüfen lassen (`/de-ch/jobs/` und `/de-ch/`), dann die von `/lp-auditor` bereits benannten Vorlagen-Fixes umsetzen. RSA-Arbeit ist hier **nicht** der Hebel — die Anzeigenrelevanz ist gut.

---

## Evidence Ladder

### Creative — LP (dominant)
- **176 von 223 bewerteten Keywords: LP BELOW_AVERAGE = 78,9 %.** → **H1**
- Bei **125 Keywords ist LP die allein limitierende Komponente**, bei 51 eine von mehreren (`MULTIPLE`). AR allein: 7. ECTR allein: 1. → **H1**
- LP-Below-Keywords tragen **3.584,96 CHF** Spend und 29.015 Impressionen im Fenster. → **H1**
- Verteilt auf **29 effektive URLs**. Spitzenreiter: `/de-ch/jobs/` 570,52 CHF (9 KW) · `/de-ch/` 362,00 CHF (4 KW) · `/de-ch/jobs/gipser-jobs/` 325,18 CHF (8 KW). → **H1**
- LP-Trajektorie: **111 von 132 auswertbaren Keywords STABLE**, nur 10 DECLINING. Chronisch, nicht akut. → **H1**

### Creative — ECTR (nachrangig)
- 38 von 223 = **17,0 %** ECTR BELOW_AVERAGE. → **H2**
- ECTR-Trajektorie: 75 STABLE, 10 IMPROVING, 9 DECLINING. Keine Verschlechterung. → **H2**
- Von den 38 haben mehrere gleichzeitig AR Below → im inneren Kaskaden-Modell **blockiert**, AR zuerst. → **H2**

### Creative — AR (klein, teilweise strukturell)
- 29 von 223 AR BELOW_AVERAGE, davon **10 in der COMPETITOR-Klasse** — strukturell erwartbar beim Conquesting. → **H3**
- Bereinigt: **19 von 213 = 8,9 %** — unterhalb jeder Handlungsschwelle. → **H3**
- AR-Trajektorie: 52 STABLE, 1 IMPROVING, 0 DECLINING. → **H3**

### Competitive
- **26 Keywords verlieren Impressionen an den Rang mit QS als Mitursache**, nur 3 ohne QS-Bezug. QS ist in **90 %** der Rang-Verluste implizitert. → **H1**
- CPC nach QS-Tier: QS 7–10 = **0,96 CHF** · QS 5–6 = **1,56 CHF** (+62 %) · QS 1–4 = 1,28 CHF. → **H4**
- Der QS-1–4-Wert liegt unter QS 5–6, weil diese Keywords kaum ausgeliefert werden und nur die billigsten Auktionen gewinnen — kein Gütesiegel. → **H4**

### Datenlage (begrenzt die Aussagekraft)
- **166 von 389 Keywords (42,7 %) haben gar keinen QS.** → **H5**
- **215 Keywords stehen auf `UNSTABLE_QS`** (zu wenig Impressionen). Nur **8** Keywords sind stabil bewertet. → **H5**
- Trend-Analyse: **255 von 387 = 65,9 % INSUFFICIENT_DATA**, obwohl die Schwelle bereits auf 10 Impr/Woche gesenkt ist (niedrigste angebotene Stufe). → **H5**

---

## Module Scores

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| 1 · QS Distribution (D01–D06) | 8,0 / 13,33 | 60 % | Needs Attention |
| 2 · Component Breakdown (D07–D10) | 18,0 / 45 | 40 % | Critical |
| 3 · Historical Trends (D11–D14) | 6,0 / 7,5 | 80 % | Good |
| 4 · Competitive Context (D15–D16) | 6,0 / 20 | 30 % | Critical |
| **GESAMT** | **38,0 / 85,83** | **44 %** | **Critical** |

> **Nenner-Reduktionen:** D04/D05 (Kampagnen-/Ad-Group-Rollups) als INFO, D13 (Changelog-Korrelation) als INFO, D14 (Saisonalität) SKIP — 180 Tage Historie reichen für keinen YoY-Vergleich.
> **Modul 2 trägt 45 der 100 Punkte** und ist damit der Score-Treiber. Die 40 % dort sind praktisch allein die LP-Komponente.

---

## Actions — segmentiert nach Kaskaden-Zustand

### 🔴 Zuerst — LP Experience (erklärt ~79 % der QS-Last)

| # | Was | Warum | Wohin |
|---|---|---|---|
| 1 | **Die zwei ungeprüften Hub-URLs auditieren** | `/de-ch/jobs/` (570 CHF, 9 KW, 6.653 Impr) und `/de-ch/` (362 CHF, 4 KW, 2.942 Impr) sind zusammen die teuerste LP-Position — und in keinem bisherigen Audit geprüft. `/lp-auditor` hat nur die Gewerke-Vorlage getestet. | `/lp-auditor` mit expliziter URL — **neuer Lauf nötig**, der bestehende deckt sie nicht ab |
| 2 | **Die bereits benannten Vorlagen-Fixes umsetzen** | **Bestehenden Report lesen:** `context/analysis/lp/lp-audit.md` (11.08., 60 %) — Prio 1: *„Facebook Rating 0 entfernen"* + abgebrochener Satz *„findet den neuen direkt über kollabo"*. Aufwand Minuten, wirkt auf 14+ Vorlagenseiten. | `/lp-optimizer` — kein Re-Run des Auditors nötig |
| 3 | **Ausgangsdichte reduzieren** | `/lp-auditor`: *„das hier ist keine Landingpage, es ist eine Website-Seite. 114 Links, vollständige Kopfnavigation, 41 Fusszeilen-Links."* Bei einem Konto, dessen Engpass die LP-Erfahrung ist, ist das der strukturell teuerste Befund. | `/lp-optimizer` |

### 🟡 Danach — Expected CTR

| Was | Umfang | Wohin |
|---|---|---|
| 38 Keywords mit ECTR Below Avg | Davon ein Teil mit gleichzeitigem AR Below → im Kaskaden-Modell blockiert, AR zuerst. Rein-ECTR-Fälle: 1 als alleinige Limitierung. | `/offer-maker` + `/rsa-maker` — **erst nach LP**, weil ECTR bei gedrosseltem Rang ohnehin schwer messbar ist |

### 🟢 Ad Relevance — kaum Handlungsbedarf

| Was | Umfang | Wohin |
|---|---|---|
| 19 Keywords AR Below Avg (non-Competitor) = 8,9 % | Unter jeder Handlungsschwelle. AR-Trajektorie 52 STABLE / 0 DECLINING. **Die RSAs sind nicht das Problem.** | Keine Aktion. `/rsa-maker` wäre hier verschwendete Arbeit. |

### ⚠️ Nicht anfassen

| Was | Umfang | Begründung |
|---|---|---|
| **10 COMPETITOR-Keywords mit AR Below Avg** | `Job24`, `Adecco`, `Jop.ch`, `Manpower jobs` u. a. | AR Below Avg ist **strukturell**, wenn du auf die Marke eines Wettbewerbers bietest — deine Anzeige kann per Definition nicht „relevant" zu deren Markennamen sein. `business.md` §13: dort bewusst relevant. Config bestätigt `EX \| 26 \| CH \| SEARCH \| LEAD \| Compeditor` als Conquesting-Kampagne. |
| **3 der 5 High-Spend/Low-QS-Keywords** | `Job24` (QS 1, 321 CHF) · `Jop.ch` (QS 3, 116 CHF) · `Adecco` (QS 1, 71 CHF) | Dieselbe Begründung. 507 der 953 CHF im Flag sind Conquesting, kein Defekt. |
| **19 BRANDED-Keywords** | Brand-Kampagne | **Kein einziges liegt unter QS 7.** Keine Eskalation nötig — ungewöhnlich gut. |

---

## Handoff Queue — LP Experience (→ `/lp-optimizer`)

Gruppiert nach effektiver URL (Keyword-URL, sonst RSA-URL der Ad Group), sortiert nach Spend.

| Spend (CHF) | Keywords | Impressionen | URL | Kontext aus `/lp-auditor` (11.08.) |
|---|---|---|---|---|
| **570,52** | 9 | 6.653 | `https://kollabo.com/de-ch/jobs/` | **nicht geprüft** — Hub-Seite |
| **362,00** | 4 | 2.942 | `https://kollabo.com/de-ch/` | **nicht geprüft** — Startseite |
| 325,18 | 8 | 1.718 | `.../jobs/gipser-jobs/` | **geprüft, 60 %** — „Facebook Rating 0", 114 Links, Versprechen erst bei 832 px |
| 223,67 | 3 | 1.809 | `.../jobs/schweisser-jobs/` | gleiche Vorlage |
| 220,76 | 7 | 1.345 | `.../jobs/bauarbeiter-jobs/` | gleiche Vorlage |
| 184,28 | 9 | 1.185 | `.../jobs/strassenbauer-jobs/` | gleiche Vorlage |
| 183,58 | 10 | 1.496 | `.../jobs/gaertner-jobs/` | gleiche Vorlage |
| 182,02 | 5 | 1.223 | `.../jobs/heizungsmonteur-jobs/` | gleiche Vorlage |
| 175,41 | 9 | 1.259 | `.../jobs/maler-jobs/` | gleiche Vorlage |
| 119,43 | 1 | 851 | `.../jobs/automatikmonteur-jobs/` | gleiche Vorlage |
| 109,33 | 10 | 988 | `.../jobs/montage-schreiner/` | gleiche Vorlage |
| 101,65 | 4 | 697 | `.../jobs/elektroinstallateur-jobs/` | gleiche Vorlage |
| 91,86 | 7 | 665 | `.../jobs/montage-elektriker-jobs/` | gleiche Vorlage |
| 91,22 | 10 | 644 | `.../jobs/sanitaer-jobs/` | gleiche Vorlage |
| 85,72 | 4 | 527 | `.../jobs/zimmermann-jobs/` | gleiche Vorlage |
| 84,59 | 5 | 1.712 | `.../jobs/produktionsmechaniker-jobs/` | gleiche Vorlage |

*29 URLs insgesamt; die restlichen 13 liegen unter 85 CHF.*

> **Die Vorlagen-Fixes aus `/lp-auditor` wirken auf alle Zeilen ab #3.** Die ersten beiden brauchen eine eigene Prüfung — es sind andere Seitentypen.

## Handoff Queue — Expected CTR (→ `/offer-maker` + `/rsa-maker`)

| Ad Group | Keywords ECTR Below | Status |
|---|---|---|
| verteilt über 38 Keywords | 38 | **blockiert bis LP gefixt** — bei 47 % Rang-Verlust ist ECTR nicht sauber messbar |

## Handoff Queue — Ad Relevance (→ `/rsa-maker`)

| Ad Group | Keywords AR Below (non-Competitor) | Status |
|---|---|---|
| — | 19 (8,9 %) | **leer** — unter Handlungsschwelle. Keine Empfehlung. |

---

## Module Details

### Modul 1 — QS Distribution (8,0 / 13,33)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| QS-D01 | WARN | 2,0/3,33 | Impressions-gewichteter Konto-QS **5,04**. `business.md` führte 5,5 spend-gewichtet — gleiche Grössenordnung. |
| QS-D02 | WARN | 2,0/3,33 | **45 von 223 Keywords bei QS ≤ 3 = 20,2 %.** Verteilung: QS 1 = 8, QS 2 = 4, QS 3 = 33. |
| QS-D03 | WARN | 2,0/3,33 | 5 High-Spend/Low-QS-Keywords, 953 CHF. **Nach Competitor-Filter bleiben 2 echte** (446 CHF): `polymechaniker schweiz` QS 4, `gipser job` QS 3. |
| QS-D04 | INFO | — | Kampagnen-Rollup |
| QS-D05 | INFO | — | Ad-Group-Rollup |
| QS-D06 | WARN | 2,0/3,33 | **166 von 389 Keywords ohne QS = 42,7 %** (Schwelle 30 %). Re-Audit in 30 T empfohlen. |

### Modul 2 — Component Breakdown (18,0 / 45)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| QS-D07 | PASS | 11,25 | AR Below Avg **19 von 213 non-Competitor = 8,9 %**. Gesund. |
| QS-D08 | WARN | 6,75/11,25 | ECTR Below Avg **38 von 223 = 17,0 %**. |
| QS-D09 | FAIL | 0/11,25 | **LP Below Avg 176 von 223 = 78,9 %.** Werte: ABOVE_AVG 18 · AVG 29 · BELOW_AVG 176. |
| QS-D10 | FAIL | 0/11,25 | Dominante Limitierung: **LP 125** · MULTIPLE 51 · AR 7 · ECTR 1 · NONE 205. Ein einziger Fehlerpunkt. |

### Modul 3 — Historical Trends (6,0 / 7,5)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| QS-D11 | WARN | 2,25/3,75 | 34 von 132 auswertbaren = **25,8 % DECLINING/DECLINING_SHARP**. Gesamt: 68 STABLE, 30 IMPROVING, 14 DECLINING, 20 DECLINING_SHARP. |
| QS-D12 | PASS | 3,75 | Komponenten-Trends ohne Verschlechterung. LP: 111 STABLE / 10 DECLINING / 5 IMPROVING. AR: 52 STABLE / 0 DECLINING. |
| QS-D13 | INFO | — | 96 Keywords mit Changelog-Event in zeitlicher Nähe. Bei 1.649 API-unsichtbaren Änderungen (`account-changelog.md`) nicht sauber attribuierbar. |
| QS-D14 | SKIP | — | 180 Tage Historie < 52 Wochen — kein YoY möglich. |

**Die 20 scharfen Absteiger (Top nach Impressionen):**

| QS-Verlauf | Impressionen | Keyword | Kampagne |
|---|---|---|---|
| 3 → 1 | 5.743 | `Job24` | Compeditor *(Conquesting — erwartbar)* |
| 7 → 5 | 3.726 | `montage elektriker jobs` | Montage-Elektriker |
| 6 → 4 | 3.642 | `garten jobs` | Gärtner |
| 5 → 3 | 3.409 | `zimmermann arbeit` | Zimmermann |
| **7 → 3** | 3.113 | `elektroinstallateur jobs` | Elektroinstallateur |
| 7 → 5 | 2.823 | `arbeit maler` | Maler |
| 5 → 3 | 1.903 | `gipser job` | Gipser |
| **8 → 5** | 1.392 | `strassenbauer jobs` | Strassenbauer |

### Modul 4 — Competitive Context (6,0 / 20)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| QS-D15 | FAIL | 0/10 | **26 Keywords mit Rang-Verlust und QS als Mitursache**, nur 3 ohne QS-Bezug. QS erklärt 90 % des messbaren Rang-Verlusts auf Keyword-Ebene. |
| QS-D16 | WARN | 6,0/10 | CPC nach Tier: **QS 7–10 = 0,96 CHF** (1.687 Klicks) · QS 5–6 = **1,56 CHF** (1.218 Klicks, **+62 %**) · QS 1–4 = 1,28 CHF (973 Klicks). |

---

## Data Sufficiency Notes

| Punkt | Bedeutung |
|---|---|
| **42,7 % der Keywords haben keinen QS** | 166 von 389. Google vergibt erst ab ausreichend Impressionen. Konto ist Low-Volume. |
| **55,3 % stehen auf `UNSTABLE_QS`** | 215 Keywords mit zu wenig Impressionen für belastbare Bewertung. **Nur 8 Keywords sind stabil klassifiziert** (3 OK, 3 CRITICAL, 2 WATCH). |
| **65,9 % der Trend-Analyse: INSUFFICIENT_DATA** | 255 von 387 — und das bei einer bereits auf **10 Impr/Woche** gesenkten Schwelle (am 10.08. von 25 gesenkt, dort waren es 75,9 %). 10 ist die niedrigste vom Skill angebotene Stufe. **Das ist keine Konfigurationslücke, sondern die Volumenrealität des Kontos.** M3 wertet auf den 132 qualifizierenden Keywords. |
| **Alle Keywords auf Smart Bidding** | QS speist den Ad Rank weiter, die direkte CPC-Wirkung ist aber gedämpft. Kein Keyword läuft Manual CPC. |
| **Keine Ad Customizer im Konto** | 36 Ad Groups, alle `NO_CUSTOMIZERS`. Keine defekten Bindungen — Headline-Test läuft im Standard-Modus. |
| **`account-changelog.md` 7 Tage alt** | Begrenzt QS-D13. Zusätzlich sind laut Changelog 1.649 Änderungen API-unsichtbar. |

---

## For the record

| Feld | Wert |
|---|---|
| Top-Hypothese | **H1 — Creative/LP: Landing-Page-Erfahrung als alleiniger dominanter Limitierer** |
| Konfidenz | hoch |
| Erklärt | ~79 % der QS-Last |
| Blockiert | ECTR-Arbeit (H2) bis LP gefixt |
| Frische Peer-Reports integriert | `/lp-auditor` (11.08., 60 %) · `/budget-auditor` (18.08., 80 %) · `/bidding-auditor` (18.08., 65 %) · `/search-term-auditor` (18.08., 81 %) · `/competitive-analyst` (11.08., 41 %) · `/offer-auditor` (11.08., 78 %) · `/tracking-specialist` (10.08., 48 %) · `/strategy-specialist` (10.08., 55 %) |
| Stale Peers | `/keyword-auditor` (10.08., 8 T alt bei 7-T-Fenster) |
| Klassifikator | 353 GENERIC · 19 BRANDED · 17 COMPETITOR · 0 INFORMATIONAL |
| Score-Trend | 44 % (10.08.) → **44 %** (18.08.) |
