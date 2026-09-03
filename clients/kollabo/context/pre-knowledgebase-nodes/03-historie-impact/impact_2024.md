---
kunde: kollabo
customer_id: "1487707588"
zeitraum: 2024-07-04 .. 2024-12-31 (Changes) · Performance-Fenster 2024-06-01 .. 2025-01-31 · YoY-Referenz 2023-07 .. 2024-01
quelle_changes: Cowork UI-Export (changes_kollabo_2024_normalized.csv, 87 Änderungen)
quelle_perf: Google Ads API, täglich, Kampagnen- + Ad-Group-Ebene inkl. Lost-IS (Budget/Rank)
outcome_kpi: CPA (Cost/Conv), DiD-normiert vs. Konto-Trend; YoY gegen 2023-Kalenderfenster
tracking_status: 2024 VALIDE (Conv-Tracking lief durchgängig) — Caveat: Zielvorhaben-Wechsel 16.10.2024
scope: KUNDEN-SCOPED — verlässt diesen Ordner nie, nicht kundenübergreifend nutzen (Roh-CSV enthält PII)
stand: 2026-07-02
---

# Kollabo — Change-Impact-Report 2024 (historisch, UI-Export)

> Analyse der Cowork-UI-Änderungshistorie **Jul–Dez 2024** gegen tatsächlich gezogene 2024-API-Performance,
> **inkl. echtem YoY gegen 2023** (Kern-Lücke des 2025-Reports geschlossen — siehe Caveat 5).
> **Attribution, keine Kausalität.** Bei vielen parallelen Changes / Saison bewusst niedrige Confidence.
> Roh-Verdikte: `../../../data/kollabo/change_impact_2024.csv` (git-ignored).

## Zusammenfassung

- **87 Änderungen** (2024-07-04 … 2024-12-31) → **36 bewertete Cluster** (Datum × Kampagne × Kategorie).
- Verdikte: **POSITIV 11 · NEGATIV 7 · NEUTRAL 6 · MANUELL 1 · UNKLAR 11**.
- **Konto-Ø-CPA Jul–Dez 2024: 13,86 CHF** → Top-Performer-Schutz (agent_methodik §3): **CPA ≤ 11,09 CHF UND ≥3 Conv**.
  (Der Wert 15,6 CHF aus dem 2025-Report ist der **2025-**Anker — 2024 lag das Konto effizienter.)
- Monatsverlauf Konto-CPA: Jul 13,0 · Aug 14,5 · Sep 12,2 · Okt 14,0 · Nov 13,7 · **Dez 17,1** — **stabil** (kein Jahresend-Kollaps wie 2025, weil 2024 kein 30→60-T-Conv-Fenster-Wechsel).
- **Der Account-Schwerpunkt ist dieselbe Kampagne wie 2025: `UMLAND TEST`** (16 der 36 Cluster, mit Abstand grösster Spend-at-Risk). Das UMLAND-Sättigungsmuster **wiederholt sich 2024** — damit auf **zwei Jahren** belegt.

## Wichtigste Caveats (ehrlich)

