# Bidding Audit — Kollabo

**Datum:** 2026-08-18 · **Fenster:** 30 Tage · **Conversion-Lag:** 14 T · **Modus:** full (27 Diagnostiken, 7 Module)
**Account:** 1487707588 · **Kampagnen im Scope:** 30 (Experimente ausgeschlossen) · **Währung:** CHF
**Posture:** efficiency (PAR-Ziel 2,0) · **Primär-KPI:** CPA · **Break-even:** 75 CHF *(Proxy, nicht margenbasiert)*

---

## Executive read

**65 % — und die Gebotsmechanik ist dabei kaum das Problem.** Von den 27 Diagnostiken schlagen genau zwei flächendeckend an, und beide sagen dasselbe: **28 von 30 Kampagnen liefern zu wenig Conversions, als dass Smart Bidding arbeiten könnte.** Google braucht 15 Conversions pro 30 Tage für eine Search-Kampagne. Das Konto liefert im Median **3 bis 4**. Zwei Kampagnen stehen bei null (Gerüstbauer, Kranführer), vier bei eins. Max Conversions rechnet dann mit einer Schätzung, der es selbst nicht traut, bietet konservativ und verliert die Auktion — das ist der mechanische Zwischenschritt zwischen der Fragmentierung des Kontos und der Rang-Limitierung, die `/competitive-analyst` (11.08., 41 %) von aussen misst und `/lp-auditor` (11.08., 60 %) von innen erklärt.

**Die beiden Ausnahmen sind der wichtigste Befund dieses Laufs.** Nur `Brand` (23 Conv) und `UMLAND TEST` (16 Conv) liegen über der Lernschwelle. Das sind die einzigen zwei Kampagnen im Konto, deren Gebotsalgorithmus überhaupt lernen kann — und **UMLAND ist genau die Kampagne, die `/budget-auditor` (heute, 80 %) als einzige gedeckte Erhöhung identifiziert hat.** Beide Audits landen unabhängig auf derselben Kampagne. Ein Budget-Uplift auf UMLAND trifft damit die eine Stelle im Konto, an der zusätzliches Volumen auch verarbeitet werden kann.

Ein Befund vom 10.08. hat sich erledigt: **BID-D08 meldete damals eine tCPA-Abweichung von 259 % bei UMLAND**, BID-D07 ein Performance-Achievement-Ratio von 0,33. Beides ist weg, weil der Ziel-CPA am 11.08. entfernt wurde. Der Preis dafür: jetzt laufen **30 von 30 Kampagnen ohne jede Zielvorgabe**, und die gesamte Target-Validierung (BID-D05 bis D09, 25 Punkte) läuft SKIP. Der Business-Layer-Block trifft weiterhin eine leere Fläche.

Kein Problem sind: Lernphasen-Hygiene (keine Kampagne in Lernphase, keine überstürzten Ziel-Änderungen), Strategie-Wahl gegen den KPI (BID-D02 30/30 PASS), Gebots-Modifikatoren (keine manuellen vorhanden) und Conversion Value Rules (keine im Konto — Modul SKIP). Auffällig, aber nachrangig: **acht Kampagnen mit drei aufeinanderfolgenden CPC-Anstiegen**, angeführt von Montage-Elektriker (1,84 → 2,30 → 2,54 CHF).

**Trend: 66 % (10.08.) → 65 %.** Praktisch unverändert — strukturell hat sich ausser dem UMLAND-Ziel nichts bewegt.

---

## Diagnose

**Der Engpass sitzt im Volumen-Layer, nicht im Bidding-Layer.** Solange sich 30 Kampagnen rund 176 Conversions im Monat teilen, ist jede Zielvorgabe Kosmetik — ein tCPA auf einer Kampagne mit 2 Conversions steuert nichts, er begrenzt nur. Die richtige Reihenfolge lautet deshalb: erst das Signal reparieren (Salesforce-Import, `/tracking-specialist`), dann die Fläche konsolidieren (30 Kampagnen sind für dieses Volumen zu viele), dann den Ad Rank heben (LP), und **erst danach** Ziele setzen. Die einzige Ausnahme ist UMLAND: dort ist die Lernschwelle erreicht, die Rang-Limitierung seit dem 11.08. gefallen, und ein Budget-Schritt ist heute begründbar.

