---
kunde: stay-cold
typ: briefing (für Jonas) — v4: Review Jonas 10.07. eingearbeitet (Promo-Fenster/Intraday Scaling; W4 ersetzt, V1/V2 konditioniert)
basis: 5.870 Änderungen (Jul 2024 – Jul 2026) × tägliche API-Performance (Jun 2023 – Jul 2026),
  467 bewertete Cluster; Wirkung = DiD (konto-trend-bereinigt) auf bereinigter Kauf-Serie
scope: KUNDEN-SCOPED
stand: 2026-07-10 (v4)
---

# Stay Cold Google Ads — zwei Jahre Änderungshistorie, mit Belegen

**Lesehilfe:** „DiD" = Wirkung der Kampagne **relativ zum Konto-Trend** im selben
28-Tage-Fenster (Saison/BFCM rausgerechnet). „LB" = Lost-IS-Budget vor der Änderung
(wie budget-limitiert die Kampagne wirklich war). „SaR" = Spend-at-Risk (bewegtes
Medienvolumen im Fenster). Alle ROAS-Werte bereinigt (nur echte Käufe).

## TL;DR

Zwei Jahre, 855 echte Änderungen, netto **±0** aus der Masse (Median-DiD +1 %) — die
Bewegung kam aus **drei strukturellen Entscheidungen**: Verknappung Okt 2024 (bester
Move), BFCM 2025 (sauber, +62 % YoY bereinigt), Skalierung 2026 (über den
Sättigungspunkt: Juni marginal **0,63**). Härteste Einzel-Empirie: **keine einzige
Budget-Erhöhung > +90 % war positiv (0/6 — alle sechs lagen außerhalb von
Promo-Fenstern, der Befund hält also auch nach dem Intraday-Scaling-Review)**;
Senkungen waren 9/17 positiv. Und seit
10.11.2025 zeigt das Konto **~1,5× geschönten ROAS** — Steuerung darauf ist Steuerung
auf Phantom-Umsatz (Juni: angezeigt 7,85, real 5,04).

## 1. Konto-Story in fünf Phasen (bereinigte Kauf-Serie)

| Phase | Zeitraum | Spend/Mon | Clean-ROAS | Kern |
|---|---|---|---|---|
| Baseline | Jul–Sep 2024 | 24–32k € | 5,2–5,6 | breites PMax/Shopping-Setup |
| **Effizienz-Programm** | Okt 2024 | 25k | **8,0** | Budgets runter + tROAS rauf (§2.1) |
| Plateau | Nov 24 – Okt 25 | 16–33k | 9–14 | Disziplin; Bestwerte Aug/Sep 25: 12,8 / 14,2 |
| **BFCM 2025** | Nov 2025 | 34k | **19,4** | +62 % YoY, auch bereinigt echt |
| **Skalierung** | Jan–Jun 2026 | 21k → **62k** | 11,6 → **5,0** | ROAS fällt 6 Monate in Folge (§2.3) |

YoY: H2 25 vs. H2 24 = Spend flach, Kauf-Umsatz **+66 %** (echte Verbesserung).
H1 26 vs. H1 25 = Spend +92 %, Clean-ROAS **−23 %**; marginaler ROAS des
Zusatz-Spends ~5,3 übers Halbjahr, im Juni kippend.

## 2. Die drei strukturellen Entscheidungen

**2.1 — 04.–09.10.2024, das Effizienz-Programm (Confidence hoch).**
FEED ONLY OVER-INDEX: tROAS **360 % → 560 %** (04.10., DiD **+126 %**) und Budget
**175 € → 76 €/Tag** (09.10., DiD **+246 %**). Parallel SCALING BROAD **136 € → 102 €**
(09.10., DiD +31 %). Konto-Clean-ROAS Sep→Okt→Nov: 5,45 → 8,01 → 11,93; der Effekt
hielt (Mär 25: 11,1 vs. Mär 24: 7,05 — nicht Saison). Vorläufer am **16.07.2024**:
SCALING BROAD **330 € → 150 €** (−55 %) → DiD **+45 %**, hoch.
*Warum es wirkte:* Lockere Ziele/Budgets lassen Smart Bidding unrentable
Grenz-Auktionen mitkaufen; Verknappung zwingt es, die schwächsten zuerst aufzugeben.
*Ehrlicher Zusatz:* Selbst dieses Programm hatte Verlierer — die parallelen Cuts auf
PROSPECTING BROAD (130 € → 76 €, DiD −27 %) und USA TESTING (89 € → 76 €, **−38 %,
hoch**) zeigen: auch Verknappung muss selektiv sein, nicht pauschal.

**2.2 — BFCM 2025 (Paket ab 23.11.).** Bereinigt +62 % vs. BFCM 2024, Monats-ROAS
19,4 bei 34k Spend. >100 Änderungen an einem Tag — als Paket wirksam, einzeln bewusst
nicht attribuierbar. Promos sind bei Stay Cold Kern-Taktik (inkl. Intraday
Scaling) und werden als Paket bewertet — Promo vs. Vorjahres-Promo, bereinigt.
Beide BFCMs waren richtige Calls.

