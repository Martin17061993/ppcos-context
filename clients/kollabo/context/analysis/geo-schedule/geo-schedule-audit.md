# Geo-Schedule Audit — Kollabo

**Datum:** 2026-08-11 · **Fenster:** 30 T (Geo/Schedule/Device) · 90 T (Demografie) · 6 Wochen (Konsistenz)
**Account:** 1487707588 · **Währung:** CHF · **Kampagnen:** 30 aktive (Experimente ausgeschlossen)

---

## Executive read

74 % — die Zielsteuerung dieses Kontos ist strukturell sauber, aber sie ist auch weitgehend **ungenutzt**. Es gibt null Gebotsmodifikatoren und null Anzeigenpläne im ganzen Konto. Das ist kein Fehler — es ist eine leere Werkzeugkiste, und zwei der Werkzeuge darin würden sich sofort auszahlen.

Prio eins sind die Nachtstunden. Zwischen **01:00 und 04:00 sowie 22:00 und 23:00** gibt das Konto **513,80 CHF in 30 Tagen aus und erhält dafür genau eine Conversion** — ein CPA von 514 gegen einen Kontodurchschnitt von 50. Das sind 6,4 % des Spends in einem Zeitfenster, das nachweislich nicht liefert. Wichtig: Mitternacht selbst ist gut (CPA 30,74), es ist also keine pauschale Nachtregel, sondern ein präzises Fenster. Bei Smart Bidding werden Zeitplan-*Modifikatoren* ignoriert — der Hebel ist deshalb die **Entfernung dieser Stunden aus dem Anzeigenplan**, nicht ein negativer Modifikator.

Prio zwei ist Deutschland. Der DE-Traffic der UMLAND-Kampagne kostet **29,02 CHF je Conversion gegen 53,82 in der Schweiz** — 46 % effizienter — und macht trotzdem nur 9,1 % des Spends aus. Das ist dieselbe Kampagne, die laut `/bidding-auditor` (heute, 66 %) mit einem falsch abgeleiteten tCPA von 11 CHF gedrosselt wird und 78,5 % ihrer Impressionen an den Rang verliert. Zwei unabhängige Audits zeigen auf dieselbe Kampagne: **UMLAND ist der beste Performer und wird künstlich klein gehalten.**

Kein Problem sind: die Standort-Zielmethode (durchgehend `PRESENCE` für Targeting *und* Ausschluss — korrekt, keine Streuung auf Interessenten im Ausland), die Modifikator-Hygiene (nichts gestapelt, weil nichts gesetzt ist), die Zeitplan-Konsistenz (699 über sechs Wochen bestätigte Muster — die Daten sind belastbar), und der Streuverlust in Nicht-Zielländer (Frankreich, Italien, Rumänien zusammen 22,91 CHF — irrelevant).

**Ein Befund wird ausdrücklich blockiert.** Die Mechanik meldet Frauen mit einem CPA von 52,82 gegen 33,14 bei Männern und würde einen Demografie-Ausschluss vorschlagen. **Das ist hier nicht zulässig** — `business.md` §12 hält das Diversity Statement der kollabo ag, den Swissstaffing Code of Conduct und das Arbeitsvermittlungsgesetz fest. Ein Geschlechter-Ausschluss auf einer Stellenvermittlungsplattform ist ein Compliance-Verstoß, unabhängig davon, was der CPA sagt. Ich führe den Befund als Information, nicht als Empfehlung.

Kein Score-Trend — erster Lauf.

---

## Score

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| Geographic (GS-D01–D05) | 29,4 / 35 | 84 % | Good |
| Schedule & Device (GS-D06–D09) | 18,2 / 28 | 65 % | Needs Attention |
| Demographics & Advanced (GS-D10–D14) | 15,68 / 22,4 | 70 % | Good |
| **Gesamt** | **63,3 / 85,4** | **74 %** | **Good** |

> GS-D13 als INFO aus dem Nenner genommen — Compliance-Blockade, siehe unten.

---

## Kritische Befunde

### 1. GS-D07 FAIL — Nachtfenster verbrennt 513,80 CHF für 1 Conversion

**Stundenprofil (30 Tage, Konto):**

