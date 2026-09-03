# Pre-Knowledgebase Stay Cold

Vorbefüllung für `/business-context-gatherer`. Alles hier ist **bestehendes Wissen**, das vor dem Interview gelesen werden soll — damit der Gatherer nicht 20 Fragen stellt, die schon beantwortet sind.

Stand: 03.08.2026. Quellen sind Snapshots, keine Live-Verbindung.

## Verwendung

Vor dem Gatherer-Lauf:

> Lies zuerst alles unter `context/pre-knowledgebase-nodes/`. Beantworte die Interview-Fragen daraus, soweit möglich, und frag mich nur noch das, was dort nicht drinsteht oder wo die Quellen sich widersprechen.

## Inhalt

### `01-notion-kb/` — Business-Kontext aus der Notion-KB
Kuratierte Zusammenfassungen des Notion-Vollcrawls vom 21.07.2026 (Obsidian `05 Kunden/Stay Cold`).

- `Stay Cold.md` — Hub: Kunden-Card, Status Google Ads, 3 Kernerkenntnisse, offene Punkte
- `Stay Cold - Brand & Marketing.md` — Brand-Ton, Positionierung, Kanal-Mix
- `Stay Cold - Produkte & Drops.md` — Sortiment, Drop-Logik, **Promo-Regeln (gelockt)**
- `Stay Cold - Team & Organisation.md` — Ansprechpartner, Rollen
- `Stay Cold - Daten & Systeme.md` — Shopify, Airtable, Tracking-Landschaft
- `Stay Cold - Ads-Implikationen.md` — was daraus für Google Ads folgt
- `00 Notion-Seitenkarte.md` — Quellenkarte mit Notion-Page-IDs (Basis für den späteren Sync)

### `02-gads-guardrails/` — evidenzbasierte Account-Regeln
Aus dem eigenen Agent-Stack, abgeleitet aus 2024–2026-Daten des Accounts 359-911-6618.

- `sc_gads_guardrails.md` — Do/Don't-Regeln mit Schwellwerten → **direkter Input für "Known Constraints" + "Performance Targets"**
- `sc_gads_known_limits.md` — was der Account nachweislich nicht kann
- `sc_gads_campaign_profiles.md` — Kampagnen-Profile
- `sc_gads_account_timeline.md` — Timeline der Struktur-Änderungen
- `sc_gads_decision_evidence.md` — Belege hinter den Regeln
- `sc_gads_measurement_regimes.md` — Messregime/Attributionswechsel (wichtig für Zahlenvergleiche über Zeit)

### `03-account-config/` — bestehende Customer-Files
- `account-info.md` — Account-Stammdaten, Tracking, Guardrails
- `ad-copy-rules.md` — Copy-Regeln (Brand-Ton) → Input für alle Maker-Skills
- `search-terms-rules.md` — Search-Term-Regeln

### `04-historie/` — Verlauf & Briefing
- `Jonas-Briefing_StayCold_2024-2026.md` — ausführlichstes Dokument, Account-Entwicklung
- `gads-account-history.md` — Changelog
- `history_facts.md` — extrahierte Fakten (strukturiert)

## Bewusst nicht kopiert

- `rag/00_INGESTION_README.md`, `Testing-Protokoll_*`, `benchmark/*` — Meta-Doku zum eigenen Agent-Stack, kein Business-Kontext
- `05 Kunden/Kollabo` — anderer Kunde, gehört nicht in diesen Client-Ordner
- Rohdaten-CSVs/JSONs — die zieht PPC OS selbst über `/gads-context`

## Achtung

Die Notion-Quellen enthalten laut Quellenkarte **Interna (Passwörter, Finanzdaten)**. Die hier liegenden Zusammenfassungen sind bereits gefiltert — trotzdem: nichts aus diesem Ordner ungeprüft in kundenferne Artefakte oder Reports übernehmen.

Widersprüche zwischen `01-notion-kb/` (Kundensicht, Stand 21.07.) und `02-gads-guardrails/` (Datensicht, Stand 03.07.) sind möglich. Im Zweifel gilt die Datensicht für Performance-Zahlen, die Kundensicht für Strategie und Ton.
