---
id: kollabo.history
layer: customer
client: kollabo
status: canonical
triggers: ["*"]
topics: [history, budget, bidding, tracking, kpis]
last_reviewed: 2026-07-09
---
# Kollabo — Historischer Kontext (Context-Pack)

> **Zweck:** Das destillierte Konto-Gedächtnis 2023–heute für JEDEN Agent-Lauf und
> jede manuelle Entscheidung. Jede Zahl stammt aus `data/kollabo/history_facts.md`
> (generiert) oder den versionierten Impact-Reports — nichts hier ist geschätzt.
> **Pflege:** via `/build-history-context kollabo` nach jedem Monatsabschluss
> oder Review-Fenster. Nicht von Hand Zahlen ergänzen, die nicht in den Quellen stehen.

## 0. Bevor du IRGENDEINE historische Zahl benutzt: Messbrüche

| Ab | Was | Regel |
|---|---|---|
| ~Jul 2023 | davor Micro-/Alt-Zielvorhaben (CPA ~1.5–5) | 2023-H1-Zahlen NIE vergleichen; YoY erst ab Jul 2023 |
| 16.10.2024 | Zielvorhaben-Wechsel (Qualified/Converted dazu) | milder Bruch — über den Bruch nur relativ (DiD) |
| 30.10.2025 | **SF „Closed Won" primär + Klick-Fenster 30→60 T** | **KEIN absoluter CPA-Vergleich über dieses Datum.** Conv-Volumen fiel Okt 433 → Dez 160 als Mess-Effekt. Andere, bessere Conv-Population (echte Vermittlungen) |
| ~Mitte Jun 2026 | SF-Import defekt (New Lead = 0), entdeckt 30.06. | Conv/CPA ab Mitte Juni 2026 bis Fix-Bestätigung NICHT belastbar → conv-abhängige Bewertungen UNKLAR |

## 1. Konto-Ären (CPA jeweils innerhalb der Ära lesbar)

| Ära | Spend/Monat | CPA | Kern |
|---|---|---|---|
| Q3 2023 | 2–4k | 10.70 | heutige Lead-Basis etabliert, Konto klein |
| Q4 2023 | 4–7k | 19.41 | erste Saison-Verteuerung Nov/Dez |
| Jun–Sep 2024 | 4–10k | 13.32 | Budget-Leiter-Experimente UMLAND (35→185 CHF/Tag) |
| Q4 2024 | 6–8k | 14.74 | **YoY 24–35 % günstiger als Q4 2023** — Q4 ist teuer, aber 2024 besser gemanagt |
| H1 2025 | 7–10k | 15.2 → 18.1 | schleichende Verteuerung; 23.06. Portfolio-Experiment (gescheitert) |
| Jul–Okt 2025 | 8–11k | 20.79 | Aug/Sep = teuerste Monate (25.2/22.8) |
| Nov–Dez 2025 | 6–9k | (44.50)* | *Pivot-verzerrt — kein echter Effizienzverlust; nur DiD lesbar |
| Jan 2026 | 7k | 19.83 | neue Closed-Won-Basis: ~20 CHF ist das neue „normal" |
| Apr–Mai 2026 | 7k | 17.05 | solide; 8.5k-Plan-Skalierung läuft (280 CHF/Tag seit Ende Jun) |
| ab Mitte Jun 2026 | 8k+ | n/a | Tracking defekt — CPA-Steuerung blind bis Fix |

Datenlücken (gezogen ≠ vorhanden): **Feb–Mai 2024** und **Feb–Mär 2026** fehlen im
Backfill. 37-Monats-Fenster rollt monatlich — ältester Monat fällt laufend raus.

## 2. Validierte Leitplanken (empirisch aus 2024+2025, nicht Theorie)

1. **UMLAND-Sättigungsdeckel ~85 CHF/Tag.** In BEIDEN Jahren identisch: jede
   Erhöhung über ~85 machte Leads relativ teurer (2024: 50→101 DiD +21 %,
   120→185 +34 %; 2025: DiD +24…+177 %), jede Senkung besser (2024: 185→86
   −13 %; 2025: −15…−127 %). UMLAND = Effizienz-, nicht Volumen-Hebel.
2. **Budget-Headroom ist kein Freibrief.** Aug-2024-Erhöhungen liefen bei hohem
   Budget-Lost-IS und wurden TROTZDEM teurer — vor jeder Erhöhung Budget- vs.
   Rank-Lost-IS prüfen UND CPC ≤ RPU (kpis_metrics §2.3).
3. **Keine Batch-Budget-Pushes.** 15.08.2024: 4 Kampagnen gleichzeitig hoch →
   Schweisser +29 %, SOLAR +23 % (beide NEG); selektive Rücknahme 05.09. −38 % (POS).
