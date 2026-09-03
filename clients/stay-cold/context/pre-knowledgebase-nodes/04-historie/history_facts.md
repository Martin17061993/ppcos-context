---
kunde: staycold
typ: history-facts (GENERIERT — nicht von Hand editieren)
generator: build_history_context.py v1.0
quelle_dateien: 1 perf + 0 changes + 1 impact
stand: 2026-07-14
scope: KUNDEN-SCOPED — bleibt in data/<kunde>/ (gitignored)
---

# staycold — Historische Faktenbasis (deterministisch)

> Jede Zahl hier ist aus den Roh-CSVs nachrechenbar. Der Context-Pack (`customer/.../history.md`) darf nur Zahlen zitieren, die hier stehen oder in einem versionierten Report hergeleitet sind.

## 1. Datenabdeckung (ehrlich)

- Performance täglich: **2023-06-05 → 2026-07-03**
- keine Lücken > 3 Tage
- Änderungs-Historie normalisiert: 0 Änderungen aus 0 Datei(en)
- 37-Monats-Fenster der API rollt monatlich — älteste Monate verschwinden; Backfill-Stand oben ist der gesicherte Bestand.

## 2. KPI-Pivots / Messbrüche (Pflicht-Kontext für JEDE Zahl)

| Datum | Typ | Was | Konsequenz |
|---|---|---|---|
| 2023-08-01 | doppelzaehlung | Regime 1: 'GA4 (bereinigt)' + 'Google Shopping App Purchase' parallel primär (bis Apr 2024) — Käufe doppelt gezählt (z.B. Feb 2024: 410+435 ≈ dieselben Käufe) | Aug 2023–Apr 2024 berichtete Conv/Werte nie absolut verwenden; nur bereinigt/relativ |
| 2024-05-01 | regime-wechsel | Regime 2 beginnt: nur noch purchase_gads_mable zählt — einzige saubere Rohserie (Mai 2024 – Sep 2025) | Baseline-/YoY-Anker aus diesem Fenster nehmen |
| 2025-11-10 | conv-definition | Regime 3 beginnt: purchase_gads_mable 'Primär' + Conv-Restrukturierung (CheckoutStarted → OLD); ab jetzt Doppelzählungs-Kette | ab hier berichteten ROAS nur noch mit Inflations-Faktor lesen |
| 2025-11-23 | conv-definition | Conversion-Goal 'Käufe' → 'Käufe + New Customers' (NewCustomerPurchase ins Bidding-Goal, 2 Tage vor BFCM) | BFCM-2025-Zahlen im Konto überzeichnet; nur bereinigte Serie für YoY |
| 2025-12-11 | conv-definition | NewCustomerPurchase auf 'Sekundär (nur beobachten)' zurückgestellt | kurzes Zwischenfenster — Zählung uneinheitlich |
| 2026-02-18 | bidding-setup | NCA-Setup Konto-Ebene: 'nur für Neukunden bieten' an + 16,46 € Zusatz-Conversion-Wert je Neukunde | strategisch gewollt; tROAS-Ziele wirken seit dem faktisch lockerer als beziffert |
| 2026-03-13 | conv-definition | Kampagnen-Zielvorhaben 'Käufe + New Customers' — NewCustomerPurchase zählt bis heute in conversions/conversions_value (Faktor ~1,5× seit Dez 2025) | berichteter Konto-ROAS dauerhaft ~1,5× überzeichnet; Entscheidungen NUR auf Clean-ROAS (purchase-only) oder DiD |

## 2b. Promo-/Sale-Fenster (Intraday Scaling = bewusste Taktik)

| Von | Bis | Promo | verifiziert |
|---|---|---|---|
| 2024-11-20 | 2024-12-02 | BFCM 2024 | nein |
| 2025-11-20 | 2025-12-01 | BFCM 2025 | nein |
| 2026-03-12 | 2026-03-20 | Black Spring Sale 2026 | nein |

Innerhalb dieser Fenster sind schnelle/grosse Budget- und Gebotsänderungen bewusstes Intraday Scaling. Einzel-Verdikte mit 28-T-Fenstern sind dort NICHT belastbar und aus §6 ausgeschlossen; Promos werden als Paket bewertet (Promo vs. Vorjahres-Promo, bereinigte Serie).

## 3. Monats-Zeitreihe Konto (ROAS-Sicht)

