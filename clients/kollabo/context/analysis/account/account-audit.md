# Account Audit — Kollabo

**Datum:** 2026-08-10 · **Modus:** full (24 Diagnostiken, 5 Module) · **Account:** 1487707588
**Vertical:** Lead Gen · **Brand:** Kollabo · **Währung:** CHF
**Datenfenster:** 2026-07-11 – 2026-08-09 (Performance) · Struktur-Pulls tagesaktuell

---

## Executive read

77 % heißt: die Struktur dieses Kontos ist handwerklich gut gebaut und die Probleme liegen woanders. Namenskonvention, Geo-Einstellungen, Display-Netzwerk-Trennung, Brand-Abgrenzung und Ad-Group-Zuschnitt sind allesamt sauber — das ist selten und verdient festgehalten zu werden. Punktverluste kommen fast ausschließlich aus einer einzigen Entscheidung: der Account ist in 30 gewerkespezifische Kampagnen zerlegt, und **keine einzige davon erreicht 30 Conversions im Monat**. 18 von 30 laufen mit unter 10 CHF Tagesbudget. Das ist die strukturelle Ursache dafür, dass Smart Bidding in jeder einzelnen Kampagne zu wenig Signal hat, und es ist die plausibelste Erklärung für die Rang-Limitierung, die in `business.md` §6 dokumentiert ist. Max Conversions mit 5 Conversions pro Monat kann keinen belastbaren Ad Rank aufbauen.

Prio eins ist deshalb Konsolidierung, nicht Feintuning: 30 Kampagnen mit je 0–24 Conversions produzieren zusammen dieselbe Datenmenge wie sechs Kampagnen mit je 25 — nur dass Google im zweiten Fall daraus lernen kann. Prio zwei: vier aktive Kampagnen mit null Conversions bei 85–146 CHF Spend (Abdichter, Kranführer, Montage-Schreiner, Gerüstbauer). Prio drei, und operativ am dringendsten: auf `UMLAND TEST` steht `TEXT_ASSET_AUTOMATION = OPTED_IN` — Google generiert dort Anzeigentexte automatisch. Bei verbindlicher Duz-Form, Swissstaffing Code of Conduct und AVG ist das ein Compliance-Risiko auf der besten Kampagne des Kontos. Weitere 10 Kampagnen haben die Einstellung gar nicht gesetzt und laufen damit auf Google-Default.

Kein Problem sind: Display-Netzwerk (überall aus), Standort-Targeting und -Ausschluss (durchgehend PRESENCE, korrekt), Brand-Trennung (null Leakage, 16 Brand-Varianten sauber in der Brand-Kampagne), Anzeigenrotation, Tracking-Templates, Ad-Group-Benennung (0 generische Namen) und SKAGs (keine).