4. **Portfolio-Bidding nur bei CPA-Homogenität (CV ≤ ~30 %).** 23.06.2025: 8
   Gewerke (CPA-Spanne ~15–90, CV 52 %) in eine Portfolio-Strategie → **7/8
   NEGATIV** (Schweisser +188 %); Auflösung 05/06.08. → wieder besser. Bündelung
   quer über Gewerke ist bei Kollabo widerlegt.
5. **Pausen kampagnenscharf, nie blanko.** Regel aus 29.12.2025 + 22.10.2025:
   pausieren nur bei Pre-CPA ≥ ~1.5× Konto-Ø; bei ≤ 0.8× nie (Top-Performer).
   Die Jahresend-Blankopause traf Schweisser (0.67×), Polymechaniker (0.22×),
   UMLAND (0.33×) — effizientes Volumen abgeschaltet.
6. **Auto-Apply = Münzwurf (2025: 5 POS / 6 NEG).** Nach Empfehlungs-Typ
   kuratieren, nie global an. 2024 (nur Keyword-Removals) harmlos — der Schaden
   kommt mit Budget-/Bidding-Empfehlungen.
7. **Broad-lastige Sammel-Keyword-Eingriffe sind das Struktur-Risiko.** Einzelne
   Exact/Phrase-Pausen auf teuren Keywords nützten (Elektroinstallateur DiD −69 %);
   die Broad+Exact-Sammelpause 25.08.2024 schadete (+168 %, kleiner Spend).
8. **Budget ±20 %/Schritt mit ≥7 T Ruhe** (Brain §8) — die Verstöße dagegen
   (Whipsaw 2025) sind ein Grund, warum 70 % der 2025-Verdikte niedrige
   Confidence haben: zu viele parallele Änderungen machen Wirkung unmessbar.

## 3. Experimente-Log (was schon probiert wurde)

| Wann | Was | Ausgang |
|---|---|---|
| 04.07.2024 | Brand: Manueller CPC → Conversions maximieren | kurzfristig NEG (DiD +25 %, Lernphase); Brand blieb bester Performer |
| Jun–Aug 2025 | „Portfolio Test JM" — 8 Gewerke in eine Gebotsstrategie | GESCHEITERT (7/8 NEG), selbst zurückgenommen |
| 29.12.2025 | Jahresend-Blankopause durch Client | teils sinnvoll (teure Kampagnen), teils schädlich (Top-Performer mit aus) |
| 30.06.2026 | tCPA-Experiment UMLAND (Drafts & Experimente, 50/50) | GEPLANT, Start verschoben bis Tracking-Fix + 3–5 saubere Tage; Ziel-CPA aus sauberem 14-T-CPA ×1.15 |

## 4. Kampagnen-Langzeitprofil (3-Jahres-Sicht, Spend-Top)

Effizient über die Zeit: **Brand 7.34** · Schweisser 9.98 · SOLAR 12.13 ·
Gerüstbauer 13.06 · Strassenbauer 12.66. Chronisch teuer: **Zimmermann 37.67** ·
Metallbauer 36.37 · Automatiker 24.52 · Montage-Elektriker 22.97.
UMLAND = grösster Einzelposten (17 % des 3-J-Spends, CPA 16.68, aber sättigungs-
limitiert, siehe §2.1). Vollregister: `history_facts.md` §4.

## 5. Was die Historie NICHT hergibt (ehrlich)

- **Lead-Wert / Close-Rate:** unbekannt — CPA misst die halbe Wahrheit. Grösster
  offener Hebel (steht auch in account-info leer).
- **Konto-Ebene-Changes** (Portfolio-Topup 05.08.2025, User-Entzug, Conv-Setup):
  grösste Spend-Bewegungen, gegen Konto-Trend nicht isolierbar → MANUELL bewerten.
- **Ad-Group-/Keyword-Ebene:** Analyse war kampagnenscharf; Match-Type-Mix nicht
  systematisch geprüft.
- **Änderungs-Historie vor 2024** existiert nicht (UI-Export begann 2024; API kann
  nur 30/90 T zurück). Ab 30.06.2026 manueller Zeitstrahl, Forward-Capture per Cron
  schliesst die Lücke ab Aktivierung.

## Quellen
`data/kollabo/history_facts.md` (generiert) · `reporting/kollabo/reports/impact_2024.md`
· `impact_2025.md` · `threshold-kandidaten_2024/2025.md` · `reporting/kollabo/learnings.md`
· Obsidian: `Änderungen Zeitstrahl/2026-06-30.md`, `Testing-Roadmap 7.5k zu 15k.md`
