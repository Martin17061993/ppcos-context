# Stay Cold — Ads-Implikationen (Synthese aus Notion-KB)

Was aus der Notion-KB (Crawl 2026-07-21) konkret in die Google-Ads-Arbeit einfließt. Die Punkte unter „Vorschlag Agent-KB" sind **noch nicht** in die Agent-Files übernommen — Freigabe Martin ausstehend.

## 1. Strategische Lage

- Deren aktives Marketing Cheat Sheet kennt Google **nicht** als Kanal — nur als offene Frage („Is Google still an active acquisition channel, and what's its role?"). Gleichzeitig: ~50–60k €/Monat Spend, clean ROAS 5–8.
- **Chance:** Die Change-Impact-Analyse + der Agent beantworten deren offene Frage #1 faktisch. Freitag-Termin so framen: „Hier ist die Antwort auf die offene Frage in eurem Marketing-Sheet."
- **Risiko:** Solange Googles Rolle strategisch undefiniert ist, ist das Budget politisch angreifbar (Meta gilt als DER Paid-Kanal). Ziel: Google-Rolle ins v0.2 Marketing Sheet bringen (Owner „to be assigned" — Vakuum nutzbar).
- Attribution: Tracify ist deren Attributions-Tool (Owner Jonas). Vorher klären, was Tracify zu Google sagt — sonst Zahlen-Streit im Termin.

## 2. Harte Regeln aus der KB, die Ads-Verhalten ändern

| Regel (Quelle) | Konsequenz für Ads |
|---|---|
| Keine Sitewide-Discounts; keine Rabatte auf Drops <90 Tage; Rabatte nur BF auf Slow Mover (03-Sheet, locked) | Promo-Fenster-Logik: außer BFCM keine „Sale"-Kampagnen/-Assets; `promo_windows.csv` gegen Drop Base validieren |
| Nie „Premium Quality"/„Community"/„Streetwear"; kein Discount-Ton; „We don't advertise" (01-Sheet) | RSA-/Feed-Copy-Regeln; belegbare Claims stattdessen: 400gsm, 250gsm Heavy Tees, 200-Wäschen-Prints, Berlin 2015, no investors |
| Kommunikation NUR an den 70 %-Kern (01-Sheet) | Kein Broad-Audience-Softening in Copy; Suchbegriffs-Relevanz am Kern messen (Metal/Tattoo/Dark) |
| Symbolik: dunkle Energie ja, Anti-Religion nein; Richtung „positive symbolism" (02-Draft) | Asset-Auswahl/Freigaben; keine okkult-provokanten Neu-Motive pushen |
| Business-Sprache Englisch | Alles Kundenseitige (Plugin, Commands, Reports, Sheets-Spalten) auf EN |

## 3. Operative Anknüpfungspunkte

- **Drop Base = künftiger Promo-/Kampagnen-Kalender:** Early-Access-/Public-Fenster, AIC-Dates, Drop Dates, Activation Types (inkl. „Intra-Day Scaling — Profit/New-Customer Focus" — deckt sich mit Guardrail DO-4).
- **Feed-Segmentierung:** `mm-google-shopping.custom_label_0/1/2` + Analytics-Twins (Design/Artist/Design-Line/GSM) sind live → Shopping/PMax nach Design-Line oder Drop-Frische segmentierbar statt nur nach Preis.
- **Bestandslogik:** Shop demotet Produkte <10 Units / kaputter Größenlauf (nightly Score). Paid sollte dieselbe Logik spiegeln (mittelfristig: Skript/Supplemental Feed aus `collection_sorting_score`).
- **Class-C-Warehouse (Supabase):** Google-Ads-Daten sind dort eingeplant — Andockpunkt für unsere Pull-Pipeline (mit Maxobert/Shaun).
- **Returns-Signale:** 260gsm Oversized Jerseys mit Sizing-Problemen → bei Produkt-Pushes berücksichtigen.
- Legacy klären: „Google Product Master Sheet" (Sebastian, inaktiv) + `custom.internal_rolling_number`.

## 4. Vorschlag Agent-KB (⚠️ Freigabe Martin ausstehend)

Geplante Änderungen an `customer/stay-cold/`-Files (Workspace + Plugin) — erst nach Absegnung:

1. **Sprache:** beide Customer-Files + Commands + Plugin-README auf **Englisch** umstellen (Reports des Agents ebenfalls EN).
2. **account-info.md:** Website staycoldapparel.com; Stakeholder (Founder-Runde, Performance-Team inkl. Valentin); Business-Kontext präzisieren (Drops-not-seasons, 70/30-Budget-Annahme, Wettbewerber-Liste); Hinweis Tracify-Attribution.
3. **search-terms-rules.md:**
   - Brand-Claims-Whitelist für ADD_KEYWORD-Kontext (400gsm etc.) — und Competitor-Liste aus dem Marketing-Sheet (Killstar, DropDead, Disturbia, Sullen, Named Collective, Blackcraft Cult, Bad Monday) als dokumentierte Fremdmarken-Referenz für die Fremdmarken-Regel
   - Sortimentsgrenzen aus Katalog (37 Kategorien; z.B. keine Schuhe) → „Generisch/Irrelevant"-Definition schärfen
   - Sprachregeln präzisieren: EN-Kern; DE/FR/Skandi-Brand läuft über Brand-Kampagnen
4. **Neue Datei `ad-copy-rules.md` (für späteren Ad-Copy-Agent):** No-Go-Wörter (Premium Quality, Community, Streetwear), kein Discount-Ton außer BF-Slow-Mover, Claims-Whitelist, Ton dunkel/knapp/selbstbewusst, keine Emojis.
5. **Brain: KEINE Änderung** (alles Stay-Cold-spezifisch → gehört in Customer-Layer, nicht ins generische Brain).

## 5. Offene Fragen an Jonas

- Googles Ziel-Rolle: Brand-Harvesting + Shopping-Effizienz, oder aktiver Neukunden-Kanal (dann Non-Brand/PMax-Prospecting-Strategie nötig)?
- Rollenteilung mit Valentin Hertweck (Meta?) — wer verantwortet was im Performance-Bereich?
- Tracify-Sicht auf Google vs. unsere Purchase-only-DiD — welche Zahl gilt im Weekly?
- Soll unser Agent als SOP-Seite in deren Notion-KB dokumentiert werden (deren Betriebsmodell)?
- DB1-Marge: ohne sie bleibt „ist Non-Brand bei clean ROAS 2,4 profitabel?" unbeantwortbar (bekannte Grenze).
