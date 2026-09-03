# Keyword Audit — Kollabo

**Datum:** 2026-08-10 · **Fenster:** 30 Tage · **Conversion-Lag:** 14 T
**Periode A:** 2026-06-28 – 2026-07-27 · **Periode B:** 2026-05-29 – 2026-06-27
**Account:** 1487707588 · **Keywords im Scope:** 386 (aktive Ketten) · **Währung:** CHF

---

## Executive read

57 % — und die wichtigste Aussage dieses Audits ist eine Warnung davor, das Naheliegende zu tun. 18 Keywords stehen als UNPROFITABLE geflaggt und verbrennen 1.792 CHF, das sind 23,4 % des gesamten Keyword-Spends bei einem CPA von 118,59 gegen eine operative Schwelle von 75. Der Reflex wäre, sie zu pausieren. **Das wäre falsch.** 91,3 % dieses Spends liegt auf Core-Terms — `sanitär jobangebote`, `gipser stellen zürich`, `heizungsmonteur stellenangebote`, `bauwerksabdichter jobs`. Das sind keine Streuverluste, das ist Kollabos Haustür. Wer sie abschaltet, schaltet das Geschäft ab. Die B3-Regel des Playbooks feuert weit über ihrer 50-%-Schwelle und blockiert jede Pause-Empfehlung: **das Problem liegt nicht bei den Keywords, sondern hinter ihnen** — bei Landing Page, Angebot und Ziel.

Prio zwei ist ein Befund, den ich so nicht erwartet hatte: **die Match-Type-Verengung ist funktional wirkungslos.** Strukturell sieht das Konto diversifiziert aus (162 Broad, 139 Phrase, 85 Exact), aber von den 85 Exact-Keywords sind 27 komplett ohne Impressionen und 25 weitere Low-Performer — genau ein einziges ist ein HERO. Bei Phrase dasselbe Muster: 35 Zombies, 31 Low-Performer, 3 HEROs. 62 der 93 impressionslosen Keywords sind Phrase oder Exact. Sie wurden angelegt, aber die Broad-Geschwister in derselben Ad Group gewinnen die interne Auktion. Die Verengung hat stattgefunden und nichts bewirkt — das erklärt, warum Phrase weiterhin den schlechteren CPA liefert als Broad.

Prio drei sind die immer sicheren Strukturfixes: 12 Match-Type-Redundanzen, 4 kampagnenübergreifende Konflikte, 3 echte Duplikate — und **keiner davon ist durch ein Negativ abgedeckt** (0 von 19). `polymechaniker schweiz` läuft in zwei Kampagnen gleichzeitig und ist in der einen HERO (CPA 40,66), in der anderen UNPROFITABLE (CPA 97,04). Dieselbe Suchanfrage, zwei Gebote, doppelt bezahlt.

Kein Problem sind: die Hygiene (384 von 386 Keywords ELIGIBLE, alle APPROVED, keine Erstseiten-Gebotsprobleme), die Intent-Ausrichtung (praktisch keine informationellen Keywords, Brand sauber getrennt), und die HERO-Schicht — 33 Keywords tragen 43,7 % des Spends bei einem CPA von 32,59, also deutlich unter Schwelle.

Der frische `/tracking-specialist`-Report von heute (48 %) entwertet einen Befund: 82 Keywords sind als TIER_DEGRADED markiert, aber der Vergleich Periode A gegen B fällt genau in den Zusammenbruch des Salesforce-Imports (`SF: New Lead` seit 01.07. bei null). Die Degradation misst überwiegend Messverlust, nicht Performance. **Ich habe D09 deshalb aus der Wertung genommen statt es als FAIL zu zählen.** Und `/strategy-specialist` (55 %, heute) präzisiert, woran die Rentabilitätsaussage hängt: die Schwelle von 75 CHF ist Kollabos eigene empirische Pause-Schwelle, kein margenbasierter Break-even — der bleibt offen bis der Erlös je Vermittlung bekannt ist.

