# Budgetplan 8.500 CHF + UMLAND-Uplift

**Datum:** 2026-08-11 · **Account:** Kollabo (1487707588) · **Währung:** CHF
**Anlass:** Kundenauftrag — Monatsbudget 8.500 CHF, UMLAND (Grenzgänger) aufstocken
**Kontext:** Qualifikationskriterien ab 01.07.2026 geändert — vorher 2 Jahre Erfahrung in der
Schweiz, jetzt 6 Monate in der EU

---

## Kernaussage vorab

**1. Das Budget liegt bereits bei 8.512 CHF/Monat.** Die 30 aktiven Kampagnen summieren sich auf
280 CHF/Tag. Der Auftrag „auf 8.500 erhöhen" ist damit keine Erhöhung, sondern die **formale
Freigabe des Ist-Zustands**. Das ist eine gute Nachricht — die Freigabe schliesst
`business.md` [GAP-6]. Ein UMLAND-Uplift muss aber aus **Umverteilung** kommen, nicht aus Neugeld.

**2. UMLAND kann sein bestehendes Budget nicht ausgeben.** Es ist die **einzige** der 30
Kampagnen, die unter 90 % Budgetausnutzung liegt:

| Kampagne | Budget | Ist-Spend | Ausnutzung |
|---|---|---|---|
| **UMLAND TEST** | **26,0** | **19,9** | **76 %** |
| Brand | 13,0 | 12,3 | 95 % |
| Elektroinstallateur | 20,0 | 19,5 | 97 % |
| Compeditor | 20,0 | 19,3 | 97 % |
| *alle übrigen 26* | | | **91–100 %** |

**Mehr Budget auf UMLAND würde derzeit nichts bewirken.** Die Kampagne lässt schon jetzt
6 CHF/Tag liegen.

**3. Der Grund ist nicht das Budget, sondern die Gebotsvorgabe.**

| Kennzahl | Juli | August |
|---|---|---|
| Impressionen verloren durch **Budget** | **1,4 %** | **2,9 %** |
| Impressionen verloren durch **Rang** | **77,7 %** | **79,6 %** |

UMLAND läuft seit dem 24.07. auf einem **tCPA von 11,00 CHF** — das Ergebnis des
Experiments „UMLAND tCPA vs. MaxConv". Der reale Qualified-CPA der Kampagne liegt bei
**35–38 CHF**. Die Zielvorgabe ist also rund **dreimal zu niedrig**; Google bietet folgerichtig
zu vorsichtig und verliert die Auktion.

Der `/bidding-auditor` misst das unabhängig: **Performance Achievement Ratio 0,33** und
**259 % Abweichung** vom eigenen Ziel.

> **Die Freigabe des Budgets löst das Problem nicht. Die Korrektur der Zielvorgabe löst es.**

---

## Was die Kriterienänderung tatsächlich bewirkt hat

Die Umstellung zum 01.07. ist in den Daten klar sichtbar — **aber nicht dort, wo man sie
erwartet.**

### Auf Kontoebene: deutliche Verbesserung

| Monat | Spend | Qualified | **Qualified-CPA** |
|---|---|---|---|
| 2026-03 | 6.466 | 96,9 | 66,73 |
| 2026-04 | 6.863 | 83,7 | 81,99 |
| 2026-05 | 7.003 | 66,6 | 105,15 |
| 2026-06 | 7.977 | 115,8 | 68,89 |
| **2026-07** | 8.175 | **162,9** | **50,18** |
| 2026-08 (10 T) | 2.826 | 39,8 | 71,01 |

Die Qualified-Menge springt im Juli auf 162,9 — der höchste Wert des Jahres. Das ist die
Kriterienlockerung: **mehr Bewerber erfüllen die Schwelle.**

### Auf UMLAND-Ebene: keine Verbesserung

