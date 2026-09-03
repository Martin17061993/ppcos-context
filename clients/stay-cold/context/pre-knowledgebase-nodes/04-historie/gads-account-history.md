---
kunde: stay-cold
customer_id: "3599116618"
mcc: "5591362086"
account_typ: ecom (Apparel, D2C, stark saisonal Q4/BFCM)
typ: history-context-pack (v2, Historical Data Agent)
scope: KUNDEN-SCOPED — verlässt diesen Ordner nie, nicht kundenübergreifend nutzen
stand: 2026-07-10
hinweis: Stay Cold ist bewusst NICHT im frameworks/customer/-Stack (Projekt-Entscheidung
  "Stay-Cold-Integration out of scope"). Kommt das Konto je in den Agenten-Kreislauf,
  diesen Pack nach frameworks/customer/stay-cold/history.md heben + Index-Front-Matter geben.
---
# Stay Cold — Historischer Kontext (Context-Pack)

> **Zweck:** Destilliertes Konto-Gedächtnis Jun 2023 – Jul 2026 für jede Analyse-
> und Jonas-Diskussion. Jede Zahl stammt aus `data/stay cold apparal/history_facts.md`
> (generiert, mit bereinigter Kauf-Serie) oder `reports/impact_staycold.md`.
> **Refresh:** Generator mit `--purchase-only-csv` laufen lassen (Befehl unter Quellen).

## 0. Bevor du IRGENDEINEN ROAS aus diesem Konto zitierst: drei Zähl-Regime

| Regime | Zeitraum | Zählung | Regel |
|---|---|---|---|
| 1 | Aug 2023 – Apr 2024 | GA4 **+** Shopping-App parallel → **Doppelzählung** | nie absolut verwenden |
| 2 | **Mai 2024 – Sep 2025** | nur `purchase_gads_mable` | **einzige saubere Rohserie** — Anker-Fenster |
| 3 | seit 10.11.2025 | + `NewCustomerPurchase` (Kette: 10.11. → 23.11. Bidding-Goal → 18.02.26 NCA +16,46 € → 13.03.26 dauerhaft) | berichteter ROAS **~1,5× überzeichnet** (Dez 25–Jun 26 konstant 1,49–1,57×) — nur Clean-ROAS oder DiD |

NCA-Setup ist *gewollte Strategie*, kein Fehler — aber: wer im Konto „7,85" liest
(Jun 26), hat real **5,04** Kauf-Umsatz je Euro. tROAS-Ziele wirken seit 18.02.26
faktisch lockerer als beziffert.

## 1. Konto-Phasen (bereinigte Kauf-Serie)

| Phase | Zeitraum | Spend/Mon | Clean-ROAS | Kern |
|---|---|---|---|---|
| Baseline | Jul–Sep 2024 | 24–32k | 5,2–5,6 | breites PMax/Shopping-Setup |
| **Effizienz-Programm** | Okt 2024 | 25k | **8,0** | Budgets −40–60 % + tROAS rauf → Sprung |
| Effizienz-Plateau | Nov 24 – Okt 25 | 16–33k | 9–14 | diszipliniert; Bestwerte Aug/Sep 25 (12,8/14,2) |
| **BFCM 2025** | Nov 2025 | 34k | **19,4** | herausragend, auch bereinigt **+62 % YoY** |
| **Skalierung** | Jan–Jun 2026 | 21k → **62k** | 11,6 → **5,0** | Spend ×3, Clean-ROAS fällt 6 Monate in Folge |

YoY-Anker: H2 25 vs. H2 24 = Spend flach, Clean-Value **+66 %** (echte Verbesserung).
H1 26 vs. H1 25 = Spend +92 %, Clean-ROAS **−23 %**; marginaler ROAS des Zusatz-Spends
~5,3 übers Halbjahr — im Juni kippt er auf **0,63** (§3).

## 2. Leitplanken-Kandidaten (berechnet, NOCH NICHT approved — Martins Entscheid offen)