---

## Top-Hypothese

| | |
|---|---|
| **Layer** | Volume (Vol) — mit blockierendem M und B darüber |
| **Name** | Signal-Aushungerung: 28/30 Kampagnen unter der Smart-Bidding-Lernschwelle |
| **Evidenz** | BID-D01 (28 FAIL), BID-D03 (28 FAIL, Median 3–4 Conv/30 T), gestützt von BUD-D08 (30/30 unter Floor) |
| **Konfidenz** | hoch |
| **Blockiert Ziel-Mutationen?** | ja — ausser UMLAND und Brand |

---

## Module Scores

| Modul | Punkte | % | Anmerkung |
|---|---|---|---|
| 1 · Target Validation (D05–D09) | **SKIP** | — | 30/30 Kampagnen ohne Ziel — nichts zu validieren. 25 Pkt aus dem Nenner. |
| 2 · Strategy Selection (D01–D04) | 5 / 15 | 33 % | D01 + D03 flächendeckend FAIL; D04 INFO |
| 3 · Learning Phase (D10–D13) | 7,5 / 7,5 | 100 % | D10/D12 INFO (Feld nicht verfügbar / keine Ausschlüsse) |
| 4 · Portfolio Health (D14–D17, D27) | 4,8 / 6 | 80 % | D15 WARN; D14/D16/D27 SKIP bzw. INFO |
| 5 · CPC & Cost Health (D22–D24) | 4,0 / 6,67 | 60 % | D22 (2 WARN) + D23 (8 WARN) |
| 6 · Conversion Value Rules (D25–D26) | **SKIP** | — | Keine Value Rules im Konto. 10 Pkt aus dem Nenner. |
| 7 · Bid Adjustments (D18–D21) | 5 / 5 | 100 % | Keine manuellen Modifikatoren |
| **GESAMT** | **26,3 / 40,17** | **65 %** | **Needs Attention** |

> **Nenner-Reduktionen:** Target Validation komplett SKIP (−25) — seit dem 11.08. hat keine einzige Kampagne mehr eine Zielvorgabe. Value Rules SKIP (−10). Dazu D04, D10, D12, D16, D24, D27 als INFO.
> **Die 100 % bei Learning Phase sind kein Verdienst** — sie bedeuten nur, dass niemand kürzlich an Zielen gedreht hat.

---

## Risiken

### 🔍 Investigate first — blockierend

| Was | Warum | Wohin |
|---|---|---|
| **Salesforce-Import (M-Layer)** | Das Gebotssignal ist seit April um 63 % eingebrochen. Genau dieses Signal fehlt den 28 Kampagnen. Die Aushungerung ist zu einem Teil ein Messproblem, nicht nur ein Strukturproblem. | **Bestehenden Report lesen:** `tracking/tracking-audit.md` (10.08., 48 %, Completeness 34 %) — *„`SF: New Lead (1)` — tot und aus der Conversions-Metrik entfernt."* |
| **Erlös je Vermittlung (B-Layer)** | Ohne ihn ist kein Ziel-CPA ableitbar. Betrifft heute allerdings eine leere Fläche. | **Bestehenden Report lesen:** `strategy/strategy-audit.md` (10.08., 55 %) — *„Conditional Go — Deckungsbeitrag je Vermittlung > 278 CHF."* |

### 🔧 Struktureller Fix — vor jeder Zielvorgabe

