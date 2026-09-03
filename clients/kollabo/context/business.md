# Business Context — Kollabo

> **Was diese Datei ist:** Das Kontextbuch des Kollabo-Accounts. Sie verbindet Vergangenheit
> (2 Jahre Änderungshistorie), Gegenwart (Pull vom 10.08.2026) und Zukunft (Ziele, Guardrails).
> Jede Audit- und Optimizer-Skill liest sie als Entscheidungsgrundlage.
>
> **Stand:** 2026-08-10 · **Datenfenster:** 2026-07-11 – 2026-08-09 (30 T) · **Währung: CHF**
>
> **Lesehinweis:** `[ASSUMPTION]` = Ableitung von Martin, **nicht** vom Kunden freigegeben.
> `[GAP]` = offen, Quelle genannt. Keine Skill darf `[ASSUMPTION]`-Werte als Kundenvorgabe behandeln.

---

## 0. Die drei Dinge, die du wissen musst, bevor du irgendetwas entscheidest

**1. Das Konto ist rang-limitiert, nicht budget-limitiert.** 29 von 30 aktiven Kampagnen
verlieren Impressionen an den Rang, nicht ans Budget. Mehr Budget kauft hier teurere Klicks,
keine zusätzlichen guten. Der dokumentierte 15k-Skalierungspfad steht damit auf einer
widerlegten Annahme (Details §6).

**2. Der Grund ist die Landing-Page-Erfahrung.** 78,4 % der bewerteten Keywords stehen auf
`BELOW_AVERAGE` bei der LP-Erfahrung — bei guter Anzeigenrelevanz (75 % überdurchschnittlich)
und normaler erwarteter CTR. Der Ad Rank wird von genau einer Komponente gedrückt. Das ist
der Wachstumsengpass des Kontos, nicht das Budget.

**3. Das Gebotssignal hat seit April ~63 % seines Volumens verloren.** Nicht weil weniger
Bewerbungen kommen — die sind stabil bei ~520/Monat — sondern weil der Salesforce-Import
zerfällt. Smart Bidding lernt auf einem Bruchteil der Daten. Jede CPA-Zahl ab Juni 2026 ist
mit diesem Vorbehalt zu lesen (Details §3).

---

## 1. Geschäftsmodell

| Feld | Wert |
|---|---|
| Firma | kollabo ag, Blegi 5, 6343 Rotkreuz (Kanton Zug) |
| Branche | Personalvermittlung Handwerk & Fachkräfte Baugewerbe (Temporär + Festanstellung) |
| Modell | Zweiseitiger Marktplatz — **Bewerber kostenlos**, Arbeitgeber zahlt Vermittlungsprovision |
| Was Google Ads bewirbt | **Bewerberseite** (Lead-Gen: Handwerker registrieren sich) |
| Website | https://kollabo.com/ · Bewerber-App: https://app.kollabo.com/ |
| Customer ID | 1487707588 (148-770-7588) |
| MCC | 5591362086 (Jonas Makki) — UI zeigt zusätzlich Ex Machina Agency 815-273-5088 als direkten Manager |
| Markt | Deutschschweiz + deutsche Grenzregionen (UMLAND) |
| Sprache | Deutsch (Schweizer Hochdeutsch), Website nur DE |
| Swissstaffing | Mitglied |

**Wichtig fürs Verständnis:** Google Ads kauft hier **Angebot ein, nicht Nachfrage**. Der
Engpass des Geschäfts kann auf der Arbeitgeberseite liegen (zu wenig offene Stellen für die
akquirierten Bewerber) — das würde sich als sinkende Vermittlungsquote zeigen, nicht als
schlechterer CPA. **[GAP-7]**

### Abgedeckte Gewerke
Elektro · Holz (inkl. Schreiner/Bankschreiner) · Gebäudehülle (Dach/Fassade/Spengler) ·
HLKS (Heizung/Lüftung/Klima/Sanitär) · Industrie (Schweisser/Produktion) · Mechaniker ·
Innenausbau · Hoch- & Tiefbau

### Zielgruppe
Handwerker und Fachkräfte in der Deutschschweiz auf aktiver Jobsuche. Laut Google-Reviews
starker Anteil **Zuwanderer/Neuankömmlinge**, die Hilfe beim Einstieg in den Schweizer
Arbeitsmarkt suchen. Pain Points: Aufwand vieler Einzelbewerbungen · Einstiegshürde als
Einwanderer · Wunsch nach persönlicher Betreuung statt anonymem Portal · Existenzdruck.

### USPs
Nur 1× bewerben — Kollabo übernimmt den Rest · Kostenlos für Bewerber · Persönliche
Personalberater · Matching-Technologie + menschliche Beratung · Großes Arbeitgebernetzwerk
Bau · Blitzschnelle Vermittlung · Google Rating 4.9 · Mehrsprachige Beratung

---

## 2. Messmodell — worauf geboten wird vs. was Erfolg ist

**Diese Trennung ist bewusst. Sie darf nicht wieder vermischt werden.**

### 2.1 Gebotsziel (worauf das Konto optimiert)
**`SF: Qualified (2)`** — Offline-Import aus Salesforce, primär, in den Zielvorhaben.
Entscheidung Martin, 10.08.2026.

Begründung: erste Stufe, auf der Kollabo Geld verdienen kann. Auf Bewerbungen zu bieten würde
Smart Bidding auf den Ausschuss hin optimieren. `Closed Won` ist mit ~14/Monat zu dünn für
Gebotssteuerung.

### 2.2 Geschäftserfolg (was berichtet wird)
Beide Stufen führen: **Qualified** (Steuerung) und **Closed Won** (Ertrag). Bewerbungs-Volumen
als sekundärer Indikator.

**`SF: Qualified (2)` ist nicht bestätigt als Kollabos eigene Erfolgsdefinition.** Es gibt keine
abgestimmte Conversion-Definition. **[ASSUMPTION]** · **[GAP-2]**

