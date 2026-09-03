---
id: kollabo.keyword-rules
layer: customer
client: kollabo
status: canonical
triggers: [keyword-optimization]
topics: [match-types, pause-thresholds, brand-patterns]
last_reviewed: 2026-05-20
---
# Keyword-Rules — Kollabo

Topic-spezifische Regeln für den keyword-optimization-agent. Phase 1 deckt: Match-Type-Switches + Pause-Empfehlungen + QS-Hinweise. Bid-Anpassungen kommen in den Budget-Optimierungs-Agent.

## Account-Kontext
- **Customer ID:** 1487707588 (148-770-7588)
- **MCC:** 5591362086 (Jonas Makki)
- **Aktive Search-Kampagnen:** ~27 (Stand 28.04.2026, aus UI ermittelt)
- **Account-Stufe:** 1 (7.000 CHF Monatsbudget, < 15k → Brain miroboard §1 Stufe 1)
- **Lookback:** 60 Tage (Brain agent_methodik.md §1: Budget < 10k → 60 Tage)
- **Wichtige Beobachtung:** Stand 28.04.2026 sind **alle aktiven Keywords auf „Weitgehend passend" (Broad)**. Daher ist NARROW_TO_PHRASE der dominante Hebel. SWITCH_TO_EXACT wird selten greifen weil keine Phrase-Keywords da sind.

## Bidding-Strategie pro Kampagne

| Kampagne (Pattern) | Bidding-Strategie | Hinweis |
|---|---|---|
| `EX \| 25 \| CH \| SEARCH \| LEAD \| Brand` | (zu kalibrieren beim ersten Pipeline-Run) | Brand: Manual CPC oder Conversion-max |
| `EX \| 25/26 \| CH \| SEARCH \| LEAD \| <Gewerk>` | Conversionen maximieren (vermutlich) | Smart Bidding — Lernphase-Warning bei Switch |
| `EX \| 26 \| CH \| SEARCH \| LEAD \| Compeditor` | Conversionen maximieren | Compeditor — Sonderbehandlung |
| `EX \| DE \| DACH \| SEARCH \| LEAD \| UMLAND TEST` | Test-Kampagne | NICHT anfassen ohne Eskalation |

**Hinweis:** Die exakte Bidding-Strategy pro Kampagne kommt aus `get_keywords_raw` Response-Feld `bidding_strategies_per_campaign`. Diese Tabelle hier ist eine erste Annahme aus UI-Beobachtung und wird beim ersten Pipeline-Run mit echten Werten überschrieben.

## Match-Type-Switch — Schwellen

### SWITCH_TO_EXACT (Phrase → Exact)
- **Mindest-Conversions:** ≥ 3
- **CPA-Bedingung:** ≤ Account-Ø-CPA
- **Mindest-Klicks:** ≥ 20

### NARROW_TO_PHRASE (Broad → Phrase)
- **Mindest-Klicks:** ≥ 50 (Broad braucht mehr Daten als Phrase, weil mehr Streuung)
- **Conv-Rate-Bedingung:** Conv-Rate < 0.5 × Account-Ø-Conv-Rate
- **Mindest-Spend:** ≥ 30 CHF in Lookback (verhindert Mikro-Empfehlungen)
- **Sonderfall:** Keyword mit ≥ 100 Klicks und 0 Conv → NARROW-Vorschlag auch ohne CPA-Vergleich

### EXPAND_TO_PHRASE (Exact → Phrase)
- **Phase 1: nicht aktiviert.** Streuungsrisiko überwiegt potenziellen Volume-Gewinn. Aktivieren wenn Bedarf da.

### NO_CHANGE / PROTECT
- Top-Performer (siehe unten)
- Pinned/Brand (siehe unten)
- Mindestdatenbasis nicht erreicht → MONITOR statt PROTECT

### Smart-Bidding-Warning
Bei Kampagnen mit `MAXIMIZE_CONVERSIONS`, `TARGET_CPA`, `TARGET_ROAS`, `MAXIMIZE_CONVERSION_VALUE`: jeder Match-Type-Switch-Vorschlag bekommt im `notes`-Feld den Hinweis: „Smart Bidding aktiv — Switch resettet Lernphase ~14 Tage. Approve nur wenn Datenbasis stark genug."

Trotzdem wird vorgeschlagen wenn Schwellen klar erreicht sind. Es ist ein Warning, kein Block.

## Pause-Empfehlungen — Schwellen

