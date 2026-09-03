---
kunde: kollabo
customer_id: "1487707588"
zeitraum: 2025-01-15 .. 2025-12-29 (Changes) · Performance-Fenster 2024-12-01 .. 2026-01-31
quelle_changes: Cowork UI-Export (changes_kollabo_2025_normalized.csv, 159 Änderungen)
quelle_perf: Google Ads API, täglich, Kampagnen-Ebene (stabile campaign_id)
outcome_kpi: CPA (Cost/Conv), DiD-normiert vs. Konto-Trend
tracking_status: 2025 VALIDE (im Gegensatz zum 2026-Live-Pull) — Caveat: Conv-Basis-Wechsel 30.10.2025
scope: KUNDEN-SCOPED — verlässt diesen Ordner nie, nicht kundenübergreifend nutzen (Roh-CSV enthält PII)
stand: 2026-07-02
---

# Kollabo — Change-Impact-Report 2025 (historisch, UI-Export)

> Analyse der Cowork-UI-Änderungshistorie 2025 gegen tatsächlich gezogene 2025-API-Performance.
> **Attribution, keine Kausalität.** Bei vielen parallelen Changes / Saison bewusst niedrige Confidence.
> Roh-Verdikte: `../../../data/kollabo/change_impact_2025.csv` (git-ignored).

## Zusammenfassung

- **159 Änderungen** → **113 bewertete Cluster** (Änderungen gleicher Datum×Kampagne×Kategorie zusammengefasst).
- Verdikte: **POSITIV 36 · NEGATIV 46 · NEUTRAL 30 · UNKLAR 1**.
- **Konto-Ø-CPA 2025: 19,54 CHF** (Basis für Top-Performer-Schutz, agent_methodik §3).
- Monatsverlauf CPA: Jan 15,3 · Apr 16,0 · Aug 25,2 · **Nov 34,0 · Dez 56,7** — der Jahresend-Anstieg ist v.a. ein **Conv-Basis-Effekt** (siehe Caveats), kein reiner Effizienzverlust. Deshalb ist **DiD** (Kampagne minus Konto im selben Fenster) hier die belastbare Grösse, nicht der absolute CPA-Delta.

## Wichtigste Caveats (ehrlich)

1. **Conv-Basis-Wechsel am 30.10.2025.** An diesem Tag wurde „SF – Closed Won (Final)“ als **primäre** Conversion aufgenommen und das Klick-Conversion-Fenster von 30 auf 60 Tage gestellt. Ab Nov bricht das Conv-Volumen ein (Okt 433 → Nov 186 → Dez 160) und der absolute CPA steigt konto­weit. Für alle Changes ab ~Nov ist der **absolute** CPA-Delta verzerrt; nur der **DiD** gegen den Konto-Trend ist lesbar. Cluster mit dem Wechsel im Fenster sind mit Notiz markiert und in der Confidence gedeckelt.
2. **UI-Daten sind gröber als API.** Nur ~50 % der Änderungen haben ein geparstes alt→neu; `category`/`operation` sind Heuristik. Wo unsicher, gilt `description_full`. Confidence generell eine Stufe demütiger lesen.
3. **Viele parallele Changes.** Besonders 20.–23.06. (Portfolio-Umbau) und 04.–23.12. bündeln 7–20 Changes im 28-T-Fenster → Attribution schwach, Confidence entsprechend niedrig.
4. **Kein YoY-Saisoncheck möglich.** Gezogen wurde ab 2024-12; für Changes vor Feb 2025 fehlt das Vorjahresfenster. DiD fängt die Saison teilweise ab, ersetzt aber keinen echten YoY.
5. **Konto-Ebene = kein DiD-Signal.** Die 4 grössten Einzeländerungen nach Spend (Portfolio-Budget-Topup 05.08., Budget-Status-Bereinigung 23.06., Nutzer-Entzug 12.03., Conv-Setup 30.10.) betreffen das ganze Konto → gegen den Konto-Trend nicht isolierbar → zwangsläufig NEUTRAL/niedrig. Die grössten Spend-Posten sind also **nicht kausal bewertbar**.

## Meta-Analyse: welcher Änderungs-TYP wirkt netto?

