# Competitive Audit — Kollabo

**Datum:** 2026-08-11 · **Fenster:** 90 Tage · **Conversion-Lag:** 14 T
**Account:** 1487707588 · **Währung:** CHF · **Kampagnen:** 30 Search (kein Shopping, kein PMax)

---

## Executive read

41 % — der Score misst die Wettbewerbsposition, und die ist schwach: das Konto sieht zwischen **10 und 40 % der verfügbaren Impressionen**, verliert aber **37 bis 73 % an den Rang**. Alle 30 Kampagnen sind gleichzeitig für hohen IS-Verlust, Budget-Verlust und Rang-Verlust geflaggt. Das ist die Außensicht auf denselben Befund, den `/quality-score-auditor` (heute, 44 %) von innen beschreibt: *„170 von 221 Keywords mit unterdurchschnittlicher LP-Erfahrung; LP ist bei 123 Keywords die allein limitierende Komponente."* Rangverlust dieser Größenordnung bei gleichzeitig **überdurchschnittlicher Ad-Relevanz** hat genau eine plausible Ursache, und sie ist bereits lokalisiert.

Die wichtigste Erkenntnis dieses Laufs ist aber eine andere, und sie korrigiert das Bild der letzten sechs Audits nach oben. Über 90 Tage liegt der Konto-CPA bei **27,25 CHF**, nicht bei den 49,98 des 30-Tage-Fensters. **28 von 30 Kampagnen liegen unter der Schwelle von 75.** Der Unterschied ist der in `business.md` §3 dokumentierte Messverlust ab Juli — das 90-Tage-Fenster enthält noch den intakt gemessenen Zeitraum. Egal welche der beiden Zahlen man nimmt: **es gibt Effizienz-Spielraum.** Das ist die Voraussetzung dafür, überhaupt um mehr Sichtbarkeit zu kämpfen, und sie ist erfüllt.

Daraus folgt das strategische Urteil: **aggressiv konkurrieren — aber über Quality Score, nicht über Gebote.** Bei 55–73 % Rangverlust und dokumentierter LP-Schwäche gewinnt man Impressionen, indem man den Ad Rank hebt, nicht indem man mehr bietet. Das ist der billigere Weg, weil er Sichtbarkeit ohne zusätzlichen Spend erzeugt. `/budget-auditor` (heute, 86 %) hat unabhängig bestätigt, dass Budgeterhöhung hier nicht der Hebel ist.

Kein Problem ist die Entwicklung. Nur **2 von 30 Kampagnen** verlieren tatsächlich Impression Share über die Zeit — Automatikmonteur (−20,4 pp über 90 T) und Gerüstbauer (−8,7 pp über 30 T). Die übrigen 28 sind stabil. Das Konto wird also nicht verdrängt; es war nie groß präsent. Und nur eine einzige Kampagne zeigt echten CPC-Wettbewerbsdruck (Montage-Schreiner, Korrelation −0,603).

Ein Detail für die Akte: UMLAND liefert über 90 Tage einen CPA von **15,33** bei 72,7 % Rangverlust. Das ist die effizienteste Kampagne des Kontos, und sie ist am stärksten gedrosselt.

Kein Score-Trend — erster Lauf.

---

## Score

| Modul | Punkte | % | Kernbefund |
|---|---|---|---|
| IS Health & Trends (CA-D01, D02) | 9 / 30 | 30 % | 30/30 Kampagnen mit hohem IS-Verlust; nur 2 mit echtem Rückgang |
| Competitive Position (CA-D05, D08, D09) | 11,4 / 35 | 33 % | 37 Keyword-Flags auf den Top-20; Top-IS fällt in 2 Kampagnen |
| Competitive Impact (CA-D11, D13) | 21 / 35 | 60 % | 4 Kampagnen mit messbarem Conversion-Verlust; 1 mit CPC-Druck |
| **Gesamt** | **41,4 / 100** | **41 %** | **Critical** |