Kein Score-Trend — erster Lauf.

---

## Business-Kontext

| Feld | Wert |
|---|---|
| Primär-KPI | CPA |
| **Rentabilitätsschwelle** | **75 CHF** |
| **Herkunft der Schwelle** | ⚠️ **Kein margenbasierter Break-even.** 1,5 × Konto-Ø (49,98) = Kollabos eigene, aus 149 bewerteten Änderungen 2024/2025 validierte INEFFICIENT-Schwelle (`business.md` §8). |
| Primäre Conversion-Aktion | `SF: Qualified (2)` |
| Conversion-Werte | **unbekannt** — [GAP-1] |
| Core-Product-Tokens | job, jobs, stelle(n), stellenangebot(e), arbeit, bewerbung, temporär, festanstellung, kollabo, schweiz, efz |

> ⚠️ Jede Rentabilitätsaussage in diesem Report ist gegen die **operative** Schwelle gemessen,
> nicht gegen echte Marge. Ein Keyword mit CPA 100 ist „über Schwelle", nicht zwingend „unrentabel".

---

## Diagnose

Die Ursache liegt auf dem **Business-Layer**. Der unprofitable Spend konzentriert sich zu 91,3 % auf
Core-Terms — Keywords, die exakt das beschreiben, was Kollabo verkauft. Wenn die zentralen
Suchbegriffe eines Geschäfts über der Effizienzschwelle liegen, ist nicht die Keyword-Auswahl
falsch, sondern die Konversion dahinter oder das Ziel davor. Der erste Schritt ist deshalb
`/lp-auditor` und `/offer-auditor`, nicht `/keyword-optimizer pause`.

---

## Evidenz-Leiter

### Measurement-Layer (aktiv — blockiert Pausen)
- 82 Keywords als TIER_DEGRADED markiert, 1.653,54 CHF betroffen. Der Periodenvergleich fällt
  in den SF-Import-Zusammenbruch → Degradation ist überwiegend Messartefakt. **→ H1**
- `/tracking-specialist` (2026-08-10, 48 %): *„SF: New Lead (1) auf
  `include_in_conversions_metric = false`, 0 Conversions seit 01.07."* **→ H1**

### Business-Layer (aktiv — blockiert Pausen)
- **B3: 91,3 % des UNPROFITABLE-Spends liegt auf Core-Terms** (15 von 18 Keywords,
  1.636,22 von 1.791,90 CHF). Schwelle für Blockade: 50 %. **→ H2**
- Rentabilitätsschwelle ist operativ, nicht margenbasiert — echter Break-even offen. **→ H2**
- `/strategy-specialist` (2026-08-10, 55 %): *„Conditional Go, Bedingung: Deckungsbeitrag je
  Vermittlung > 278 CHF."* **→ H2**

### Conversion-Layer (aktiv)
- UNPROFITABLE-CPA 118,59 vs. HERO-CPA 32,59 — Faktor 3,6 bei vergleichbarer Intent-Qualität.
  Das deutet auf Konversionsproblem, nicht auf Traffic-Qualität. **→ H3**
- `business.md` §0: 78,4 % der Keywords mit `BELOW_AVERAGE` Landing-Page-Erfahrung. **→ H3**

### Traffic/Struktur-Layer
- 12 Match-Type-Redundanzen, 4 Cross-Campaign-Konflikte, 3 Duplikate — **0 von 19 negativ abgedeckt**. **→ H4**
- 93 Zombies (0 Impressionen), davon 62 Phrase/Exact — Verengung funktional wirkungslos. **→ H5**

---

## Modul-Scores

| Modul | Punkte | % |
|---|---|---|
| Match Type Health | 8 / 20 | 40 % |
| Performance Segmentation | 9,6 / 24 | 40 % |
| Cannibalization & Duplicates | 7,5 / 18,75 | 40 % |
| Keyword Hygiene | 10 / 10 | 100 % |
| Intent Alignment | 15 / 15 | 100 % |
| **Gesamt** | **50,1 / 87,75** | **57 %** — Needs Attention |