### 2.3 Die CPA-Kaskade (Fenster 11.07.–09.08.2026, Spend 7.977,05 CHF)

| Stufe | Aktion | Conv | CPA |
|---|---|---|---|
| Bewerbung abgeschickt | `thank_you_page_view` (LIVE GA4) | 500,02 | **15,95 CHF** |
| Qualifizierter Lead | `SF: Qualified (2)` | 158,62 | **50,29 CHF** |
| Abschluss | `SF - Closed Won (Final)` | 13,93 | **572,60 CHF** |

> Der in Altnotizen geführte Ø-CPA von **14,53 CHF** bezieht sich auf die oberste Stufe
> (Bewerbungen) und ist die am wenigsten aussagekräftige Zahl. **Nicht als Leitwert verwenden.**

> ⚠️ **Korrektur 2026-08-10 durch `/strategy-specialist`:** Die 572,60 CHF sind **lag-verzerrt**
> und nicht als Kosten je Vermittlung zu verwenden. Bei 90 Tagen Klickfenster stammen die
> Abschlüsse eines Monats aus Klicks von bis zu einem Quartal zuvor — Fenster-Closed-Won gegen
> Fenster-Spend zu rechnen unterschätzt die Ausbeute systematisch. Kohorten-Rechnung siehe §2.5.

### 2.5 Unit Economics — gemessen (neu, 2026-08-10)

Aus 13 Monaten Conversion-Verlauf abgeleitet (`data/history/conv-monthly.csv`). Diese Werte
standen vorher in **keiner** Quelle.

| Trichterstufe | Quote | Fenster | Basis |
|---|---|---|---|
| Bewerbung → Qualified | **19,2 %** | 2025-10 – 2026-08 (11 Mon) | 4.578 → 878 |
| Qualified → Vermittlung | **18,1 %** | 2025-08 – 2026-08 (13 Mon) | 1.094,8 → 198,0 |
| Bewerbung → Vermittlung | 3,6 % | 11 Mon | 4.578 → 166 |

**Kosten je Vermittlung: ~278 CHF** (7.977,05 Spend / 28,7 erwartete Vermittlungen aus
158,62 Qualified × 18,1 %).

**Die Lead-to-Sale-Rate von 18,1 % liegt über der 15-%-Viabilitätsschwelle** für Lead-Gen —
Google Ads ist hier grundsätzlich konkurrenzfähig bietbar.

**Break-even-Bedingung:** Deckungsbeitrag je Vermittlung **> 278 CHF**.

| Vermittlungsquote | Kosten je Vermittlung |
|---|---|
| 25 % | 201 CHF |
| 22 % | 229 CHF |
| **18,1 % (gemessen)** | **278 CHF** |
| 15 % | 335 CHF |
| 13 % | 387 CHF |

**[GAP-1] ist damit halbiert:** die Quote ist gemessen, der **Erlös** je Vermittlung fehlt weiter.
Die Frage an Kollabo lautet jetzt binär: *Bringt eine Vermittlung mehr als 278 CHF
Deckungsbeitrag?* **[GAP-1, kritisch — verbleibender Teil]**

> **Vorbehalt:** Die Quoten messen, was aus Salesforce importiert wurde. Steht [GAP-4]
> (möglicher Mapping-Fehler New Lead → Qualified) im Raum, verschiebt ein Fix die Quote.
> Die 13-Monats-Mittelung ist robust gegen den Import-Ausfall ab Juli, aber nicht gegen einen
> systematischen Mapping-Fehler.
>
> **Guardrail:** Vermittlungsquote monatlich mitschreiben. Fällt sie beim Skalieren unter 15 %,
> steigt die Break-even-Schwelle auf 335 CHF.

### 2.4 Filterquote Bewerbung → Qualified: instabil

| Monat | Bewerbungen | Qualified | Quote |
|---|---|---|---|
| 2026-04 | 556 | 84 | 15,1 % |
| 2026-05 | 504 | 67 | 13,3 % |
| 2026-06 | 527 | 114 | 21,6 % |
| 2026-07 | 527 | 175 | **33,2 %** |
| 2026-08 (9 T) | 120 | 33 | 27,5 % |

**Die 31,7 % aus dem 30-Tage-Fenster sind der obere Rand, nicht der Normalfall.** Historisch
liegt die Quote bei 13–22 %. Jede Umrechnung zwischen den Stufen muss mit einer Bandbreite
rechnen, nicht mit einem Punktwert.

Was zwischen den 500 und den 158 passiert, ist **unbekannt**. Vermutet (unverifiziert):
Doppelbewerbungen, unvollständige Profile, falsches Gewerk, fehlende Arbeitsbewilligung.
**[GAP-3]**

---

## 3. Der Tracking-Zerfall — wichtigstes offenes Risiko

### 3.1 Was passiert ist

Bewerbungen (GA4, unabhängig von Salesforce) sind **stabil**. Die Salesforce-Kette zerfällt:

| Monat | Bewerbungen (GA4) | `SF: New Lead (1)` | `SF: Qualified (2)` | SF gesamt |
|---|---|---|---|---|
| 2026-04 | 556 | 388 | 84 | 472 |
| 2026-05 | 504 | 287 | 67 | 354 |
| 2026-06 | 527 | 179 | 114 | 293 |
| 2026-07 | 527 | **0** | 175 | 175 |
| 2026-08 (9 T) | 120 | **0** | 33 | 33 |

**Zwei getrennte Befunde:**

1. **Volumenverlust.** SF-Gesamtvolumen fiel von 472 (April) auf 175 (Juli) = **−63 %**, bei
   konstantem Bewerbungsaufkommen. Der Import verliert Datensätze.