### PAUSE_KEYWORD
- **Mindest-Spend:** ≥ 30 CHF in 60 Tagen
- **Conversions:** = 0 in 60 Tagen
- **Mindest-Klicks:** ≥ 20 (Signifikanz, Brain agent_methodik.md §2)
- **Cross-AdGroup-Check:** Es muss eine andere konvertierende Variante in derselben AdGroup geben (Plural, Synonym, Match-Type-Geschwister). Wenn das pausierte Keyword das **einzige aktive Keyword** der AdGroup ist → **eskalieren** statt PAUSE-Vorschlag.

### MONITOR
- Spend > 0 aber < 20 Klicks → kein Pause-Vorschlag, nur Hinweis im Sheet

**Kalibrierung:** 30 CHF ist konservativ für 7.000 CHF Monatsbudget (~0.4% Anteil). Falls beim ersten Pipeline-Run zu viele oder zu wenige Treffer → in dieser Datei anpassen und im Changelog dokumentieren.

## Top-Performer-Schutz (PROTECT)
- ≥ 3 Conversions in Lookback UND CPA ≤ 0.8 × Account-Ø-CPA
- Pinned Keywords (laut API-Response oder hier in „Geschützte Keywords" gelistet)

## Quality-Score-Hinweis (Modul 3, reiner Hinweis)
- **Trigger:** QS ≤ 4 UND Impressions ≥ 100 in Lookback
- **Ausgabe im Sheet:** in der `notes`-Spalte „QS=<X>, schwächste Komponente: <CTR / Anzeigenrelevanz / LP-Erfahrung>"
- **Action:** `MONITOR` (kein direkter Push-Hebel)
- Hinweis aus Brain onenote §8: hoher QS = niedrigere CPCs. Bei QS ≤ 4 ist die Differenz erheblich.

## Brand-Keywords (Hard-Regeln)
- **Brand-Patterns:** `kollabo`, `kollabo ag`, `kollabo.com`, alle Kollabo-Schreibvarianten
- **Quelle:** Shared Negative List `NKW_Brand` (siehe `search-terms-rules.md`)
- **Pause:** **NIE** ohne Eskalation
- **Match-Type-Switch:** Default Exact für Brand-Keywords. Wenn aktuell Phrase oder Broad: SWITCH_TO_EXACT mit hoher Priorität. Wenn aktuell Exact: PROTECT.
- **QS-Hinweis:** ja zeigen, weil LP-Optimierung relevant für CPC-Ersparnis

## Compeditor-Keywords (Sonderregeln)
- **Compeditor-Patterns:** Begriffe aus Shared Negative List `NKW_Compeditor` (siehe `search-terms-rules.md`)
- **Compeditor-Kampagnen:** `EX | 26 | CH | SEARCH | LEAD | Compeditor` (Pattern, falls Kampagnen-Naming sich ändert: in `search-terms-rules.md` aktualisieren)
- **Match-Type-Switch:** in Compeditor-Kampagnen typisch breitere Match-Types (Phrase) gewollt — kein NARROW-Vorschlag ohne extreme Streuungs-Indikatoren (≥ 200 Klicks, < 0.2 × Account-Ø-Conv-Rate)
- **Pause:** nur wenn Compeditor-Kampagne als Ganzes ineffizient → **eskalieren** zur Strategie-Diskussion

## Geschützte Keywords (manuelle Liste)
- (aktuell leer — Liste wird beim ersten Pipeline-Run gefüllt mit Keywords die der User explizit schützen will)

Format pro Eintrag:
```
- <keyword_text> [<match_type>] in <ad_group_name>: <Begründung>
```

## Cross-Kampagnen-Konflikte
- Wenn dasselbe Keyword in mehr als einer Kampagne aktiv ist (laut `get_keywords_raw`-Response):
- Empfehlung: in der besser performenden Kampagne behalten, in der schwächeren auf **Kampagnen-Ebene-Negativ** setzen (nicht Shared List, sonst blockiert das auch die gute Kampagne)
- Bei HIGH_PRIORITY-Konflikt (Brand vs. Generic, Search vs. PMax): immer **eskalieren**

---

## Ausnahmen vs. Brain (Topic: Keyword-Optimization)

(Aktuell leer — alle Brain-Defaults gelten unverändert. Wenn beim Arbeiten konkrete Override-Bedarfe auffallen, hier dokumentieren mit dem Format aus dem `_template/keyword-rules.md`.)

---

## Änderungshistorie
- 2026-04-28 v1: Initial. Defaults aus Brain abgeleitet + UI-Beobachtung (alle Keywords Broad). Schwellen sind konservativ und müssen nach erstem Pipeline-Run kalibriert werden.