| Monat | Spend | Qualified | **UMLAND-CPA** | Konto-CPA | UMLAND ist |
|---|---|---|---|---|---|
| 2026-03 | 243 | 14,0 | **17,36** | 66,73 | 74 % günstiger |
| 2026-04 | 243 | 8,0 | 30,38 | 82,00 | 63 % günstiger |
| 2026-05 | 326 | 13,0 | 25,08 | 105,15 | 76 % günstiger |
| 2026-06 | 615 | 20,0 | 30,75 | 68,89 | 55 % günstiger |
| **2026-07** | 531 | **15,0** | **35,40** | 50,18 | 29 % günstiger |
| 2026-08 (10 T) | 227 | 6,0 | 37,83 | 71,01 | 47 % günstiger |

**UMLAND hat von der Kriterienänderung bisher nicht profitiert.** Die Qualified-Menge liegt
im Juli bei 15,0 gegenüber 20,0 im Juni. Der CPA steigt weiter.

> **Wichtige Einschränkung:** Das sind sechs Wochen Daten, und in genau diesen sechs Wochen
> liefen zwei weitere Änderungen: das UMLAND-Experiment (02.–24.07., 50/50-Traffic-Split) und
> ab 24.07. der tCPA von 11. **Beides drückt die UMLAND-Zahlen unabhängig von der
> Kriterienänderung.** Die Aussage „hat nicht geholfen" ist deshalb **nicht belastbar** — sie ist
> nur „noch nicht sichtbar".

**Konsequenz für die Reihenfolge:** Erst die Störgrössen entfernen (tCPA), dann messen, dann
Budget. In der jetzigen Konstellation lässt sich der Effekt der Kriterienänderung auf UMLAND
gar nicht sauber messen.

### Das ökonomische Warnsignal

| Monat | Qualified | Closed Won | Vermittlungsquote |
|---|---|---|---|
| Juni | 114 | 23 | **20,2 %** |
| Juli (Kriterien neu) | 175 | 16 | **9,1 %** |

Wenn die Qualifikationsschwelle sinkt, qualifizieren auch schwächere Leads. Die Vermittlungsquote
halbiert sich rechnerisch. **Das ist zu erwarten und kein Fehler** — aber es verschiebt die
Wirtschaftlichkeit:

| Basis | Kosten je Vermittlung |
|---|---|
| Alte Quote (18,1 %, 13-Monats-Mittel) | **278 CHF** |
| Juli-Quote (9,1 %) | **~550 CHF** |

*Vorbehalt: Closed Won hat ein 90-Tage-Klickfenster und einen mehrwöchigen Vertriebszyklus.
Die Juli-Qualified hatten noch keine Zeit zu schliessen — 9,1 % ist eine Untergrenze, nicht
der Endwert. Verlässlich wird die Zahl frühestens Ende Oktober.*

**Für den Budgetplan heisst das:** Der niedrigere Qualified-CPA (50,18 statt 68,89) ist real,
aber er kauft möglicherweise schwächere Leads. Bevor auf dieser Basis dauerhaft skaliert wird,
gehört die Vermittlungsquote monatlich mitgeschrieben.

---

## Der Budgetplan

### Phase 0 — sofort, kostet 0 CHF

**Einzige Massnahme: UMLAND-tCPA korrigieren.**

| | Wert |
|---|---|
| Ist | tCPA **11,00 CHF** |
| Realer Qualified-CPA | 35–38 CHF |
| **Empfehlung** | **tCPA 43 CHF** (= 37,50 × 1,15) — oder ersatzlos entfernen, zurück auf Max Conversions |

**Warum 43 und nicht höher:** `business.md` §8 dokumentiert die eigene Formel „sauberer
14-Tage-CPA × 1,15". Bei 37,50 CHF Ist-CPA ergibt das 43. Ein höherer Wert würde die Kampagne
unnötig teuer machen; ein niedrigerer würde weiter drosseln.

**Warum die Alternative „entfernen" ernsthaft zu prüfen ist:** Der `/bidding-auditor` hat
festgestellt, dass **28 von 30 Kampagnen unter dem Smart-Bidding-Mindestvolumen** von
15 Conversions/30 Tage liegen. UMLAND liegt mit 15–20 genau an der Grenze. Ein tCPA auf
Grenzvolumen ist instabil. Max Conversions ohne Ziel wäre robuster — hat aber keine
Effizienzbremse.

**Erwartete Wirkung:** UMLAND-Spend steigt von 19,9 auf bis zu 26 CHF/Tag (das bestehende Cap).
Das sind **+6 CHF/Tag = +182 CHF/Monat ohne einen Franken Neugeld.**