| Stunde | Spend | Conv | CPA |
|---|---|---|---|
| 00:00 | 122,36 | 3,98 | **30,74** ✅ |
| **01:00** | **106,35** | **1,00** | **106,35** |
| **02:00** | **50,07** | **0** | **—** |
| **03:00** | **56,66** | **0** | **—** |
| **04:00** | **34,19** | **0** | **—** |
| 05:00 | 57,21 | 3,00 | 19,07 ✅ |
| 14:00 | 655,01 | 19,80 | **33,09** ✅ |
| 16:00 | 497,54 | 13,31 | 37,37 ✅ |
| 17:00 | 414,36 | 5,04 | 82,18 ⚠️ |
| **22:00** | **144,36** | **0** | **—** |
| **23:00** | **122,17** | **0** | **—** |

**Totes Fenster: 01:00–04:00 + 22:00–23:00 = 513,80 CHF, 1,00 Conversion, CPA 513,80.**
Das sind 6,4 % des Monatsspends.

Bemerkenswert ist, was **nicht** tot ist: 00:00 liefert CPA 30,74 und 05:00 sogar 19,07. Eine
pauschale Nachtabschaltung wäre falsch — das Fenster ist präzise abzugrenzen.

> **Mechanik-Hinweis:** 29 von 30 Kampagnen laufen Max Conversions. Smart Bidding **ignoriert
> Zeitplan-Gebotsmodifikatoren**. Der wirksame Hebel ist, die Stunden aus dem Anzeigenplan zu
> **entfernen** (Targeting), nicht sie negativ zu modifizieren.

*Vorbehalt:* Die 87 einzelnen Stunde×Tag-Zellen ohne Conversion (2.139,53 CHF) sind **kein**
belastbarer Befund — bei 160 Conversions auf 168 Zellen ist eine leere Zelle statistisch normal.
Nur die aggregierte Stundensicht trägt.

### 2. GS-D04 / GS-D14 WARN — Deutschland ist 46 % effizienter und wird klein gehalten

| Land | Spend | Anteil | Conv | CPA |
|---|---|---|---|---|
| Schweiz | 7.190,97 | 90,1 % | 133,62 | 53,82 |
| **Deutschland** | **725,44** | **9,1 %** | **25,00** | **29,02** |
| Österreich | 37,71 | 0,5 % | 1,00 | 37,71 |
| Frankreich / Italien / Rumänien | 22,91 | 0,3 % | 0 | — |

Deutschland läuft über die UMLAND-Kampagne (Grenzregionen Baden-Württemberg,
`geoTargetConstants/20228, 20229, 20236, 20048, 20049, 20238`).

**Querbezug zu `/bidding-auditor` (2026-08-11, 66 %):** *„UMLAND: PAR 0,33 und 259 % Abweichung
vom eigenen tCPA; Lost IS Rank 78,5 % bei nur 2,1 % Budget-Verlust."* Der beste Geo-Markt des
Kontos wird durch einen tCPA gedrosselt, der aus der falschen Conversion-Stufe abgeleitet wurde.
**Der Geo-Hebel und der Bidding-Fehler sind derselbe Befund aus zwei Richtungen.**

Österreich mit CPA 37,71 bei 1 Conversion ist zu dünn für eine Aussage — aber als Testkandidat
für eine UMLAND-Erweiterung notiert.

### 3. GS-D06 WARN — Mobile trägt 71,6 % des Spends bei halber Conversion-Rate

| Gerät | Spend | Anteil | Conv | CPA | Abweichung | CVR |
|---|---|---|---|---|---|---|
| MOBILE | 5.630,27 | 71,6 % | 95,94 | 58,68 | +11,6 % | **2,09 %** |
| DESKTOP | 2.197,07 | 27,9 % | 53,67 | **40,93** | −22,1 % | **4,11 %** |
| TABLET | 37,03 | 0,5 % | **0** | — | −100 % | 0 % |

Desktop konvertiert fast **doppelt so gut** wie Mobile, bekommt aber nur ein Viertel des Spends.