2. **Klassifikations-Verschiebung.** Während `New Lead` auf 0 fiel, **stieg** `Qualified` von
   67 (Mai) auf 175 (Juli).
   > ⚠️ **Korrektur 2026-08-11 (Quelle: Martin/Kollabo).** Meine ursprüngliche Hypothese eines
   > Mapping-Fehlers ist **überholt**. Die tatsächliche Ursache ist eine **Änderung der
   > Qualifikationskriterien zum 01.07.2026**: vorher **2 Jahre Erfahrung in der Schweiz**,
   > jetzt **6 Monate in der EU**. Damit qualifizieren deutlich mehr Bewerber — der Anstieg
   > ist erwartbar und kein Datenfehler.
   >
   > **Offen bleibt:** warum `SF: New Lead (1)` seit 01.07. exakt null liefert. Wurde die Stufe
   > mit der Umstellung abgeschafft oder ist der Import defekt? **[GAP-4, reduziert]**

### 3.1a Kriterienänderung 01.07.2026 — Auswirkung auf die Ökonomie

| | vorher | ab 01.07.2026 |
|---|---|---|
| Qualifikationsschwelle | 2 Jahre Erfahrung **in der Schweiz** | 6 Monate **in der EU** |

**Wirkung auf Kontoebene (gemessen):**

| Monat | Spend | Qualified | Qualified-CPA | Closed Won | Vermittlungsquote |
|---|---|---|---|---|---|
| 2026-06 | 7.977 | 115,8 | 68,89 | 23 | **20,2 %** |
| **2026-07** | 8.175 | **162,9** | **50,18** | 16 | **9,1 %** |

**Der Qualified-CPA sinkt um 27 %, die Vermittlungsquote halbiert sich.** Beides ist die
erwartbare Folge einer gesenkten Schwelle. Konsequenz für §2.5:

| Basis | Kosten je Vermittlung |
|---|---|
| Alte Quote 18,1 % (13-Monats-Mittel) | 278 CHF |
| Juli-Quote 9,1 % | **~550 CHF** |

*Vorbehalt: Closed Won hat 90 Tage Klickfenster plus mehrwöchigen Vertriebszyklus — die
Juli-Qualified hatten noch keine Zeit zu schliessen. 9,1 % ist eine Untergrenze. Belastbar
frühestens Ende Oktober.*

> **Guardrail:** Vermittlungsquote ab sofort **monatlich** mitschreiben. Die Break-even-Tabelle
> in §2.5 gilt nur für die alte Quote und muss nachgeführt werden.

**Wirkung auf UMLAND: bisher keine.** Qualified Jun 20,0 → Jul 15,0. Der Effekt ist derzeit
nicht messbar, weil Experiment (02.–24.07.) und tCPA 11 (ab 24.07.) ihn überlagern.

### 3.2 Auswirkung auf die Gebotssteuerung

Das Konto zählte im April **~476 Conversions/Monat** in den Zielvorhaben (`New Lead` war
damals gebotswirksam). Heute sind es **~176**. Smart Bidding arbeitet mit **rund einem Drittel
des früheren Signals** — bei 30 Kampagnen ohne Zielvorgabe. Das ist eine plausible Mitursache
der Rang-Limitierung.

### 3.3 Weitere Messmodell-Defekte

- **Alle drei Salesforce-Aktionen stehen auf „Überprüfung erforderlich".** Wir bieten auf ein
  Signal, dessen Zustellung nicht bestätigt ist. Reißt der Import still ab, verhungert Smart
  Bidding unbemerkt. → **Guardrail: Import-Volumen wöchentlich gegen Salesforce prüfen.**