> **Nur eine Änderung.** `business.md` §8.3: keine Batch-Pushes. Und §8.8: nach jeder Änderung
> mindestens 7 Tage Ruhe.

### Phase 1 — Tag 14 nach dem tCPA-Fix

**Messpunkt, kein Automatismus.** Prüfen:

| Kriterium | Schwelle | Wenn erfüllt |
|---|---|---|
| UMLAND-Budgetausnutzung | ≥ 95 % (24,7 von 26 CHF/Tag) | weiter zu Phase 2 |
| Lost IS (Budget) | > 10 % | weiter zu Phase 2 |
| Qualified-CPA | ≤ 43 CHF | weiter zu Phase 2 |
| **Wenn Ausnutzung < 90 %** | | **Stopp — Budget ist nicht der Engpass.** Dann liegt es am Rang: `/lp-auditor` und `/quality-score-auditor` haben die Ursachen benannt. |

### Phase 2 — Budget aufstocken, wenn Phase 1 es rechtfertigt

**UMLAND 26 → 31 CHF/Tag (+19 %, innerhalb der ±20-%-Guardrail).**

Gegenfinanzierung aus den teuersten Kampagnen. Auswahlregel aus `business.md` §8.5:
reduzieren nur bei CPA ≥ 1,5 × Konto-Ø (= 75 CHF); Top-Performer bei ≤ 0,8 × Ø (= 40 CHF) nie
anfassen.

| Kampagne | CPA | Budget alt | Budget neu | frei | Schritt |
|---|---|---|---|---|---|
| Montage-Elektriker | **231,81** | 8,0 | 6,5 | +1,5 | −19 % |
| Gärtner | **202,17** | 7,0 | 5,6 | +1,4 | −20 % |
| Maler | **104,39** | 11,0 | 8,8 | +2,2 | −20 % |
| **Summe frei** | | **26,0** | **20,9** | **+5,1** | |

**UMLAND: 26,0 → 31,0 CHF/Tag.** Konto-Summe bleibt bei 280 CHF/Tag = 8.512 CHF/Monat.

**Bewusst nicht angetastet:**

| Kampagne | CPA | Grund |
|---|---|---|
| Brand | 15,46 | Top-Performer-Schutz (≤ 0,8 × Ø) |
| Maurer | 17,73 | Top-Performer-Schutz |
| Automatikmonteur | 29,26 | Top-Performer-Schutz |
| Automatiker | 30,73 | Top-Performer-Schutz |
| Abdichter, Kranführer, Montage-Schreiner, Gerüstbauer | 0 Conv | **Blockiert** — der `/tracking-specialist` hat offen, ob der SF-Import diese Kampagnen korrekt misst. Vor der Klärung nicht anfassen. Ausserdem: `business.md` §8.10 hält den Kundenwunsch fest, keine Profession zu pausieren. |

### Phase 3 — Tag 28, nur bei Bedarf

Wiederholung von Phase 2, wenn UMLAND erneut ans Cap läuft: **31 → 37 CHF/Tag (+19 %)**.
Gegenfinanzierung aus Produktionsmechaniker (146,90), Polymechaniker (120,31), Bauarbeiter (91,46).

---

## Harte Stoppregeln

| Regel | Quelle | Wert |
|---|---|---|
| **UMLAND-Sättigungsdeckel** | `business.md` §8.1 — in **2024 und 2025 unabhängig bestätigt** | **~85 CHF/Tag** |
| Schrittgrösse | §8.8 | max. ±20 % je Schritt |
| Ruhephase | §8.8 | ≥ 7 Tage zwischen Schritten |
| Abbruch | §8.8 | wenn ein Schritt den bereinigten CPA um > 10 % treibt → eine Stufe zurück |
| Keine Sammelerhöhungen | §8.3 | 15.08.2024: 4 Kampagnen gleichzeitig hoch → mehrfach negativ |