> CA-D09 (Shopping-Ad-Group-IS) SKIP — kein Shopping im Konto. 8 Punkte innerhalb Modul 2 umverteilt.
> CA-D03, D04, D06, D07, D10, D12 sind in dieser Skill-Version nicht implementiert.

---

## Diagnose

**Verdikt: Aggressiv konkurrieren — über Quality Score, nicht über Gebote.**

Die Ökonomie trägt es. Bei einem 90-Tage-CPA von 27,25 gegen eine operative Schwelle von 75 liegen
rund 175 % Spielraum vor; selbst im pessimistischen 30-Tage-Bild (49,98) bleibt Luft. 28 von 30
Kampagnen sind unter Schwelle. Es gibt also keinen ökonomischen Grund, auf Sichtbarkeit zu
verzichten.

Der Engpass ist der Ad Rank. Bei 55–73 % Rangverlust und **überdurchschnittlicher Ad-Relevanz**
(167 Keywords laut QS-Audit) bleibt als Erklärung die Landing-Page-Komponente — und die ist mit
76,9 % `BELOW_AVERAGE` präzise vermessen. Der Weg zu mehr Impression Share führt über die
Seitenvorlage `kollabo.com/de-ch/jobs/{gewerk}-jobs/`, nicht über höhere Gebote.

**Was der Reihe nach zu tun ist:** erst die Landing Pages, dann neu messen. Gebotserhöhungen wären
hier der teure Weg zum selben Ziel — und die Kontohistorie (`business.md` §8.2) belegt, dass sie
bei Kollabo zweimal negativ ausgingen.

---

## Business-Ökonomie

**Konto, 90 Tage: Spend 22.677 CHF · Conv 832,2 · CPA 27,25 · Schwelle 75**

| Kampagne | Spend | Conv | CPA | IS | Lost Rank | Spielraum? |
|---|---|---|---|---|---|---|
| Elektroinstallateur | 1.415 | 37,6 | 37,67 | 18,3 % | 58,2 % | ✅ |
| Bauarbeiter | 1.407 | 63,2 | 22,25 | 22,5 % | 61,9 % | ✅ |
| **UMLAND TEST** | 1.363 | 88,9 | **15,33** | 15,9 % | **72,7 %** | ✅ |
| Compeditor | 1.333 | 58,3 | 22,87 | **10,0 %** | 69,1 % | ✅ |
| Heizungsinstallateur | 1.180 | 27,0 | 43,65 | 16,5 % | 59,5 % | ✅ |
| Maler | 1.023 | 29,0 | 35,21 | 17,1 % | 61,7 % | ✅ |
| Grundbauer | 990 | 31,3 | 31,63 | 12,8 % | 65,2 % | ✅ |
| Gipser | 944 | 24,7 | 38,22 | 18,3 % | 55,7 % | ✅ |
| DYN Catchall | 899 | 59,3 | 15,17 | 10,5 % | 70,6 % | ✅ |
| Automatiker | 855 | 25,8 | 33,18 | 13,6 % | 62,4 % | ✅ |
| Schweisser | 848 | 35,3 | 24,03 | 17,6 % | 64,5 % | ✅ |
| Montage-Elektriker | 809 | 23,5 | 34,37 | 14,0 % | 58,4 % | ✅ |
| **Brand** | 808 | 77,4 | **10,44** | **39,6 %** | **37,7 %** | ✅ |
| Strassenbauer | 799 | 22,5 | 35,47 | 14,2 % | 65,8 % | ✅ |
| Gärtner | 770 | 31,2 | 24,72 | 15,4 % | 62,8 % | ✅ |
| Sanitärinstallateur | 762 | 22,3 | 34,11 | 20,0 % | 57,9 % | ✅ |

**28 von 30 Kampagnen unter Schwelle. 2 darüber. Keine ohne Conversions.**

Selbst die Brand-Kampagne, die mit 39,6 % die höchste Impression Share hat, lässt 37,7 % an den
Rang liegen — auf der eigenen Marke. Das ist ungewöhnlich und stützt die QS-Hypothese zusätzlich.