| Was | Umfang | Wohin |
|---|---|---|
| **Konsolidierung: 30 Kampagnen teilen sich ~176 Conversions/Monat** | 28 Kampagnen unter 15 Conv/30 T. Zwei bei null (Gerüstbauer, Kranführer), vier bei eins. Weniger, grössere Kampagnen heben alle über die Lernschwelle. | `/account-auditor` (10.08. vorhanden) — **Achtung Guardrail #10:** keine Profession pausieren, Konsolidierung heisst zusammenlegen, nicht abschalten |
| **5 verwaiste Portfolio-Strategien, 3 davon mit aktivem CPC-Cap** | `Gebäudetechnik1`, `Gebäudetechnik2`, `DE Gebäudetechnik1 (old)`, `DE Push`, `CH Push` — ENABLED, an null Kampagnen gebunden. Altlast des 2025er-Portfolio-Experiments. | Manuell im UI löschen — **latentes Risiko:** wird versehentlich eine Kampagne angebunden, greift sofort ein CPC-Cap |

### 🔄 Effizienz zuerst

| Was | Warum | Wohin |
|---|---|---|
| **8 Kampagnen mit CPC-Anstieg über 3 Perioden** | Montage-Elektriker 1,84 → 2,30 → **2,54** · Polymechaniker 1,65 → 1,69 → **2,08** · Automatiker 1,53 → 1,55 → **1,84** · dazu Schweisser, Elektroinstallateur, Abdichter, Baumaschinenführer, Metallbaukonstrukteur. Steigende CPCs bei gleichzeitig fallendem Signal verschärfen die Aushungerung. | **Bestehende Reports:** `competitive/competitive-audit.md` (11.08., 41 %) — nur Montage-Schreiner zeigt echten Wettbewerbsdruck; die übrigen Anstiege sind eher QS-getrieben → `/quality-score-auditor` **Re-Run** (8 T alt) |
| **2 CPC-Spitzen** | Baumaschinenführer +37 %, Gerüstbauer +32 % gegenüber den 14 Tagen davor. Gerüstbauer hat **0 Conversions** bei 93 CHF Spend. | `/quality-score-auditor`, `/search-term-auditor` (18.08. frisch — dort keine Negations-Kandidaten) |

### ✅ Act now (safe)

| Was | Umfang | Wohin |
|---|---|---|
| **UMLAND: Budget-Uplift, kein Ziel setzen** | Eine von nur zwei Kampagnen über der Lernschwelle (16 Conv/30 T). Seit 11.08. budget-limitiert statt rang-limitiert. Kein tCPA — das war der Fehler vom 24.07. | `/budget-optimizer raise` — **nicht** `/bidding-optimizer` |

### ⚠️ Hold

| Was | Begründung |
|---|---|
| **Ziel-CPAs auf den 28 Kampagnen setzen** | Ein tCPA auf einer Kampagne mit 2 Conversions/Monat steuert nicht, er drosselt. Genau dieser Mechanismus hat UMLAND vom 24.07. bis 11.08. auf 78,5 % Rang-Verlust gebremst. **Nicht wiederholen.** |
| **Portfolio-Bidding als Konsolidierungs-Ersatz** | Guardrail #4: 23.06.2025 wurden 8 Gewerke (CV 52 %) gebündelt → **7 von 8 negativ** (Schweisser +188 %). Für Kollabo widerlegt. Conversion-Volumen bündelt man über Kampagnen-Struktur, nicht über Gebots-Portfolios. |
| **Strategie-Wechsel (z. B. auf tROAS)** | BID-D02 steht 30/30 auf PASS — die Strategie passt zum KPI. Ausserdem sind alle `conversionActionValues` null (GAP-1); tROAS wäre nicht berechenbar. |

---

## Opportunities

| Typ | Scope | Bewertung |
|---|---|---|
| Starvation Recovery (BID-D09) | — | Keine — Modul läuft SKIP, es gibt keine Ziele |
| Budget-Lost Recovery (BID-D24) | 27 INFO / 3 PASS | Deckt sich mit den Budget-Opportunities; dort nach Rang-Gegenrechnung **verworfen** ausser UMLAND |
| **Lernschwellen-Konsolidierung** | 28 Kampagnen | Grösster Hebel, aber strukturell — nicht über `/bidding-optimizer` erreichbar |