Der frische `/tracking-specialist`-Report von heute (48 %, „Live-Gebotspfad sauber, nur QUALIFIED_LEAD biddable in allen 30 Kampagnen") bestätigt D24 und **widerspricht teilweise D07**: der Zusammenbruch des Salesforce-Imports (`SF: New Lead (1)` seit 01.07. bei null) bedeutet, dass die vier Null-Conversion-Kampagnen unter dem alten Signal möglicherweise gemessen hätten. Vor einer Pausierung diesen Befund abwarten.

Kein Score-Trend — erster Lauf.

---

## Score

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| **Gesamt** | **124 / 161** | **77 %** | **Good** |
| Structure (D01–D08) | 45 / 75 | 60 % | Needs Attention |
| Naming (D09–D10) | 8 / 8 | 100 % | Excellent |
| Settings (D11–D19) | 44 / 48 | 92 % | Excellent |
| Ad Groups (D20–D23) | 22 / 25 | 88 % | Good |
| Defaults (D24) | 5 / 5 | 100 % | Excellent |

> D15 (Sprache) und D17 (Anzeigenplan) sind SKIP — Felder nicht im GAQL-Pull. Aus dem Nenner genommen.
> 8 beendete Experiment-Kampagnen wurden vor der Auswertung ausgeschlossen.

---

## Kritische Befunde

### 1. AUD-D04 FAIL — Datenfragmentierung: 30 Kampagnen, keine mit 30+ Conversions

| | Wert |
|---|---|
| Aktive Kampagnen | 30 (Schwelle: 15) |
| Mit ≥ 30 Conv/Monat | **0** |
| Bestwert | Brand, 23,9 Conv |
| Zweitbester | UMLAND, 16,0 Conv |
| Median | ~4 Conv |

Smart Bidding braucht 30 Conversions/Monat als Minimum für tCPA, 50+ für stabile Steuerung.
**Keine einzige Kampagne erreicht das.** Alle 30 laufen Max Conversions ohne Zielvorgabe, jede mit
einem eigenen, isolierten Lernpool.

Das ist die strukturelle Erklärung für die in `business.md` §6 dokumentierte Rang-Limitierung
(29/30 Kampagnen). Ein Gebotsalgorithmus mit 5 Conversions Monatssignal bietet konservativ und
verliert die Auktion — nicht am Budget, sondern an der Sicherheit seiner eigenen Schätzung.

**Routing:** `/bidding-auditor` (Konsolidierungs-Kandidaten nach CPA-Homogenität),
`/budget-auditor`. **Guardrail beachten:** `business.md` §8.4 — Portfolio-Bündelung nur bei
CPA-Variationskoeffizient ≤ 30 %. Der Portfolio-Versuch 2025 scheiterte bei CV 52 % (7/8 negativ).
Konsolidierung heißt hier **Kampagnen zusammenlegen**, nicht Portfolio-Strategie darüberlegen.

### 2. AUD-D05 FAIL — 18 von 30 Kampagnen unter 10 CHF Tagesbudget

| Budget | Kampagnen |
|---|---|
| 3 CHF | Baumaschinenführer, Dachdecker, Metallbaukonstrukteur, Gerüstbauer, Trockenbauer |
| 4 CHF | Kranführer, Automatikmonteur, Montage-Schreiner |
| 5 CHF | Produktionsmechaniker, Abdichter, Zimmermann, Maurer |
| 6–9 CHF | Polymechaniker, Gärtner, Montage-Elektriker, Schweisser, Metallbauer, Automatiker |

Alle 18 verfolgen dieselbe Absicht (Handwerker-Lead-Gen) und unterscheiden sich nur im Gewerk.
Bei 3 CHF/Tag und einem CPC von ~1,3 CHF sind das gut zwei Klicks pro Tag.

*Hinweis: Die Minimalbudgets sind eine bewusste Entscheidung — `business.md` §8.10 hält den
Kundenwunsch „keine Profession pausieren" fest. Die Alternative zur Pause war das Minimum.
Konsolidierung löst beides.*

### 3. AUD-D07 FAIL — Vier aktive Kampagnen ohne Conversion

| Kampagne | Spend | Impressionen | Budget |
|---|---|---|---|
| Abdichter | 146,46 | 1.209 | 5 |
| Kranführer | 119,89 | 915 | 4 |
| Montage-Schreiner | 115,28 | 1.003 | 4 |
| Gerüstbauer | 85,42 | 307 | 3 |

Zusammen **467 CHF ohne messbaren Ertrag**. Drei liegen über der 100-CHF-Schwelle → FAIL.

> ⚠️ **Widerspruch zum Tracking-Audit (2026-08-10):** `SF: New Lead (1)` liefert seit 01.07.
> null und wurde aus der Conversions-Metrik genommen. Diese vier Kampagnen könnten unter dem
> alten Signal gemessen haben. **Nicht pausieren, bevor der Import-Befund geklärt ist.**
> Gerüstbauer ist ohnehin als strukturelles Nachfrage-Problem dokumentiert (T1-Test, 307
> Impressionen in 30 Tagen = der Markt ist zu klein).

### 4. AUD-D19 WARN — Google schreibt Anzeigentexte auf der besten Kampagne um

| Einstellung | Kampagnen |
|---|---|
| `TEXT_ASSET_AUTOMATION = OPTED_OUT` | 19 |
| **`TEXT_ASSET_AUTOMATION = OPTED_IN`** | **1 — `EX \| DE \| DACH \| SEARCH \| LEAD \| UMLAND TEST`** |
| Kein Eintrag (= Google-Default) | 10: Brand, Dachdecker, Maler, Montage-Elektriker, Automatiker, Sanitärinstallateur, Metallbauer, Schweisser, Polymechaniker, Produktionsmechaniker |

UMLAND ist die Kampagne mit dem besten CPA im Konto (37,23) und dem stärksten Rang-Verlust
(78,5 %). Dort automatisch generierte Anzeigentexte laufen gegen drei dokumentierte Vorgaben:
verbindliche **Duz-Form**, **Swissstaffing Code of Conduct** (keine übertriebenen Jobversprechen)
und **AVG**. Die erlaubten quantitativen Claims sind in `business.md` §12 abschließend
aufgezählt — automatisch erzeugte Headlines können sie nicht einhalten.

Deckt sich mit dem offenen Item „Auto-Apply-Empfehlungen deaktivieren" (seit Mai 2026,
im Aktionsplan vom 30.06. als „höchstes aktives Risiko" markiert, seither unbestätigt).

---

## Ergebnisse je Modul

### Structure (D01–D08) — 45/75

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D01 | Kampagnentyp-Trennung | PASS | 10/10 | 30/30 SEARCH, `target_content_network = false` auf allen. Keine Vermischung. |
| D02 | Brand/Non-Brand | PASS | 10/10 | **0 Brand-Terms in Nicht-Brand-Kampagnen.** 16 Brand-Varianten sauber in der Brand-Kampagne (kollabo, kolabo, collabo, kollabro, kollabi, kolaboo, + regionale). Kein PMax → keine ungeprüfte Fläche. |
| D03 | Business-Alignment | PASS | 5/5 | Lead Gen, Search-only. Jede Kampagne bildet ein in `business.md` §1 gelistetes Gewerk ab. Brand, Compeditor und DYN Catchall haben dokumentierte Sonderrollen. |
| D04 | Kampagnenanzahl-Effizienz | **FAIL** | 0/5 | 30 Kampagnen, **0 mit ≥ 30 Conv**. Siehe Befund 1. |
| D05 | Budget-Fragmentierung | **FAIL** | 0/5 | 18/30 unter 10 CHF/Tag bei identischer Absicht. Siehe Befund 2. |
| D06 | Targeting-Überschneidung | WARN | 5/10 | 5 von 369 Keywords (**1,4 %**) in 2 Kampagnen: `elektriker stellenangebote` + `montage elektriker efz` (Elektro ↔ Montage-Elektriker), `polymechaniker schweiz` + `trockenbauer jobs schweiz` (↔ UMLAND), `cnc fräser jobs` (Metallbaukonstrukteur ↔ Polymechaniker). Alle sind bekannte Overlaps aus der Relevanzmatrix. |
| D07 | Null-Conversion-Kampagnen | **FAIL** | 0/15 | 4 Kampagnen, 467 CHF. Siehe Befund 3. |
| D08 | Null-Impression-Kampagnen | PASS | 15/15 | Keine. Alle 30 aktiven Kampagnen liefern aus. |

### Naming (D09–D10) — 8/8

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D09 | Kampagnen-Namenskonvention | PASS | 5/5 | **100 %** folgen `EX \| {Jahr} \| {Land} \| SEARCH \| LEAD \| {Gewerk}`. Vorbildlich. |
| D10 | Ad-Group-Benennung | PASS | 3/3 | **0 generische Namen.** Konvention `AG \| RSA \| {Gewerk}`, Sonderfälle sprechend benannt (`DYN \| Catchall`, `STAN \| HOME \| BROAD`, `Kollabo Name`). Einziger Mangel: Tippfehler `Metallbaukonstukteur` (fehlendes r) in 2 Ad Groups. |

### Settings (D11–D19) — 44/48

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D11 | Display-Netzwerk (Search) | PASS | 10/10 | 0 von 30 Kampagnen mit Content-Network. |
| D12 | Suchpartner | WARN | 3/5 | **29 von 30 aktiviert**, ohne dokumentierte Begründung. Netzwerk-segmentierte Performance prüfen — bei rang-limitiertem Konto lohnt der Blick, ob Partner-Traffic den CPA hebt. |
| D13 | Standort-Targeting | PASS | 10/10 | `PRESENCE` auf allen 30. Korrekt — kein „Anwesenheit oder Interesse", also keine Streuung auf CH-Interessierte im Ausland. |
| D14 | Standort-Ausschluss | PASS | 10/10 | `PRESENCE` auf allen 30. Korrekt konfiguriert. |
| D15 | Sprach-Targeting | SKIP | — | Feld nicht im GAQL-Pull. Manuell prüfen: Website ist ausschließlich DE (CH). |
| D16 | Anzeigenrotation | PASS | 3/3 | `OPTIMIZE` auf allen 30. |
| D17 | Anzeigenplan | SKIP | — | Nicht über diesen Pull verfügbar → `/geo-schedule-auditor`. |
| D18 | Tracking-Template | PASS | 5/5 | Alle 30 haben ein Template. 3 Varianten, jede mit erkennbarem Zweck: `utm_campaign=search` (28), `ch_brand` (1), `ch_prio3` (1). |
| D19 | URL-Expansion / Asset-Automation | WARN | 3/5 | 1× OPTED_IN (UMLAND), 10× ungesetzt. Siehe Befund 4. |

### Ad Groups (D20–D23) — 22/25

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D20 | Thematische Enge | PASS | 5/5 | 33 Ad Groups mit Keywords, jede an ein Gewerk gebunden. 2–23 Keywords je Gruppe, Median ~12. Die Relevanzmatrix aus `search-terms-rules.md` ist konsequent umgesetzt. |
| D21 | Anzeigen je Ad Group | WARN | 7/10 | 33 von 34 Ad Groups mit aktiver RSA. `DYN \| Catchall` hat keine — sie liefert aber 3.496 Impressionen und 5,5 Conversions, ist also eine **DSA-Ad-Group** (dynamische Anzeigen erscheinen nicht im RSA-Pull). Kein echter Defekt, aber verifizieren. **Wichtiger:** 8 Ad Groups haben nur **1** aktive RSA — zu wenig für Rotation und Asset-Lernen. |
| D22 | Impressions-Verteilung | PASS | 5/5 | 0 Ad Groups unter 10 Impressionen/Woche. Schwächste (`Trockenbauer`, 170 in 30 T) liegt noch über der Schwelle. Top-3 vereinen 26,8 % — gesunde Streuung. |
| D23 | SKAG-Erkennung | PASS | 5/5 | **0 SKAGs.** Keine Ad Group mit nur einem Keyword. |

### Defaults (D24) — 5/5

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| D24 | Konto-Standardeinstellungen | PASS | 5/5 | **Alle 30 aktiven Kampagnen auf `goal_config_level = CAMPAIGN`** — bewusst konfiguriert, nicht Default. Bestätigt durch den Tracking-Audit von heute: in allen 30 ist ausschließlich `QUALIFIED_LEAD` gebotswirksam. |

---

## Nebenbefund: Match-Type-Verteilung korrigiert die Aktenlage

`keyword-rules.md` (28.04.2026) hält fest: „alle aktiven Keywords auf Weitgehend passend (Broad)".
**Das gilt nicht mehr.** In aktiven Ketten stehen heute:

| Match Type | Keywords (strukturell) | Keywords mit Impressionen | Spend | Conv | CPA |
|---|---|---|---|---|---|
| BROAD | 162 | 138 | **6.639,57 (88 %)** | 131,25 | **50,59** |
| PHRASE | 139 | 106 | 779,84 (10 %) | 11,86 | 65,74 |
| EXACT | 85 | 54 | 156,66 (2 %) | 1,00 | 156,66 |

Die Verengung hat also stattgefunden — aber **88 % des Spends fließt weiter über Broad**, und
Phrase liefert bislang den *schlechteren* CPA (65,74 vs 50,59). Exact ist mit 1 Conversion
statistisch wertlos. Das ist ein Auftrag für `/keyword-auditor`, nicht für die Struktur.
`business.md` §4.4 wurde entsprechend korrigiert.

---

## Routing

| Befund | Ziel | Status |
|---|---|---|
| D04/D05 Fragmentierung + Minimalbudgets | `/bidding-auditor`, `/budget-auditor` | **Beide in diesem Lauf noch offen** — Konsolidierungsvorschlag dort einholen |
| D07 Null-Conversion-Kampagnen | Klärung SF-Import zuerst | **Blockiert** durch Tracking-Befund 1 (Report von heute: `context/analysis/tracking/tracking-audit.md`) |
| D19 Asset-Automation UMLAND | Google Ads UI, sofort | Manuell — 5 Min |
| D06 Keyword-Overlap (5 KW) | `/keyword-auditor` | offen |
| D21 8 Ad Groups mit nur 1 RSA | `/rsa-maker` | offen |
| D12 Suchpartner-Performance | `/geo-schedule-auditor` (Netzwerk-Segment) | offen |
| Match-Type-Effizienz (Phrase schlechter als Broad) | `/keyword-auditor` | offen |
| D15 Sprach-Targeting, D17 Anzeigenplan | `/geo-schedule-auditor` | offen |

**Frische Peer-Reports integriert:**
`/tracking-specialist` (2026-08-10, 48 %) — bestätigt D24, widerspricht D07. Kernaussage:
„Live-Gebotspfad sauber: 34/37 aktive Kampagnen kampagnenspezifisch, nur QUALIFIED_LEAD biddable."

---

## Datenfrische

| Quelle | Zeilen | Stand |
|---|---|---|
| `account/campaigns-settings.csv` | 319 | 2026-08-10 (frisch) |
| `account/keywords-all.csv` | 3.550 | 2026-08-10 (frisch) |
| `account/conversion-goal-config.csv` | 319 | 2026-08-10 (frisch) |
| `campaigns.csv` | 331 | 2026-08-10 |
| `adgroups.csv` / `ads.csv` / `keywords.csv` | 34 / 1.183 / 298 | 2026-08-10 |
| `context/account-changelog.md` | — | **fehlt** |
