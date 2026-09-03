---
kunde: kollabo
customer_id: "1487707588"
mcc: "5591362086"
account_typ: lead_gen
outcome_kpi: CPA (Cost/Conv), sekundär Conv-Volumen + Lead-Qualität
scope: KUNDEN-SCOPED — verlässt diesen Ordner nie, nicht kundenübergreifend nutzen
stand: 2026-07-01
---

# Kollabo — Change-Impact Learnings (kunden-scoped)

Rollierende, verdichtete Verdikte für Kollabo. Roh-CSVs: `../../../data/kollabo/`
(git-ignored). Vollreports: `reports/`.

## Kontext-Flags (beeinflussen jede Bewertung)
- ⚠️ **Tracking defekt seit ~30.06.** (SF „Überprüfung erforderlich", New Lead 0).
  → conv-abhängige Verdikte = `UNKLAR`, bis Fix bestätigt. Analyse mit `--tracking-ok false`.
- Budget zuletzt auf **280 CHF/Tag** (8.5k-Plan) skaliert → viele parallele Changes,
  Confidence bei Attribution entsprechend vorsichtig.
- CPA-Anker: April-Baseline 14,53 · letzter sauberer 7-T-Block (06.–12.06.) 18,32.

## Kategorisierung deiner manuellen Änderungen (Zeitstrahl 30.06.) als Format-Demo

> Zeigt, wie der Agent **kategorisiert** und wann er bewertet — abgeglichen mit deiner
> eigenen „Conv-abhängig?"-Spalte. Echte Verdikte kommen aus dem Live-Pull.

| # | Änderung (30.06.) | Typ | Messbar via | Conv-abh.? | Verdikt-Pfad jetzt (Tracking defekt) |
|---|---|---|---|---|---|
| 1 | Batch exakt-Negatives (NKL_Generisch + Grundbauer) | NEG | Suchbegriff-Relevanz, Klicks, CTR | Nein | **bewertbar** → CTR/CPC-Delta |
| 2 | Auto-Apply umgestellt; „Maximize conversion value" NEU | SET | Einstellung (kein Perf-Delta direkt) | Ja | **UNKLAR** + ⚠️ „Max conv value" muss AUS sein → verifizieren |
| 3 | Negative „gipser" (Phrase), Trockenbauer | NEG | Relevanz sofort; Conv-Rate später | teils | **teil-bewertbar** → Relevanz/CTR jetzt, Conv-Rate nach Fix |
| 4 | Weitere Cross-Trade-Negatives (mehrere Kampagnen) | NEG | Suchbegriff-Relevanz, CTR/CPC | Nein | **bewertbar** → CTR/CPC-Delta |
| 5 | RSA-Headlines Trockenbauer (QS 3/10 bei 16% CTR) | AD | Qualitätsfaktor, CTR, CPC | Nein | **bewertbar** → CTR/QS/CPC-Delta |
| 6 | tCPA-Experiment UMLAND (geplant, NICHT gestartet) | TEST/BID | Conv + CPA beider Arme | Ja | **UNKLAR** (nicht gestartet) → erst nach Start + Fix |

**Muster-Kandidaten (noch NICHT fürs Brain — erst nach Live-Daten + Approve):**
- (offen) Cross-Trade-Negatives → Effekt auf Relevanz/CTR quantifizieren.
- (offen) Wirkt Googles Auto-Apply („Maximize conversion value") bei Kollabo netto negativ?

## Verifikations-Notiz
Sobald der Live-Report vorliegt: Verdikte gegen diesen Zeitstrahl + bekannte
Account-Historie prüfen (Konzept §8). Wo Verdikt ≠ deine Einschätzung → Grund
dokumentieren (zu wenig Daten / parallele Changes / Saison).

---

# 2025 (historisch) — validierte Muster aus UI-Export + API-Performance

Quelle: `reports/impact_2025.md` (159 Änderungen → 113 Cluster, 2025-01-15 … 2025-12-29).
**Tracking 2025 war valide** (anders als 2026-Live-Pull) → CPA belastbar, DiD-normiert.
Konto-Ø-CPA 2025 = **19,54 CHF**. Stand: 2026-07-02.

## Belastbare Muster (mittel/hohe Confidence)
1. **Portfolio-Bidding über heterogene Gewerke schadet der CPA-Steuerung.**
   23.06.2025 wurden 8 Kampagnen in eine gemeinsame Portfolio-Strategie („Portfolio Test JM“)
   gelegt → **7/8 NEGATIV** (Automatiker DiD +25 %, Schweisser +188 %, Polymechaniker/Montage +12–13 %).
   Am 05.–06.08. wieder auf Einzelbudgets zurückgenommen → mehrere POSITIV (Schweisser DiD −68 %).
   **Anwendung:** Portfolio-Gebotsstrategien pro Gewerk/CPA-Klasse getrennt halten, nicht quer bündeln.
2. **UMLAND TEST skaliert nicht linear — Budget rauf = CPA rel. schlechter, runter = besser.**
   Erhöhungen 22./25.04. (DiD +36/+24 %) und 18.12. (+177 %) negativ; Senkungen (Jan −28 %, Sep −15 %,
   Nov −127 %) positiv/neutral. **Anwendung:** UMLAND als Effizienz-, nicht Volumen-Hebel; Erhöhung nur
   mit CPC≤RPU-Check (kpis_metrics §2.3).
3. **Blanko-Pausen schalten effizientes Volumen mit ab.**
   Jahresend-Pause 29.12. + 22.10.: teure Kampagnen zu pausieren war POSITIV (Automatiker x1,63,
   Brand x2,23), effiziente NEGATIV (Schweisser x0,67, Polymechaniker x0,22, UMLAND x0,33/x0,63).
   **Anwendung:** Pausen kampagnenscharf am Pre-CPA-vs-Konto-Ø ausrichten (Top-Performer-Schutz §3).

## Typ- & Urheber-Signale (Trend, nicht hart)
- **Auto-Apply (Google-Empfehlungen)** = Münzwurf (5 POS / 6 NEG) → kein Blind-Vertrauen, kuratieren.
- **system_bulk „Low activity“-Keyword-Pausen** netto leicht negativ, aber Mini-Volumen.
- **Manager** machte die meisten Changes inkl. Portfolio-Experiment (selbst zurückgenommen);
  **Client**-Eingriffe (Pausen) überwiegend sinnvoll, kleines n.

## Nicht kausal bewertbar (ehrlich)
- Die 4 grössten Spend-Posten sind **Konto-Ebene** (Portfolio-Budget-Topup, User-Entzug,
  Conv-Setup 30.10.) → gegen Konto-Trend nicht isolierbar → NEUTRAL/niedrig.
- **Conv-Basis-Wechsel 30.10.2025** (SF „Closed Won“ primär, Fenster 30→60 T) verzerrt absolute
  CPAs ab Nov; nur DiD lesbar. Kein YoY (Pull erst ab 2024-12).

## Brand-Kandidaten (erst nach Approve, PII-frei abstrahieren)
- (offen) „Portfolio-/Smart-Bidding-Konsolidierung über heterogene Lead-Gen-Gewerke → CPA-Verschlechterung“
  als generische Heuristik? Braucht 2. Kunde zur Bestätigung.
- (offen) „Umland-/Broad-Geo-Testkampagnen sättigen früh — Budget-Erhöhung erhöht CPA überproportional.“

---

# 2024 (historisch, Jul–Dez) — validierte Muster aus UI-Export + API-Performance

Quelle: `reports/impact_2024.md` (87 Änderungen → 36 Cluster, 2024-07-04 … 2024-12-31).
**Tracking 2024 war valide** → CPA belastbar; **erstmals echtes YoY gegen 2023** (siehe unten).
Konto-Ø-CPA Jul–Dez 2024 = **13,86 CHF** (Top-Performer-Deckel 0,8× = **11,09 CHF**). Stand: 2026-07-02.

## Belastbare Muster (bestätigt / neu)
1. **UMLAND-Sättigung auf ZWEI Jahren bestätigt.** 2024-Budget-Leiter: 35→50 CHF/Tag DiD −17 % (POS),
   50→101 +21 % (NEG), 120→185 +34 % (NEG), Rückstufung 185→86 −13 % (POS). Effizienz-Deckel
   **≈ 85 CHF/Tag (~2.600 CHF/Mon)**. Identisch zum 2025-Muster. **Anwendung:** UMLAND als Effizienz-,
   nicht Volumen-Hebel; Erhöhung nur bei **Budget-Lost-IS-Dominanz** + CPC ≤ RPU, nie über ~85 CHF/Tag.
2. **Lost-IS-Nuance zur Sättigung (neu).** Die Aug-Erhöhungen liefen bei **hohem Budget-Lost-IS**
   (echte Knappheit) und wurden **trotzdem** teurer → Budget-Headroom allein ist **kein** Freibrief.
   Grenz-Traffic war unrentabel. Senkungen/Rücknahmen liefen bei **Rank-Lost-IS-Dominanz**.
3. **Simultane Sammel-Budgeterhöhungen sind teuer.** 15.08. wurden 4 Kampagnen gleichzeitig hochgesetzt
   → Schweisser +29 %, SOLAR +23 % (beide NEG, beide Rank-Lost-IS-dominiert), Schweisser-Rücknahme
   05.09. −38 % (POS). **Anwendung:** kein Batch-Push; Erhöhung selektiv wo Budget-Lost-IS dominiert.
4. **Broad-lastige Massen-Keyword-Eingriffe sind das Risiko (Match-Type).** Einzelne Exact/Phrase-Pausen
   auf teuren Keywords nützten (Elektroinstallateur DiD −69 %, Metallbauer −39 %); die grosse
   Broad+Exact-Sammelpause 25.08. (Zürich-Handwerk) schadete (+168 %, aber Mini-Spend).

## YoY-Erkenntnis (Korrektur der 2025-Annahme)
- **Das Konto trackt NICHT erst ab Jul 2024** — Conversions laufen bis 2023-01 zurück. 2023 H1 ist eine
  **andere Conv-Population** (Micro-/Alt-Zielvorhaben, CPA ~5), ab ~Jul 2023 die heutige Lead-Basis.
  → YoY **Jul–Dez 2024 vs. 2023 ist sauber** (beide im gleichen Regime).
- **Ergebnis:** H2-2024 hielt CPA im 13–17-CHF-Band; **Q4 2024 YoY 24–35 % günstiger** als Q4 2023.
  Aug/Sep 2024 wirken YoY teurer, aber nur gegen anomal billige 2023-Basis (Basis-Effekt).

## Typ- & Urheber-Signale
- **Auto-Apply 2024 = nur Keyword-Removals**, netto harmlos/leicht positiv (2 POS / 1 NEU / 3 UNK, n=6).
  Kein Münzwurf wie 2025 — aber n zu klein; 2025 (mit Budget/Bidding-Empfehlungen) bleibt der schärfere Punkt.
  **Unverändert: kuratieren.**
- **system_bulk „Low activity"-Pausen** überwiegend POS/harmlos, Ausnahme Broad-Sammelpausen.
- **Brand Manueller-CPC → Conversions-maximieren (04.07.)** kurzfristig NEG (DiD +25 %, Lernphase);
  Brand ist mit 5,67 CHF Jahres-CPA bester Performer — Umstellung methodisch ok, kurzfristig teuer.

## Nicht kausal / MANUELL (ehrlich)
- Kunden-Asset-Erstellung 04.07. = Konto-Ebene → MANUELL.
- Zielvorhaben-Wechsel **16.10.2024** = KPI-Pivot (Qualified/Converted leads dazu) → über den Bruch nur DiD.
  Milder als der 30.10.2025-Bruch (kein 30→60-T-Fensterwechsel) — Konto-CPA bricht nicht ein.
- Dachdecker „Maximale Conversions" 2024 inaktiv (kein Spend) → UNKLAR, nicht auf Konto hochgerechnet.