**2.3 — Skalierung 2026.** Jan 21k → Jun 62k. Bis ~April vertretbar, dann kippt es
(Akten §4.2, §4.4). Größte Einzelbewegung des Halbjahrs: **29.05.2026, FEED ONLY
PROSPECTING, 450 € → 880 €** (~17.400 € im Fenster) → **DiD −27 %**. Der Rückbau bei
Fokusprodukte am **30.06.2026 (1.600 € → 550 €)** war richtig — die Kampagne stand
bei Wochen-ROAS 0,77.

## 3. Ranking: Die Top-Entscheidungen aus zwei Jahren

**Methode (transparent):** Eine „Entscheidung" = alle Änderungen desselben Tages an
derselben Kampagne (z. B. zählt das USA-Brand-Paket vom 13.03.26 als EINE
Entscheidung, nicht als drei Cluster). Gereiht nach **Impact-Score = SaR × |DiD|**
(≈ relativ bewegte Euro im 28-T-Fenster) — eine Heuristik zur Reihung, beide
Komponenten stehen daneben. Nur Kampagnen-Ebene, nur Confidence mittel/hoch.
**Bewusst NICHT im Ranking:** die Konto-Ebene-Entscheidungen (Conv-Setup-Kette,
NCA-Umstellung, BFCM-Pakete) — vermutlich die größten Hebel überhaupt, aber gegen
den Konto-Trend nicht isolierbar (Regel V8). Ein Ranking, das sie enthielte, wäre
Scheingenauigkeit. **‡ = Entscheidung liegt in einem dokumentierten Promo-Fenster**
(Black Spring 12.–20.03.26): DiD ist konto-trend-bereinigt, Promo-Mix-Effekte sind
aber nicht voll ausschließbar; solche Einträge zählen nicht als Leitplanken-Empirie
(Review Jonas 10.07.26).

### 3.1 Top 10 POSITIV — was das Konto nach vorne gebracht hat

| # | Datum | Kampagne | Entscheidung | DiD | SaR | Conf |
|---|---|---|---|---|---|---|
| P1 | 09.10.2024 | PMax FEED ONLY OVER-INDEX | Budget 175 € → 76 € | **+246 %** | 5.266 € | hoch |
| P2 ‡ | 13.–18.03.2026 | Search USA BRAND | Paket: Budget 100 € → 140 € + Broad raus/Phrase rein + AG-tROAS 10.0 | **+261 %** | 2.966 € | mittel |
| P3 | 04.10.2024 | PMax FEED ONLY OVER-INDEX | tROAS 360 % → 560 % | **+126 %** | 5.327 € | hoch |
| P4 | 16.07.2024 | PMax SCALING BROAD | Budget 330 € → 150 € (−55 %) | +45 % | 9.185 € | hoch |
| P5 | 23.09.2024 | Search SKANDI BRAND | Broad-Keyword „stay cold hoodie" pausiert | **+278 %** | 1.178 € | hoch |
| P6 | 13.01.2026 | Search SKANDI BRAND | Angebots-Asset nach Sale-Phase pausiert | **+396 %** | 800 € | hoch |
| P7 | 23.10.2024 | PMax SCALING BROAD | Tracking-Vorlagen-Umstellung ⚠️ | +84 % | 3.401 € | mittel |
| P8 | 23.01.2026 | Shopping FOKUSPRODUKTE | AG-Restrukturierung (Einkommens-Ausrichtung) + Pause | +29 % | 6.497 € | mittel |
| P9 | 06.03.2026 | Search USA BRAND | Tracking-Vorlagen-Fix | +66 % | 2.795 € | mittel |
| P10 | 11.08.2025 | Shopping FOKUSPRODUKTE | Budget 185 € → 136 € | +29 % | 5.764 € | mittel |

Knapp dahinter: **15.04.2025** OVER-INDEX-Korrektur-Paket (Budget 115 → 66 € +
tROAS 450 → 250 %, **+86 %, hoch**) — inhaltlich einer der wichtigsten Belege (§4.1).

### 3.2 Top 10 NEGATIV — was das Konto Geld gekostet hat

| # | Datum | Kampagne | Entscheidung | DiD | SaR | Conf |
|---|---|---|---|---|---|---|
| N1 | 29.05.2026 | PMax FEED ONLY PROSPECTING | Budget 450 € → 880 € (+96 %) bei LB ≈ 0 % | −27 % | **17.435 €** | mittel |
| N2 | 13.05.2025 | PMax PROSPECTING BROAD | Kampagne pausiert | **−118 %** | 3.048 € | hoch |
| N3 | 23.10.2024 | Shopping FOKUSPRODUKTE | Tracking-Vorlagen-Umstellung (Rollout) | −47 % | 2.804 € | mittel |
| N4 | 23.10.2025 | PMax FEED ONLY PROSPECTING | Budget 90 € → 130 € (8 par. Änderungen) | −31 % | 3.760 € | mittel |
| N5 | 04.04.2025 | PMax FEED ONLY PROSPECTING | Budget 115 € → 280 € (+143 %) | −23 % | 4.865 € | mittel |
| N6 | 17.04.2025 | Shopping FOKUSPRODUKTE | Panik-Rückbau 310 € → 151 € (12 T nach N10) | −22 % | 4.991 € | mittel |
| N7 | 20.02.2025 | Shopping FOKUSPRODUKTE | Negativ-Liste „EXCLUSIONS FOR BRAND" angewendet | −23 % | 4.674 € | mittel |
| N8 | 21.08.2024 | PMax SCALING BROAD | Budget 150 € → 170 € (5 Wo. nach P4) | −22 % | 4.875 € | mittel |
| N9 | 11.10.2025 | PMax SCALING BROAD | Budget 115 € → 350 € (+204 %) bei LB 8,6 % | −18 % | 5.896 € | mittel |
| N10 | 05.04.2025 | Shopping FOKUSPRODUKTE | Budget 175 € → 310 € (+77 %) trotz LB 56 % | −17 % | 6.117 € | mittel |