| Monat | Spend | ROAS berichtet | ROAS bereinigt (nur Kauf) | Inflations-Faktor | Käufe | Tage |
|---|---|---|---|---|---|---|
| 2023-06 | 9'224 | 6.62 | – | – | 0.0 | 26 |
| 2023-07 | 14'520 | 7.24 | – | – | 0.0 | 31 |
| 2023-08 † | 18'330 | 5.02 | – | – | 0.0 | 31 |
| 2023-09 | 19'382 | 5.53 | – | – | 0.0 | 30 |
| 2023-10 | 18'088 | 6.01 | – | – | 0.0 | 31 |
| 2023-11 | 22'337 | 6.47 | – | – | 0.0 | 30 |
| 2023-12 | 19'518 | 6.88 | – | – | 0.0 | 31 |
| 2024-01 | 14'266 | 8.33 | – | – | 0.0 | 31 |
| 2024-02 | 17'543 | 6.36 | – | – | 0.0 | 29 |
| 2024-03 | 14'734 | 7.05 | – | – | 0.0 | 31 |
| 2024-04 | 15'173 | 6.76 | – | – | 0.0 | 30 |
| 2024-05 † | 23'501 | 7.14 | 6.89 | 1.04× | 1353.5 | 31 |
| 2024-06 | 30'643 | 5.57 | 5.57 | 1.00× | 1402.2 | 30 |
| 2024-07 | 29'105 | 5.22 | 5.22 | 1.00× | 1208.6 | 31 |
| 2024-08 | 24'179 | 5.62 | 5.62 | 1.00× | 1094.5 | 31 |
| 2024-09 | 31'993 | 5.45 | 5.45 | 1.00× | 1326.6 | 30 |
| 2024-10 | 25'012 | 8.01 | 8.01 | 1.00× | 1383.5 | 31 |
| 2024-11 ‡ | 26'179 | 11.93 | 11.93 | 1.00× | 2456.1 | 30 |
| 2024-12 ‡ | 21'711 | 10.73 | 10.73 | 1.00× | 1652.4 | 31 |
| 2025-01 | 21'073 | 9.90 | 9.90 | 1.00× | 1377.4 | 31 |
| 2025-02 | 21'399 | 10.14 | 10.14 | 1.00× | 1417.8 | 28 |
| 2025-03 | 19'043 | 11.10 | 11.10 | 1.00× | 1356.0 | 31 |
| 2025-04 | 32'968 | 9.02 | 9.02 | 1.00× | 1758.4 | 30 |
| 2025-05 | 19'792 | 10.22 | 10.22 | 1.00× | 1628.6 | 31 |
| 2025-06 | 15'680 | 11.05 | 11.05 | 1.00× | 1497.5 | 30 |
| 2025-07 | 24'147 | 9.74 | 9.74 | 1.00× | 2509.9 | 31 |
| 2025-08 | 19'739 | 12.78 | 12.78 | 1.00× | 1854.2 | 31 |
| 2025-09 | 20'164 | 14.24 | 14.24 | 1.00× | 1927.6 | 30 |
| 2025-10 | 26'367 | 10.51 | 10.42 | 1.01× | 1830.9 | 31 |
| 2025-11 † ‡ | 33'877 | 24.85 | 19.38 | 1.28× | 7535.7 | 30 |
| 2025-12 † ‡ | 27'690 | 16.80 | 10.68 | 1.57× | 1986.3 | 31 |
| 2026-01 | 20'952 | 17.79 | 11.63 | 1.53× | 1558.7 | 31 |
| 2026-02 † | 29'256 | 16.63 | 10.84 | 1.53× | 1946.1 | 28 |
| 2026-03 † ‡ | 48'297 | 13.51 | 9.05 | 1.49× | 4553.6 | 31 |
| 2026-04 | 40'915 | 11.79 | 7.62 | 1.55× | 1756.2 | 30 |
| 2026-05 | 48'127 | 10.02 | 6.67 | 1.50× | 2246.0 | 31 |
| 2026-06 | 61'961 | 7.85 | 5.04 | 1.56× | 2272.9 | 30 |
| 2026-07 \* | 4'558 | 7.66 | 4.55 | 1.68× | 144.7 | 3 |

† = Monat enthält KPI-Pivot (§2) — Zahlen über den Bruch hinweg nicht absolut vergleichen. ‡ = Monat enthält Promo-/Sale-Fenster (§2b) — Spend-/ROAS-Spitzen sind Taktik, kein Trend. \* = Monat unvollständig abgedeckt (< 25 Tage Daten) — nicht als Monatswert zitieren.

'ROAS bereinigt' = nur echte Käufe (purchase-only-Serie) / Cost. Der Inflations-Faktor zeigt, wie stark der berichtete ROAS durch Doppelzählung (§2-Pivots) überzeichnet ist.