> **Mechanik-Hinweis:** Bei Smart Bidding werden Geräte-Gebotsmodifikatoren ignoriert — **außer
> −100 % (Ausschluss)**. Ein „Mobile −20 %" hätte also keine Wirkung. Realistische Optionen:
> Tablet ausschließen (37,03 CHF, 0 Conversions — klein, aber sauber), und die Mobile-Schwäche
> dort adressieren, wo sie entsteht: auf der Seite.
>
> **Querbezug zu `/quality-score-auditor` (2026-08-11, 44 %):** *„170 von 221 Keywords mit
> unterdurchschnittlicher LP-Erfahrung; die Gewerke-Seitenvorlage ist der Engpass."* Eine
> Mobile-CVR von 2,09 % gegen 4,11 % Desktop ist ein klassisches Symptom mobiler Seitenprobleme.
> **Die Geräte-Spreizung ist wahrscheinlich kein Targeting-Problem, sondern dasselbe
> LP-Problem in mobiler Ausprägung.** Kein Geräte-Eingriff vor dem LP-Audit.

---

## Modul-Ergebnisse

### Geographic (GS-D01–D05) — 29,4/35

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| GS-D01 | Standort-Zielmethode | PASS | 7/7 | Alle 30 Kampagnen `PRESENCE` für Targeting **und** Ausschluss. Korrekt — keine Streuung auf CH-Interessenten im Ausland. |
| GS-D02 | Geo-CPA-Varianz | WARN | 4,2/7 | CH 53,82 vs DE 29,02 — Spreizung 46 %, aber zugunsten des kleineren Marktes. Chance, kein Leck. |
| GS-D03 | Null-Conversion-Standorte | PASS | 7/7 | FR/IT/RO zusammen 22,91 CHF, 24 Klicks — unterhalb jeder Materialitätsschwelle. |
| GS-D04 | Chance bei Top-Standorten | WARN | 4,2/7 | DE: 46 % besserer CPA bei 9,1 % Spend-Anteil. |
| GS-D05 | Ausschluss-Abdeckung | PASS | 7/7 | Keine relevanten Lecks. UMLAND-DE ist beabsichtigt. |

### Schedule & Device (GS-D06–D09) — 18,2/28

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| GS-D06 | Geräte-CPA-Varianz | WARN | 4,2/7 | Mobile 58,68 / CVR 2,09 % vs Desktop 40,93 / CVR 4,11 %. Tablet 0 Conv bei 37,03 CHF. |
| GS-D07 | Zeitplan-Verschwendung | **FAIL** | 0/7 | **513,80 CHF für 1 Conversion** in 01:00–04:00 + 22:00–23:00. |
| GS-D08 | Zeitplan-Konsistenz | PASS | 7/7 | **699 bestätigte Muster über 6 Wochen** — das Nachtfenster ist kein Ausreißer. |
| GS-D09 | Modifikator-Stapelung | PASS | 7/7 | **0 Gebotsmodifikatoren im Konto.** Nichts gestapelt. |

### Demographics & Advanced (GS-D10–D14) — 15,68/22,4

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| GS-D10 | Demografische Ausreißer | WARN | 3,36/5,6 | Geschlecht: FEMALE 52,82 vs MALE 33,14 (+59 %). Alter: gleichmäßig (28,89–40,49). |
| GS-D11 | Smart-Bidding-Konflikt | PASS | 5,6/5,6 | 0 Modifikatoren bei 29/30 Smart-Bidding-Kampagnen → kein Konflikt möglich. |
| GS-D12 | Saisonale Geo-Muster | WARN | 3,36/5,6 | 4 Standorte mit YoY-Auffälligkeit im Vergleichslauf. |
| GS-D13 | Demografischer Ausschluss | **INFO** | — | **Compliance-blockiert, siehe unten.** |
| GS-D14 | Geo-Optimierungschance | WARN | 3,36/5,6 | DE-Ausbau; AT als Testkandidat (zu dünn für Entscheidung). |

**Einkommens-Targeting:** 100 % `INCOME_RANGE_UNDETERMINED` — Einkommens-Targeting ist in der
Schweiz nicht verfügbar. Kein Befund möglich.

---

## ⛔ GS-D13 — ausdrücklich blockiert