- **Vier Aktionen sind primär und liefern 0 Conversions:** `generate_lead_montage`,
  `generate_lead_allg`, `generate_lead_elektro`, `generate_lead_sanitär` (letztere mit
  Tippfehler „Perscpective").
  > **Korrektur 2026-08-10 durch `/tracking-specialist`:** Diese vier verwässern das
  > Gebotssignal **nicht**. Ihre Kategorien (DEFAULT, PAGE_VIEW) sind nur in 3 beendeten
  > Experiment-Armen gebotswirksam. **34 von 37 aktiven Kampagnen nutzen kampagnenspezifische
  > Zielvorhaben, und dort ist ausschliesslich QUALIFIED_LEAD biddable** — also nur
  > `SF: Qualified (2)`. Einzige Abweichung: `DYN Catchall` bietet zusätzlich auf
  > CONVERTED_LEAD. Der Steuerungs-KPI ist damit sauber implementiert.
  > Aufräumen bleibt sinnvoll (Hygiene), ist aber **nicht dringend**.
  > Details: `context/analysis/tracking/tracking-audit.md`
- **`thank_you_page_view` (500 Conv) ist sekundär und nicht in den Zielvorhaben.** Korrekt so —
  als Volumen-Indikator behalten, nicht bebieten.
- **Alle zehn Aktionen am GA4-Stream `Kollabo.com_Webseite_Staging_GA4` haben 0 Conversions.**
  Nur der LIVE-Stream liefert. `bewerbung_gesendet`, in Altnotizen als Hauptkonversion geführt,
  ist tot. Die Aussage in `account-info.md` ist überholt.
- **`Anrufe über Anzeigen`** lieferte bis März 2026 6–31/Monat, seit April **0**. Ungeklärt.

### 3.4 Conversion-Lag (gemessen 01.05.–09.08.2026)

| Fenster | Anteil erfasst |
|---|---|
| < 1 Tag | 86,5 % |
| ≤ 7 Tage | 93,4 % |
| ≤ 8 Tage | 93,8 % |
| ≤ 14 Tage | 95,9 % |
| ≤ 30 Tage | 98,5 % |

`conversionLagDays: 8` ist damit **vertretbar**, aber knapp. Empfehlung: **14** (erfasst 95,9 %).
Einschränkung: die Messung ist über alle gebotswirksamen Aktionen gemischt; eine saubere
Trennung nur für `Qualified` ist damit nicht möglich. **[GAP-5]**

---

## 4. Performance — Ist-Stand

### 4.1 Konto (Fenster 11.07.–09.08.2026)

| Kennzahl | Wert |
|---|---|
| Spend | 7.977,05 CHF |
| Conversions (Zielvorhaben) | 159,62 |
| CPA (Qualified-Basis) | **49,98 CHF** |
| Klicks | 5.939 |
| Aktive Kampagnen | 30 (+ 281 pausiert, 12 entfernt, 8 Experiment-Reste) |
| Tagesbudget-Summe | 280 CHF (~8.512 CHF/Monat) |
| Search Impression Share | 10–34 % |

### 4.2 Monatlicher Verlauf

Conversions = jeweils gültige Zielvorhaben; über Messbrüche **nicht absolut vergleichbar**.

| Monat | Spend | Conv | CPA |
|---|---|---|---|
| 2025-08 | 11.172 | 443,6 | 25,19 |
| 2025-09 | 10.440 | 457,1 | 22,84 |
| 2025-10 | 8.390 | 432,7 | 19,39 |
| 2025-11 | 6.308 | 185,5 | 34,01 |
| 2025-12 | 9.044 | 159,5 | 56,70 |
| 2026-01 | 6.991 | 352,6 | 19,83 |
| 2026-02 | 6.671 | 277,4 | 24,05 |
| 2026-03 | 6.687 | 454,5 | 14,71 |
| 2026-04 | 6.917 | 475,8 | 14,54 |
| 2026-05 | 7.003 | 354,9 | 19,73 |
| 2026-06 | 7.977 | 293,6 | 27,16 |
| 2026-07 | 8.342 | 175,8 | 47,45 |
| 2026-08 (9 T) | 2.361 | 32,9 | 71,87 |

> Der Einbruch Nov/Dez 2025 ist der KPI-Pivot vom 30.10.2025. Der Rückgang ab Mai 2026 ist
> **überwiegend Messverlust** (§3), nicht Effizienzverlust — die Bewerbungszahlen sind stabil.

### 4.3 Kampagnen (Fenster, Qualified-Basis, Top nach Spend)

| Kampagne | Spend | Conv | CPA | IS | Lost Budget | Lost Rank |
|---|---|---|---|---|---|---|
| UMLAND TEST | 596 | 16,0 | 37,23 | 19,4 % | **2,1 %** | **78,5 %** |
| Elektroinstallateur | 585 | 14,4 | 40,54 | 21,2 % | 34,4 % | 44,5 % |
| Compeditor | 580 | 11,1 | 52,11 | 10,0 % | 31,8 % | 58,5 % |
| Heizungsinstallateur | 507 | 6,3 | 80,44 | 20,5 % | 23,7 % | 55,8 % |
| Bauarbeiter | 502 | 5,5 | 91,46 | 21,8 % | 20,2 % | 58,0 % |
| Gipser | 447 | 6,0 | 74,83 | 20,8 % | 24,2 % | 55,0 % |
| **Brand** | 370 | 23,9 | **15,46** | 34,1 % | 26,9 % | 39,0 % |
| Grundbauer | 359 | 5,5 | 65,28 | 13,0 % | 29,2 % | 57,8 % |
| Strassenbauer | 343 | 5,0 | 68,83 | 14,8 % | 34,0 % | 51,2 % |
| Maler | 313 | 3,0 | 104,39 | 17,2 % | 27,1 % | 55,7 % |
| DYN Catchall | 288 | 5,5 | 52,42 | 10,7 % | 25,2 % | 64,1 % |
| Automatiker | 246 | 8,0 | 30,73 | 15,0 % | 25,4 % | 59,6 % |

**Über der harten Grenze (2× Ziel):** Montage-Elektriker 231,81 · Gärtner 202,17 ·
Produktionsmechaniker 146,90 · Polymechaniker 120,31 · Maler 104,39.
**0 Conversions bei Spend:** Abdichter 146,46 · Kranführer 119,89 · Montage-Schreiner 115,28 ·
Gerüstbauer 85,42.

> ⚠️ **Die Performance-Klassifikation aus `Skalierung Kundenprojekt Kollabo.md`
> (TOP/SOLIDE/MITTELFELD/SCHWACH) steht auf der Bewerbungs-Basis und ist mit diesen Zahlen
> nicht vergleichbar.** Beispiel: Bauarbeiter war „TOP", steht hier bei CPA 91,46.
> Klassifikation muss auf Qualified-Basis neu gerechnet werden.

### 4.4 Struktur & Qualität

- **Bidding:** 30/30 Kampagnen `MAXIMIZE_CONVERSIONS`. **Einzige Ausnahme: UMLAND mit
  tCPA 11,00 CHF** (§7.1). Kein Portfolio-Bidding aktiv — das 2025er-Desaster bleibt sauber
  zurückgenommen.
- **Match Types:** BROAD 162 / PHRASE 139 / EXACT 85 in aktiven Ketten — die Verengung hat
  stattgefunden (korrigiert 2026-08-10, `keyword-rules.md` war veraltet). Aber **88 % des Spends
  laufen weiter über Broad** (6.640 von 7.576 CHF), und Phrase liefert bisher den schlechteren
  CPA: Broad 50,59 · Phrase 65,74 · Exact 156,66 (1 Conv, Rauschen).
- **Quality Score:** Spend-gewichtet **5,5**. QS 1–4 = 47 Keywords (823 CHF Spend),
  QS 5 = 84, QS 7+ = 58.
- **QS-Komponenten (199 bewertete Keywords):**

| Komponente | unterdurchschnittlich | durchschnittlich | überdurchschnittlich |
|---|---|---|---|
| Erwartete CTR | 32 (16,1 %) | 100 | 67 |
| Anzeigenrelevanz | 25 (12,6 %) | 24 | 150 |
| **LP-Erfahrung** | **156 (78,4 %)** | 27 | 16 |

- **Anzeigen:** 60 Live-RSAs in 33 Ad Groups; **8 Ad Groups mit nur 1 RSA**. 10 abgelehnte
  Anzeigen — alle auf pausierten Ketten (latent, blockiert nichts).
- **Geräte:** Mobile 5.630 CHF / CPA 58,68 / CVR 2,09 % — Desktop 2.197 CHF / CPA 40,93 /
  CVR 4,11 %. **Desktop konvertiert doppelt so gut, 71 % des Spends läuft auf Mobile.**
- **Geo:** CH 7.191 CHF / 133,6 Conv / CPA 53,8 — **DE 725 CHF / 25,0 Conv / CPA 29,0**.
  UMLAND targetet deutsche Grenzregionen (`geoTargetConstants/20228, 20229, 20236, 20048,
  20049, 20238` — Raum Baden-Württemberg). DataForSEO-Ländercode DE = **2276**.
- **Negativ-Listen:** `NKL_Generisch` (466 KWs, 312 Kampagnen) · `NKW_Compeditor` (1.035, 35) ·
  `NKW_Brand` (48, 35) + 3 Legacy-Listen (`Negative KWs`, `... 1-Campaigns`, `... DE`).
- **Suchbegriffs-Sichtbarkeit:** nur 3.483 von 7.977 CHF (44 %) sind sichtbaren Suchbegriffen
  zugeordnet. Davon 86 % ohne Conversion.

---

## 5. Ziele

> ⚠️ **Es existiert kein von Kollabo freigegebenes Ziel.** Alles hier ist aus der
> Testing-Roadmap abgeleitet. **[ASSUMPTION]** · **[GAP-2]**

### 5.1 Dokumentierter Plan (Quelle: `Testing-Roadmap 7.5k zu 15k.md`, 09.06.2026)

> Spend 7,5k → **15k/Monat bei Account-CPA ≤ 18 CHF**, Pfad Aug ~9,5k → Sep ~12k → **Okt 15k**.
> Bei CPA 15–18 entspricht 15k rund **830–1.000 Bewerbern/Monat**.

**Diese 18 CHF sind pro Bewerbung.** Umgerechnet auf die Qualified-Basis ergibt sich je nach
Filterquote eine große Spanne — deshalb **kein fixer Qualified-CPA-Deckel**:

| Filterquote | Qualified-CPA bei 18 CHF/Bewerbung | Qualified/Monat bei 15k |
|---|---|---|
| 13 % (Mai-Tief) | 138 CHF | 108 |
| 18 % (Median) | 100 CHF | 150 |
| 33 % (Juli-Hoch) | 55 CHF | 273 |

**Korrektur:** Eine frühere Rechnung in dieser Session setzte 56,80 CHF als Qualified-Deckel an.
Sie beruhte auf der 31,7 %-Quote des Einzelfensters und ist damit das optimistische Ende der
Spanne, nicht der Erwartungswert.

### 5.2 Status des Plans

**Der Plan liegt im Verzug und seine Grundannahme ist widerlegt.** Heute 10.08., Ist-Spend
~8,3k statt der geplanten 9,5k. Wichtiger: die Skalierung setzt Budget-Limitierung voraus —
tatsächlich sind 29/30 Kampagnen rang-limitiert (§6).

**Empfehlung: 15k-Pfad aussetzen, nicht abblasen.** Erst Ad Rank, dann Budget.

### 5.3 Budgetfreigabe
**8.500 CHF/Monat sind seit 2026-08-11 kundenseitig freigegeben** (Auftrag an Martin).
Das Konto läuft bereits auf 280 CHF/Tag = 8.512 CHF/Monat — die Freigabe bestätigt den
Ist-Zustand, sie erhöht ihn nicht. **[GAP-6 geschlossen für 8,5k.]**
Für **15k** liegt weiterhin keine Freigabe vor. **[GAP-6 offen für 15k]**

---

## 6. Der Wachstumsengpass — warum Budget aktuell nicht der Hebel ist

**29 von 30 aktiven Kampagnen sind rang-limitiert.** Nur eine verliert überwiegend ans Budget.

Das trifft zwei eigene, empirisch validierte Leitplanken:

> „Budget-Headroom ist kein Freibrief — vor jeder Erhöhung Budget- vs. Rank-Lost-IS prüfen."
> (account-history §2.2, aus Aug-2024-Daten)
>
> „Bei Ranking-Limit kauft mehr Budget nur teurere Klicks, keine zusätzlichen guten."
> (Exec-Summary Erkenntnis 2)

Der `Budgetplan 8.5k` verteilte +51 CHF/Tag explizit auf „limitierte Kampagnen mit gutem CPA" —
auf Basis von Budget-Lost-IS. Diese Grundlage besteht heute nicht mehr.

**Die Ursache ist identifiziert: LP-Erfahrung.** 78,4 % `BELOW_AVERAGE` bei gleichzeitig guter
Anzeigenrelevanz. Ad Rank wird von einer einzigen Komponente gedrückt.

### Hebel-Reihenfolge (statt Budget)
1. **Landing-Page-Erfahrung** — größter Hebel, betrifft 78 % der Keywords → `/lp-auditor`
2. **Gebotssignal reparieren** — SF-Import + 4 Null-Aktionen aus den Zielvorhaben (§3)
3. **UMLAND-tCPA korrigieren** — Einzeländerung, sofort messbar (§7.1)
4. **Quality Score** — 47 Keywords auf QS ≤ 4 → `/quality-score-auditor`
5. **RSA-Abdeckung** — 8 Ad Groups mit nur 1 RSA → `/rsa-maker`
6. **Mobile/Desktop-Spreizung** — CPA 58,68 vs 40,93 → `/geo-schedule-auditor`
7. **Erst danach Budget.**

---

## 7. Offene Fehlstände im Konto

### 7.1 UMLAND läuft auf tCPA 11,00 CHF — falsche Conversion-Stufe
Das Experiment `UMLAND tCPA vs. MaxConv` lief 02.07.–24.07.2026 und wurde **PROMOTED**
(Kosteneffekt signifikant, p = 0,0019, −38 %). Dabei wurde tCPA 11,00 auf die Basiskampagne
geschrieben. Die 11 stammen erkennbar aus der Bewerbungs-Stufe (UMLAND lag dort bei ~9,5 ×
1,15 = 11 — die Formel aus der Roadmap). Die Kampagne optimiert aber gegen die Zielvorhaben,
und ihr realer Qualified-CPA ist **37,23**.

Folge: 2,1 % Budget-Verlust, **78,5 % Rang-Verlust** — der stärkste Rang-Verlust im Konto,
ausgerechnet beim besten Performer (DE-CPA 29,0 vs CH 53,8).
> ✅ **ERLEDIGT 2026-08-11.** Der Ziel-CPA wurde **entfernt** — UMLAND läuft wieder auf
> Max Conversions ohne Ziel (Budget unverändert 26,00 CHF/Tag). Manuell im UI ausgeführt,
> nachdem `/bidding-optimizer setup` in Phase 0.5 hart blockierte (Measurement- und
> Business-Layer, kein Override-Flag vorhanden). Gegen die API verifiziert.
>
> **Nicht auf 43 angehoben**, weil dieser Wert aus dem CPA einer *gedrosselten* Kampagne
> abgeleitet gewesen wäre und damit systematisch zu niedrig — eine gedrosselte Kampagne gewinnt
> nur die billigste Traffic-Scheibe. Ein belastbares Ziel lässt sich erst aus 14 Tagen
> ungedrosselter Messung ableiten.
>
> **Nachkontrolle 2026-08-25** — `tmp/bidding-optimizer/follow-ups-UMLAND-2026-08-11.md`.
> **Erwartung: der CPA steigt.** Das ist gewollt — die Drossel ist weg. Maßstab ist die
> Qualified-Menge bei einem CPA unter der Schwelle, nicht der CPA allein.
> Vollständig dokumentiert in `context/analysis/bidding/bidding-changelog.md`.

### 7.2 Auto-Apply — **bestätigt weiterhin aktiv** (2026-08-11)

> ⚠️ **Der `/account-changelog` vom 11.08. beweist es:** Am **30.07.2026 um 03:45** hat
> `Recommendations Auto-Apply` (`GOOGLE_ADS_RECOMMENDATIONS_SUBSCRIPTION`) ein **negatives
> Keyword** in *Metallbauer › AG | RSA | Metallbauer KW Testing* angelegt. Einen Monat nach der
> Abschaltentscheidung greift Google weiterhin selbstständig ins Konto ein.
> **Höchste Priorität unter den Hygiene-Punkten** — es kontaminiert jede Messung, auch die
> UMLAND-Nachkontrolle.

**Ursprünglicher Befund (30.06.2026):**
Am 30.06.2026 als „höchstes aktives Risiko" dokumentiert: 7 von 7 Typen unter „Anzeigen besser
verwalten" aktiv, inkl. *RSA automatisch umschreiben* (Compliance-Risiko AVG/Swissstaffing,
Duz-Form). Seither **6 Wochen ohne Bestätigung**. Über API nicht auslesbar → **manuell in der
UI prüfen.** Historische Trefferquote: ~45 % positiv (Münzwurf).