> D09 (Tier-Degradation) und D12 (PMax-Overlap) aus dem Nenner: Messartefakt bzw. kein PMax.

---

## Tier-Verteilung

| Tier | KW | Spend | Anteil | Conv | CPA |
|---|---|---|---|---|---|
| **HERO** | 33 | 3.348,03 | 43,7 % | 102,73 | **32,59** |
| **UNPROFITABLE** | 18 | 1.791,90 | 23,4 % | 15,11 | **118,59** |
| INSUFFICIENT_DATA | 130 | 1.545,76 | 20,2 % | — | — |
| ACTIVE | 23 | 625,52 | 8,2 % | 32,41 | 19,30 |
| OVER_TARGET | 8 | 346,17 | 4,5 % | 7,48 | 46,28 |
| ZOMBIE | 93 | 0,00 | 0 % | 0 | — |
| LOW_PERFORMER | 81 | 0,00 | 0 % | 0 | — |

**Match Type × Tier**

| | HERO | ACTIVE | OVER_TARGET | UNPROF. | LOW_PERF | ZOMBIE | INSUFF. |
|---|---|---|---|---|---|---|---|
| BROAD (162) | **29** | 12 | 6 | 15 | 25 | 31 | 44 |
| PHRASE (139) | 3 | 9 | 2 | 3 | 31 | **35** | 56 |
| EXACT (85) | **1** | 2 | 0 | 0 | 25 | **27** | 30 |

---

## Aktionen

### 🔍 Zuerst untersuchen (blockierend)

| Befund | Warum blockierend | Handoff |
|---|---|---|
| SF-Import-Zusammenbruch verzerrt Periodenvergleich | 82 TIER_DEGRADED sind überwiegend Messartefakt | **Bestehender Report von heute:** `context/analysis/tracking/tracking-audit.md` — kein Re-Run nötig |
| Break-even unbestimmt | „UNPROFITABLE" ist gegen operative Schwelle gemessen, nicht gegen Marge | **Bestehender Report von heute:** `context/analysis/strategy/strategy-audit.md` — offene Frage: DB je Vermittlung > 278 CHF? |

### 🔧 Struktureller Fix (statt Pause)

**B3 feuert bei 91,3 % — die 18 UNPROFITABLE-Keywords sind Core-Terms.**

| Keyword | Match | Core | QS | Spend | Conv | CPA |
|---|---|---|---|---|---|---|
| `sanitär jobangebote` | BROAD | ✅ | — | 204,58 | 1,95 | 105,02 |
| `jobplattformen` | BROAD | ✅ | — | 183,23 | 2,22 | 82,37 |
| `gipser stellen zürich` | BROAD | ✅ | — | 153,82 | 1,50 | 102,55 |
| `bauwerksabdichter jobs` | BROAD | ✅ | — | 146,18 | 1,00 | 146,18 |
| `polymechaniker schweiz` | BROAD | ✅ | 6 | 145,56 | 1,50 | 97,04 |
| `temporär Strassenbauer` | BROAD | ❌ | — | 123,98 | 1,00 | 123,98 |
| `heizungsmonteur stellenangebote` | BROAD | ✅ | — | 114,33 | 1,00 | 114,33 |
| `gipser freie stellen` | BROAD | ✅ | 5 | 113,09 | 1,50 | 75,39 |
| `hilfsarbeiter bau` | BROAD | ✅ | 5 | 96,70 | 0,02 | **4.529,70** |
| `gipser job` | BROAD | ✅ | 3 | 96,68 | 0,50 | 193,36 |

