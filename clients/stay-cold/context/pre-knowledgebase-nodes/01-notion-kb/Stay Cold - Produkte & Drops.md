# Stay Cold — Produkte & Drops

Quelle: Notion „03 - Product + Offer Cheat Sheet v0.1" (Active), Product Catalogue Overview/Data Structure, Drop Base, SOPs. Stand 2026-07-21.

## Produkt-Kern

- **Heavyweight Apparel:** Hoodies, Tees, Jackets. Qualitäts-Standard: Hoodies **400gsm**, „Heavy" Tees **250gsm**, **200-Wäschen-Print-Haltbarkeit** — das sind die belegbaren Claims für Ad-Copy.
- **Bread & Butter:** Heavyweight Hoodie, Graphic Tee, Jogger („These run, convert, get worn")
- **Hero:** Hoodies historisch; **„Reign of Blood" ist das Blueprint-Produkt**
- Design-Lines-Evolution: 2021–23 „Tattoo-Poster" (Icon-DNA: Hangover, Hannya, Witch, Medusa, Zombie Fox, Reign of Blood) → 2024–26 „Dark Uniform" (Washes, Metal-Logos, Sets, Pants, Caps, Socks) → „Stay Cold Logo Line" → 2026+ Symbol-System
- Strategische Richtung: „Growth. Scaling. International markets. **Higher prices. Fewer products.**" — kein Sell-out.
- Katalog-Umfang: 495 Produkte / 2.549 SKUs / 280 Designs / 26 Artists / 37 Produktkategorien / 47 Cuts (Airtable Product Catalogue)

## Offer-Regeln (LOCKED, Max1, 2026-05-08) ⚠️

- **Keine Sitewide-Discounts**
- **Keine Rabatte auf neue Drops in den ersten 90 Tagen**
- **Rabatte nur am Black Friday, und nur auf Slow Mover**
- Konsequenz für Ads: kein Rabatt-Messaging außerhalb BF; Promo-Fenster-Kalender (`promo_windows.csv`) muss dieser Logik entsprechen. Deals existieren als „Unlock-/Geschenk-Moment" (z.B. Tag `Buy3Get1ForFree`), nicht als Preisnachlass-Kommunikation.

## Drop-Mechanik

- **„Drops, not seasons."** Jeder Drop bekommt eigene Landingpage + echte Scarcity. Max1-Instinkt: „like a rapper dropping singles — flood the market"; aber: „No structured drop plan yet".
- **Thunder Drop Weeks:** Friday Drops mit Special-/Deal-Produkt, laufen i.d.R. bis zum nächsten Freitag. **Daily Drops:** 1 Tag.
- E-Mail-Sendout-Standard: 18:00 DE (16:00 UTC), Absender „Max from Stay Cold Apparel", Kampagnen-Naming `EX I <THEMA> I DDMMYYYY`.
- Planung lebt in der **Drop Base** (Airtable, „Planned Activations", 390 migrierte Zeilen): Activation Types = Intra-Day Scaling (Profit Focus / New Customer Focus), New Product, New Product Drop, Restock, Special Marketing Activation. Je Activation: Early-Access- + Public-Go-Live-Fenster, Order Batch, Cargo-/AIC-Dates → Drop Date, Inventory-Snapshots.
- → Der Ads-Promo-Kalender kann und sollte künftig direkt aus der Drop Base gespeist werden.

## Produktnummern & Feed-Relevantes

- **Stay Cold Product Number:** 4-stellig (1001–1495), = Shopify-Metafield `custom.staycold_product_number`; **ab 2026 je Production Run neue Nummer + neue SKUs** (Production Country, Kosten, Patch-Details) — Achtung bei Produkt-Historien im Feed: „gleiche" Produkte wechseln die ID.
- Shopify = **Master für Bestand** (Warehouse spielt live ein; kein Inventory-Sync aus Airtable, Entscheidung 04.07.2026).
- Google-Shopping-relevante Metafelder (live): `mm-google-shopping.custom_label_0/1/2`, Age Group, Condition; Analytics-Twin-Strings je Dimension (`design_for_analytics`, `artist_for_analytics`, `generic_color_for_analytics`, `gsm_for_analytics` …) → saubere Feed-Segmentierung nach Design/Artist/Design-Line möglich.
- `custom.drop_date`, `custom.early_access_start/end`, `custom.last_restock_date`, `custom.collection_sorting_score` — nutzbar für Kampagnen-Timing.
- Legacy ungeklärt: `custom.internal_rolling_number` → „Google Product Master Sheet" (Sebastian, inaktiv).

## Verfügbarkeits-Logik (wichtig für Ads-Planung)

- Order Base (Airtable): POs → Shipments mit **Cargo Date** (Übergabe Producer) und **Arrival/AIC Date** (Ankunft Lager AIC); Dimension „Transport Methods" enthält Lieferzeit in Tagen je Produktionsland+Methode. Planungs-Anker: „Manual AIC Date committed to Vuven".
- Nightly **Collection Sorting Score** (Claude-Routine auf Maxoberts Rechner): frische Drops top (Boost 4000, Halbwertszeit ~7 Tage), Restocks (1500, ~14 Tage), Rest nach 30-Tage-Revenue/Units; **Demotion ans Listenende bei Bestand <10 Units oder gewichteter Größenverfügbarkeit <25 %** (M/L/XL doppelt gewichtet); Top-10-Rohertrag +1500.
- → Wenn der Shop ein Produkt demotet (Bestand/Größenlauf), sollte Paid es auch nicht mehr pushen. Kandidat für spätere Feed-/Skript-Automation.

## Qualitäts-/Ops-Prinzipien (Operations Cheat Sheet v0.1)

- „**AI only for marketing and video. Product art stays human.**" (locked)
- Pipeline: Idea (Maxx) → Design (Caro, Maxx) → Sampling/Production/QC (Marvin) → Fulfillment (AIC-Logistik) → Shop/Drop (Jonas, Maxobert)
- Bekanntes Risiko: „Production → Fulfillment: if AIC isn't informed in time, stock problems hit on drop day."
- Returns (erster Report 18.07.2026): Store-Rate ~0,6 %; Gründe: Sizing 54 %, Style 30 %; Treiber: 260gsm Oversized Jerseys (Red Devil, Garnet, Galactico).
  > ⚠️ **KORREKTUR 2026-08-03:** Die ~0,6 % sind falsch — der Snapshot vom 18.07. war ein unvollständiger Pull (25.395 Units / 162 Retouren). Die Folgeläufe in Airtable `Return Controlling` (`apppNMIKbDaGtGHrD`, Weekly Snapshots) zeigen 20.07. = **4,61 %** und 27.07. = **5,07 %**. Arbeitswert: **~5 %**. Definition: trailing 60 Tage, Unit-basiert, B2B-exkludiert, ohne Non-EU-Retouren über Global-e (echte USA-Quote also höher). Die Sizing/Style-Gründe und die Jersey-Treiber bleiben gültig. Stay Colds Notion-KB trägt die falsche Zahl noch — Jonas informieren.