### 7.3 Config-Fehler in `config/ads-context.config.json`

| Feld | Ist | Korrekt |
|---|---|---|
| `sharedNegativeLists.primary` | `Search Term Exclusions` | `NKL_Generisch` |
| `sharedNegativeLists.ngram*` | `Non-Converting N-grams` / `Inefficient N-grams` | **existieren nicht** → auf `null`, damit ein Push laut scheitert |
| `brandedCampaigns` | `["Branded campaign name"]` | `["EX \| 25 \| CH \| SEARCH \| LEAD \| Brand"]` |
| `ngramAnalysis.defaultAOV` | `200` | ungeprüfte Annahme — hängt an [GAP-1] |
| `conversionLagDays` | `8` | `14` empfohlen (§3.4) |
| `competitors.location_code` | `2756` (CH) | korrekt für CH; **UMLAND = 2276 (DE)** |

### 7.4 Test-Debris
281 pausierte Kampagnen, 12 entfernte, 8 Experiment-Reste ohne Archivierungsstrategie.
Kein akutes Risiko, aber jede Struktur-Analyse muss sie herausfiltern.

---

## 8. Validierte Guardrails (empirisch, 2 Jahre / 149 bewertete Änderungen)

Diese Regeln sind aus echten Kollabo-Daten abgeleitet, nicht aus Theorie. Sie überschreiben
generische Best Practices.