| Typ | POSITIV | NEGATIV | NEUTRAL | UNKLAR | Netto-Lesart |
|---|---|---|---|---|---|
| BUD | 20 | 22 | 12 | 1 | Budget-Feintuning dominiert das Konto; wirkt richtungslos — **Richtung** (rauf/runter) zählt mehr als der Akt an sich (siehe UMLAND). |
| BID | 1 | 5 | 4 | 0 | Gebots-/Strategie-Eingriffe netto **negativ** — v.a. die Portfolio-Bidding-Migration. |
| NEG | 0 | 0 | 1 | 0 | zu wenige echte Negativ-Cluster 2025 (2) für ein Urteil. |
| STRUKT | 8 | 12 | 4 | 0 | Keyword-Umbauten gemischt, leicht negativ — Hinzufügen breiter Keywords tendenziell teurer. |
| AD | 0 | 1 | 2 | 0 | zu dünn (3) für Aussage. |
| SET | 0 | 1 | 5 | 0 | Einstellungen überwiegend NEUTRAL/unattributierbar (Konto-Ebene). |
| STATUS | 7 | 5 | 2 | 0 | Pausen **gemischt** — sinnvoll bei teuren Kampagnen, schädlich bei effizienten (Jahresend-Blankopause). |

## Meta-Analyse: Client vs. Manager vs. Auto-Apply vs. System

| user_type | POSITIV | NEGATIV | NEUTRAL | UNKLAR | n | Lesart |
|---|---|---|---|---|---|---|
| manager | 24 | 33 | 24 | 1 | 82 | meiste Changes (inkl. Portfolio-Experiment, das sie selbst wieder zurücknahmen). Netto leicht negativ — getrieben vom Portfolio-Umbau + Aug-Budgetkürzungen im CPA-Hochmonat. |
| auto_apply | 5 | 6 | 3 | 0 | 14 | Google-Empfehlungen (Keyword-Removals) — **Münzwurf** (5:6), kein klarer Nutzen. |
| client | 5 | 3 | 1 | 0 | 9 | wenige, überwiegend sinnvolle Eingriffe (Pausen). Netto positiv, kleines n. |
| system_bulk | 1 | 4 | 1 | 0 | 6 | „Low activity“-Keyword-Pausen — netto negativ, aber Mini-Volumen, geringe Materialität. |
| client, manager | 0 | 0 | 1 | 0 | 1 | Mischcluster, n=1. |
| auto_apply, manager | 1 | 0 | 0 | 0 | 1 | Mischcluster, n=1. |

## Die 3 belastbarsten Muster (mittel/hohe Confidence, Spend-relevant)

### 1. Portfolio-Bidding-Migration 23.06.2025 → netto CPA-schädlich, wurde zurückgenommen
Am 23.06. wurden **8 Kampagnen in eine gemeinsame Portfolio-Gebotsstrategie** („Portfolio Test JM 200625“) verschoben. Ergebnis im 28-T-Post-Fenster: **7 von 8 NEGATIV** (nur UMLAND neutral). Am deutlichsten Automatiker (DiD **+25 %**, mittel), dazu Schweisser (+188 %), Polymechaniker (+12 %), Montage-Elektriker (+13 %). ~6 Wochen später (05.–06.08.) wurden die Kampagnen **wieder aus dem Portfolio gelöst** (eigene Budgets) — die Rücknahme zeigt mehrere POSITIV (Schweisser DiD **−68 %**, Polymechaniker −11 %). **Learning:** die Portfolio-Konsolidierung über heterogene Gewerke hinweg hat die CPA-Steuerung verschlechtert; Einzel-Budget/-Bidding pro Gewerk war besser. *(Confidence gedeckelt: Aug ist CPA-Hochmonat, mehrere Parallel-Changes.)*

### 2. UMLAND TEST — Budget rauf verschlechtert, Budget runter verbessert (Sättigung)
Über das Jahr klarer Richtungszusammenhang bei der grössten Einzelkampagne (bis ~2.600 CHF Spend-at-Risk/Fenster): **Budget-Erhöhungen → CPA rel. schlechter** (22./25.04. DiD +36 %/+24 %; 18.12. +177 %), **Budget-Senkungen → CPA rel. besser/neutral** (Jan −28 %, Sep −15 %, Nov −127 %). **Learning:** UMLAND TEST skaliert **nicht** linear — mehr Budget kaufte teureren Traffic ein. Für 2026: UMLAND als Effizienz-, nicht als Volumen-Hebel behandeln; Erhöhungen nur mit CPC≤RPU-Check.