---

## Evidenz-Leiter

### Datenvalidierung
- 90-Tage-Fenster gewählt, weil IS-Trends kürzere Fenster nicht von Rauschen trennen. **→ DV**
- **Messbruch beachtet:** 90-T-CPA 27,25 vs. 30-T-CPA 49,98. Die Differenz ist der SF-Import-Verfall
  ab Juli (`/tracking-specialist`, heute, 48 %), nicht Effizienzverlust. Beide Werte liegen unter
  Schwelle → das Urteil ist gegen beide robust. **→ DV**
- 29 von 30 Kampagnen auf Max Conversions **ohne Zielvorgabe** — Smart Bidding tauscht hier nicht
  bewusst IS gegen Effizienz, es hat schlicht kein Ziel. **→ DV**

### Business-Ökonomie
- Konto-CPA 27,25 gegen Schwelle 75 = **175 % Spielraum**. **→ BE1**
- 28 von 30 Kampagnen unter Schwelle. **→ BE1**
- `/budget-auditor` (2026-08-11, 86 %): *„Die Budgetseite ist der gesunde Teil des Kontos"* —
  Budget ist nicht der Engpass. **→ BE3**

### QS- und Rang-Diagnose (entscheidende Schicht)
- Rangverlust **37–73 %** über alle 30 Kampagnen. **→ H1**
- `/quality-score-auditor` (2026-08-11, 44 %): *„170 von 221 Keywords (76,9 %) mit
  unterdurchschnittlicher LP-Erfahrung; LP ist bei 123 Keywords die allein limitierende
  Komponente; Ad-Relevanz ist mit 167 überdurchschnittlichen Keywords die stärkste Komponente."*
  **→ H1 — der Rangverlust ist QS-getrieben, nicht gebotsgetrieben.**
- `/quality-score-auditor` zählt **26 Keywords mit QS-verursachtem Rangverlust** — dieselbe Kette
  aus der Keyword-Perspektive. **→ H1**
- `/bidding-auditor` (2026-08-11, 66 %): *„28 von 30 Kampagnen unter dem 15-Conv-Minimum für
  Smart Bidding"* — ein zweiter, unabhängiger Grund für konservative Gebote. **→ H2**

### Strategische Bewertung
- SA3-Verdikt: **Compete aggressively** — Effizienz hat Spielraum, QS ist der Hebel, Budget ist da.
- SA2 Marken-Verteidigung: Brand-CPA 10,44 bei 39,6 % IS. Kein Anlass zur Sorge, aber
  `/bidding-auditor` meldet steigende Brand-CPCs (0,38 → 0,48 → 0,55 über drei Perioden) —
  beobachten.

---

## IS-Trend-Dashboard (CA-D01)

**Nur 2 von 30 Kampagnen verlieren tatsächlich Impression Share:**

| Kampagne | Metrik | Δ | Fenster |
|---|---|---|---|
| Automatikmonteur | Search IS | **−20,4 pp** | 90 T |
| Gerüstbauer | Search IS | −8,7 pp | 30 T |

Die übrigen 28 sind stabil. **Das Konto wird nicht verdrängt — es war nie präsent.** Die niedrige
IS ist ein Ausgangszustand, kein Verfall.

## Top-of-Page-Position (CA-D05)

| Kampagne | Metrik | Δ | Fenster |
|---|---|---|---|
| Automatikmonteur | Top IS | −7,1 pp | 30 T |
| Gerüstbauer | Absolute Top IS | −9,8 pp | 30 T |

Dieselben zwei Kampagnen. Beide sind in `business.md` §10 bereits als Problemfälle dokumentiert
(Gerüstbauer: strukturelles Nachfrageproblem, 307 Impressionen in 30 Tagen; Automatikmonteur:
Test seit Mai ohne Auswertung).

## Keyword-Wettbewerbsdruck (CA-D08)