1. **UMLAND-Sättigungsdeckel ~85 CHF/Tag.** In 2024 **und** 2025 identisch: jede Erhöhung
   darüber verteuerte Leads (+21 bis +177 %), jede Senkung verbesserte sie. UMLAND ist ein
   Effizienz-, kein Volumenhebel. *(Aktuell 26 CHF/Tag — weit unter dem Deckel.)*
2. **Budget-Headroom ist kein Freibrief.** Vor jeder Erhöhung Budget- vs. Rank-Lost-IS prüfen
   **und** CPC ≤ RPU.
3. **Keine Batch-Budget-Pushes.** 15.08.2024: 4 Kampagnen gleichzeitig hoch → mehrfach negativ.
4. **Portfolio-Bidding nur bei CPA-Homogenität (Variationskoeffizient ≤ ~30 %).** 23.06.2025:
   8 Gewerke (CV 52 %) gebündelt → **7/8 negativ** (Schweisser +188 %). Für Kollabo widerlegt.
5. **Pausen kampagnenscharf, nie blanko.** Nur bei Pre-CPA ≥ ~1,5× Konto-Ø; bei ≤ 0,8× nie.
6. **Auto-Apply = Münzwurf** (2025: 5 positiv / 6 negativ). Nach Typ kuratieren, nie global an.
7. **Broad-lastige Sammel-Keyword-Eingriffe sind das Strukturrisiko.** Einzelne Exact/Phrase-
   Pausen auf teuren Keywords nützten (−69 %); die Sammelpause 25.08.2024 schadete (+168 %).