**Routing statt Pause:**
1. `/lp-auditor` — 78,4 % `BELOW_AVERAGE` LP-Erfahrung ist der dokumentierte Hauptverdacht
2. `/offer-auditor` — Angebotsqualität auf den Gewerke-Landingpages
3. `/search-term-auditor ngrams` — prüfen, ob einzelne n-Gramme den Verlust erklären (dann n-Gramm ausschließen statt Keyword pausieren)
4. `/strategy-specialist` — Ziel gegen echte Marge validieren, sobald [GAP-1] geschlossen ist

> **Einzige Ausnahme:** `hilfsarbeiter bau` mit CPA 4.529,70 bei 0,02 Conversions und QS 5.
> Das ist kein Konversionsproblem, das ist ein Relevanzproblem. Kandidat für Match-Type-Verengung
> oder Negativ — nicht für Pause der Kampagne.

### ✅ Sofort sicher

| Aktion | Umfang | Detail |
|---|---|---|
| **Duplikate auflösen** | 3 Gruppen | `polymechaniker schweiz` (UMLAND ↔ Polymechaniker — HERO CPA 40,66 vs. UNPROFITABLE CPA 97,04), `elektriker stellenangebote`, `cnc fräser jobs` |
| **Cross-Campaign-Konflikte** | 4 | `trockenbauer jobs schweiz`, `elektriker stellenangebote`, `montage elektriker efz`, `cnc fräser jobs` |
| **Match-Type-Redundanzen** | 12 | u. a. `schweisser jobs schweiz`, `metallbauer jobs schweiz`, `sanitärinstallateur jobs`, `maler job schweiz` |
| **Negativ-Abdeckung herstellen** | **0 von 19** | Keiner der 19 Overlaps ist durch ein Negativ abgedeckt. Kampagnen-Ebene-Negative, **nicht** Shared List (sonst blockiert es auch die gute Kampagne) |
| **Zombie-Bereinigung prüfen** | 93 KW | 0 Impressionen, 0 Spend. Kein Schaden, aber Rauschen. **Vorher klären:** 62 davon sind Phrase/Exact — siehe unten |

### ⚠️ Niemals pausieren

**OVER_TARGET (8 Keywords, 346,17 CHF, CPA 46,28)** — liegen unter der Schwelle von 75 und sind
profitabel. Sie erscheinen nur über dem Kampagnenziel, weil 29 von 30 Kampagnen gar kein Ziel haben.

`Jop.ch` · `stellenangebote tiefbaufacharbeiter` · `stelle als automatiker` · `maler schweiz` ·
`Manpower jobs` · `schreiner jobs zürich` · `kollabo ch` · `kollabo jobs`

---

## Der Match-Type-Befund im Detail

`keyword-rules.md` (28.04.2026) hielt fest, alle Keywords stünden auf Broad. Die Verengung hat
seither stattgefunden — **aber sie wirkt nicht.**

| | Angelegt | Ohne Impressionen | HERO | Spend-Anteil |
|---|---|---|---|---|
| BROAD | 162 | 31 | **29** | 88 % |
| PHRASE | 139 | 35 | 3 | 10 % |
| EXACT | 85 | **27** | **1** | 2 % |

62 der 93 impressionslosen Keywords sind Phrase oder Exact. Die Ursache ist strukturell: Broad
und Phrase/Exact liegen in **derselben** Ad Group, und bei Smart Bidding gewinnt in der internen
Auktion regelmäßig das Broad-Keyword mit der breiteren Signalbasis. Die engeren Varianten
verhungern.

**Konsequenz:** Die 12 Match-Type-Redundanzen sind nicht nur Hygiene — sie sind die Erklärung.
Solange beide Varianten in derselben Ad Group stehen, bleibt die Verengung wirkungslos.
Entweder Broad-Geschwister entfernen oder in getrennte Ad Groups legen.

---

## Diagnostik-Details