**Mechanischer Befund:** FEMALE hat einen CPA von 52,82 gegen 33,14 bei MALE (+59 %) bei
13,5 % Spend-Anteil (3.115,09 CHF über 90 Tage). Die Diagnostik würde einen Ausschluss
(−100 %) vorschlagen.

**Diese Empfehlung wird nicht ausgesprochen.** Begründung aus `business.md` §12:

- **Diversity Statement der kollabo ag**
- **Swissstaffing Code of Conduct** — Kollabo ist Mitglied
- **Arbeitsvermittlungsgesetz (AVG)**
- Dokumentierte Vorgabe: „Keine diskriminierenden Formulierungen"

Ein Geschlechter-Ausschluss auf einer Stellenvermittlungsplattform ist ein Compliance-Verstoß,
unabhängig vom CPA. Der Befund bleibt als **Information** stehen — er kann ein Hinweis darauf
sein, dass Anzeigen oder Landingpages Frauen schlechter ansprechen. Das wäre ein Fall für
`/rsa-maker` und `/lp-auditor`, nicht für Targeting.

---

## Empfohlene nächste Schritte

| # | Aktion | Wirkung | Route |
|---|---|---|---|
| 1 | **Nachtfenster aus dem Anzeigenplan entfernen** (01:00–04:00, 22:00–23:00). **Nicht** 00:00 und 05:00 — die liefern. | 513,80 CHF/Monat umlenkbar | `/geo-schedule-optimizer schedule` |
| 2 | **UMLAND-tCPA korrigieren** — Geo-Chance und Bidding-Fehler sind derselbe Befund | Bester Geo-Markt entdrosseln | Bestehender Report von heute: `context/analysis/bidding/bidding-audit.md` |
| 3 | **Tablet ausschließen** (−100 %) | 37,03 CHF, 0 Conversions | `/geo-schedule-optimizer schedule` |
| 4 | **Geräte-Spreizung erst nach LP-Audit bewerten** | Mobile-CVR-Schwäche ist wahrscheinlich das LP-Problem | Bestehender Report von heute: `context/analysis/quality-score/quality-score-audit.md` — *„LP-Erfahrung bei 76,9 % der Keywords unterdurchschnittlich"* |
| 5 | **FR/IT/RO ausschließen** (optional) | 22,91 CHF — Hygiene, keine Wirkung | `/geo-schedule-optimizer geo` |
| 6 | **Geschlechter-Befund an Creative/LP geben**, nicht an Targeting | Compliance-konform | `/rsa-maker`, `/lp-auditor` |

**Reihenfolge-Hinweis:** Aktion 1 und 3 sind reine Targeting-Eingriffe und unabhängig von den
blockierenden Layern (M/B) der anderen Audits — sie entfernen Auslieferung, sie ändern keine
Gebote. Aktion 4 wartet auf das LP-Audit.

---

## Datenfrische

| Quelle | Zeilen | Stand |
|---|---|---|
| `geo-schedule/campaign-criteria.csv` | 1.893 | 2026-08-11 (frisch) |
| `geo-schedule/schedule-performance.csv` | 4.216 | 2026-08-11 (frisch) |
| `geo-schedule/demographics-age.csv` | 238 | 2026-08-11 (frisch, 90 T) |
| `geo-schedule/demographics-gender.csv` | 102 | 2026-08-11 (frisch, 90 T) |
| `geo-schedule/demographics-income.csv` | 71 | 2026-08-11 (frisch, 90 T) |
| `evidence/schedule-consistency.csv` | 4.216 | 6 Wochen, 699 bestätigte Muster |
| `evidence/geo-seasonal-comparison.csv` | 6 | 4 WARN-Standorte |
| `geo-user-location.csv` · `device-performance.csv` · `campaigns.csv` | — | frisch (< 3 T), übersprungen |
| `context/account-changelog.md` | — | **fehlt** |

> ⚠️ Die Demografie-Zahlen decken 90 Tage ab und zeigen deshalb einen niedrigeren Konto-CPA
> (35,14) als das 30-Tage-Fenster (49,98). Grund ist der in `business.md` §3 dokumentierte
> Messverlust ab Juli — nicht eine Verschlechterung der Demografie-Segmente.
