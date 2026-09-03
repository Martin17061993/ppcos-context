# Stay Cold — Daten & Systeme

Quelle: Notion „Our Data Structure", Airtable Data Documentation, Shopify Shop Management, Tools & Software. Stand 2026-07-21.

## 3-Klassen-Datenmodell

| Klasse | Inhalt | System |
|---|---|---|
| A | Unstrukturierter Kontext (Strategie, SOPs, Brand Guide) | **Notion** (Stay Cold Knowledge Base) |
| B | Operative Tabellendaten | **Airtable** (Team-Workspace „Stay Cold Apparel") |
| C | Read-only Big Data: Shopify Orders, **Meta Ads, Google Ads**, Klaviyo, Reviews.io | **Supabase** („Class C Data Warehouse", Pro Plan; Hosting Railway) |

→ **Google-Ads-Daten sind als Class-C-Quelle eingeplant.** Anknüpfungspunkt für unsere Pull-Pipeline/Reports: mittelfristig könnte unser Stack direkt in deren Supabase liefern statt nur in unsere Sheets. Mit Maxobert/Shaun klären.

## Airtable-Basen (Class B)

- **Product Catalogue** (`app72sPNYvvMonkXg`) — Source of Truth aller Produktdaten, feedet Shopify. 495 Produkte, 2.549 SKUs, O_-Dimensionstabellen (Artist, Design, GSM, Cut …), Function-Tabellen (Price Recommender: Markup ×4 auf Einkaufspreis; HS-Code; EAN-Pool; Weight).
- **Drop Base** (`app9nQAQ5BiI6OpPY`) — Jahres-Marketing-/Drop-Kalender („Planned Activations", 390 Zeilen) — **relevanteste Base für Ads-Planung** (Early-Access-/Go-Live-Fenster, AIC-Dates, Drop Dates).
- **Order Base** (`appM65nblESBXYQ00`) — POs/Shipments/Invoices (577 PO-Products, 370 Shipments; Deposits Σ ~2,98 Mio. €). Liefert erwartete Warenverfügbarkeit (Cargo→Arrival, Transport-Lieferzeiten).
- **Project Management** (`appIdDeEdOGEPCyXX`) — Goals/Projects/Tasks + Daily Check-in.
- **SCA PRODUCT-LAB** — Creative-Pipeline (Caro). **Influencer Base** — Migration läuft. **Return Controlling** — Weekly Snapshots des Return-Reports.
- Doku-System: je Domain Concept Page + Data Overview + maschinenlesbare Registries (Bases/Tables/Fields/Automations); Scripts referenzieren IDs, nie Namen.

## Shopify (Master-System Shop)

- Shopify Plus, Shop `rapid-4.myshopify.com` → staycoldapparel.com; **Shopify ist Master für Inventory** (Warehouse spielt live ein; kein Sync aus Airtable — Entscheidung 04.07.2026).
- Source-of-Truth-Kette: Notion = Struktur/Regeln · Airtable = Produktdaten · Shopify = Zielsystem.
- Metafield-Landschaft dokumentiert in „Shopify Shop Management" (DB_Shopify Fields, Metaobject Types/Fields): Analytics-Twins je Dimension (`*_for_analytics`), `custom.drop`/`drop_date`/`early_access_*`/`last_restock_date`, Reviews (`reviews.rating`, `rating_count`), Search & Discovery, `mm-google-shopping.*` (Custom Labels 0–2!), Zoll (`mid_info.midaddress`).
- Bekannter Bug (aus Klaviyo-SOP): dynamische Produkt-Feeds verlinken teils auf `rapid-4.myshopify.com` statt staycoldapparel.com.
- B2B-Orders existieren (`is_b2b_order`) — in Reports exkludieren, gleiche Frage für unsere GAds-Reports stellen (Wholesale läuft separat).
- Cross-Border: Global-e im Einsatz (Returns außerhalb Shopify möglich) — Attributions-/Report-Lücken möglich.

## Marketing-/Analytics-Stack

- **Tracify** (Attribution!), **Klaviyo** (E-Mail), Reviews.io, Gojiberry, Mable — Owner jeweils Jonas. → Klären, was Tracify über Google-Ads-Beitrag erzählt und wie das neben unserer Purchase-only-DiD-Methodik steht (Konflikt-Potenzial bei ROAS-Diskussionen).
- Anthropic Claude.ai Team + Claude API; OpenAI Business + API; Higgsfield.ai (Creative).
- Google Workspace Business Standard (Sheets/Drive — dort liegen unsere Review-Sheets).
- Legacy-Google-Sheets (Migration → Airtable läuft): Conversion Database, Drop Dashboard, Weekly Stay Cold Metrics, Yearly Marketing + Drop Schedule (→ Drop Base migriert), Influencer Marketing Controlling (Maxobert + Jonas).

## SOP-/Automations-Landschaft (Claude-basiert)

| SOP | Rhythmus | Für uns relevant |
|---|---|---|
| Daily Check-in (`/stay-cold-daily-checkin`) | täglich | Betriebsmodell-Vorbild für unseren Agent |
| Net-Sales Dashboard (`/net-sales-dashboard`) | montags | Deren Umsatz-Sicht (B2B-exkludiert, Mo–So-Wochen) — mit unseren GAds-Reports synchronisieren |
| Return-Rate Report (`/return-rate-report`) | montags | Produkt-Qualitätssignale (z.B. Sizing-Probleme) → Ads-Produktauswahl |
| Collection Sorting Score | nightly | Bestands-/Frische-Logik des Shops — Kandidat für Feed-Sync |
| Klaviyo Drop-Kampagne (`/klaviyo-drop-campaign`) | je Drop | Drop-Timing + Naming-Schema `EX I <THEMA> I DDMMYYYY` |
| Airtable↔Shopify-Abgleich | täglich 06:00 (Draft) | Datenqualität Produktdaten |

- Anmerkung: Deren SOP-Guardrail-Stil (nie proaktiv senden, Preview-Pflicht, Writes nur aufs Zielsystem, jede Aussage gegen Live-Daten verifizieren) ist deckungsgleich mit unserem Human-in-the-Loop-Prinzip — gutes Argument beim Rollout.