---

## Learning State

| Kennzahl | Wert |
|---|---|
| Kampagnen in Lernphase | **0** von 30 |
| Kampagnen mit Strategie-Änderung < 14 T | 0 |
| Kampagnen mit Ziel-Änderung < 14 T | 0 (UMLAND-Zielentfernung 11.08. = 7 T, Ziel danach leer) |
| Kampagnen über Lernschwelle (≥15 Conv/30 T) | **2** — Brand (23), UMLAND TEST (16) |
| Kampagnen unter Lernschwelle | **28** — Median 3–4 Conv/30 T |
| Data Exclusions aktiv | 0 |

### Conversions/30 T — die 28 geflaggten Kampagnen

| Conv | Kampagnen |
|---|---|
| 0 | Gerüstbauer · Kranführer |
| 1 | Abdichter · Baumaschinenführer · Montage-Schreiner · Trockenbauer |
| 2 | Dachdecker · Metallbaukonstrukteur · Montage-Elektriker |
| 3 | Gärtner · Polymechaniker · Produktionsmechaniker · Sanitärinstallateur |
| 4 | Automatikmonteur · Strassenbauer · Zimmermann |
| 5 | DYN Catchall · Maler · Metallbauer |
| 6 | Heizungsinstallateur · Schweisser |
| 7 | Bauarbeiter · Gipser · Grundbauer · Maurer |
| 8 | Automatiker |
| 13 | Elektroinstallateur |
| 14 | Compeditor |

> Elektroinstallateur (13) und Compeditor (14) liegen knapp unter der Schwelle. Bei beiden würde ein moderater Volumen-Zuwachs reichen — sie sind die nächsten Konsolidierungs-Kandidaten nach oben.

---

## Sequenzierte Handoffs

1. **Salesforce-Import klären** → Frage an Kollabo. Report liegt: `tracking/tracking-audit.md` (10.08.)
2. **Erlös je Vermittlung klären** → Frage an Kollabo. Report liegt: `strategy/strategy-audit.md` (10.08.)
3. **`/quality-score-auditor`** → Re-Run (8 T alt). Erklärt die 8 CPC-Anstiege und misst LP-Wirkung
4. **LP-Fixes umsetzen** → `lp/lp-audit.md` Prio 1
5. **Konsolidierung planen** → `/account-auditor`, unter Beachtung von Guardrail #10
6. **`/budget-optimizer raise` — nur UMLAND** → beide Audits von heute zeigen auf dieselbe Kampagne
7. **Ziel-CPAs — frühestens nach Schritt 1, 3 und 5.** Vorher steuert kein Ziel, es drosselt nur.

---

## Modul-Details

### Modul 1 — Target Validation (SKIP)

| ID | Verdikt | Befund |
|---|---|---|
| BID-D05 | SKIP ×30 | Ziel vs. Break-even — keine Kampagne hat ein Ziel |
| BID-D06 | SKIP ×30 | Ziel-Realismus — dito |
| BID-D07 | SKIP ×30 | Performance Achievement Ratio — dito. *(Am 10.08. noch 0,33 für UMLAND)* |
| BID-D08 | SKIP ×30 | Ziel-Abweichung — dito. *(Am 10.08. noch 259 % für UMLAND)* |
| BID-D09 | SKIP ×30 | Starvation Recovery — dito |

### Modul 2 — Strategy Selection (5 / 15)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BID-D01 | FAIL | 0/5 | 28 Kampagnen: Smart Bidding unter absolutem Mindestvolumen |
| BID-D02 | PASS | 5/5 | 30/30: Strategie passt zum Primär-KPI (CPA ↔ MAXIMIZE_CONVERSIONS) |
| BID-D03 | FAIL | 0/5 | 28 Kampagnen unter 15 Conv/30 T. Median 3–4 |
| BID-D04 | INFO | — | Strategie-Alter/Wechselhistorie — 30 INFO |

