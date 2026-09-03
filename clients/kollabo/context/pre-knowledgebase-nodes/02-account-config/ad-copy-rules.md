---
id: kollabo.ad-copy-rules
layer: customer
client: kollabo
status: canonical
triggers: [ad-copy]
topics: [ad-copy, assets, compliance, angles]
last_reviewed: 2026-05-20
---
# Kollabo — Ad-Copy-Regeln

Kundenspezifische Schwellwerte, Validation-Cases und Copy-Regeln für den Ad-Copy-Agent.

Seit dem Sheet-Refactor vom 25.04.2026 arbeitet der Agent auf einem 12-Spalten-Replace-Layout: pro Zeile ein konkreter Vorschlag (entweder Replace einer schwachen Headline, reine Slot-Auffüllung, oder Asset einer komplett neuen RSA via bundle_id). Pro schwachem Asset werden mehrere Replace-Vorschläge generiert (Default 3) — der Admin wählt einen via Approve-Checkbox.

## Kalibrierungs-Grundlage

Asset-Ebene-Schwellwerte basieren auf 100 Top-Headlines aus dem Kollabo Asset Performance Report (UI-Export 25.04.2026). Methodik dokumentiert in `reports/asset_level_refactor_concept.md`.

Account-Percentile pro Headline-Asset:
- Impressions: p10=23, p25=78, p50=236, p75=816, p90=1320
- Clicks: p10=2, p25=9, p50=26, p75=80, p90=180
- CTR (≥100 Impr): p10=6.04%, p25=8.88%, p50=10.45%, p75=13.05%, p90=16.97%
- Conv-Rate (≥10 Klicks): p10=0%, p25=2.76%, p50=6.42%, p75=8.84%, p90=13.5%
- CPA mit Conv: p50=14.16 CHF, p75=19.94, p90=37.52
- Verwendungen pro Asset: p50=2 Anzeigen, p75=4, p90=9, max=43

**API-Validierung 25.04.2026:** `ad_group_ad_asset_view` mit `metrics.*`-Feldern liefert Per-Asset-Aggregation mit ~3-5% Abweichung gegenüber UI-Werten (Status-Filter / UI-Zeitzone-Differenz). Akzeptabel für Trigger-Entscheidungen.

## Mindestdatenbasis (Asset-Ebene)

Bevor der Agent ein Asset bewertet:
- `impressions >= 200` UND `clicks >= 15`

Begründung: zwischen Account-p25 (78 Impr) und p50 (236). Filtert ~30% Long-Tail-Assets als nicht-aussagekräftig.

Assets unter Schwelle: Status `ASSET_MONITOR`, keine Aktion.

## Asset-Trigger

**ASSET_LOSER** (priorisierter Replace-Kandidat):
- `conv_rate < 1.5%` UND `clicks >= 30` UND `cost_chf >= 20`
- Begründung: Account-p25 Conv-Rate ist 2.76%. Unter 1.5% deutlich darunter. Cost-Schwelle gegen False Positives.

**ASSET_WEAK** (sekundärer Replace-Kandidat):
- `ctr < 6%` UND `conv_rate < 2.76%` UND Mindestdatenbasis
- Begründung: Account-p10 CTR ist 6.04%, Account-p25 Conv-Rate ist 2.76%. Unter beiden Quartilen.

**ASSET_TOP** (DO_NOT_TOUCH, vor Replace geschützt):
- (`conv_rate >= 8.84%` UND `conversions >= 5`) ODER `pinned != null`
- Begründung: Top-Quartil Conv-Rate plus genug Daten. Gepinnte Assets sind explizite User-Entscheidung.

Konflikt-Regeln: ASSET_TOP sticht alles. Pinned overrides everything. Bei gleichzeitig LOSER und WEAK gewinnt LOSER (höhere Priorität).

## Replace-Workflow (12-Spalten-Sheet)

Pro `ASSET_LOSER` und pro `ASSET_WEAK` generiert der Agent **3 Replace-Vorschläge** als 3 separate Sheet-Zeilen:

| Spalte | Inhalt |
|---|---|
| current_text | die schwache Headline / Description |
| new_text | Vorschlag 1, 2 oder 3 (je Zeile anders) |
| char_count | Zeichenzahl von new_text |
| reason | warum dieser Ersatz: datenbezogen + Angle-Bezug |
| action | `HEADLINE_ADD_TO_EXISTING` oder `DESCRIPTION_ADD_TO_EXISTING` |
| campaign | Kampagnen-Name |
| ad_group_name | AdGroup-Name |
| ad_group_id | ID der AdGroup |
| angle_tag | `Produkt`, `USPs` oder `CTAs/Brand` (siehe Mapping unten) |
| approved | Default leer/FALSE — der User checkt eine der 3 Zeilen an |
| notes | „Vorschlag 1 von 3" / „Vorschlag 2 von 3" / „Vorschlag 3 von 3" |
| bundle_id | leer (nur bei NEW-Actions gesetzt) |

Der Agent stellt sicher dass die 3 Vorschläge **inhaltlich verschieden** sind — verschiedene Angles oder Hooks, nicht 3 Varianten desselben Satzes.

## angle_tag — 3 Werte (User-Wunsch 25.04.2026)

Reduziert von 11 auf 3 Werte für saubere Sheet-Filterung:

- **Produkt** — beschreibt was/wo der Job ist. Mapping aus altem Schema: BENEFIT, REGIONAL, PRICE, PROCESS. Beispiele: „Kranführer in Zürich", „Top-Lohn am Bau", „In 2 Minuten bewerben".
- **USPs** — was Kollabo besser macht oder welcher Pain gelöst wird. Mapping: USP, RISK_REVERSAL, PROOF, PAIN. Beispiele: „nur 1x bewerben", „kostenlos für Bewerber", „4.9 Google Rating", „Schluss mit endlosen Bewerbungen".
- **CTAs/Brand** — Call-to-Action oder Brand-Erwähnung. Mapping: CTA, URGENCY, BRAND. Beispiele: „Jetzt bewerben", „Heute starten", „Mit Kollabo durchstarten".

Bei Zweifel zwischen zwei Kategorien: für die wählen die im RSA aktuell unterrepräsentiert ist (siehe Compliance unten).

## Compliance: RSA-Komposition (User-Regel 25.04.2026)

Jede RSA muss **mindestens 9 Headlines** haben, davon **mindestens 3 pro angle_tag** (3 Produkt + 3 USPs + 3 CTAs/Brand).

Praktische Implikation für den Agent:

1. **Vor jedem Replace:** prüfen welche angle_tags der schwachen Headline zugeordnet ist (durch Re-Klassifikation). Der Replace-Vorschlag soll im selben Tag bleiben — sonst kippt die 3+3+3-Balance.
2. **Vor jedem Pause/Replace:** prüfen ob die RSA nach dem Tausch noch 3 Headlines im betroffenen Tag hätte. Wenn nein: nicht ersetzen, Hinweis im reason-Feld („Würde Compliance verletzen — alternative Tag-Mischung schlagen wir nicht vor").
3. **Bei reiner Slot-Auffüllung:** den Tag wählen der im RSA bisher unterrepräsentiert ist.

Descriptions: kein hartes Compliance-Minimum nach User-Regel. Empfehlung bleibt 3-4 Stück, aber kein automatischer Block.

## Bundle-Logik (HEADLINE_NEW / DESCRIPTION_NEW)

Wenn der Agent eine komplett neue RSA vorschlägt (z.B. weil mehr als 5 Assets in einer bestehenden RSA gleichzeitig zu schwach sind, oder wenn eine AdGroup keine aktive RSA hat):

- Alle Drafts dieser neuen RSA tragen dieselbe `bundle_id` (Format: `bundle-<adgroup-slug>-<seq>`)
- Mindestens 9 Headlines (3+3+3) + mindestens 4 Descriptions im Bundle
- Maximal 15 Headlines + 4 Descriptions im Bundle (Google-Ads-Limit)
- `current_text` ist leer
- `notes` enthält „Bundle X von Y" zur Orientierung

Der Push wird bundle_id-gruppiert verarbeitet: erst wenn alle Pflicht-Assets eines Bundles approved sind, wird die RSA in Google Ads erstellt.

## Batch-Limits

- Maximal **30 Replace-Vorschläge** account-weit pro Agent-Lauf (= max 10 schwache Headlines pro Lauf, da je 3 Vorschläge generiert werden)
- Maximal **5 schwache Headlines pro Source-RSA** pro Lauf — bei mehr Schwachstellen → kompletten Bundle-Vorschlag statt Einzel-Replace
- Maximal **3 RSAs pro AdGroup** pro Lauf anfassen

## Push-Realität

Phase 1 (jetzt): Sheet zeigt Empfehlungen. `push_decisions` für ADD_TO_EXISTING-Replace ist noch nicht implementiert — der User entscheidet im Sheet via Checkbox und setzt die Änderung manuell im Google-Ads-UI um.

Phase 2 (geplant): Push-Tool baut für jeden approved Replace-Eintrag den RSA neu (alte Headline raus, neue rein) und ersetzt den alten RSA. Bei Bundle-NEW-Drafts: erstellt eine neue RSA aus allen approved Assets desselben bundle_id.

## Validation-Cases (zur Überprüfung der Kalibrierung)

**Muss als ASSET_LOSER getriggert werden:**
- „Effektiv dank grossem Netzwerk" (30 Klicks, 0% Conv-Rate, 20.30 CHF Cost)
- „Faire Löhne für Sanitär-Jobs" (65 Klicks, 0% Conv-Rate, 81.42 CHF Cost)

**Darf NICHT als Trigger feuern (geschützt):**
- Top-Performer mit Conv-Rate ≥ 8.84% bei mind. 5 Conv

## Kollabo-spezifische Copy-Regeln

**Tonalität.** Konsequente Duz-Form. Kurze, klare Sätze. Service-Mentalität.

**Erlaubte quantitative Claims** (wörtlich übernehmen, keine Abkürzungen):
- „4.9 Google Rating" (17 Zeichen)
- „jeder dritte Bewerber findet einen Job" (38 Zeichen — nur Description)
- „über 500 offene Stellen" (23 Zeichen)
- „in 2 Minuten bewerben" (21 Zeichen)
- „nur 1x bewerben" (15 Zeichen)

Andere Zahlen/Rankings/Zertifizierungen sind nicht erlaubt.

## Änderungshistorie

- 2026-04-25 v2: User-Refactor auf 12-Spalten-Sheet. angle_tag auf 3 Werte. RSA-Compliance 9 Headlines (3+3+3). Replace-Workflow mit 3 Vorschlägen pro schwachem Asset. ASSET_PAUSE entfällt. bundle_id für neue RSAs.
- 2026-04-25 v1: Erstmaliger Asset-Ebene-Refactor (15 Spalten mit source_asset_id).
- 2026-04-23: Initiale Ad-Ebene-Schwellwerte.