1. **Datenbasis dünn & einseitig verteilt.** Nur 87 Changes, davon **46 „Low activity"-System-Bulk-Keyword-Pausen** (Mini-Spend) und **6 Auto-Apply-Keyword-Removals**. Die materiell relevanten Manager-Changes sind ~20 Cluster — vieles davon UMLAND. Long-Tail-Cluster < 150 CHF Spend sind CPA-Artefakt-anfällig (z. B. +168 %/+440 % DiD auf ~100 CHF) → als niedrige Materialität lesen, nicht als Effekt.
2. **Zielvorhaben-Wechsel 16.10.2024 = KPI-Pivot.** An diesem Tag wurden die **Standardzielvorhaben des Kontos** geändert („Qualified leads (Website)" + „Converted leads (Website)" hinzugefügt, Konto-Standard nicht mehr verwendet). Für Cluster, deren 28-T-Fenster über den 16.10. läuft, ist der **absolute** CPA-Delta verzerrt → nur **DiD** lesbar; diese Zeilen sind markiert und in der Confidence gedeckelt. (Anders als der 30.10.2025-Bruch war es **kein** Fenster-Wechsel 30→60 T, daher milder — der Konto-CPA-Verlauf bricht nicht ein.)
3. **UI-Daten gröber als API.** Nur ~36 % der Änderungen (31/87) mit geparstem alt→neu. `category` ist Heuristik und lag oft daneben: „Low activity Keyword pausiert **jobangebote**…" wurde durch den Teilstring **„gebot"** fälschlich als **BID** klassifiziert. **Korrigiert** — hier gilt `description_full` als Ground Truth; die BID-Zeilen sind zu **STRUKT** (Keyword-Pausen) rekategorisiert.
4. **Bidding-Umstellung mitten im Zeitraum.** Am 04.07. wurde die Brand-Kampagne von **Manueller CPC → Conversions maximieren** umgestellt und UMLAND als „Conversions maximieren" neu erstellt — Smart-Bidding-Lernphasen überlagern die frühen Juli/August-Fenster.
5. **YoY ist möglich — Korrektur der 2025-Annahme.** Der 2025-Report nahm an, das Konto tracke „erst ab Jul 2024". Der API-Pull zeigt: **Conversions laufen bis 2023-01 zurück.** 2023 H1 war eine **andere Conv-Population** (Micro-/Alt-Zielvorhaben, ~2.000–3.500 Conv/Mon @ CPA ~5) — **nicht** vergleichbar. Ab **~Jul 2023** ist die Basis die heutige Lead-Registrierung (CPA 10–23, Conv 200–340/Mon). Das YoY-Fenster **Jul–Dez 2024 vs. Jul–Dez 2023 liegt komplett in der vergleichbaren Regime** → sauber nutzbar, mit ~1,5 Jahren Historie aber weiterhin dünn.

## YoY: Konto-CPA Jul–Dez 2024 vs. 2023

| Monat | CPA 2024 | CPA 2023 | YoY |
|---|---|---|---|
| Jul | 13,00 | 14,12 | **−8 %** |
| Aug | 14,52 | 10,10 | +44 % |
| Sep | 12,24 | 7,56 | +62 % |
| Okt | 13,95 | 13,71 | +2 % |
| Nov | 13,70 | 21,10 | **−35 %** |
| Dez | 17,11 | 22,65 | **−24 %** |

**Lesart:** Aug/Sep 2024 wirken YoY „teurer", aber gegen eine **anomal billige** 2023-Basis (Aug/Sep 2023 CPA 8–10 direkt nach dem Mid-2023-Umbau) — Basis-Effekt, kein Effizienzverlust. **Q4 2024 (Nov/Dez) war YoY 24–35 % günstiger** als das teure Q4 2023. Netto hielt das Konto H2-2024 seinen CPA im 13–17-CHF-Band, robuster als H2-2023. Die per-Zeile-YoY-Spalte in der Verdikt-Tabelle ist **Konto-Kontext** (die meisten Kampagnen — EX|25, UMLAND — existierten 2023 noch nicht, kampagnen-scharfes YoY daher n/a).

## Meta-Analyse: welcher Änderungs-TYP wirkt netto?

| Typ | POSITIV | NEGATIV | NEUTRAL | UNKLAR | Netto-Lesart |
|---|---|---|---|---|---|
| BUD | 3 | 4 | 4 | 1 | Richtungs­abhängig — **Erhöhungen überwiegend NEGATIV** (UMLAND +21/+34 %, Schweisser +29 %, SOLAR +23 %), **Senkungen POSITIV/NEUTRAL** (Schweisser −38 %, UMLAND −13 %). Gleiches Muster wie 2025. |
| STRUKT | 7 | 1 | 2 | 5 | Keyword-Pausen/-Removals überwiegend POSITIV, aber viele UNKLAR (Mini-Volumen). Der eine NEGATIV: die grosse **Zürich-Handwerk-Broad+Exact-Bulk-Pause** 25.08. |
| BID | 0 | 1 | 0 | 1 | Brand-Gebotsstrategie-Umstellung 04.07. NEGATIV (DiD +25 %); UMLAND-tCPA-Setup UNKLAR (Testphase). |
| NEG | 0 | 0 | 0 | 1 | nur 1 echter Negativ-Cluster (16.10. UMLAND-Relaunch) → UNKLAR. |
| AD | 0 | 1 | 0 | 2 | zu dünn; 2× Dachdecker ohne Perf-Daten (inaktiv). |
| SET | 1 | 0 | 0 | 1 | UMLAND-Test-Aufsatz 16.10. POSITIV (aber Pivot-Fenster). |
| MANUELL | — | — | — | — | 1 Konto-Ebene (Kunden-Asset 04.07.) — nicht attribuierbar. |