8. **Budget ±20 %/Schritt mit ≥ 7 Tagen Ruhe.** Stopp, wenn ein Schritt den bereinigten CPA
   über +10 % treibt.
9. **Jede Änderung der Conversion-Definition ist ein Stichtag.** Darüber nur relativ (DiD).
10. **Keine Profession pausieren** (Kundenwunsch) — schwache Gewerke auf Minimum 3–4 CHF/Tag
    statt Pause.

### Operative Schwellen (aus `keyword-rules.md` / `search-terms-rules.md`)
- WASTED-Flag: Spend > 30 CHF ohne Conversion
- INEFFICIENT: CPA > 2× Konto-Ø
- Mindestentscheidungsbasis: 20 Klicks, 30 Tage
- Irrelevanz-Negativ: ab 5 CHF Spend
- Top-Performer-Schutz: ≥ 3 Conv **und** CPA ≤ 0,8 × Konto-Ø
- Pause-Kandidat: ≥ 30 CHF Spend, 0 Conv, ≥ 20 Klicks in 60 T
- Brand-Keywords: **nie** ohne Eskalation pausieren

---

## 9. Messbrüche — vor jedem historischen Vergleich prüfen

| Ab | Was | Regel |
|---|---|---|
| ~Jul 2023 | davor Micro-/Alt-Zielvorhaben (CPA ~1,5–5) | 2023-H1 nie vergleichen |
| 16.10.2024 | Zielvorhaben-Wechsel (Qualified/Converted dazu) | milder Bruch — nur DiD |
| 30.10.2025 | SF „Closed Won" primär + Klickfenster 30→60 T | **kein absoluter CPA-Vergleich über dieses Datum** |
| 10.05.–03.06.2026 | Tracking-Ausfall | CPAs absolut unbrauchbar |
| ~Mitte Jun 2026 | SF-Import-Zerfall (§3) | conv-abhängige Bewertungen mit Vorbehalt |
| ab Jul 2026 | `SF: New Lead` = 0, aus Zielvorhaben raus | Conv-Volumen nicht mit Vor-Juli vergleichbar |

**Datenlücken im Backfill:** Feb–Mai 2024, Feb–Mär 2026.

---

## 10. Experimente-Log

| Wann | Was | Ausgang |
|---|---|---|
| 04.07.2024 | Brand: Manueller CPC → Max Conversions | kurzfristig negativ (Lernphase); Brand blieb bester Performer |
| Jun–Aug 2025 | „Portfolio Test JM" — 8 Gewerke in eine Strategie | **gescheitert** (7/8 negativ), zurückgenommen |
| 29.12.2025 | Jahresend-Blankopause (Client) | teils sinnvoll, teils schädlich (Top-Performer mit aus) |
| 02.07.–24.07.2026 | tCPA-Experiment UMLAND (50/50) | **PROMOTED** — Kosten −38 %, p = 0,0019. tCPA aber auf falscher Stufe gesetzt (§7.1) |

### Offene Tests aus der Roadmap (Status unbekannt)
T1 Gerüstbauer-Rettung · T2 Trockenbauer-Liste · T4 Bankschreiner-Reaktivierung
(„Bankschreiner verschollen" — im Konto mit Filter „alle Status" suchen)

---

## 11. Saisonalität

Aus 25 Monaten Kontodaten — **eingeschränkt lesbar**, weil Messbrüche und Budgetänderungen die
Effekte überlagern.

- **Teuerste Monate: Aug/Sep.** 2025-08 CPA 25,19 · 2025-09 22,84 — höchste Werte des Jahres
  bei gleichzeitig höchstem Spend (11,2k / 10,4k).
- **Günstigste Phase: Feb–Apr.** 2026-03 CPA 14,71 · 2026-04 14,54 · 2025-03 14,75.
- **Nov/Dez:** 2024 unauffällig (13,70 / 17,11); 2025 durch den KPI-Pivot verzerrt.
- **Q4 2024 lag YoY 24–35 % günstiger als Q4 2023** — Q4 ist teuer, aber steuerbar.

**Relevanz jetzt:** Wir sind im August, dem historisch teuersten Monat. Ein Teil der aktuellen
CPA-Verschlechterung ist saisonal — aber nicht der Hauptteil (§3).

**[GAP-8]** Kollabos eigene Geschäfts-Saisonalität (Bau-Hochsaison, Ferienwirkung auf
Stellenangebote) ist nicht dokumentiert.

---

## 12. Marke, Sprache, Compliance

**Tonalität:** Persönlich, direkt, ermutigend, niederschwellig. **Konsequente Duz-Form
(verbindlich).** Kurze, klare Sätze. Service-Mentalität.

**Kernbotschaften:** „Nur 1× bewerben" · „Wir übernehmen den Rest"

**Erlaubte quantitative Claims — wörtlich, keine Abkürzungen:**
`4.9 Google Rating` · `jeder dritte Bewerber findet einen Job` (nur Description) ·
`über 500 offene Stellen` · `in 2 Minuten bewerben` · `nur 1x bewerben`
Andere Zahlen, Rankings oder Zertifizierungen **nicht erlaubt**.

**Rechtlicher Rahmen:** Schweizer DSG · Swissstaffing Code of Conduct · Arbeitsvermittlungs-
gesetz (AVG) · Diversity Statement kollabo ag.
**Verboten:** falsche oder übertriebene Jobversprechen · diskriminierende Formulierungen.

