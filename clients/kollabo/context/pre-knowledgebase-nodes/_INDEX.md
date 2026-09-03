# Pre-Knowledgebase Kollabo

Vorbefüllung für `/business-context-gatherer`. Alles hier ist **bestehendes Wissen** aus zwei Jahren Betreuung über den eigenen Agent-Stack — damit der Gatherer nicht Fragen stellt, die längst beantwortet sind.

Stand: 10.08.2026. Snapshots, keine Live-Verbindung.

## Verwendung

Vor dem Gatherer-Lauf:

> Lies zuerst alles unter `context/pre-knowledgebase-nodes/`, inklusive dieser Datei. Beantworte die Interview-Fragen daraus, soweit möglich. Frag mich nur, was dort nicht drinsteht, wo Quellen sich widersprechen, oder wo unter „Was hier NICHT steht" ein Punkt offen markiert ist.

## Inhalt

### `01-kunden-kontext/` — Geschäftsmodell und Marke
- `Kollabo.md` — Kunden-Card, Zielgruppe, abgedeckte Gewerke, USPs, Tonalität, Compliance
- `Brand-Voice.md` — Sprachregeln

### `02-account-config/` — bestehende Betreuungsregeln
- `account-info.md` — Account-Stammdaten, Kampagnenstruktur, Konversions-Definition
- `ad-copy-rules.md` — Copy-Regeln inkl. Duz-Form → Input für `/rsa-maker` und `/offer-maker`
- `keyword-rules.md` — Kampagnen-Namensschema, Bidding-Zuordnung, Schwellwerte
- `search-terms-rules.md` — Negativ-Regeln, WASTED-Schwelle (>30 CHF ohne Conversion)

### `03-historie-impact/` — zwei Jahre Änderungsverlauf
- `Executive-Summary_Kollabo_2024-2025.md` — Verdichtung
- `impact_2024.md` / `impact_2025.md` — Change-Impact-Analysen
- `threshold-kandidaten_2024.md` / `_2025.md` — abgeleitete Schwellwerte
- `learnings.md` — was gewirkt hat und was nicht
- `account-history.md` — Changelog

---

## ⚠️ Wichtig: Die Conversion-Messung ist defekt