> ⚠️ **Der 85-CHF-Deckel steht unter Vorbehalt.** Er wurde 2024 und 2025 ermittelt — also unter
> der **alten Qualifikationsregel** (2 Jahre Schweiz) und auf der **alten Messbasis**
> (New Lead inklusive). Wenn die EU-Regel den adressierbaren Markt tatsächlich vergrössert,
> kann der Sättigungspunkt höher liegen. **Bis zum Gegenbeweis gilt der Deckel.** Er wird erst
> ab ~50 CHF/Tag relevant — bei der aktuellen Schrittfolge frühestens im Oktober.

---

## Was ich am Auftrag anders sehen würde

**Die Begründung des Kunden ist plausibel.** Wenn Grenzgänger vorher 2 Jahre Schweizer Erfahrung
brauchten, konnten sie faktisch nicht qualifizieren — ein in Deutschland arbeitender Handwerker
hat diese Erfahrung per Definition nicht. Mit „6 Monate EU" öffnet sich der Markt tatsächlich.

**Aber die Umsetzung über das Budget greift zu kurz**, aus drei Gründen:

1. **UMLAND ist nicht budgetlimitiert** (1,4 % Verlust ans Budget) — es ist gebotslimitiert.
2. **Der Effekt der Kriterienänderung ist derzeit nicht messbar**, weil Experiment und tCPA
   ihn überlagern.
3. **Die Zielgruppe wird möglicherweise geografisch verfehlt.** Alle 30 Kampagnen nutzen
   Standort-Targeting auf **`PRESENCE`** (Anwesenheit). UMLAND zielt auf deutsche Grenzregionen.
   Ein **Grenzgänger arbeitet aber in der Schweiz** — sucht er während der Arbeitszeit, wird er
   von den Schweizer Kampagnen erfasst, nicht von UMLAND. Wer die Grenzgänger-Zielgruppe
   gezielt erreichen will, sollte prüfen, ob `PRESENCE_OR_INTEREST` oder eine eigene
   Grenzgänger-Kampagne mit Schweizer Standort und deutschsprachiger Grenzregion-Ansprache
   der bessere Weg ist.

**Mein Vorschlag an den Kunden:** Die Budgetfreigabe annehmen, den tCPA sofort korrigieren, und
in 14 Tagen mit belastbaren Zahlen entscheiden. Das kostet keine zwei Wochen Wachstum — UMLAND
gewinnt durch den tCPA-Fix sofort 6 CHF/Tag an nutzbarem Budget, das heute verfällt.

---

## Offene Punkte

| # | Frage | An wen | Warum |
|---|---|---|---|
| 1 | **Vermittlungsquote nach der Kriterienänderung** — bleibt sie bei ~9 % oder erholt sie sich? | Kollabo / Salesforce | Entscheidet, ob der niedrigere Qualified-CPA echte Wirtschaftlichkeit ist. Kosten je Vermittlung: 278 CHF (alt) vs. ~550 CHF (Juli) |
| 2 | **Warum liefert `SF: New Lead (1)` seit 01.07. null?** | Kollabo / Salesforce | Wurde die Stufe mit der Kriterienänderung abgeschafft — oder ist der Import defekt? |
| 3 | **Deckungsbeitrag je Vermittlung** | Kollabo | Ohne diese Zahl bleibt jede Skalierungsentscheidung ungedeckt. `business.md` [GAP-1] |
| 4 | **Warum wurde der frühere deutsche Markteintritt beendet?** | Kollabo | 22 tote `/de-de/`-Seiten belegen einen vollständigen, eingestellten DE-Versuch (`de-tischler-sea`, `DE_GSN_DE_Brand`, `DE_GSN_DE_Meister_Stuttgart`). Bevor Deutschland ausgebaut wird, gehört der Grund geklärt. |
| 5 | **Sollen Grenzgänger über deutsche oder schweizerische Standortsignale erreicht werden?** | Martin/Kollabo | Siehe Punkt 3 oben |

---

## Zusammenfassung in einem Satz

Das Budget ist bereits freigegeben und ausgeschöpft — **ausser bei UMLAND, das 24 % seines
Budgets nicht ausgeben kann, weil eine dreifach zu niedrige Gebotsvorgabe es drosselt.**
Der Uplift beginnt deshalb nicht mit Geld, sondern mit einer Zahl: tCPA 11 → 43.