**RSA-Komposition (Kundenregel 25.04.2026):** mind. 9 Headlines, davon mind. 3 pro angle_tag
(`Produkt` / `USPs` / `CTAs/Brand`). Ein Replace darf die 3+3+3-Balance nicht kippen.

---

## 13. Wettbewerb

**Jobportale:** jobs.ch · jobup.ch · jobscout24.ch · Indeed · JobCloud
**Personalvermittler Bau:** Adecco · Randstad · Manpower · Kelly Services
**Temporär/Flex:** Coople · DasTeam · Inova Personal · Bautech Personal u. a.

Die **Compeditor-Kampagne** bietet bewusst auf Competitor-Brands — dort sind diese Terms
**relevant, nicht negativ**. `NKW_Compeditor` wird auf sie **nicht** angewendet.
Performance im Fenster: 580 CHF, 11,1 Conv, CPA 52,11, IS nur 10,0 %.

---

## 14. Cross-Channel

**[GAP-9] — praktisch undokumentiert.** Bekannt ist nur: GTM, GA4, Salesforce, Cookie-Banner
mit Opt-In, Perspective-Funnels (vier gewerkespezifische Landingpages, deren Conversion-
Aktionen 0 liefern). Ob Kollabo SEO, Social, Meta Ads, Jobportale oder Offline-Recruiting
betreibt — und wie stark diese Kanäle die 500 Bewerbungen/Monat speisen — ist unbekannt.

**Warum das zählt:** Wenn ein anderer Kanal Bewerber liefert, ist der Google-Ads-Anteil an den
158 Qualified überschätzt. Attribution über Kanäle hinweg ist nicht geprüft.

---

## 15. Gaps — priorisiert

| # | Lücke | Warum kritisch | Quelle | Prio |
|---|---|---|---|---|
| 1 | **Erlös pro Vermittlung** | Ohne diesen Wert ist 572,60 CHF/Abschluss weder gut noch schlecht. Kein Break-even, keine Rentabilitätsschwelle, kein sinnvoller CPA-Deckel. Blockiert jede Zielsetzung. | Kollabo | **Kritisch** |
| 2 | **Freigegebene Conversion-Definition + Zielmenge** | Es gibt kein abgestimmtes Ziel. Alle Zielwerte hier sind `[ASSUMPTION]`. | Kollabo | **Kritisch** |
| 3 | **Was zwischen 500 Bewerbungen und 158 Qualified passiert** | Direkter Hebel für Negatives, Zielgruppen und LP-Vorqualifizierung. Aktuell raten wir. | Kollabo / Salesforce | **Kritisch** |
| 4 | **SF-Import: Volumenverlust + mögliche Fehlklassifikation** | Gebotssignal −63 %; Verdacht, dass New-Lead-Datensätze als Qualified importiert werden. Untergräbt den Steuerungs-KPI direkt. | Kollabo / Salesforce | **Kritisch** |
| 5 | Echte Conversion-Verzögerung je Aktion | Bestimmt jedes Auswertungsfenster. Gemessen nur gemischt. | Salesforce | Hoch |
| 6 | Ist die 15k-Budgetfreigabe erteilt? | Der gesamte Skalierungsplan hängt daran. | Kollabo | Hoch |
| 7 | Arbeitgeberseite: genug offene Stellen für mehr Bewerber? | Bei Marktplätzen kann der Engpass auf der anderen Seite liegen. | Kollabo | Hoch |
| 8 | Geschäfts-Saisonalität (Bau-Hochsaison, Ferien) | Budgetplanung und Zielkorridore je Monat. | Kollabo | Mittel |
| 9 | Cross-Channel-Aktivitäten und deren Beitrag | Attribution und echter Google-Ads-Anteil. | Kollabo | Mittel |
| 10 | Auto-Apply-Status | Seit 6 Wochen unbestätigt; historisch Münzwurf. Nicht über API prüfbar. | UI-Check Martin | Hoch |
| 11 | Stakeholder, Reporting-Rhythmus, Eskalationsweg | Nicht dokumentiert. | Kollabo | Niedrig |
| 12 | Entscheidungsbefugnis des Agents | Was darf ohne Rückfrage geändert werden? | Martin/Kollabo | Mittel |

---

## 16. Quellen

**Pre-Knowledgebase** (`context/pre-knowledgebase-nodes/`): `Kollabo.md` · `Brand-Voice.md` ·
`account-info.md` · `ad-copy-rules.md` · `keyword-rules.md` · `search-terms-rules.md` ·
`account-history.md` · `Executive-Summary_Kollabo_2024-2025.md` · `impact_2024.md` ·
`impact_2025.md` · `learnings.md` · `threshold-kandidaten_2024/2025.md`

**Obsidian** (`Obsidian/Claude - Google Ads/02 Projekte/Skalierung Gads Account/Kollabo/`):
`Skalierung Kundenprojekt Kollabo.md` · `Testing-Roadmap 7.5k zu 15k.md` ·
`Budgetplan 7.5k (2026-06-09).md` · `Budgetplan 8.5k (2026-06-13).md` ·
`Aktionsplan 2026-06-30.md`

**Google Ads API** (Pull 10.08.2026, Fenster 11.07.–09.08.2026):
`context/google-ads/data/` (33 Dateien, `_manifest.json`) ·
`context/google-ads/data/history/` (`monthly.csv` 25 Mon · `conv-monthly.csv` · `lag.csv`)

---

## 17. Änderungshistorie dieser Datei

- **2026-08-10 v1** — Ersterstellung. Ersetzt die Template-Platzhalter vollständig (die alte
  Fassung beschrieb einen fremden Account: 4 Kampagnen statt 30, tCPA/PMax/Manual CPC statt
  durchgehend Max Conversions, USD statt CHF, Conversion-Aktionen die nicht existieren).
  Grundlage: Pre-Knowledgebase + Obsidian-Projektordner + frischer API-Pull.
  Steuerungs-KPI-Entscheidung durch Martin. Alle Zielwerte `[ASSUMPTION]`.