## Meta-Analyse: Urheber (user_type)

| user_type | POS | NEG | NEU | MAN | UNK | n | Lesart |
|---|---|---|---|---|---|---|---|
| manager | 5 | 5 | 4 | 1 | 5 | 20 | Alle materiellen Changes (UMLAND-Budgets, Batch-Erhöhung 15.08., Brand-Bidding). Netto ausgeglichen — getrieben von den UMLAND-Budget-Erhöhungen (NEGATIV) vs. -Senkungen (POSITIV). |
| system_bulk | 4 | 2 | 1 | 0 | 3 | 10 | Googles „Low activity"-Keyword-Pausen. Überwiegend POSITIV/harmlos, **aber** die grosse 25.08.-Broad+Exact-Pause auf Zürich-Handwerk war NEGATIV. |
| auto_apply | 2 | 0 | 1 | 0 | 3 | 6 | **Nur Keyword-Removals** (Metallbauer/UMLAND). Netto leicht positiv, viel UNKLAR (Mini-Volumen). **Kein Münzwurf wie 2025** — aber n zu klein für ein Urteil. |

## Auto-Apply nach Typ (Kritikpunkt e)

2024 hat Auto-Apply **ausschliesslich Keyword-Removals** ausgelöst (keine Budget-/Bidding-/Conversion-Empfehlungen):

| Empfehlungs-Art | n | Verdikte | Materialität |
|---|---|---|---|
| Keyword-Removal (STRUKT) | 6 | 2 POSITIV · 1 NEUTRAL · 3 UNKLAR | 4 von 6 < 100 CHF Spend; nur 2 (UMLAND-Phrase 07.06.→? und 03.12. broad) materiell. Broad-Removal 03.12. NEUTRAL, Phrase-Removals eher POSITIV. |

→ **2024 ist Auto-Apply harmlos-bis-nützlich**, aber die Stichprobe deckt nur eine Empfehlungsart ab. Die 2025-Beobachtung „Auto-Apply = Münzwurf" (5:6, dort auch Budget/Bidding dabei) bleibt der schärfere Datenpunkt. **Empfehlung unverändert: kuratieren statt blind an.**

## Die belastbarsten Muster (Spend-relevant)

### 1. UMLAND TEST — Sättigung bestätigt (2. Jahr): Budget rauf verschlechtert, runter verbessert
Grösste Einzelkampagne (bis ~5.200 CHF Spend-at-Risk/Fenster). Die **Budget-Leiter 2024** ist eindeutig:

| Datum | Op | alt→neu CHF/Tag | DiD-CPA | Verdikt |
|---|---|---|---|---|
| 04.07. | increase | 35 → 50 | **−17 %** | POSITIV |
| 01.08. | increase | 50 → 101 | **+21 %** | NEGATIV |
| 15.08. | increase | 101 → 120 | +0 % | NEUTRAL |
| 19.09. | increase | 120 → 185 | **+34 %** | NEGATIV |
| 15.10. | decrease | 185 → 86 | **−13 %** | POSITIV |
| 19.12. | decrease | 86 → 66 | −9 % | NEUTRAL |

