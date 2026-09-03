---
kunde: kollabo
typ: schwellenwert-kandidaten (verfeinert mit 2024-Daten)
quelle: impact_2024.md + impact_2025.md + Brain-Abgleich
scope: KUNDEN-SCOPED · Kandidaten, NICHT freigegeben — bleiben Kandidaten bis Martins Approve
stand: 2026-07-02
---

# Kollabo — Schwellenwert-Kandidaten (2024 + 2025 zusammengeführt)

> ⚠️ **Provisorisch, aber jetzt auf 2 Jahren.** 2024 (36 Cluster) + 2025 (113 Cluster), 1 Account.
> Schärft die Kandidaten aus `threshold-kandidaten_2025.md` mit **berechneten Zahlen**.
> Weiterhin dünn (v. a. UMLAND-lastig, viele Mini-Spend-Pausen) → Hypothesen, keine Gesetze.

## A. Verfeinerte Schwellenwert-Kandidaten

| # | Schwelle | 2025-Stand | **2024-Verfeinerung (berechnet)** | Status | Conf. |
|---|---|---|---|---|---|
| 1 | **Top-Performer-Schutz-CPA** | ≤ 15,6 CHF (0,8× Ø 19,54) | **Jahres-spezifisch:** 2024 Ø-CPA **13,86** → Deckel **≤ 11,09 CHF** UND ≥3 Conv. Der Anker ist **nicht konstant** — jährlich neu aus Konto-Ø rechnen, nicht 15,6 fixieren. | Verfeinerung | hoch |
| 2 | **Pause-Schwelle** | Pausieren nur bei Pre-CPA ≥ ~1,5× Ø; bei ≤0,8× nie | 2024 stützt schwach (nur Keyword-Pausen, keine Voll-Kampagnen-Pausen): teure Elemente pausiert = POS (Automatikmonteur ~2,2× Ø), effiziente Broad-Sammelpause = NEG. **Schwelle ~1,5× bleibt plausibel**, 2024 liefert keinen Gegenbeleg. | Verfeinerung | mittel |
| 3 | **Portfolio-Bidding-Gate (CPA-CV)** | Nur bündeln, wenn CV ≤ ~30% | **Berechnet 2024: Konto-CPA-CV = 51,6 %** (19 Kampagnen, CPA-Spanne 5,7…42,3, Mean 19,45, SD 10,03). Weit über 30 % → **Bündelung wäre klar kontraindiziert.** Deckt sich mit dem 2025-Portfolio-Schaden (7/8 NEG). Gate **≤ 30 %** bestätigt (Kollabo liegt strukturell weit darüber). | **NEU → gestützt** | mittel-hoch |
| 4 | **Budget-Sättigungs-Stopp (UMLAND)** | +20%-Schritt treibt DiD-CPA > +10% → zurück | **Berechneter CHF-Deckel: UMLAND ≈ 85 CHF/Tag (~2.600 CHF/Mon).** Leiter 2024: 35→50 −17% (ok), 50→101 **+21%**, 120→185 **+34%**, 185→86 −13% (Erholung). **Über ~100 CHF/Tag reproduzierbar negativ** — auf **2 Jahren** bestätigt. | **NEU → gestützt** | mittel-hoch |
| 4b | **Lost-IS-Vorbedingung für Budget-Up** | (implizit) | **NEU:** Budget-Erhöhung nur wenn **Budget-Lost-IS** dominiert — und selbst dann Vorsicht: 2024 stiegen CPAs trotz hohem Budget-Lost-IS (Grenz-Traffic unrentabel). Bei **Rank-Lost-IS-Dominanz** Erhöhung **unterlassen** (kauft teuren Auktionsdruck). | **NEU** | mittel |
| 5 | **Auto-Apply-Trefferquote** | 2025 ~45% (5:6) → nicht blind | 2024: 2 POS / 1 NEU / 3 UNK (n=6), **nur Keyword-Removals**. Über beide Jahre: **kuratieren, nicht blind an**. Nach Empfehlungsart trennen — Keyword-Removal (Phrase/Exact) eher ok, Broad riskanter. | Verfeinerung | mittel |
| 6 | **Attribution-Wechsel-Marker** | jede Conv-Basis-/Fenster-Änderung = Pivot | 2024 **zweiter Beleg:** 16.10.2024 Standardzielvorhaben-Wechsel (Qualified/Converted leads) = Pivot; über den Bruch nur DiD. Prozess bestätigt (auch ohne 30→60-T-Fensterwechsel gilt Pivot). | Verfeinerung | hoch |

## B. Erledigte offene Rechnungen aus threshold-kandidaten_2025.md
- ✅ **Portfolio-CV #3** konkret gerechnet → **51,6 %** (2024).
- ✅ **UMLAND-CHF-Deckel #4** → **~85 CHF/Tag**, Bruchzone ~100 CHF/Tag.
- ✅ **Saison/YoY** → 2023-Vergleich **möglich** und gezogen (2025-Annahme „erst ab Jul 2024" war falsch).
  Regime-Bruch liegt Mid-2023, nicht Mid-2024 → YoY ab Jul 2023 sauber.

## C. Noch offen / für 2. Kunde
- **Portfolio-Bidding direkt**: 2024 gab es keine Portfolio-Migration → CV nur als struktureller Proxy
  gerechnet, nicht am Portfolio-Effekt selbst (das liefert nur 2025). Generalisierung braucht 2. Kunde.
- **Voll-Kampagnen-Pause-Schwelle (#2)**: 2024 nur Keyword-Pausen → 1,5×-Schwelle weiter aus 2025 getragen.
- **Lead-Qualität ≠ CPA (f)**: Wert/Lead + Close-Rate weiter undokumentiert; Brand/Closed-Won sind andere
  Conv-Populationen — CPA misst die halbe Wahrheit. Separat mit Kollabo zu klären.

## D. Nach Approve
- **#1 (jährlicher Ø-CPA-Anker) / #4 / #4b / #6** → Kollabo-Customer-Overrides (`account-info.md` „Ausnahmen vs. Brain").
- **#3 (CPA-CV-Gate) / #5 (Auto-Apply)** → generische Brain-Kandidaten (brauchen 2. Kunde), PII-frei abstrahiert.