1. **Anker, kein Ziel:** Konto-Clean-ROAS 6,16 (90 T z. 03.07.26); **Brand 54,95 / Non-Brand 2,40** — nie mischen (ROAS-CV der aktiven Kampagnen 1,17).
2. **Top-Performer-Schutz:** Clean-ROAS ≥ 7,7 (1,25× Konto-Ø) + ≥3 Käufe = nicht anfassen → trifft aktuell die 4 Brand-Kampagnen.
3. **Budget-Erhöhung nur bei echtem Budget-Limit:** Lost-IS-Budget ≥ ~20 %; bei < 5 % Stopp/Rückbau. PMax ohne Lost-IS → Proxy: marginaler Clean-ROAS der letzten Stufe < 0,8× Kampagnen-Ø = zurückstufen. (Beleg: FOKUSPRODUKTE trug Feb–Apr bei 52–67 % Lost-IS-Budget; Juni bei 0–1 % → marginal 0,63.)
4. **Budget-Schritte max ±30 %, ≥7 T Ruhe — NUR außerhalb dokumentierter Promo-Fenster** (Review Jonas 10.07.26: in Sales ist Intraday Scaling bewusste Taktik). Ohne Promo-Fenster gerechnet: 78 % der 95 Schritte > ±30 %, 28 % < 7 T; die Hälfte aller Budget-Schritte der 2 Jahre lag in Promo-Fenstern. Schrittgrößen-Kern hält auch ohne Promos: Erhöhungen > +90 % = 0/6 positiv.
5. **tROAS-Ziel-Ruhe ≥ 14 T** — die einzigen zwei hoch-Confidence-Erfolge hatten ≥14 T Ruhe; Ziel-Thrash (OVER-INDEX 5× in 6 Mon) ist unbewertbar + destabilisierend.
6. **Keyword-/Asset-Auto-Apply aus** (Trefferquote ~38 %, n=8, ausschließlich in Brand-Kampagnen; 21.11.24 wurde `[stay cold]` Exact aus DE-Brand entfernt = NEGATIV).
7. **Zero-Conversion-Alarm:** > 1.000 € kumuliert ohne Kauf → Review (Beleg: „Video View DRAFT" 4.750 € / 2 Käufe / 4 Wochen unbemerkt).
8. **Brand-IS 95–99 %** ausbauen — Lücke (83–93 %, v.a. USA 82,8 %) ist **Rank-**, nicht Budget-bedingt → Gebot/QS, kein Budget nötig. Billigster Hebel im Konto.
9. **Promo-Kalender ist Pflicht-Infrastruktur** (`data/.../promo_windows.csv`, Seed 10.07.26 mit BFCM 24/25 + Black Spring 26 — von Jonas verifizieren/ergänzen lassen). Innerhalb der Fenster: Intraday Scaling erlaubt, Einzel-Verdikte nicht belastbar, Bewertung nur als Paket (Promo vs. Vorjahres-Promo, bereinigt). Die frühere „BFCM-Ausnahmepaket"-Regel ist damit ersetzt (W4 gestrichen, Review Jonas).

## 3. Schlüssel-Ereignisse / Experimente-Log

| Wann | Was | Ausgang |
|---|---|---|
| 04.–09.10.2024 | Effizienz-Programm: tROAS OVER-INDEX 360→560 %, Budgets runter | **POSITIV, Conf. hoch** — Clean-ROAS 5,45→8,01→11,93, hielt bis Frühjahr 25 |
| 21.11.2024 | Auto-Apply entfernt `[stay cold]` Exact aus DE-Brand | NEGATIV — Anlass für Leitplanke 6 |
| Nov 2025 | BFCM-Paket (>100 parallele Changes) | Ergebnis top (+62 % YoY bereinigt); Einzel-Attribution unmöglich = korrekt UNKLAR |
| 10.11.25–13.03.26 | Conv-Setup-Kette → Regime 3 (§0) | MANUELL — strategisch, nicht attribuierbar |
| Jan–Jun 2026 | Skalierung 21k→62k | Sättigung überschritten: FOKUSPRODUKTE Juni marginal **0,63**, Lost-IS-Budget 0 % |
| Mär/Apr 2026 | BS DEALS Pause/Aktiv-Thrash (9 Statuswechsel/6 Wo) | Verdikte volatil; Demand-Gen-Lernphasen-Resets teuer |
| 27.04.–24.05.2026 | „Video View DRAFT" versehentlich live | 4.750 € / 2 Käufe (ROAS 0,04) — Prozess-Lücke Alarm |
| 30.06.2026 | Budget-Cut FOKUSPRODUKTE 1.600→551 € | richtig (Sättigungs-Beleg) |
| 03.07.2026 | Jonas pausiert Bidding-Auto-Apply | vermutlich richtig, MANUELL |

## 4. Kampagnen-Langzeitprofil (Clean-ROAS)

**Rückgrat:** 4 Brand-Search-Kampagnen ≈ 7 % Spend, ~64 % des getrackten Kauf-Werts
(90 T): FRA 64,2 · DE 63,0 · USA 58,0 · SKANDI 24,2 — alle Top-Performer-Schutz.
**Größter Spender:** EX I SHOPPING I FOKUSPRODUKTE (H1 26: 97k = 39 % Konto-Spend,
Clean-ROAS 2,32, sättigungslimitiert). **Non-Brand gesamt Clean-ROAS 2,40** (90 T) —
ob das profitabel ist, entscheidet die DB1-Marge, nicht das Konto.
Vollregister (12 von 35 Kampagnen, mit Clean-ROAS je Kampagne): `history_facts.md` §4.

## 5. Was die Historie NICHT hergibt (ehrlich)

- **Marge/Retouren fehlen** → Break-even-/Ziel-ROAS wäre erfunden. Wichtigste offene
  Zahl; erst DB1-Input von Stay Cold, dann POAS-Logik statt Brutto-ROAS.
- **PMax-Innenleben:** keine Suchbegriffe, kein Lost-IS — Asset-Gruppen-Tiefenanalyse
  steht aus (Daten liegen: `perf_assetgroup_daily_*.csv`).
- **BFCM-Muster n=2** mit zwei verschiedenen Zähl-Regimen → keine Saison-Schwellen.
- **Client-Eingriffe** Median-DiD −22 %, aber n=13 — Tendenz, kein Urteil.
- **Änderungs-Historie vor Jul 2024** existiert nicht; Forward-Capture (VPS-Cron,
  `data/staycold/change_log.csv`) schließt die Lücke ab Aktivierung.

## Quellen & Refresh
`reports/impact_staycold.md` (467 Cluster) · `reports/threshold-kandidaten_staycold.md`
· `learnings.md` · `data/stay cold apparal/history_facts.md` (generiert).
Refresh: `python system-prompts/agents/change-impact-agent/build_history_context.py
--indir "system-prompts/agents/change-impact-agent/data/stay cold apparal"
--customer staycold --account-type ecom
--purchase-only-csv "system-prompts/agents/change-impact-agent/data/stay cold apparal/perf_campaign_daily_purchaseonly.csv"`