Direkt im Konto geprüft am 10.08.2026 (Google Ads UI, 148-770-7588, Zeitraum 11.07.–09.08.2026, Filter „Alle aktivierten"). **Diese Befunde stehen in keiner der Dateien hier** und überschreiben teilweise, was dort dokumentiert ist.

**23 Conversion-Aktionen, 672,57 Conversions im Zeitraum.** Sechs Aktionen sind primär *und* in den Zielvorhaben auf Kontoebene einbezogen — steuern also die Gebote. Davon liefern zwei überhaupt Volumen:

| Aktion | Primär | In Zielvorhaben | Conv. | Quelle |
|---|---|---|---|---|
| `SF: Qualified (2)` | ✅ | ✅ | **158,62** | Offline-Import (Salesforce) |
| `SF - Closed Won (Final)` | ✅ | ✅ | **13,93** | Offline-Import (Salesforce) |
| `Perspective - Montage-Schreiner (web) generate_lead_montage` | ✅ | ✅ | 0 | GA4 |
| `Perspective - Allgemein (web) generate_lead_allg` | ✅ | ✅ | 0 | GA4 |
| `Perspective - Elektro (web) generate_lead_elektro` | ✅ | ✅ | 0 | GA4 |
| `Perscpective - Sanitär (web) generate_lead_sanitär` | ✅ | ✅ | 0 | GA4 |
| `Kollabo.com_Webseite_LIVE_GA4 (web) thank_you_page_view` | ❌ sekundär | ❌ **Nein** | **500,02** | GA4 |

Drei Befunde daraus:

**1. Die dokumentierte Hauptkonversion existiert praktisch nicht.** `account-info.md` nennt `bewerbung_gesendet` als Hauptkonversion. Die Aktion hängt am **Staging**-GA4-Stream (`Kollabo.com_Webseite_Staging_GA4`) und hat **0 Conversions**. Das gilt für **alle zehn Staging-Aktionen** im Konto. Nur der LIVE-Stream liefert. → Beim Lesen von `02-account-config/account-info.md` diese Aussage als überholt behandeln.

**2. Die Aktion mit dem meisten Volumen steuert nichts.** `thank_you_page_view` trägt mit 500,02 den Großteil der 672,57 — ist aber sekundär und nicht in den Zielvorhaben. Sie wird gezählt und ignoriert.

**3. Vier gewerkespezifische Perspective-Aktionen sind gebotssteuernd und liefern null.** Smart Bidding optimiert auf leere Signale. Bei einer ist zusätzlich der Name falsch geschrieben (`Perscpective - Sanitär`).

Dazu stehen alle drei Salesforce-Importe auf **„Überprüfung erforderlich"**.

**Konsequenz für die Unit Economics:** Der in `Kollabo.md` genannte Ø-CPA von **14,53 CHF** bezieht sich auf 158 qualifizierte Leads, nicht auf 500 abgeschickte Bewerbungen. Welche Zahl Kollabo selbst im Kopf hat, ist ungeklärt — das ist die erste Frage im Gatherer-Interview.

---

## Was hier NICHT steht — die offenen Punkte

| Offen | Warum es zählt |
|---|---|
| **Wert einer Vermittlung** | Ohne diese Zahl hat der CPA von 14,53 CHF keinen Vergleichsmaßstab. Das ist bei Kollabo das Äquivalent zum Break-even-ROAS. Herleitbar über Bewerber → Vermittlungsquote → Provision. |
| **Umsatzziel 2026 / Ist 2025** | Kein dokumentiertes Unternehmensziel |
| Welche Conversion Kollabo als „Erfolg" versteht | 500 Bewerbungen oder 158 qualifizierte Leads |
| Zielwert für qualifizierte Leads pro Monat | Monatsbudget 7.500 CHF ist bekannt, Zielmenge nicht |
| Vermittlungsquote qualifizierter Lead → Platzierung | Nötig für die Kette CPA → Cost per Placement |
| UMLAND-Kampagne: Ziel-Länder | Steht als offener Punkt in `config/ads-context.config.json` |
| Ob die Salesforce-Importe verlässlich laufen | Alle drei auf „Überprüfung erforderlich" |

## Konfigurations-Platzhalter, die noch echte Werte brauchen

In `clients/kollabo/config/ads-context.config.json` stehen noch Template-Defaults, die still in Analysen einfließen:

- `searchTermAnalysis.brandedCampaigns: ["Branded campaign name"]` — **Platzhalter.** Laut `keyword-rules.md` heißt die Brand-Kampagne `EX | 25 | CH | SEARCH | LEAD | Brand`. Solange der Platzhalter steht, greift `excludeBrandedCampaigns: true` ins Leere und Brand-Suchbegriffe landen in der Non-Brand-Analyse.
- `ngramAnalysis.defaultAOV: 200` — Default. Bei Lead-Gen ist das der Wert eines Leads, nicht ein Warenkorb. 200 CHF gegen einen CPA von 14,53 CHF ist eine sehr bestimmte Annahme, die niemand geprüft hat.
- `searchTermAnalysis.sharedNegativeLists` — drei Listennamen gesetzt (`Search Term Exclusions`, `Non-Converting N-grams`, `Inefficient N-grams`). Ob die im Konto existieren, ist ungeprüft. Bei Stay Cold wurden sie bewusst auf `null` gesetzt, damit ein Push laut scheitert statt in die falsche Liste zu schreiben.
- `conversionLagDays: 8` — Default, nicht verifiziert.
- `googleAds.loginCustomerId: 5591362086` — die Google-Ads-UI zeigt **Ex Machina Agency 815-273-5088** als direkten Manager über Kollabo. Falls `/gads-context` mit einem Auth-Fehler abbricht, `8152735088` probieren.

## Achtung

Kollabo ist **Lead-Gen, nicht E-Commerce.** Nicht anwendbar: `/feed-auditor`, die Feed-Module von `/pmax-auditor`, das `ecommerce`-Modul von `/lp-auditor`. Kein Merchant Center, kein Produktfeed.

Währung ist **CHF**. Compliance: Schweizer DSG, Swissstaffing Code of Conduct, Arbeitsvermittlungsgesetz AVG. Die **Duz-Form ist verbindlich** — siehe `02-account-config/ad-copy-rules.md`.