### 3. Jahresend-Blankopause 29.12. war nicht chirurgisch
Der Client pausierte am 29.12. mehrere „25“-Kampagnen pauschal. **Sinnvoll** bei teuren (Automatiker Pre-CPA 91,6 = x1,63 Konto-Ø; Brand x2,23; Elektroinstallateur x10,7 → POSITIV), **aber schädlich** bei effizienten (Schweisser x0,67; Polymechaniker x0,22; UMLAND x0,33 → NEGATIV: gut laufendes Volumen abgeschaltet). Gleiches Muster 22.10. (UMLAND bei x0,63 pausiert = NEGATIV). **Learning:** Pausen kampagnenscharf am Pre-CPA-vs-Konto-Ø ausrichten, keine Blanko-Abschaltung.

## Alle Verdikte (sortiert nach Spend-at-Risk)

| # | Datum | Typ | Op | Ebene/Entity | Verdikt | Conf. | Kern-Delta (DiD) | Spend-at-Risk | Par. | user_type | Notiz |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2025-08-05 | BUD | increase | account: KONTO | **NEUTRAL** | niedrig | CPA +66% (DiD +0%) | 11173 | 18 | manager | 18 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 2 | 2025-06-23 | BUD | remove | account: KONTO | **NEUTRAL** | niedrig | CPA -10% (DiD +0%) | 9262 | 20 | manager | 20 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 3 | 2025-03-12 | SET | remove | account: KONTO | **NEUTRAL** | niedrig | CPA -10% (DiD +0%) | 9070 | 7 | client, manager | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 4 | 2025-10-30 | SET | change | account: KONTO | **NEUTRAL** | niedrig | CPA +51% (DiD +0%) | 7657 | 11 | manager | 11 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar; Delta ~ Konto-Trend (DiD~0) |
| 5 | 2025-09-05 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -30% (DiD -8%) | 2632 | 4 | manager | 4 parallele Changes im Fenster |
| 6 | 2025-08-06 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA +21% (DiD -43%) | 2584 | 4 | manager | 4 parallele Changes im Fenster |
| 7 | 2025-08-06 | STRUKT | add | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA +21% (DiD -43%) | 2584 | 4 | auto_apply, manager | 4 parallele Changes im Fenster |
| 8 | 2025-09-11 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -31% (DiD -15%) | 2564 | 4 | manager | 4 parallele Changes im Fenster |
| 9 | 2025-04-22 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +81% (DiD +36%) | 2502 | 3 | manager | 3 parallele Changes im Fenster |
| 10 | 2025-04-25 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | mittel | CPA +58% (DiD +24%) | 2463 | 2 | manager | 2 parallele Changes im Fenster |
| 11 | 2025-06-23 | BUD | add | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -9% (DiD +1%) | 2406 | 7 | manager | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 12 | 2025-06-20 | SET | add | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -18% (DiD -5%) | 2405 | 7 | manager | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 13 | 2025-06-20 | BID | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -18% (DiD -5%) | 2405 | 7 | manager | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 14 | 2025-06-20 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -18% (DiD -5%) | 2405 | 7 | manager | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 15 | 2025-06-21 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -17% (DiD -4%) | 2396 | 7 | auto_apply | 7 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 16 | 2025-08-18 | BID | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA +9% (DiD -1%) | 2362 | 5 | auto_apply | 5 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 17 | 2025-01-30 | BUD | decrease | campaign: CH_GSN_DE_Zimmermann_1 | **POSITIV** | hoch | CPA -54% (DiD -53%) | 2332 | 0 | manager |  |
| 18 | 2025-01-30 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -28% (DiD -28%) | 2167 | 3 | manager | 3 parallele Changes im Fenster |
| 19 | 2025-02-03 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -23% (DiD -28%) | 2137 | 3 | auto_apply | 3 parallele Changes im Fenster |
| 20 | 2025-01-15 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | mittel | CPA -21% (DiD -12%) | 2081 | 2 | manager | 2 parallele Changes im Fenster |
| 21 | 2025-09-25 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -15% (DiD -4%) | 1940 | 6 | manager | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 22 | 2025-06-20 | BUD | decrease | campaign: CH_GSN_DE_Zimmermann_1 | **POSITIV** | mittel | CPA -76% (DiD -63%) | 1893 | 1 | manager | 1 parallele Changes im Fenster |
| 23 | 2025-09-29 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -12% (DiD -4%) | 1787 | 6 | manager | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 24 | 2025-04-22 | BUD | increase | campaign: CH_GSN_DE_Zimmermann_1 | **POSITIV** | hoch | CPA -13% (DiD -58%) | 1764 | 0 | manager |  |
| 25 | 2025-07-06 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -25% (DiD -17%) | 1725 | 7 | auto_apply | 7 parallele Changes im Fenster |
| 26 | 2025-02-27 | STRUKT | add | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +9% (DiD +12%) | 1707 | 5 | manager | 5 parallele Changes im Fenster |
| 27 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **NEGATIV** | mittel | CPA +16% (DiD +25%) | 1680 | 2 | manager | 2 parallele Changes im Fenster |
| 28 | 2025-03-12 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -14% (DiD -5%) | 1633 | 4 | auto_apply | 4 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 29 | 2025-06-20 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **NEGATIV** | mittel | CPA +15% (DiD +28%) | 1604 | 2 | manager | 2 parallele Changes im Fenster |
| 30 | 2025-03-27 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -21% (DiD -17%) | 1556 | 5 | manager | 5 parallele Changes im Fenster |
| 31 | 2025-07-11 | BID | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -13% (DiD -15%) | 1513 | 10 | auto_apply | 10 parallele Changes im Fenster |
| 32 | 2025-04-03 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +43% (DiD +26%) | 1380 | 5 | manager | 5 parallele Changes im Fenster |
| 33 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **POSITIV** | mittel | Pre-CPA 91.6 vs Konto-Ø 56.3 (x1.63) | 1379 | 2 | client | 2 parallele Changes im Fenster |
| 34 | 2025-08-06 | BUD | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | mittel | CPA +286% (DiD +223%) | 1341 | 2 | manager | 2 parallele Changes im Fenster |
| 35 | 2025-12-23 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **NEGATIV** | mittel | CPA -7% (DiD +32%) | 1323 | 2 | manager | 2 parallele Changes im Fenster |
| 36 | 2025-06-12 | BUD | decrease | campaign: EX | DE | CH | SEARCH | LEAD | GERÜSTBAUER | **NEGATIV** | mittel | CPA +64% (DiD +73%) | 1273 | 1 | manager | 1 parallele Changes im Fenster |
| 37 | 2025-12-04 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **NEUTRAL** | mittel | CPA +112% (DiD +9%) | 1269 | 2 | manager | 2 parallele Changes im Fenster |
| 38 | 2025-09-05 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **POSITIV** | niedrig | CPA -42% (DiD -19%) | 1160 | 4 | manager | 4 parallele Changes im Fenster |
| 39 | 2025-09-05 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **POSITIV** | niedrig | CPA -42% (DiD -19%) | 1160 | 4 | manager | 4 parallele Changes im Fenster |
| 40 | 2025-12-23 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | niedrig | CPA -23% (DiD +15%) | 1154 | 7 | manager | 7 parallele Changes im Fenster |
| 41 | 2025-12-23 | STRUKT | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | niedrig | CPA -23% (DiD +15%) | 1154 | 7 | auto_apply | 7 parallele Changes im Fenster |
| 42 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **POSITIV** | niedrig | Pre-CPA 93.8 vs Konto-Ø 56.3 (x1.67) | 1130 | 6 | client | 6 parallele Changes im Fenster |
| 43 | 2025-11-30 | STRUKT | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEUTRAL** | niedrig | CPA +76% (DiD +5%) | 1130 | 6 | system_bulk | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 44 | 2025-08-06 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +135% (DiD +71%) | 1096 | 4 | manager | 4 parallele Changes im Fenster |
| 45 | 2025-10-10 | SET | enable | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -6% (DiD +1%) | 1077 | 5 | manager | 5 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar; Delta ~ Konto-Trend (DiD~0) |
| 46 | 2025-10-10 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEUTRAL** | niedrig | CPA -6% (DiD +1%) | 1077 | 5 | manager | 5 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar; Delta ~ Konto-Trend (DiD~0) |
| 47 | 2025-08-06 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **POSITIV** | mittel | CPA +53% (DiD -11%) | 1065 | 1 | manager | 1 parallele Changes im Fenster |
| 48 | 2025-12-17 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | niedrig | CPA +40% (DiD +18%) | 1044 | 7 | manager | 7 parallele Changes im Fenster |
| 49 | 2025-08-21 | BID | change | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEUTRAL** | niedrig | CPA +5% (DiD -1%) | 1044 | 6 | manager | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 50 | 2025-08-21 | AD | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEUTRAL** | niedrig | CPA +5% (DiD -1%) | 1044 | 6 | manager | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 51 | 2025-08-21 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEUTRAL** | niedrig | CPA +5% (DiD -1%) | 1044 | 6 | manager | 6 parallele Changes im Fenster; Delta ~ Konto-Trend (DiD~0) |
| 52 | 2025-08-21 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **POSITIV** | mittel | CPA -54% (DiD -60%) | 1020 | 2 | manager | 2 parallele Changes im Fenster |
| 53 | 2025-01-17 | STRUKT | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **POSITIV** | hoch | CPA -51% (DiD -42%) | 994 | 0 | system_bulk |  |
| 54 | 2025-12-04 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **POSITIV** | niedrig | CPA +90% (DiD -13%) | 993 | 7 | manager | 7 parallele Changes im Fenster |
| 55 | 2025-12-04 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **POSITIV** | niedrig | CPA +90% (DiD -13%) | 993 | 7 | manager | 7 parallele Changes im Fenster |
| 56 | 2025-10-22 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **POSITIV** | niedrig | CPA -72% (DiD -88%) | 988 | 3 | manager | 3 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 57 | 2025-10-27 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **POSITIV** | niedrig | CPA -58% (DiD -90%) | 934 | 3 | manager | 3 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 58 | 2025-10-10 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | mittel | CPA +54% (DiD +60%) | 928 | 1 | manager | 1 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 59 | 2025-10-22 | STATUS | pause | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | Pre-CPA 13.0 vs Konto-Ø 20.8 (x0.63) | 898 | 7 | manager | 7 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar; Top-Performer-naeher Kandidat pausiert |
| 60 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Schweisser | **NEGATIV** | mittel | Pre-CPA 37.9 vs Konto-Ø 56.3 (x0.67) | 884 | 1 | client | 1 parallele Changes im Fenster; Top-Performer-naeher Kandidat pausiert |
| 61 | 2025-12-08 | STRUKT | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **POSITIV** | niedrig | CPA +43% (DiD -44%) | 883 | 7 | auto_apply | 7 parallele Changes im Fenster |
| 62 | 2025-12-17 | BID | change | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 63 | 2025-12-17 | AD | pause | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 64 | 2025-12-17 | STRUKT | add | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 65 | 2025-12-17 | STATUS | pause | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | Post-CPA 46.7 vs Konto-Ø 52.8 (x0.88) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 66 | 2025-12-17 | BUD | change | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 67 | 2025-12-17 | SET | add | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 68 | 2025-12-17 | NEG | change | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **NEUTRAL** | niedrig | CTR n/a / CPC n/a (CPA n/a) | 871 | 8 | manager | 8 parallele Changes im Fenster |
| 69 | 2025-08-06 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Automatiker | **NEGATIV** | mittel | CPA +139% (DiD +75%) | 825 | 1 | manager | 1 parallele Changes im Fenster |
| 70 | 2025-12-04 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Schweisser | **POSITIV** | mittel | CPA +62% (DiD -41%) | 815 | 1 | manager | 1 parallele Changes im Fenster |
| 71 | 2025-08-06 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Schweisser | **POSITIV** | mittel | CPA -4% (DiD -68%) | 777 | 1 | manager | 1 parallele Changes im Fenster |
| 72 | 2025-12-23 | STRUKT | remove | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **POSITIV** | niedrig | CTR +13% / CPC -44% (CPA n/a) | 763 | 8 | auto_apply | 8 parallele Changes im Fenster |
| 73 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Schweisser | **NEGATIV** | mittel | CPA +179% (DiD +188%) | 735 | 1 | manager | 1 parallele Changes im Fenster |
| 74 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEUTRAL** | mittel | Pre-CPA 62.0 vs Konto-Ø 56.3 (x1.10) | 679 | 1 | client | 1 parallele Changes im Fenster |
| 75 | 2025-11-30 | STRUKT | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | mittel | CPA +251% (DiD +180%) | 679 | 1 | system_bulk | 1 parallele Changes im Fenster |
| 76 | 2025-12-29 | STATUS | pause | campaign: EX | 26 | CH | SEARCH | LEAD | Elektroinstallateur | **POSITIV** | niedrig | Pre-CPA 602.1 vs Konto-Ø 56.3 (x10.69) | 656 | 8 | client | 8 parallele Changes im Fenster |
| 77 | 2025-04-03 | BUD | decrease | campaign: CH_GSN_DE_Maurer_1 | **POSITIV** | mittel | CPA -57% (DiD -75%) | 631 | 1 | manager | 1 parallele Changes im Fenster |
| 78 | 2025-12-04 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | mittel | CPA +207% (DiD +104%) | 617 | 2 | manager | 2 parallele Changes im Fenster |
| 79 | 2025-10-10 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | mittel | CPA +22% (DiD +28%) | 612 | 1 | manager | 1 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 80 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **POSITIV** | niedrig | Pre-CPA 125.8 vs Konto-Ø 56.3 (x2.23) | 602 | 3 | client | 3 parallele Changes im Fenster |
| 81 | 2025-11-30 | STRUKT | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +231% (DiD +160%) | 598 | 3 | system_bulk | 3 parallele Changes im Fenster |
| 82 | 2025-12-17 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **POSITIV** | niedrig | CPA -5% (DiD -28%) | 595 | 4 | manager | 4 parallele Changes im Fenster |
| 83 | 2025-12-08 | STRUKT | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +1299% (DiD +1212%) | 554 | 4 | auto_apply | 4 parallele Changes im Fenster; CPA instabil (Conv-Nenner <2) |
| 84 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **NEGATIV** | mittel | CPA +2% (DiD +12%) | 530 | 1 | manager | 1 parallele Changes im Fenster |
| 85 | 2025-12-04 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +866% (DiD +763%) | 526 | 4 | manager | 4 parallele Changes im Fenster; CPA instabil (Conv-Nenner <2) |
| 86 | 2025-12-17 | BID | change | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +251% (DiD +228%) | 506 | 7 | manager | 7 parallele Changes im Fenster |
| 87 | 2025-12-18 | BUD | increase | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +184% (DiD +177%) | 504 | 7 | manager | 7 parallele Changes im Fenster |
| 88 | 2025-12-29 | STATUS | pause | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | Pre-CPA 18.6 vs Konto-Ø 56.3 (x0.33) | 500 | 5 | client | 5 parallele Changes im Fenster; Top-Performer-naeher Kandidat pausiert |
| 89 | 2025-02-27 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Schweisser | **NEGATIV** | mittel | CPA +25% (DiD +28%) | 481 | 1 | manager | 1 parallele Changes im Fenster |
| 90 | 2025-08-06 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | niedrig | CPA +334% (DiD +270%) | 449 | 3 | manager | 3 parallele Changes im Fenster |
| 91 | 2025-08-05 | SET | enable | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | niedrig | CPA +334% (DiD +268%) | 432 | 3 | manager | 3 parallele Changes im Fenster |
| 92 | 2025-08-05 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | niedrig | Post-CPA 57.3 vs Konto-Ø 27.3 (x2.10) | 432 | 3 | manager | 3 parallele Changes im Fenster |
| 93 | 2025-11-17 | BUD | decrease | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **NEUTRAL** | niedrig | CPA +81% (DiD +5%) | 429 | 4 | manager | 4 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar; Delta ~ Konto-Trend (DiD~0) |
| 94 | 2025-01-17 | BID | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | hoch | CPA +64% (DiD +73%) | 408 | 0 | system_bulk |  |
| 95 | 2025-12-09 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +222% (DiD +143%) | 380 | 9 | auto_apply | 9 parallele Changes im Fenster |
| 96 | 2025-12-08 | BID | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +222% (DiD +134%) | 363 | 9 | auto_apply | 9 parallele Changes im Fenster |
| 97 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Montage-Elektriker | **NEGATIV** | mittel | CPA +3% (DiD +13%) | 322 | 1 | manager | 1 parallele Changes im Fenster |
| 98 | 2025-11-30 | BID | pause | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +94% (DiD +23%) | 312 | 8 | system_bulk | 8 parallele Changes im Fenster |
| 99 | 2025-12-04 | BID | pause | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +358% (DiD +254%) | 301 | 9 | manager | 9 parallele Changes im Fenster |
| 100 | 2025-03-20 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Automatikmonteur | **POSITIV** | mittel | Pre-CPA 25.0 vs Konto-Ø 15.9 (x1.58) | 288 | 1 | client | 1 parallele Changes im Fenster |
| 101 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +42% (DiD +51%) | 282 | 3 | manager | 3 parallele Changes im Fenster |
| 102 | 2025-06-14 | STRUKT | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +65% (DiD +74%) | 258 | 3 | auto_apply | 3 parallele Changes im Fenster |
| 103 | 2025-06-12 | STRUKT | add | campaign: EX | 25 | CH | SEARCH | LEAD | Brand | **NEGATIV** | niedrig | CPA +55% (DiD +64%) | 252 | 3 | manager | 3 parallele Changes im Fenster |
| 104 | 2025-12-29 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **NEGATIV** | mittel | Pre-CPA 12.2 vs Konto-Ø 56.3 (x0.22) | 238 | 1 | client | 1 parallele Changes im Fenster; Top-Performer-naeher Kandidat pausiert |
| 105 | 2025-11-25 | STRUKT | remove | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **NEGATIV** | niedrig | CPA +109% (DiD +19%) | 236 | 9 | auto_apply | 9 parallele Changes im Fenster |
| 106 | 2025-12-04 | BUD | increase | campaign: EX | 25 | CH | SEARCH | LEAD | Polymechaniker | **POSITIV** | mittel | CPA +79% (DiD -24%) | 222 | 2 | manager | 2 parallele Changes im Fenster |
| 107 | 2025-11-17 | BUD | decrease | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | CPA -51% (DiD -127%) | 143 | 8 | manager | 8 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 108 | 2025-11-17 | STATUS | pause | campaign: EX | DE | DACH | SEARCH | LEAD | UMLAND TEST | **POSITIV** | niedrig | Post-CPA 9.1 vs Konto-Ø 41.6 (x0.22) | 143 | 8 | manager | 8 parallele Changes im Fenster; Conv-Basis-Wechsel 30.10. im Fenster -> CPA nur DiD-normiert lesbar |
| 109 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Sanitärinstallateur | **NEGATIV** | niedrig | CPA +100% (DiD +110%) | 141 | 2 | manager | 2 parallele Changes im Fenster; CPA instabil (Conv-Nenner <2) |
| 110 | 2025-06-24 | AD | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Sanitärinstallateur | **NEGATIV** | niedrig | CPA +68% (DiD +74%) | 140 | 2 | manager | 2 parallele Changes im Fenster; CPA instabil (Conv-Nenner <2) |
| 111 | 2025-06-23 | BUD | add | campaign: EX | 25 | CH | SEARCH | LEAD | Metallbauer | **NEGATIV** | niedrig | CPA +6369% (DiD +6379%) | 95 | 1 | manager | 1 parallele Changes im Fenster; CPA instabil (Conv-Nenner <2) |
| 112 | 2025-08-06 | STATUS | pause | campaign: EX | 25 | CH | SEARCH | LEAD | Sanitärinstallateur | **POSITIV** | mittel | Pre-CPA 44.8 vs Konto-Ø 16.7 (x2.68) | 63 | 2 | manager | 2 parallele Changes im Fenster |
| 113 | 2025-08-06 | BUD | remove | campaign: EX | 25 | CH | SEARCH | LEAD | Sanitärinstallateur | **UNKLAR** | niedrig | Post-Fenster < 7 Tage | 63 | 2 | manager | 2 parallele Changes im Fenster |

## Methodik
- Fenster **28/28 T** um `change_datetime` (Budget <10k, agent_methodik §1).
- Signifikanz-Gate: **≥20 Klicks ODER ≥2 Conv** im Post-Fenster (§2), sonst UNKLAR.
- Outcome **CPA**, **DiD-normiert** = Kampagnen-CPA-Delta minus Konto-CPA-Delta im selben Fenster (trennt Change-Effekt vom kontoweiten Trend/Saison).
- Material-Schwelle DiD **±10 %**; |DiD|<5 % → niedrig („~Konto-Trend“).
- **CPA-Instabilitäts-Guard:** Cluster mit <2 Conv in einem Fenster → Confidence niedrig (Mini-Nenner-Artefakt).
- **STATUS-Pausen** gesondert: bewertet am Pre-CPA vs. Konto-Ø (teure Kampagne pausiert = POSITIV, effiziente = NEGATIV; Top-Performer-Schutz §3).
- Kampagnen-Matching auf **stabile campaign_id**; 2025-Namen (Jahres-Präfix/Renames) über Trade-Token + `description_full` aufgelöst — **0 unaufgelöste** Referenzen.