## 4. Kampagnen-Register (Top 12 von 35 nach Spend)

| Kampagne (alle Namen) | Spend | Anteil | Conv | Clean-ROAS | aktiv | Tage |
|---|---|---|---|---|---|---|
| EX I SHOPPING I FOKUSPRODUKTE | 165'851 | 18% | 4999.0 | 3.29 | 2023-11-28→2026-07-03 | 893 |
| EX I WW I PMAX I SCALING I BROAD | 156'124 | 17% | 8810.6 | 4.95 | 2023-06-05→2025-11-28 | 908 |
| EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | 144'988 | 16% | 4887.4 | 3.43 | 2024-03-26→2026-07-03 | 830 |
| EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX + NEAR-INDEX | 79'335 | 8% | 2348.7 | 3.22 | 2023-07-14→2026-07-03 | 975 |
| EX I USA I PMAX I TESTING I BROAD | 52'010 | 6% | 1253.1 | 3.57 | 2023-09-06→2025-11-28 | 744 |
| EX I EN I WW I TOF I BROAD I PUR I T-CPA II BROAD I NO PROMO I Kollektionen + Types | 42'145 | 4% | 1663.7 | 3.35 | 2023-06-05→2026-07-03 | 694 |
| EX \| DE \| SEARCH \| BRAND | 38'382 | 4% | 25783.5 | 55.83 | 2023-09-06→2026-07-03 | 1028 |
| EX I WW I PMAX I PROSPECTING I BROAD | 36'072 | 4% | 1111.3 | 3.53 | 2024-03-22→2025-11-28 | 424 |
| EX \| USA \| SEARCH \| BRAND | 25'576 | 3% | 7129.1 | 33.92 | 2023-09-06→2026-07-03 | 1028 |
| EX I WW I YOU I BROAD TESTING I INFLUENCER & ANIM.C. | 24'118 | 3% | 443.9 | 1.83 | 2023-07-28→2025-10-14 | 507 |
| EX I WW I PMAX I SCALING I RE/HOT | 24'074 | 3% | 1599.4 | – | 2023-06-14→2024-03-27 | 268 |
| EX I FRA I PMAX I TESTING I BROAD | 22'016 | 2% | 845.8 | 3.01 | 2023-06-27→2025-11-28 | 886 |

## 6. Verdikt-Bestand (aus change_impact*.csv)

- `change_impact_staycold.csv`: {'MANUELL': 45, 'UNKLAR': 44, 'NEUTRAL': 127, 'NEGATIV': 122, 'POSITIV': 129} · Confidence {'n/a': 45, 'niedrig': 335, 'mittel': 67, 'hoch': 20}

### Zitierfähiger Kern (nur mittel/hoch-Confidence, POSITIV/NEGATIV)