### Modul 3 — Learning Phase (7,5 / 7,5)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BID-D10 | INFO | — | Lernstatus-Feld über die API nicht verfügbar |
| BID-D11 | PASS | 3,75 | Keine Kampagne in aktiver Lernphase |
| BID-D12 | INFO | — | Keine Data Exclusions konfiguriert |
| BID-D13 | PASS | 3,75 | Keine überstürzten Ziel-/Strategie-Änderungen (<14 T) |

### Modul 4 — Portfolio Health (4,8 / 6)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BID-D14 | SKIP | — | Keine Portfolio-Strategie an einer aktiven Kampagne |
| BID-D15 | WARN | 1,8/3 | 0 Kampagnen + **3 Portfolios mit aktivem CPC-Cap**. Caps können Smart Bidding beschränken. |
| BID-D16 | INFO | — | Portfolio-Zusammensetzung |
| BID-D17 | PASS | 3/3 | Kein Konflikt Shared Budget ↔ Portfolio-Strategie |
| BID-D27 | INFO ×5 | — | 5 verwaiste Portfolios ENABLED an 0 Kampagnen |

### Modul 5 — CPC & Cost Health (4,0 / 6,67)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BID-D22 | WARN | 2,0/3,33 | 2 CPC-Spitzen: Baumaschinenführer +37 %, Gerüstbauer +32 % |
| BID-D23 | WARN | 2,0/3,33 | **8 Kampagnen mit CPC-Anstieg über 3 Perioden** |
| BID-D24 | INFO | — | 27 INFO / 3 PASS — Simulator-Gap-Heuristik |

### Modul 6 — Conversion Value Rules (SKIP)

| ID | Verdikt | Befund |
|---|---|---|
| BID-D25 | SKIP | Keine Conversion Value Rules im Konto |
| BID-D26 | SKIP | dito |

### Modul 7 — Bid Adjustments (5 / 5)

| ID | Verdikt | Pts | Befund |
|---|---|---|---|
| BID-D18–D21 | PASS | 5/5 | Keine manuellen Gebots-Modifikatoren (Gerät/Standort/Zeit/Zielgruppe) vorhanden |

> **Anmerkung zur Geräte-Spreizung:** `business.md` §4.4 dokumentiert Desktop-CPA 40,93 gegen Mobile 58,68 bei 71 % Mobile-Spend. Unter Smart Bidding sind Geräte-Gebotsanpassungen wirkungslos (ausser −100 % als Ausschluss) — deshalb steht D18 zu Recht auf PASS. Der Hebel liegt bei `/geo-schedule-auditor`, nicht hier.

---

## Datengrundlage & Vorbehalte

| Punkt | Bedeutung |
|---|---|
| **Break-even ist ein Proxy** | 75 CHF = 1,5 × Konto-Ø, **nicht margenbasiert**. GAP-1 offen. Betrifft heute keine gewertete Diagnostik, weil Modul 1 komplett SKIP läuft. |
| **Engine-Ausgabe zeigt `$` statt CHF** | Anzeigefehler in `analyze-temporal.js`; alle Werte sind CHF. |
| **Fenster überspannt den 11.08.** | UMLAND-Zielentfernung liegt 7 Tage zurück. CPC- und Conversion-Werte der Kampagne mitteln über den Bruch. |
| **`account-changelog.md` 7 Tage alt** | Lernstatus-Findings stützen sich teilweise darauf. Vor Ziel-Mutationen refreshen. |
| **Conversion-Zahlen sind Qualified-Basis** | Die Lernschwelle von 15 gilt für die gebotswirksame Aktion — das ist `SF: Qualified (2)`. Auf Bewerbungs-Basis läge das Konto deutlich darüber, aber darauf wird nicht geboten. |