Knapp dahinter: die zwei negativen Cuts im Okt-24-Programm (§2.1) und der
Auto-Apply-Removal von `[stay cold]` am **21.11.2024** (im BFCM-Fenster, formal
niedrigere Confidence — inhaltlich einer der klarsten Fehler, §4.5).

### 3.3 Aufschlüsselung Top 10 POSITIV

- **P1 · 09.10.24 · OVER-INDEX-Budget-Cut (175 → 76 €).** Teil des
  Effizienz-Programms; die Kampagne kaufte bei lockerem Budget Grenz-Traffic.
  Nach dem Cut: DiD +246 %, und der Konto-ROAS sprang von 5,45 auf 8,01→11,93.
  Der stärkste Einzelbeleg für W1 (Verknappung).
- **P2 · 13.–18.03.26 · USA-Brand-Paket.** Budget 100 → 140 €, Broad „stay cold
  shop" raus / Phrase rein, AG-tROAS 10.0. USA-Brand war mit IS 82,8 % und
  Lost-IS-Rank 15,6 % die unterversorgte Brand-Kampagne — das Paket schloss die
  Lücke: +261 %. Der Auto-Apply-Removal am 18.03. im selben Fenster („+250 %")
  ist Trittbrettfahrer dieses Pakets, nicht eigenständig kausal. Beleg für W6.
- **P3 · 04.10.24 · tROAS 360 → 560 %.** Ziel schärfen = Grenz-Auktionen
  abschneiden. Zusammen mit P1 das Muster-Paket; danach ≥14 T Ruhe (W1+V2).
- **P4 · 16.07.24 · SCALING BROAD −55 % Budget.** Der früheste Verknappungs-Beweis,
  größtes bewegtes Volumen der Positiv-Liste (9.185 €). Wurde 5 Wochen später
  durch N8 teilweise wieder verspielt.
- **P5 · 23.09.24 · Broad-Keyword-Pause in SKANDI-Brand.** „stay cold hoodie"
  (Broad!) streute in generische Auktionen; Pause → +278 %. Broad hat in
  Brand-Kampagnen nichts verloren — Vorlage für die Keyword-Regel in V4.
- **P6 · 13.01.26 · SKANDI Angebots-Asset pausiert.** Abgelaufene Sale-Assets nach
  der Saison abräumen: +396 %. Aber Achtung: dieselbe Aktion am selben Tag war bei
  USA −32 % (N-Bereich) — Markt-für-Markt statt Batch (V9).
- **P7 · 23.10.24 · Tracking-Umstellung SCALING BROAD.** ⚠️ Einzelner Gewinner
  eines Rollouts, der netto negativ war (7/11 Cluster negativ, N3). Steht hier der
  Ehrlichkeit halber — Score-Ranking kennt keinen Kontext; als Vorbild taugt der
  Rollout nicht.
- **P8 · 23.01.26 · Fokusprodukte-Restrukturierung.** Einkommens-Ausrichtungs-Umbau
  samt AG-Pause bei LB ≈ 0: +29 % auf 6.497 € — der letzte klar positive Eingriff
  vor der Sättigungsphase. Struktur schlug Budget.
- **P9 · 06.03.26 · USA-Brand-Tracking-Fix.** Aufräumen der tw_source-Vorlagen:
  +66 %; am selben Tag auch auf zwei weiteren Brands positiv (+25/+17 %).
  Gegenstück zum chaotischen 23.10.24-Rollout: gezielt statt flächig.
- **P10 · 11.08.25 · Fokusprodukte-Budget-Cut (185 → 136 €).** Verknappung
  funktionierte auch hier (+29 % bei 5.764 €) — drei Monate bevor die
  Skalierungswelle das Gegenteil versuchte.

### 3.4 Aufschlüsselung Top 10 NEGATIV

- **N1 · 29.05.26 · PROSPECTING +96 % Budget bei LB ≈ 0.** Die teuerste
  Einzelentscheidung des Halbjahrs (17.435 € bewegt): kein Budget-Limit vorhanden
  → der Zukauf war Rank-Traffic. −27 % gegen den Konto-Trend. Verstoß gegen V1+V3
  gleichzeitig.
- **N2 · 13.05.25 · PROSPECTING BROAD pausiert.** Härtestes Negativ-Verdikt (−118 %,
  hoch): die Pause beendete profitables Prospecting-Volumen mitten im Plateau —
  das Konto verlor den Beitrag ersatzlos. Pausen brauchen dieselbe Evidenz wie
  Erhöhungen.
- **N3 · 23.10.24 · Tracking-Rollout (Fokusprodukte-Teil).** Konto-weiter
  Vorlagen-Umbau an einem Tag (Client-Login, vermutlich Tracify-Migration): auf dem
  größten Spender −47 %. Teil-Effekt ist Mess- statt Auktionsschaden — trotzdem:
  Rollouts gestaffelt (V9), sonst ist nicht mal unterscheidbar, was kaputt ging.
- **N4 · 23.10.25 · PROSPECTING 90 → 130 €.** +44 % wäre okay gewesen (vgl.
  23.01.25: +43 % DiD!) — aber inmitten von 8 parallelen Änderungen: −31 %.
  Gleicher Schritt, anderes Umfeld, anderes Ergebnis → Ruhefenster (V1) sind kein
  Formalismus.
- **N5 · 04.04.25 · PROSPECTING 115 → 280 € (+143 %).** Der klassische Über-Push:
  Lernphasen-Reset + Grenz-Traffic → −23 %. Vgl. P-Seite: am selben Tag bekam
  OVER-INDEX +400 % Budget — verpuffte (DiD −1 %). Große Sprünge liefern
  bestenfalls nichts.
- **N6 · 17.04.25 · Fokusprodukte-Rückbau 310 → 151 €.** Die Panik-Korrektur von
  N10 nur 12 Tage später — auch negativ (−22 %). Whipsaw kostet in BEIDE
  Richtungen, weil das Bidding zweimal neu kalibriert.
- **N7 · 20.02.25 · „EXCLUSIONS FOR BRAND" auf Fokusprodukte.** Brand-Käufe aus der
  Shopping-Kampagne gedrängt: −23 % im Kampagnen-ROAS. Strukturell vertretbar
  (Brand-Traffic gehört in Brand-Kampagnen) — aber als Batch ohne Messplan
  eingeführt; auf FRA-Brand am 23.01. kostete dieselbe Liste −32 % (V9).
- **N8 · 21.08.24 · SCALING BROAD 150 → 170 €.** Fünf Wochen nach dem
  Verknappungs-Erfolg P4 wurde wieder aufgedreht — moderat, aber gegen die frische
  Evidenz: −22 %. Erkenntnisse müssen Regeln werden, sonst verfallen sie.
- **N9 · 11.10.25 · SCALING BROAD 115 → 350 € (+204 %).** Ein Jahr nach P4/P1
  exakt der Fehler, den das Okt-24-Programm korrigiert hatte — bei LB 8,6 %.
  −18 %. Der stärkste Beleg, dass ohne festgeschriebene Regeln dieselben Fehler
  zyklisch wiederkehren.
- **N10 · 05.04.25 · Fokusprodukte 175 → 310 € (+77 %) bei LB 56 %.** Der
  wichtigste Lehrsatz-Fall: ECHTES Budget-Limit vorhanden — und der Sprung war
  trotzdem zu groß. Headroom ist notwendige, nicht hinreichende Bedingung (W2);
  die Schrittgröße (V1) gilt immer.

## 4. Kampagnen-Akten (Detail je Kampagne)

### 4.1 EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX — der Beweis für Verknappung

| Datum | Änderung (alt → neu) | Wirkung (DiD) | Conf | Lesart |
|---|---|---|---|---|
| 04.10.24 | tROAS 360 % → 560 % | **+126 %** | hoch | Ziel schärfen = Grenz-Traffic abschneiden |
| 09.10.24 | Budget 175 € → 76 € | **+246 %** | hoch | Verknappung, Teil 2 |
| 11.11./19.11.24 | tROAS 560→300→450 | unbewertbar | — | BFCM-Fenster, Ziel-Thrash |
| 04.04.25 | Budget 23 € → 115 € (**+400 %**) | −1 % (neutral) | mittel | Riesen-Push verpuffte |
| 15.04.25 | Budget 115 € → 66 € **+** tROAS 450 % → 250 % | **+86 %** | hoch | Korrektur-Paket — danach ≥14 T Ruhe |
| 14.07.25 | Budget 66 € → 95 € (+44 %) | +58 % | mittel | *moderater* Schritt in gutem Fenster funktionierte |

**Fazit:** Beide hoch-Confidence-Erfolge waren Verknappungs-/Korrektur-Pakete mit
Ruhe danach. Der +400-%-Sprung brachte nichts, der moderate +44-%-Schritt schon.

### 4.2 EX I SHOPPING I FOKUSPRODUKTE — die Sättigungs-Akte (39 % des H1-26-Spends)

| Datum | Änderung | LB vorher | Wirkung (DiD) | Conf | Lesart |
|---|---|---|---|---|---|
| 08.07.24 | Umbau zu „FOKUSPRODUKTE" + AG-Pause | 0 % | **+60 %** | hoch | Fokussierung wirkte |
| 16.07.24 | pausierte AG wieder aktiviert | 0 % | **−43 %** | hoch | Rück-Verbreiterung kostete sofort |
| 20.02.25 | Negativ-Liste „EXCLUSIONS FOR BRAND" | 51 % | −23 % | mittel | Brand-Käufe rausgedrängt (N7) |
| 04.+10.03.25 | Budget 160 → 131 → 86 € | 34/33 % | +14 % / **+17 %** | mittel | Senkung positiv trotz Budget-Limit |
| 05.04.25 | Budget 175 € → 310 € (+77 %) | **56 %** | **−17 %** | mittel | **Headroom ≠ Freibrief** (N10) |
| 17.04.25 | Panik-Rückbau 310 € → 151 € | 31 % | −22 % | mittel | Whipsaw: rauf UND runter negativ (N6) |
| 11.08.25 | Budget 185 € → 136 € | 12 % | +29 % | mittel | Verknappung, wieder (P10) |
| 18.09.25 | Suchnetzwerk-Partner deaktiviert | 64 % | +17 % | mittel | Qualität vor Reichweite |
| 23.01.26 | AG-Restrukturierung + Pause | 0 % | **+29 %** | mittel | letzter klar positiver Eingriff (P8) |
| 29.05.26 | Budget 650 € → 1.000 € | ~0 % | −8 % (unreif) | niedrig | Sättigungszone |
| 19.06.26 | Budget 1.000 € → 1.600 € | ~0 % | (unreif) | niedrig | Wochen-ROAS 1,5–1,8, **marginal 0,63** |
| 30.06.26 | Budget 1.600 → 751 → 550 € | 0 % | offen | — | richtiger Rückbau (bei 0,77) |

**Fazit:** Feb–Apr 26 trug die Skalierung in Stufen (LB 52–67 %) — aber selbst dort
scheiterte der einzelne +77-%-Sprung. Ab Mai LB ≈ 0 → jeder weitere Euro kaufte
Rank-Traffic. Beide Hälften der Budget-Regel in einer Kampagne bewiesen.

### 4.3 EX I WW I PMAX I SCALING I BROAD — Lektion gelernt, Lektion vergessen

16.07.24: 330 € → 150 € → **+45 % (hoch, P4)** · 21.08.24: 150 → 170 € → −22 % (N8) ·
09.10.24: 136 → 102 € → **+31 % (hoch)** · **11.10.25: 115 € → 350 € (+204 %) bei
LB 8,6 % → −18 % (N9).** Ein Jahr nach dem Verknappungs-Beweis wiederholte die
Steuerung exakt den Fehler, den sie 2024 korrigiert hatte.

### 4.4 EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING — Schrittgröße entscheidet

| Datum | Schritt | Wirkung (DiD) |
|---|---|---|
| 23.01.25 | 66 → 95 € (**+44 %**) | **+43 % POSITIV (hoch)** |
| 04.04.25 | 115 → 280 € (**+143 %**) | **−23 % NEGATIV** (N5) |
| 14.07.25 | 76 → 125 € (+64 %) | −21 % NEGATIV |
| 20.07.25 | 125 → 90 € (6 Tage später!) | +27 % POSITIV |
| 23.10.25 | 90 → 130 € (8 par. Änderungen) | −31 % NEGATIV (N4) |
| 29.05.26 | **450 → 880 €** | **−27 % NEGATIV** (N1, größter SaR des H1) |

Dieselbe Kampagne: moderater Schritt positiv, jeder große Sprung negativ, Whipsaw
im 6-Tage-Abstand sichtbar.

### 4.5 Brand-Kampagnen (DE/FRA/USA/SKANDI) — hebelstark in beide Richtungen

| Datum | Änderung | Wirkung (DiD) | Conf | Lesart |
|---|---|---|---|---|
| 23.09.24 | Broad „stay cold hoodie" pausiert (SKANDI) | **+278 %** | hoch | Broad in Brand = Streuverlust (P5) |
| 21.11.24 | **Auto-Apply entfernt `[stay cold]` Exact (DE)** | negativ | — | Google schnitt am Kern-Keyword, 2 T vor BFCM-Woche |
| 25.11.24 | system_bulk pausiert „stay cold accessoires" + Asset | −35 % / −105 % | mittel | Automatik mitten im BFCM-Fenster |
| 23.01.25 | Negativ-Liste auf alle Brands | **FRA −32 % (hoch)**, 2 Märkte +30/+24 % | gemischt | Pauschal-Rollout wirkt je Markt gegensätzlich |
| 13.01.26 | Angebots-Assets pausiert (nach Sale) | USA **−32 % (hoch)** · −19 % · SKANDI **+396 % (hoch)** | gemischt | dieselbe Aktion, drei Märkte, drei Ergebnisse |
| 06.03.26 | Tracking-Vorlagen-Fix (3 Brands) | +66 / +25 / +17 % | mittel | gezieltes Aufräumen zahlte ein (P9) |
| 13.03.26 | **USA-Paket:** Budget 100 → 140 € + Broad raus/Phrase rein + AG-tROAS 10.0 | **+261 %** | mittel | unterversorgte Kampagne versorgt (P2) |
| 18.03.26 | Auto-Apply entfernt `[stay cold]` Exact (USA) | „+250 %" | mittel | ⚠️ Trittbrettfahrer des 13.03.-Pakets |

**Fazit:** Brand = 7 % Spend, ~64 % des getrackten Kauf-Werts (FRA 64,2 · DE 63,0 ·
USA 58,0 · SKANDI 24,2). Kleinste Eingriffe, größte Ausschläge — in beide
Richtungen. DO NOT TOUCH per Default; Änderungen einzeln, je Markt.

### 4.6 BS DEALS (Demand Gen) — Intraday Scaling im Black Spring Sale (Reframe nach Jonas-Review)

13.–18.03.26, komplett im dokumentierten Promo-Fenster: Gebotswechsel Ziel-ROAS →
Ziel-CPA, Budget 350 → 2.450 € in drei Tagen, dann gestaffelter Rückbau und Pause.
**Jonas' Review stellt klar: Das war bewusstes Intraday Scaling, keine Panik.**
Konsequenz für die Methodik: 28-T-Einzel-Verdikte sind für Intraday-Taktik das
falsche Messinstrument — die Tages-Verdikte dieses Fensters (−35 % bis +32 %) sind
aus der Leitplanken-Empirie gestrichen. Bewertbar ist so ein Fenster nur als
**Paket** (Promo vs. Vorjahres-Promo, bereinigte Serie) oder mit Tages-/Stunden-
Granularität, die dieser Agent nicht hat. Die Kampagne selbst: H1-Clean-ROAS 5,78 —
gesund.

### 4.7 „Video View DRAFT" — der stille Verlust

**27.04.–24.05.2026**, Peak 1.869 €/Woche: **4.750 € für 2 Käufe (ROAS 0,04)**.
Kein Änderungs-Eintrag matcht die Erstellung — vermutlich versehentlich live
gegangener Test. Vier Wochen unbemerkt = Prozess-Lücke (kein Alarm), kein
Analyse-Fehler.

### 4.8 Tracking-Vorlagen-Rollout 23.10.2024 — die „Kunden-Eingriff"-Geschichte, präzisiert

Der Median −22 % der Client-Eingriffe stammt fast vollständig aus **einem** Tag:
Konto-weite Tracking-Vorlagen-Umstellung (Client-Login, vermutlich
Tracify-Migration) — **11 signifikante Cluster: 7 negativ (bis −47 %, 2× hoch),
2 neutral, 2 positiv.** Korrektur zur früheren Fassung: Die BS-DEALS-Steuerung
(§4.6) lief laut Log über die Agentur, nicht den Kunden. Lehre: nicht „der Kunde
schadet", sondern „unkoordinierte Konto-weite Rollouts schaden — egal von wem".
(Teil der Deltas ist Mess- statt Auktionseffekt; genau deshalb V9.)

## 5. Die Messfalle: drei Conversion-Zähl-Regime

| Regime | Zeitraum | Problem |
|---|---|---|
| 1 | Aug 2023 – Apr 2024 | GA4 **und** Shopping-App parallel — Käufe doppelt (Feb 24: 410 + 435 ≈ dieselben) |
| 2 | Mai 2024 – Sep 2025 | **sauber** — nur `purchase_gads_mable` (Anker-Fenster) |
| 3 | seit 10.11.2025 | + NewCustomerPurchase → berichteter ROAS **~1,5× überzeichnet** (Dez 1,57× … Jun 1,56×) |

Kette: 10.11.25 Restrukturierung → **23.11.25** NCP ins Bidding-Goal (2 Tage vor
BFCM) → 11.12.25 zurück auf sekundär → **18.02.26** NCA („nur Neukunden bieten" +
16,46 € Zusatzwert) → **13.03.26** kampagnenspezifisch wieder rein, bis heute.
Strategisch vertretbar — aber: Konto zeigt 7,85 (Jun), real 5,04; tROAS-Ziele
wirken seit 18.02. lockerer als beziffert. **Reporting auf die bereinigte
Kauf-Serie umstellen, sonst diskutiert ihr Phantom-Umsatz.**

## 6. Regelwerk für den automatisierten Agent — mit Begründung

Jede Regel: **Mechanismus** (warum sie gilt) → **Empirie** (womit belegt) →
**Preis des Verstoßes**. Alle Werte aus DIESEM Konto → Stay-Cold-Customer-Rules,
nicht generisches Brain (dafür fehlt das zweite E-Com-Konto).

### Weiter so

**W1 · Verknappung als Effizienz-Hebel.** Kampagne unter Ziel → Budget −20–40 %
UND/ODER tROAS anheben, danach 14 T Ruhe.
*Mechanismus:* Smart Bidding kauft bei lockerem Ziel/Budget Grenz-Auktionen mit;
Verknappung zwingt es, die schwächsten zuerst abzugeben. *Empirie:* P1, P3, P4,
P10, 15.04.25 — sämtliche hoch-Confidence-Gewinne sind Verknappungs-/
Korrektur-Pakete. *Grenze:* selektiv anwenden — die 09.10.24-Cuts auf PROSPECTING
BROAD/USA TESTING waren negativ (§2.1).

**W2 · Budget rauf nur bei echtem Budget-Limit — und auch dann nur in Stufen.**
Notwendig: Lost-IS-Budget ≥ ~20 % (Search/Shopping); PMax ohne Lost-IS: marginaler
Clean-ROAS der letzten Stufe ≥ 0,8× Kampagnen-Ø. **Nicht hinreichend:** Schrittgröße
bleibt gedeckelt (V1). *Mechanismus:* ohne Limit hebt Mehr-Budget nur den
Grenzpreis (Rank-Traffic); mit Limit erschließt es Nachfrage — solange das Bidding
die Stufe verdauen kann. *Empirie:* Fokusprodukte Feb–Mär 26 trug (LB 52–67 %,
stufenweise); **N10: +77 % bei LB 56 % trotzdem −17 %**; N1: LB ≈ 0 → marginal 0,63.
*Preis:* fünfstellig allein im Juni 26.

**W3 · Sättigungs-Rückbau sofort, wenn W2 kippt.** *Mechanismus:* jede Woche
Verzögerung kauft 0,6-€-Umsatz für 1 €. *Empirie:* 30.06.26 Cut bei Wochen-ROAS
0,77 — richtig, ~4 Wochen zu spät.

**W4 · Promo-Kalender führen; im Promo-Fenster ist Intraday Scaling legitime
Taktik** *(ersetzt die alte „BFCM-Ausnahmepaket"-Regel — Review Jonas 10.07.26).*
*Mechanismus:* Sales sind bei Stay Cold Kern-Taktik inkl. schneller, großer
Budget-/Gebots-Moves; innerhalb dokumentierter Fenster sind V1/V2 ausgesetzt,
außerhalb gelten sie strikt. Bewertung von Promos nur als Paket (Promo vs.
Vorjahres-Promo, bereinigt). *Empirie:* Die Hälfte aller Budget-Schritte der zwei
Jahre (94/189) lag in Promo-Fenstern — sie als Einzelfehler zu werten war der
größte Fehler der ersten Analysefassung. BFCM 2025 als Paket: +62 % YoY bereinigt.
*Infrastruktur:* `promo_windows.csv` (Seed: BFCM 24/25, Black Spring 26 — Jonas
verifiziert/ergänzt).

**W5 · Bewertung nur konto-trend-bereinigt (DiD) auf bereinigter Kauf-Serie,
28-T-Fenster.** *Mechanismus:* sonst bewertet der Agent Saison, Zähl-Regime (§5)
oder Konto-Trend — nicht die Änderung. *Empirie:* Nov/Dez 25 sähe im berichteten
ROAS wie ein Steuerungserfolg aus; real: NCP-Doppelzählung + Saison.

**W6 · Brand-Pflege Richtung 95–99 % IS über Gebot/QS (v.a. USA).** *Mechanismus:*
Brand-Lücke ist Rank-bedingt (USA: IS 82,8 %, Lost-IS-Rank 15,6 %) — Gebot/Relevanz
löst das, Budget nicht; billigster Traffic im Konto. *Empirie:* P2 (+261 %).
*Caveat:* Brand erntet kaufbereite Nachfrage — Inkrement ≠ +261 % für immer.

### Nie wieder

**V1 · Budget-Schritte > ±30 % oder < 7 T Abstand je Kampagne — NUR außerhalb
dokumentierter Promo-Fenster** *(Konditionierung nach Jonas-Review: in Sales ist
Intraday Scaling erlaubt).* *Mechanismus:* jeder Sprung resettet die Lernphase;
das Bidding kalibriert auf ein Spend-Niveau. *Empirie (ohne Promo-Fenster
gerechnet):* **Erhöhungen > +90 %: 0 positiv / 4 negativ / 2 neutral — alle sechs
außerhalb von Promos** (N5 +143 % → −23 %; N9 +204 % → −18 %; N1 +96 % → −27 %;
+400 % → ±0); moderate Schritte ≤ +44 % mehrfach positiv (23.01.25 +43 %,
14.07.25 +58 %). Frequenz außerhalb Promos: 78 % der 95 Schritte > ±30 %,
28 % < 7 T → Netto ≈ 0. *Preis:* Nicht-Promo-Budget-Arbeit ohne messbaren Ertrag.

**V2 · tROAS-Ziel-Änderung < 14 T nach letzter Änderung derselben Kampagne —
außerhalb von Promo-Fenstern.**
*Mechanismus:* das Ziel ist der stärkste Bidding-Input; ohne Ruhe weder Lernen
noch Messen. *Empirie:* OVER-INDEX-Thrash Nov 24 (560→300→450, unbewertbar); die
zwei hoch-Confidence-Erfolge hatten ≥14 T Ruhe. *Preis:* unbewertbare Monate.

**V3 · Budget-Erhöhung bei Lost-IS-Budget < 5 %.** *Mechanismus:* die Kampagne
gewinnt bereits jede Auktion, die sie will — mehr Geld hebt nur den Grenzpreis.
*Empirie:* N1 (marginal 0,63), N9 (LB 8,6 % → −18 %). *Preis:* im Juni real
~37 Cent Fehlbetrag je zusätzlichem Euro — vor Marge.

**V4 · Brand-Kampagnen anfassen** (Clean-ROAS ≥ 7,7 = 1,25× Konto-Ø UND ≥ 3 Käufe
→ DO NOT TOUCH; Gebote nur nach oben; kein Broad in Brand). *Mechanismus:* höchste
Wertdichte — kleinste Eingriffe, größte Ausschläge (§4.5: −32 % bis +396 % aus
ähnlichen Aktionen). *Empirie:* 21.11.24, 23.01.25 FRA −32 %, 13.01.26 USA −32 %;
Gegenrichtung P5/P6. *Preis:* Eingriffe an ~64 % des Kauf-Werts ohne Not.

**V5 · Keyword-/Asset-Auto-Apply aktiv lassen.** *Mechanismus:* Google optimiert
ohne Konto-Kontext — und traf hier 8/8-mal Brand. *Empirie:* ~38 % Trefferquote;
21.11.24 Kern-Keyword entfernt, 2 Tage vor der BFCM-Woche. *Preis:* unkontrollierte
Eingriffe am wertvollsten Asset zur wichtigsten Zeit.

**V6 · > 1.000 € kumuliert ohne Kauf weiterlaufen lassen.** *Mechanismus:* Fehler
passieren — teuer wird, was unbemerkt bleibt. *Empirie:* §4.7 (4.750 €/2 Käufe).
*Preis:* exakt beziffert.

**V7 · Berichteten Konto-ROAS als Entscheidungsgrundlage nutzen.** *Mechanismus:*
seit 10.11.25 misst er eine andere Größe; Inflation konstant 1,49–1,57×.
*Empirie:* §5. *Preis:* jede Entscheidung seit Dez 25 rechnete mit ~50 %
Phantom-Umsatz; tROAS-Ziele faktisch lockerer als beschlossen.

**V8 · Konto-Ebene-Änderungen autonom bewerten oder ausführen** (Conv-Setup, NCA,
Zugriffe, Vorlagen-Rollouts → immer MANUELL/Mensch). *Mechanismus:* größte
Spend-Bewegungen, gegen den Konto-Trend nicht isolierbar — erzwungene Verdikte
wären halluzinierte Kausalität; deshalb fehlen sie auch im Ranking (§3).
*Empirie:* 45 MANUELL-Cluster (Conv-Kette §5, Rollout §4.8).

**V9 · Pauschal-Rollouts über alle Märkte/Kampagnen in einem Schritt.**
*Mechanismus:* dieselbe Änderung wirkt je Markt gegensätzlich; ein Batch macht
Wirkung unmessbar und Fehler flächig. *Empirie:* 23.01.25 (FRA −32 % vs. +24/+30 %),
13.01.26 (USA −32 % vs. SKANDI +396 %), 23.10.24 (7/11 negativ). *Regel:* pro
Markt einzeln, 1–2 Wochen versetzt.

## 7. Was wir ehrlich nicht wissen

1. **Marge & Retouren** — Non-Brand-Clean-ROAS 90 T = 2,40; ob das über Break-even
   liegt, weiß nur die DB1-Rechnung. Wichtigste offene Zahl.
2. **PMax-Innenleben** — Asset-Gruppen-Analyse steht aus (Daten liegen vor).
3. **BFCM-Muster: n=2** Saisons, zwei Zähl-Regime.
4. **DiD misst relativ zum Konto** — bei kontoweiten Events (Tracking-Rollout) sind
   Teile des Deltas Mess- statt Auktionseffekt. Deshalb Confidence-Stufen, und
   deshalb ist der Impact-Score eine Reihungs-Heuristik, kein Euro-Betrag.

## 8. Nächste Schritte

1. Reporting auf **Clean-ROAS** umstellen (nur `purchase_gads_mable`).
2. **Margen-/Retourendaten** → Ziel-ROAS/POAS je Kampagnen-Typ statt Bauchgefühl.
3. Regelwerk §6 mit Jonas abstimmen → als Stay-Cold-Customer-Rules festschreiben.
4. Forward-Capture läuft täglich (VPS-Cron) — nie wieder UI-Export-Archäologie.
5. PMax-Asset-Gruppen-Analyse als nächster Block.

---
*Methodik: Cluster = Datum × Kampagne × Kategorie; Entscheidungen (§3) = Cluster
desselben Tags & derselben Kampagne zusammengefasst; Pre/Post 28/28 T; Wirkung =
DiD gegen Konto-Trend auf bereinigter Kauf-Serie; Signifikanz ≥ 20 Klicks oder
≥ 2 Käufe; Confidence „hoch" nur bei |DiD| ≥ 30 %, ≤ 3 parallelen Änderungen, kein
Regime-Bruch im Fenster (8/467). Impact-Score = SaR × |DiD| — Reihungs-Heuristik. Promo-Fenster (BFCM 24/25,
Black Spring 26, `promo_windows.csv`) sind aus der Leitplanken-Empirie
ausgeschlossen: dort ist Intraday Scaling bewusste Taktik (Review Jonas 10.07.26).
Quellen: `reports/impact_staycold.md`, `change_impact_staycold.csv`,
`data/.../history_facts.md`.*
