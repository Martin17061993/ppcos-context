# PPC OS — Kunden-Kontext Kollabo & Stay Cold

Dieses Repo enthält **ausschließlich den Kontext-Layer** zu zwei Google-Ads-Konten,
die über PPC OS betreut werden — Geschäftskontext, Marken-/Account-Regeln,
Änderungshistorie und die fertigen Audit-Reports.

**Die PPC-OS-Software selbst ist nicht enthalten** (Skills, Agents, Hooks, Rules,
`CLAUDE.md`). Die sind lizenziertes Produkt und kommen über deine eigene Lizenz
per `ppcos init`. Dieses Repo füllt nur die Lücke, die `ppcos init` offen lässt.

Stand des Exports: siehe Commit-Datum. Alle Daten sind Snapshots, keine Live-Verbindung.

---

## Die zwei Konten

| Client | Display Name | Customer ID | Markt | Modell |
|---|---|---|---|---|
| `stay-cold` | Stay Cold Apparel | 359-911-6618 | DE / EU, EUR | E-Commerce (Shopify, Merchant Center) |
| `kollabo` | Kollabo | 148-770-7588 | CH, CHF | Lead-Gen (Personalvermittlung, 22 Gewerke) |

Beide hängen unter MCC **559-136-2086**.

---

## Voraussetzungen auf deiner Seite

Ohne diese fünf Punkte läuft nichts davon — nichts davon lässt sich aus diesem Repo liefern:

1. **Eigene PPC-OS-Lizenz** — die CLI authentifiziert per `ppcos login` gegen deinen Account.
2. **PPC-Hub-Login** (os.ppcmastery.com) für die Knowledge Base — hängt an der Lizenz.
3. **Eigene Google-Ads-API-Credentials** — vier Variablen in `clients/<client>/config/.env`:
   `GOOGLE_ADS_DEVELOPER_TOKEN`, `GOOGLE_ADS_CLIENT_ID`, `GOOGLE_ADS_CLIENT_SECRET`,
   `GOOGLE_ADS_REFRESH_TOKEN`.
   Der **Developer Token ist der Zeitkiller** — Google prüft den Antrag, das dauert Tage bis Wochen.
   Client ID/Secret + Refresh Token gehen schnell; PPC OS bringt `get-refresh-token.js` mit.
4. **Claude Code oder Cursor** plus Anthropic-Zugang.
5. *Optional:* DataForSEO-API-Key für `/competitor-scraper`.

---

## Einspielen

```bash
# 1. Im eigenen Hub die beiden Clients anlegen (legt Skills, Hooks, CLAUDE.md an)
cd <dein-hub>
/add-client stay-cold
/add-client kollabo

# 2. Dieses Repo daneben klonen
git clone <repo-url> /tmp/ppcos-context

# 3. Kontext hineinkopieren (überschreibt die leeren Templates, NICHT die Skills)
cp -r /tmp/ppcos-context/clients/stay-cold/context/*  <dein-hub>/clients/stay-cold/context/
cp -r /tmp/ppcos-context/clients/kollabo/context/*    <dein-hub>/clients/kollabo/context/
cp    /tmp/ppcos-context/clients/stay-cold/config/ads-context.config.json <dein-hub>/clients/stay-cold/config/
cp    /tmp/ppcos-context/clients/kollabo/config/ads-context.config.json   <dein-hub>/clients/kollabo/config/

# 4. Konto-Daten selbst ziehen (die CSVs sind bewusst nicht im Repo)
cd <dein-hub>/clients/stay-cold && /gads-context
cd <dein-hub>/clients/kollabo   && /gads-context

# 5. Prüfen
cd <dein-hub> && /health-check
```

`main-config.json` im Repo-Root ist als Referenz beigelegt — die Client-Einträge legt
`/add-client` bei dir selbst an, überschreib deine Datei nicht blind.

---

## Was drin ist

```
main-config.json                              Referenz-Eintrag beider Clients
clients/<client>/
  config/ads-context.config.json              Schwellwerte, Break-even, Brand-Terms,
                                              Conversion-Actions — jede Abweichung vom
                                              Skill-Default ist im JSON begruendet (_note-Felder)
  context/business.md                         Geschaeftsmodell, Unit Economics, Ziele, Constraints
  context/brand.md                            Markenkontext (nur stay-cold)
  context/brand-colours/palette.md            Farbpalette (nur stay-cold)
  context/account-changelog.md / .csv         Aenderungshistorie, aufbereitet und roh
                                              (-invisible.csv = nur ueber change_status
                                              sichtbare Aenderungen, i.d.R. Google Ads Editor)
  context/website/pages/*.md                  20 gescrapte Seitenanalysen (nur stay-cold)
  context/pre-knowledgebase-nodes/            Vorbefuellung fuer /business-context-gatherer:
                                              Notion-KB-Auszuege, Account-Guardrails,
                                              Copy-/Keyword-/Search-Term-Regeln, Historie
  context/analysis/<domain>/                  Fertige Audit-Reports, Audit-Logs und die
                                              vollstaendigen evidence/-Artefakte der Auditoren
                                              (account, bidding, budget, competitive, feed,
                                              geo-schedule, keyword, lp, offer, placement,
                                              pmax, quality-score, search-term, strategy, tracking)
  context/memory/*.md                         Session-Protokolle aller bisherigen Laeufe —
                                              Befunde, Entscheidungen, verworfene Hypothesen
  context/.logs/                              Logs des /ads-context-gatherer (nur stay-cold)
  created/                                    Erzeugte Deliverables: Ops-Files, Budgetplaene,
                                              Website-Fix-Listen, Executive-Summary-Report
```

## Was NICHT drin ist

| Ausgeschlossen | Grund |
|---|---|
| `.claude/skills\|agents\|hooks\|rules/`, `CLAUDE.md` | lizenzierte PPC-OS-Software — kommt ueber deine eigene Lizenz per `ppcos init` |
| `.env`, `.managed*.json` | Credentials bzw. Checksummen einer fremden Installation |
| `context/google-ads/` | ~940 MB Roh-CSVs. Ziehst du dir per `/gads-context` selbst und aktueller |
| `context/feed/cache/`, `node_modules/`, `tmp/` | Caches und Build-Artefakte |

Sonst ist alles drin.

## Vor dem ersten Lauf lesen

`LUECKEN.md` — die dokumentierten offenen Punkte beider Konten. Mehrere davon
verfälschen Audit-Ergebnisse, wenn man sie nicht kennt.