**37 Flags auf den Top-Keywords** — 19 × `KEYWORD_IS_PRESSURE`, 18 × `KEYWORD_POSITION_LOSS`.

| Keyword | Spend | Conv | CPA (90 T) | IS | Lost Rank |
|---|---|---|---|---|---|
| `efz jobs schweiz` | 1.081 | 25,2 | 42,93 | 19,2 % | 48,3 % |
| `Job24` | 784 | 38,2 | 20,50 | 10,0 % | 65,2 % |
| `polymechaniker schweiz` | 773 | 45,0 | **17,18** | 15,7 % | **69,3 %** |
| `spezialtiefbau stellen` | 640 | 16,5 | 38,82 | 12,6 % | 59,4 % |
| `schweißer arbeit` | 624 | 27,1 | 23,04 | 14,7 % | 62,3 % |
| `jobplattformen` | 571 | 21,3 | 26,76 | 14,3 % | 60,0 % |
| `sanitär jobangebote` | 507 | 13,1 | **38,56** | 18,9 % | 52,9 % |
| `stellenangebote maurer` | 490 | 17,4 | 28,26 | 10,1 % | 46,8 % |
| `temporärbüro maler` | 480 | 12,3 | 39,12 | 17,1 % | 54,5 % |
| `kollabo ag` | 408 | 37,3 | 10,93 | 26,9 % | 42,2 % |
| `handwerker jobs schweiz` | 371 | 26,9 | **13,78** | 16,1 % | **69,5 %** |
| `gipser freie stellen` | 275 | 3,2 | **87,30** | 16,6 % | 56,6 % |

> **Wichtige Korrektur zum Keyword-Audit:** `sanitär jobangebote` steht dort mit CPA 105,02 als
> UNPROFITABLE. Über 90 Tage liegt derselbe Begriff bei **38,56** — deutlich unter Schwelle.
> Dieselbe Verschiebung bei `polymechaniker schweiz` (30 T: 97,04 → 90 T: 17,18). **Die
> 30-Tage-Unrentabilität ist überwiegend Messartefakt.** Das stützt die dortige Entscheidung,
> nicht zu pausieren, zusätzlich.

Nur `gipser freie stellen` (87,30) liegt auch über 90 Tage über der Schwelle.

## CPC-Wettbewerbsdruck (CA-D11)

| Kampagne | CPC-IS-Korrelation | Lesart |
|---|---|---|
| Montage-Schreiner | **−0,603** | Steigende CPCs gehen mit fallender IS einher — echter Auktionsdruck |

**Nur eine von 30 Kampagnen.** Kein flächendeckender Wettbewerbsdruck.

## KPI-Auswirkung (CA-D13)

| Kampagne | Geschätzter Conversion-Verlust | Schwelle |
|---|---|---|
| Automatikmonteur | **165,2 %** | 10 % |
| Gerüstbauer | 21,3 % | 10 % |
| Trockenbauer | 11,6 % | 10 % |
| Montage-Schreiner | 6,2 % | 5 % |

> **Ökonomischer Realitätscheck:** Diese Verluste sind bei Automatikmonteur und Gerüstbauer
> rechnerisch groß, aber die Basis ist winzig — Gerüstbauer hatte 307 Impressionen in 30 Tagen.
> `business.md` §10 dokumentiert das als **Nachfrageproblem, nicht Wettbewerbsproblem**: der Markt
> für dieses Gewerk ist zu klein. Mehr Sichtbarkeit zu kaufen, wo es nichts zu sehen gibt,
> funktioniert nicht.

## Übersprungene Diagnostiken

CA-D03, CA-D04, CA-D06, CA-D07, CA-D10, CA-D12 — in dieser Skill-Version nicht implementiert.
CA-D09 — kein Shopping im Konto.

---

## Aktionen

### 🔍 Zuerst untersuchen