| ID | Diagnostik | Verdikt | Pts | Befund |
|---|---|---|---|---|
| KW-D01 | Match-Type-Verteilung | WARN | 3/5 | Strukturell diversifiziert, funktional Broad-only (88 % Spend) |
| KW-D02 | Broad ohne Smart Bidding | PASS | 5/5 | Alle 30 Kampagnen auf Max Conversions |
| KW-D03 | Match-Type-Redundanz | **FAIL** | 0/5 | 12 Gruppen, 0 abgedeckt |
| KW-D04 | Cross-Campaign-Konflikt | **FAIL** | 0/5 | 4 Konflikte, 0 abgedeckt |
| KW-D05 | HERO-Identifikation | PASS | 6/6 | 33 HEROs, 43,7 % Spend, CPA 32,59 |
| KW-D06 | Tier-Verteilung | WARN | 3,6/6 | 130 INSUFFICIENT_DATA (34 %) + 93 ZOMBIE (24 %) |
| KW-D07 | UNPROFITABLE | **FAIL** | 0/6 | 18 KW, 1.792 CHF, CPA 118,59 — **Pause durch B3 blockiert** |
| KW-D08 | Zombies + Low-Performer | **FAIL** | 0/6 | 174 von 386 KW (45 %) ohne Spend |
| KW-D09 | Tier-Degradation | INFO | — | 82 KW — **Messartefakt, aus Wertung genommen** |
| KW-D10 | Duplikate | **FAIL** | 0/6,25 | 3 Gruppen, 0 abgedeckt |
| KW-D11 | Kannibalisierung | WARN | 3,75/6,25 | Ad Groups gewerkescharf; Overlaps sind die bekannten Cross-Trade-Fälle |
| KW-D12 | PMax-Overlap | SKIP | — | kein PMax |
| KW-D13 | Ähnliche Broad-Keywords | WARN | 3,75/6,25 | Semantische Varianten je Gewerk (`gipser job` / `gipser freie stellen` / `gipser stellen zürich`) |
| KW-D14 | Erstseiten-Gebot | PASS | 5/5 | keine Flags |
| KW-D15 | Serving-Status | PASS | 5/5 | 384 ELIGIBLE, 2 RARELY_SERVED, alle APPROVED |
| KW-D17 | Informationelle Intention | PASS | 7,5/7,5 | Praktisch alle Keywords transaktional job-suchend |
| KW-D18 | Brand-Terms | PASS | 7,5/7,5 | Brand sauber in Brand-Kampagne; Competitor-Terms bewusst in Compeditor |

---

## Sequenzierter Handoff

**Top-Hypothese:** Business-Layer — Core-Term-Konzentration im unprofitablen Spend (91,3 %),
erklärt ~23 % des geflaggten Spends.

1. **Measurement** — `context/analysis/tracking/tracking-audit.md` (heute). Lesen, nicht neu laufen.
2. **Business** — `context/analysis/strategy/strategy-audit.md` (heute). DB je Vermittlung klären.
3. **Search-Term-Ebene verifizieren** — `/search-term-auditor` (offen): erklären einzelne n-Gramme den Verlust?
4. **Effizienz zurückholen** — `/lp-auditor` (offen, größter dokumentierter Hebel), `/offer-auditor` (offen)
5. **Immer sichere Strukturfixes** — 3 Duplikate, 4 Cross-Campaign-Konflikte, 12 Match-Type-Redundanzen, Negativ-Abdeckung für alle 19

**Keine Pause-Empfehlung.** B3 bei 91,3 % schließt sie aus.

---

## Datenfrische

| Quelle | Zeilen | Stand |
|---|---|---|
| `keyword/keywords-periodA.csv` / `periodB.csv` | 386 / 386 | 2026-08-10 |
| `keyword/keywords-structural.csv` | 386 | 2026-08-10 |
| `keyword/negatives-*.csv` | 1.197 / 1.644 / 88 / 116 | 2026-08-10 |
| `keyword/pmax-search-terms.csv` | 0 | kein PMax |
| `evidence/keyword-tiers.csv` / `keyword-flags.csv` / `keyword-overlaps.csv` | 386 / 315 / 19 | 2026-08-10 |
| `context/account-changelog.md` | — | **fehlt** |