**Learning:** UMLAND skaliert sauber bis **~50 CHF/Tag**; **jeder Schritt über ~100 CHF/Tag** trieb den DiD-CPA material nach oben, und **Zurückstufen von 185 → 86 holte die Effizienz zurück**. Effizienz-Deckel ≈ **85 CHF/Tag (~2.600 CHF/Mon)**. Deckt sich 1:1 mit dem 2025-Muster (Erhöhungen +24…+177 %, Senkungen negativ).

**Sättigungs-Diagnose via Lost-IS (Kritikpunkt c) — Nuance:** Die Budget-Erhöhungen im August liefen bei **hohem Budget-Lost-IS** (echte Budgetknappheit, „Headroom"), **trotzdem** stieg der CPA — d. h. die Nachfrage war da, aber der **Grenz-Traffic war teurer** (nicht profitabel zum Ziel-CPA). Die Senkungen und die Juli-Erhöhung liefen bei **Rank-Lost-IS-Dominanz** — hier kauft mehr Budget v. a. teureren Auktionsdruck. **Regel geschärft:** Budget-Lost-IS-Headroom allein rechtfertigt keine UMLAND-Erhöhung; erst mit CPC ≤ RPU-Check (kpis_metrics §2.3) und nur bis ~85 CHF/Tag.

### 2. Die Sammel-Budgeterhöhung vom 15.08. war netto teuer
Am 15.08. wurden **vier** Kampagnen gleichzeitig hochgesetzt (UMLAND, Schweisser, SOLAR, GERÜSTBAUER). Ergebnis: **Schweisser +29 % (NEG), SOLAR +23 % (NEG)**, UMLAND/GERÜSTBAUER neutral. Alle vier zeigten **Rank-Lost-IS-Dominanz** vor der Erhöhung → mehr Budget kaufte teureren Traffic. Schweisser wurde 05.09. wieder gesenkt → **−38 % (POSITIV)**. **Learning:** breite Simultan-Erhöhungen ohne CPC-≤-RPU-Gate verschlechtern den Konto-CPA; Erhöhung nur wo **Budget-Lost-IS** (nicht Rank-Lost-IS) dominiert.

### 3. Brand von Manuellem CPC auf „Conversions maximieren" (04.07.) → kurzfristig NEGATIV
Die Umstellung der Brand-Kampagne auf Smart Bidding zeigte im 28-T-Fenster DiD **+25 %**. Typische Lernphasen-Delle; Brand hatte 2024 einen Jahres-CPA von nur **5,67 CHF** (bester Performer) — die Umstellung selbst war methodisch vertretbar, aber der kurzfristige Impact war negativ. **Caveat Lead-Qualität (f):** Brand-Conversions sind eine andere Population (Marken-Sucher, tief im Funnel) — CPA-Vergleich hier nur begrenzt aussagekräftig.

### 4. System-Bulk-Keyword-Pausen: harmlos, ausser bei Broad-lastigen Sammel-Pausen
Die „Low activity"-Pausen waren meist POSITIV/neutral. **Ausnahme:** die **25.08.-Sammelpause** auf `CH_GSN_DE_Zürich_Handwerk` (Broad + Exact gemischt, Dutzende Keywords) → DiD **+168 %** (NEG, niedrige Materialität ~104 CHF). **Match-Type-Befund (d):** Broad-lastige Massen-Pausen/-Adds sind das Risiko; einzelne Exact/Phrase-Pausen auf teuren Keywords waren nützlich (Elektroinstallateur DiD −69 %, Metallbauer −39 %).

## Nicht kausal / MANUELL (Kritikpunkt a)

- **04.07. Kunden-Asset erstellt** (Konto-Ebene) → **MANUELL**. Gegen den Konto-Trend nicht isolierbar; Spend-at-Risk = Konto-28-T-Kosten, nicht der Kampagne zurechenbar.
- **16.10. Standardzielvorhaben-Wechsel** — im UI unter der UMLAND-Testzeitraum-Zeile geloggt, wirkt aber **konto­weit** → als **KPI-Pivot** behandelt (Caveat 2), nicht als bewertbarer Einzel-Change.
- **2× Dachdecker „Maximale Conversions"** (08.18./10.14.) → **UNKLAR**: Kampagne hatte im 2024-Fenster **keinen Spend** (inaktiv/2025er Kampagne) → korrekt **nicht** auf Konto-Spend hochgerechnet.

## Alle Verdikte (sortiert nach Spend-at-Risk)

| # | Datum | Typ | Op | Ebene/Entity (K=Kampagne) | Verdikt | Conf. | Kern-Delta | DiD | YoY(Konto) | Spend | Par. | user_type | Notiz |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2024-10-16 | SET | create/enable | K: UMLAND TEST | **POSITIV** | mittel | CPA −27% (DiD −13%) | −13% | −27% | 5243 | 2 | manager | Zielvorhaben-Pivot 16.10. im Fenster → nur DiD; broad/exact |
| 2 | 2024-10-15 | BUD | decrease | K: UMLAND TEST | **POSITIV** | mittel | CPA −20% (DiD −13%) | −13% | −24% | 5183 | 2 | manager | Pivot im Fenster → nur DiD; Rank-Lost-IS dominiert |
| 3 | 2024-09-19 | BUD | increase | K: UMLAND TEST | **NEGATIV** | mittel | CPA +43% (DiD +34%) | +34% | +39% | 5020 | 2 | manager | Pivot im Fenster → nur DiD; Budget-Lost-IS hoch (Headroom) — 120→185 |
| 4 | 2024-07-04 | AD | create | KONTO | **MANUELL** | niedrig | CPA −18% (DiD +0%) | +0% | +2% | 4795 | 5 | manager | Konto-Ebene (Kunden-Asset): nicht isolierbar |
| 5 | 2024-08-15 | BUD | increase | K: UMLAND TEST | **NEUTRAL** | niedrig | CPA +1% (DiD +0%) | +0% | +49% | 3432 | 1 | manager | Delta ~ Konto-Trend; Budget-Lost-IS hoch — 101→120 |
| 6 | 2024-08-01 | BUD | increase | K: UMLAND TEST | **NEGATIV** | niedrig | CPA +37% (DiD +21%) | +21% | +32% | 3156 | 5 | manager | Budget-Lost-IS hoch — 50→101 (Verdopplung zu weit) |
| 7 | 2024-12-19 | BUD | decrease | K: UMLAND TEST | **NEUTRAL** | mittel | CPA −9% (DiD −9%) | −9% | −5% | 2377 | 1 | manager | Rank-Lost-IS dominiert — 86→66 |
| 8 | 2024-12-03 | STRUKT | remove | K: UMLAND TEST | **NEUTRAL** | mittel | CPA +31% (DiD +6%) | +6% | −22% | 2086 | 1 | auto_apply | broad-lastig |
| 9 | 2024-07-06 | STRUKT | remove | K: UMLAND TEST | **POSITIV** | niedrig | CPA −25% (DiD −12%) | −12% | +9% | 1553 | 4 | auto_apply | phrase |
| 10 | 2024-07-04 | BUD | increase | K: UMLAND TEST | **POSITIV** | niedrig | CPA −35% (DiD −17%) | −17% | +2% | 1451 | 4 | manager | Rank-Lost-IS dominiert — 35→50 (noch Headroom) |
| 11 | 2024-07-04 | STRUKT | pause | K: UMLAND TEST | **POSITIV** | niedrig | CPA −35% (DiD −17%) | −17% | +2% | 1451 | 4 | manager | broad-lastig |
| 12 | 2024-10-16 | SET | add/change/pause | K: UMLAND Testzeitraum 263 | **UNKLAR** | niedrig | CPA n/a | n/a | −27% | 1216 | 4 | manager | Relaunch/50%-Split; Pivot im Fenster |
| 13 | 2024-10-16 | AD | add/create/remove | K: UMLAND Testzeitraum 263 | **UNKLAR** | niedrig | CPA n/a | n/a | −27% | 1216 | 4 | manager | RSA/Feed-Aufsatz; Pivot im Fenster |
| 14 | 2024-10-16 | NEG | add/change | K: UMLAND Testzeitraum 263 | **UNKLAR** | niedrig | CPA n/a | n/a | −27% | 1216 | 4 | manager | NKL_Generisch + 30 Exact-Negatives; broad/exact/phrase |
| 15 | 2024-10-16 | BID | create | K: UMLAND Testzeitraum 263 | **UNKLAR** | niedrig | CPA n/a | n/a | −27% | 1216 | 4 | manager | Ziel-CPA 22,50 gesetzt; Pivot im Fenster |
| 16 | 2024-10-16 | BUD | add | K: UMLAND Testzeitraum 263 | **UNKLAR** | niedrig | CPA n/a | n/a | −27% | 1216 | 4 | manager | Budget 15 CHF Test-Arm; Pivot im Fenster |
| 17 | 2024-08-15 | BUD | increase | K: SOLAR | **NEGATIV** | hoch | CPA +24% (DiD +23%) | +23% | +49% | 1198 | 0 | manager | Rank-Lost-IS dominiert — Sammel-Erhöhung 15.08. |
| 18 | 2024-09-05 | BUD | decrease | K: Schweisser | **POSITIV** | mittel | CPA −47% (DiD −38%) | −38% | +65% | 858 | 1 | manager | Rank-Lost-IS dominiert — Rücknahme der 15.08.-Erhöhung |
| 19 | 2024-08-15 | BUD | increase | K: Schweisser | **NEGATIV** | mittel | CPA +30% (DiD +29%) | +29% | +49% | 853 | 1 | manager | Rank-Lost-IS dominiert — Sammel-Erhöhung 15.08. |
| 20 | 2024-10-15 | BUD | decrease | K: Montage-Elektriker | **NEUTRAL** | mittel | CPA −13% (DiD −6%) | −6% | −24% | 359 | 0 | manager | Pivot im Fenster → nur DiD; Rank-Lost-IS dominiert |
| 21 | 2024-08-15 | BUD | increase | K: GERÜSTBAUER | **NEUTRAL** | niedrig | CPA +5% (DiD +4%) | +4% | +49% | 335 | 0 | manager | Delta ~ Konto-Trend; Sammel-Erhöhung 15.08. |
| 22 | 2024-11-29 | STRUKT | pause | K: Montage-Elektriker | **POSITIV** | hoch | CPA −7% (DiD −31%) | −31% | −26% | 286 | 0 | system_bulk | broad Low-Activity-Pause |
| 23 | 2024-12-22 | STRUKT | pause | K: Automatikmonteur | **POSITIV** | hoch | CPA −25% (DiD −33%) | −33% | +4% | 258 | 0 | system_bulk | broad Low-Activity-Pause (Automatikmonteur CPA ~30 = 2,2× Ø) |
| 24 | 2024-07-04 | BID | change | K: Brand | **NEGATIV** | mittel | CPA +7% (DiD +25%) | +25% | +2% | 216 | 1 | manager | Manueller CPC → Conversions maximieren (Lernphase) |
| 25 | 2024-10-14 | AD | pause | K: CH_GSN_DE_Zürich_Handwerk | **NEGATIV** | mittel | CPA +436% (DiD +440%) | +440% | −21% | 156 | 1 | system_bulk | **CPA-Artefakt** (Conv-Nenner <2); Pivot im Fenster; Mini-Spend |
| 26 | 2024-10-06 | STRUKT | pause | K: CH_GSN_DE_Zürich_Handwerk | **UNKLAR** | niedrig | CPA n/a | n/a | −9% | 133 | 1 | system_bulk | broad/exact; Signifikanz < Gate |
| 27 | 2024-08-18 | STRUKT | pause | K: CH_GSN_DE_Elektroinstallateur_1 | **POSITIV** | mittel | CPA −76% (DiD −69%) | −69% | +40% | 111 | 0 | system_bulk | Exact-Pause; CPA instabil (Conv <2) — Mini-Spend |
| 28 | 2024-08-25 | STRUKT | pause | K: CH_GSN_DE_Zürich_Handwerk | **NEGATIV** | mittel | CPA +153% (DiD +168%) | +168% | +80% | 104 | 0 | system_bulk | **Broad+Exact-Sammelpause** — CPA-Artefakt, niedrige Materialität |
| 29 | 2024-10-06 | STRUKT | pause | K: Metallbauer | **NEUTRAL** | mittel | CPA +1% (DiD −8%) | −8% | −9% | 86 | 0 | system_bulk | phrase; Pivot im Fenster |
| 30 | 2024-12-31 | STRUKT | remove | K: Metallbauer | **POSITIV** | mittel | CPA −63% (DiD −53%) | −53% | −9% | 76 | 1 | auto_apply | phrase-Removal |
| 31 | 2024-12-04 | STRUKT | remove | K: Metallbauer | **UNKLAR** | niedrig | CPA n/a | n/a | −17% | 70 | 1 | auto_apply | phrase; Signifikanz < Gate |
| 32 | 2024-08-18 | STRUKT | pause | K: Metallbauer | **POSITIV** | mittel | CPA −46% (DiD −39%) | −39% | +40% | 62 | 2 | system_bulk | exact/phrase |
| 33 | 2024-08-07 | STRUKT | remove | K: Metallbauer | **UNKLAR** | niedrig | CPA n/a | n/a | +37% | 62 | 2 | auto_apply | exact/phrase; Signifikanz < Gate |
| 34 | 2024-08-03 | STRUKT | remove | K: Metallbauer | **UNKLAR** | niedrig | CPA n/a | n/a | +29% | 60 | 2 | auto_apply | broad-lastig; Signifikanz < Gate |
| 35 | 2024-10-14 | AD | pause | K: Dachdecker (inaktiv) | **UNKLAR** | niedrig | keine Perf-Daten | n/a | −21% | 0 | system_bulk | Kampagne ohne Spend im Fenster |
| 36 | 2024-08-18 | STRUKT | pause | K: Dachdecker (inaktiv) | **UNKLAR** | niedrig | keine Perf-Daten | n/a | +40% | 0 | system_bulk | Kampagne ohne Spend im Fenster; broad |

## Methodik
- Fenster **28/28 T** um `change_datetime` (Budget < 10k, agent_methodik §1).
- Signifikanz-Gate: **≥ 20 Klicks ODER ≥ 2 Conv** im Post-Fenster (§2), sonst UNKLAR.
- Outcome **CPA**, **DiD-normiert** = Kampagnen-CPA-Delta minus Konto-CPA-Delta im selben Fenster.
- Material-Schwelle DiD **±10 %**; |DiD| < 5 % → niedrig („~Konto-Trend").
- **Kategorie-Korrektur:** `description_full` überschreibt die Import-Heuristik (jobangebot→„gebot"→BID-Fehler behoben; Keyword-Pausen = STRUKT).
- **STATUS/Keyword-Pausen** am Pre-CPA vs. Konto-Ø 13,86 CHF bewertet (teuer pausiert = POSITIV, effizient/Top-Performer = NEGATIV; §3, Deckel 11,09 CHF).
- **Konto-Ebene** (Kunden-Asset, Zielvorhaben) → **MANUELL** statt erzwungenem NEUTRAL. **Inaktive Kampagnen ohne Perf** → UNKLAR (nicht auf Konto-Spend hochgerechnet).
- **Lost-IS-Diagnose** bei BUD: `search_budget_lost_impression_share` vs. `_rank_` (Headroom vs. teurer Auktionsdruck).
- **Match-Type** aus `description_full` (genau=exact, weitgehend=broad, Wortgruppe=phrase) mitgeführt; Broad-lastige Adds/Pausen als Risiko markiert.
- **YoY:** Post-Fenster-CPA (Konto) gegen dasselbe Kalenderfenster 2023; nur im vergleichbaren Conv-Regime (ab Jul 2023).
- Kampagnen-Matching: Name-String → `campaign_id` inkl. Trade-Token-Fallback für Renames (`CH_GSN_*` → `EX|25|CH|…|Trade`). **1 unaufgelöste** Kampagne (Dachdecker, 2024 inaktiv).