| Datum | Kat | Entity | Verdikt | Conf | Kern | Spend@Risk |
|---|---|---|---|---|---|---|
| 2026-05-29 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | NEGATIV | mittel | ROAS -37% (DiD -27%) | 17435.0 |
| 2024-07-16 | BUD | EX I WW I PMAX I SCALING I BROAD | POSITIV | hoch | ROAS +48% (DiD +45%) | 9185.0 |
| 2026-01-23 | BID | EX I SHOPPING I FOKUSPRODUKTE | POSITIV | mittel | ROAS +50% (DiD +29%) | 6497.0 |
| 2026-01-23 | STATUS | EX I SHOPPING I FOKUSPRODUKTE | POSITIV | mittel | ROAS +50% (DiD +29%) | 6497.0 |
| 2025-04-05 | BUD | EX I SHOPPING I FOKUSPRODUKTE | NEGATIV | mittel | ROAS -44% (DiD -17%) | 6117.0 |
| 2025-10-11 | BUD | EX I WW I PMAX I SCALING I BROAD | NEGATIV | mittel | ROAS -33% (DiD -18%) | 5896.0 |
| 2025-08-11 | BUD | EX I SHOPPING I FOKUSPRODUKTE | POSITIV | mittel | ROAS +68% (DiD +29%) | 5764.0 |
| 2024-10-04 | BID | EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX +  | POSITIV | hoch | ROAS +171% (DiD +126%) | 5327.0 |
| 2024-10-09 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX +  | POSITIV | hoch | ROAS +302% (DiD +246%) | 5266.0 |
| 2025-04-17 | BUD | EX I SHOPPING I FOKUSPRODUKTE | NEGATIV | mittel | ROAS -16% (DiD -22%) | 4991.0 |
| 2024-08-21 | BUD | EX I WW I PMAX I SCALING I BROAD | NEGATIV | mittel | ROAS +1% (DiD -22%) | 4875.0 |
| 2025-04-04 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | NEGATIV | mittel | ROAS -49% (DiD -23%) | 4865.0 |
| 2025-02-20 | NEG | EX I SHOPPING I FOKUSPRODUKTE | NEGATIV | mittel | ROAS +2% (DiD -23%) | 4674.0 |
| 2025-03-10 | BUD | EX I SHOPPING I FOKUSPRODUKTE | POSITIV | mittel | ROAS +26% (DiD +17%) | 4611.0 |
| 2024-10-09 | BUD | EX I WW I PMAX I SCALING I BROAD | POSITIV | hoch | ROAS +88% (DiD +31%) | 4319.0 |
| 2024-10-23 | TRACK | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | NEGATIV | mittel | ROAS +19% (DiD -22%) | 4236.0 |
| 2025-09-18 | SET | EX I SHOPPING I FOKUSPRODUKTE | POSITIV | mittel | ROAS -5% (DiD +17%) | 3874.0 |
| 2025-10-23 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | NEGATIV | mittel | ROAS +28% (DiD -31%) | 3760.0 |
| 2024-10-09 | BUD | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | mittel | ROAS +29% (DiD -27%) | 3582.0 |
| 2024-10-23 | TRACK | EX I WW I PMAX I SCALING I BROAD | POSITIV | mittel | ROAS +125% (DiD +84%) | 3401.0 |
| 2025-04-04 | AD | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | mittel | ROAS -53% (DiD -27%) | 3075.0 |
| 2025-04-04 | STATUS | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | mittel | ROAS -53% (DiD -27%) | 3075.0 |
| 2025-04-04 | BUD | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | mittel | ROAS -53% (DiD -27%) | 3075.0 |
| 2025-05-13 | STATUS | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | hoch | ROAS -100% (DiD -118%) | 3048.0 |
| 2024-10-23 | TRACK | EX I WW I PMAX I PROSPECTING I BROAD | NEGATIV | mittel | ROAS +11% (DiD -30%) | 2886.0 |
| 2025-01-23 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | POSITIV | hoch | ROAS +36% (DiD +43%) | 2867.0 |
| 2024-10-23 | TRACK | EX I SHOPPING I FOKUSPRODUKTE | NEGATIV | mittel | ROAS -6% (DiD -47%) | 2804.0 |
| 2026-03-06 | TRACK | EX \| USA \| SEARCH \| BRAND | POSITIV | mittel | ROAS +59% (DiD +66%) | 2795.0 |
| 2025-07-14 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX +  | POSITIV | mittel | ROAS +41% (DiD +58%) | 2634.0 |
| 2025-04-15 | BUD | EX I USA I PMAX I TESTING I BROAD | POSITIV | mittel | ROAS +20% (DiD +21%) | 2605.0 |
| 2024-10-09 | BUD | EX I USA I PMAX I TESTING I BROAD | NEGATIV | hoch | ROAS +19% (DiD -38%) | 2513.0 |
| 2025-07-20 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | POSITIV | mittel | ROAS +22% (DiD +27%) | 2433.0 |
| 2024-10-23 | TRACK | EX I USA I PMAX I TESTING I BROAD | NEGATIV | mittel | ROAS +12% (DiD -29%) | 2308.0 |
| 2025-07-14 | BUD | EX I USA I PMAX I TESTING I BROAD | POSITIV | mittel | ROAS +1% (DiD +18%) | 2244.0 |
| 2024-10-23 | TRACK | EX I FRA I PMAX I TESTING I BROAD | NEGATIV | hoch | ROAS +1% (DiD -40%) | 2227.0 |
| 2025-07-14 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I PROSPECTING | NEGATIV | mittel | ROAS -38% (DiD -21%) | 2200.0 |
| 2026-03-06 | TRACK | EX \| DE \| SEARCH \| BRAND | POSITIV | mittel | ROAS +18% (DiD +25%) | 2167.0 |
| 2026-01-13 | STATUS | EX \| USA \| SEARCH \| BRAND | NEGATIV | hoch | ROAS -8% (DiD -32%) | 2069.0 |
| 2025-04-15 | BID | EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX +  | POSITIV | hoch | ROAS +85% (DiD +86%) | 1859.0 |
| 2025-04-15 | BUD | EX I WW I PMAX I SCALING I FEED ONLY I OVER-INDEX + INDEX +  | POSITIV | hoch | ROAS +85% (DiD +86%) | 1859.0 |

_+22 weitere im JSON._