| Befund | Handoff |
|---|---|
| Rangverlust 37–73 % über alle Kampagnen — ist es QS oder Gebot? | **Beantwortet.** Bestehender Report von heute: `context/analysis/quality-score/quality-score-audit.md` (44 %) — *„LP-Erfahrung bei 76,9 % unterdurchschnittlich, Ad-Relevanz stärkste Komponente."* **QS-getrieben.** Kein Re-Run. |
| Ist Budget der Engpass? | **Beantwortet.** `context/analysis/budget/budget-audit.md` (86 %) — *„Budgetseite ist der gesunde Teil des Kontos."* **Nein.** |
| Sind die Gebote absichtlich konservativ? | **Teilweise.** `context/analysis/bidding/bidding-audit.md` (66 %) — *„28 von 30 Kampagnen unter dem 15-Conv-Minimum"* — konservativ aus Signalmangel, nicht aus Absicht. |

### ✅ Dort konkurrieren, wo es trägt (Reihenfolge)

1. **Landing-Page-Vorlage reparieren** — der einzige Hebel, der Sichtbarkeit ohne zusätzlichen
   Spend erzeugt. 14+ URLs nach einem Muster. → `/lp-auditor` (läuft als nächstes in diesem Durchgang)
2. **UMLAND entdrosseln** — CPA 15,33 über 90 Tage bei 72,7 % Rangverlust. Der tCPA von 11 ist
   nachweislich aus der falschen Conversion-Stufe abgeleitet. → `context/analysis/bidding/bidding-audit.md`
3. **Signal verdichten** — 28 von 30 Kampagnen unter dem Smart-Bidding-Minimum. Konsolidierung
   hebt die Gebotsqualität und damit den Ad Rank. → `/account-auditor` D04, `/budget-auditor`
4. **Danach neu messen** — dieses Audit erneut fahren, sobald LP und tCPA gefixt sind. Erst dann
   ist sichtbar, ob taktische Gebotsanpassungen überhaupt noch nötig sind.

### 🗣️ Strategische Diskussion

**Gerüstbauer und Automatikmonteur** zeigen die stärksten IS-Rückgänge und die größten
rechnerischen Conversion-Verluste — aber beide leiden an zu kleinen Märkten, nicht an
Wettbewerb. Die ehrliche Frage ist, ob diese Gewerke überhaupt bespielt werden sollen.
`business.md` §8.10 hält den Kundenwunsch fest, keine Profession zu pausieren — das ist eine
Geschäftsentscheidung, keine Optimierungsfrage.

### 👀 Beobachten

- **Brand-CPC steigt** über drei Perioden (0,38 → 0,48 → 0,55) bei 37,7 % Rangverlust auf der
  eigenen Marke. Noch unkritisch (CPA 10,44), aber ein Frühindikator für Marken-Konkurrenz.
- **Montage-Schreiner** — einzige Kampagne mit echter CPC-IS-Korrelation.

### Wettbewerber-Anzeigentexte

Keine Daten aus `/competitor-scraper` vorhanden. Für Angle-Vergleiche gegen jobs.ch, Adecco,
Manpower & Co. wäre ein Lauf sinnvoll — die Compeditor-Kampagne hat mit 10,0 % die niedrigste
Impression Share im Konto bei gleichzeitig gutem CPA (22,87).

---

## Datenfrische

| Quelle | Zeilen | Stand |
|---|---|---|
| `competitive/campaign-is-timeseries.csv` | 2.662 | 2026-08-11 (90 T) |
| `competitive/keyword-is.csv` | 334 | 2026-08-11 (90 T) |
| `competitive/shopping-adgroup-is-timeseries.csv` | — | übersprungen, kein Shopping |
| `evidence/competitive-flags.csv` | 136 | 2026-08-11 |
| QS-Daten | `context/analysis/quality-score/evidence/qs-tiers.csv` (2026-08-11) | statt Neu-Pull verwendet, um den geteilten 30-Tage-`keywords.csv`-Pull nicht zu überschreiben |
| `context/account-changelog.md` | — | **fehlt** |
