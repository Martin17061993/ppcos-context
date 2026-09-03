---
kunde: kollabo
typ: learnings-review + schwellenwert-kandidaten
quelle: impact_2025.md + Brain-Abgleich + Obsidian-Vault
scope: KUNDEN-SCOPED · Kandidaten, NICHT freigegeben
stand: 2026-07-02
---

# Kollabo 2025 — Learnings, Lücken & Schwellenwert-Kandidaten

> ⚠️ **Provisorisch.** Basis: 1 Account, 1 Jahr, 113 Cluster (viele NEUTRAL/Konto-Ebene, DiD~0).
> Das sind **Hypothesen zum Validieren** (2024/2023 + 2. Kunde), keine harten Gesetze.
> „NEU" = im Brain gar nicht vorhanden · „Verfeinerung" = bestehende Regel mit Zahl geschärft.

## A. Berechnete Schwellenwert-Kandidaten

| # | Schwelle | Wert (Kollabo 2025) | Basis | Status | Conf. |
|---|---|---|---|---|---|
| 1 | **Top-Performer-Schutz-CPA** | **≤ 15,6 CHF** (0,8 × Konto-Ø 19,54) UND ≥3 Conv | agent_methodik §3, mit echtem Konto-Ø | Verfeinerung | hoch |
| 2 | **Pause-Schwelle** | Pausieren nur bei Pre-CPA **≥ ~1,5× Konto-Ø (≈ 29 CHF)**; bei ≤ 0,8× (≈15,6) **nie** | Jahresend-Pausen: POSITIV bei 1,63×/2,23×/10,7×, NEGATIV bei 0,22–0,67× | **NEU** | mittel |
| 3 | **Portfolio-Bidding-Gate** | Nur bündeln, wenn CPA-**Variationskoeffizient ≤ ~30%** | 8 Gewerke gebündelt (CPA-Spanne ~15…90) → 7/8 NEGATIV | **NEU** | mittel |
| 4 | **Budget-Sättigungs-Stopp** | Wenn +20%-Budgetschritt den **DiD-CPA > +10%** treibt → zurückstufen statt weiter | UMLAND: Erhöhungen DiD +24…+177%, Senkungen negativ (=besser) | **NEU** | mittel |
| 5 | **Auto-Apply-Trefferquote** | 2025 = **~45% positiv (5:6)** → unter „blind übernehmen" | Meta nach Urheber (auto_apply n=14) | Verfeinerung | mittel |
| 6 | **Attribution-Wechsel-Marker** | Jede Conv-Basis-/Fenster-Änderung = KPI-Pivot; danach nur DiD, kein absoluter CPA über den Bruch | 30.10. Closed Won + 30→60T → Conv Okt 433 → Dez 160 | **NEU** (Prozess) | hoch |

**Noch exakt zu rechnen (brauche Roh-CSV-Zugriff bzw. mehr Daten):**
- Portfolio-CV #3 als konkrete Zahl (aus den 8 Kampagnen-CPAs).
- UMLAND-CHF-Deckel #4 (aus den Budget-old→new-Werten).
- Saison-/YoY-Schwellen — **unmöglich ohne 2024** (Pull begann erst 2024-12).

## B. Learnings (belastbar, mittel/hohe Confidence)

1. **Portfolio-Bidding über heterogene Gewerke schadet der CPA-Steuerung** (23.06. → 7/8 negativ, selbst zurückgenommen). Bestätigt Brain implizit, macht aber die **CPA-Homogenität** (nicht nur Conv-Volumen) zur Voraussetzung.
2. **UMLAND skaliert nicht linear** — Budget rauf = CPA rel. schlechter (Sättigung). Deckt sich mit der Obsidian-Stoppregel „7-T-CPA > 18 → Stufe zurück" (Testing-Roadmap).
3. **Blanko-Pausen treffen auch effiziente Kampagnen.** Verletzt sogar die eigene dokumentierte Policy „keine Profession pausieren, nur optimieren".
4. **Meta-Erkenntnis (wichtig):** die **4 größten Spend-Bewegungen** (Portfolio-Topup, User-Entzug, Conv-Setup) sind **Konto-Ebene → nicht attribuierbar**. Die wirkungsvollsten Entscheidungen sind die **am schlechtesten messbaren** → der Agent muss Konto-Ebene-Changes als „manuell bewerten" flaggen statt ein Verdikt zu erzwingen.
5. **Auto-Apply = Münzwurf** → kuratieren, nicht blind an/aus.

## C. Fehlende Erkenntnisse / Dimensionen (aus Brain- + Obsidian-Abgleich)

- **Saison/YoY:** kein Vorjahresvergleich möglich → **2024 + 2023 nachziehen** (Kern-Lücke). Jahresende ≠ Q2.
- **Lead-Qualität ≠ CPA:** „Closed Won" ist eine **andere, bessere Conv-Population** (echte Vermittlung), nicht nur „später". Wert/Lead + Close-Rate sind **undokumentiert** → CPA allein misst die halbe Wahrheit. Separat analysieren.
- **Ad-Group-/Keyword-Ebene fehlt:** Analyse war kampagnen­scharf (Ad-Group-Perf-Pull war abgestürzt). Match-Type-Mix (z.B. Trockenbauer 7/10 Broad = teurer) nicht systematisch geprüft.
- **Auktionsdruck:** Lost IS Budget vs. Rank nicht zur Sättigungs-Diagnose genutzt.
- **Auto-Apply nach Typ:** welche Empfehlungs-Art (Conv-Tracking / Keyword / Budget / Bidding) welche Trefferquote? — nicht aufgeschlüsselt.
- **Test-Debris:** ~290 pausierte Test-Kampagnen ohne Archivierungs-Strategie (Obsidian).
- **Doku-Silo:** die Bidding-/Portfolio-/Pausen-Entscheidungen aus 2025 sind **nicht** im Obsidian-Vault zentralisiert — die `Änderungen Zeitstrahl` beginnt erst 30.06.2026.

## D. Verbindung zur dokumentierten Strategie (Obsidian)

Die 2025-Findings **validieren die eigenen Leitplanken** des 7.5k→15k-Plans (Testing-Roadmap): Gating auf „saubere 7-T-CPA", „keine Profession pausieren", „Auto-Apply aus", gestaffelte Budgets. Wo die Realität abwich (Blanko-Pausen, Budget-Staffelung ohne saubere Daten nach dem Tracking-Bruch, Auto-Apply blieb 7/7 an), ging's schief — genau das zeigt der Impact-Report jetzt mit Zahlen. **Das ist der eigentliche Wert:** die dokumentierten Regeln bekommen empirische Rückendeckung + konkrete Schwellen.

## E. Nächste Schritte
1. **2024 + 2023 nachziehen** → Saison/YoY + größeres n zum Härten der Schwellen #2–#4.
2. Exakte Zahlen rechnen für #3 (Portfolio-CV) und #4 (UMLAND-CHF-Deckel).
3. Nach deinem **Approve**: #1/#2/#6 als Kollabo-Customer-Overrides (`account-info.md` „Ausnahmen vs. Brain"), #3/#4/#5 als generische Brain-Kandidaten (brauchen 2. Kunde).
