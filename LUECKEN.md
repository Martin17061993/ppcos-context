# Bekannte Lücken und Fallstricke

Vor dem ersten eigenen Lauf lesen. Alles hier stammt aus den Setup-Logs und
Session-Protokollen der bisherigen Läufe — nicht aus Vermutungen.

---

## 1. Was beim Kontext-Aufbau gefehlt hat

### Stay Cold — Setup-Log 03.08.2026 (`/ads-context-gatherer`)

| Punkt | Status heute |
|---|---|
| **`business.md` war auf Lead-Gen konfiguriert** — Form Submit / Phone Call als Conversions, USD-Ziele, 150 $/Lead. Das ist ein EUR-E-Commerce-Konto. Wurde gemeldet, aber bewusst nicht automatisch überschrieben. | behoben — `business.md` ist neu aufgebaut (E-Commerce, EUR, Break-even Clean ROAS 1,9) |
| **`account-changelog.md` fehlte** — `/account-changelog` war nie gelaufen | behoben am 06.08., liegt im Repo |
| `/pages/what-customers-say` → 404, richtiger Pfad ist `/pages/reviews` | behoben |
| `reviews.md` ist **unvollständig** — das REVIEWS.io-Widget rendert clientseitig, die Review-Texte wurden nie erfasst. Nur Rating + Anzahl aus dem Live-DOM. | **offen** |
| Farb-Extraktion meldete Header-Hintergrund als `transparent` (Schwarz liegt auf `div.header__wrapper`), Full-Page-Screenshot lief in einen Protokoll-Timeout | manuell korrigiert, Palette stimmt |

**Folgeschaden aus dem fehlenden Changelog:** Im Bidding-Audit vom 06.08. blieb das
Modul *Learning Phase* komplett unbewertet — 15 Punkte aus der Wertung genommen, weil
`learning-state.csv` ohne Changelog keine Änderungsdaten hatte. `in_learning = no` war
ein Engine-Default, **keine Messung**. Wer den Changelog nicht zieht, bekommt still ein
verfälschtes Bidding-Ergebnis.

### Kollabo — Setup 10.08.2026

| Punkt | Status heute |
|---|---|
| **`brand.md` fehlt komplett.** Ersatz: `business.md` §12 + `pre-knowledgebase-nodes/01-kunden-kontext/` + Live-Seitentexte. | **offen** — bewusst so, aber wer `brand.md` erwartet, findet nichts |
| **`csv-parse` fehlte flächendeckend** in allen Skill-Scripts — `npm install` musste für jedes Script nachgeholt werden | bei dir vermutlich erneut nötig nach `ppcos init` |
| Kein `context/website/` und keine `brand-colours/palette.md` (nie gelaufen) | **offen** |
| Kein `.logs/` — der Gatherer lief hier nie im vollen Modus | **offen** |

---

## 2. Was heute noch offen ist

### Stay Cold

- **`/tracking-specialist` fehlte über alle 13 Audits hinweg** und ist genau der Lauf, der jeden
  Wirtschaftlichkeits-Input validiert hätte. Inzwischen gelaufen (Score 66 %), aber D13–D16
  wurden übersprungen: der volle Conversion-Test hätte einen echten Add-to-Cart im Live-Shop
  erzeugt. **SKIP, nicht FAIL** — nicht als Abdeckung lesen.
- **Feed-Audit ist blockiert, nicht gelaufen.** `context/analysis/feed/feed-preflight-blocked.md`
  erklärt es: Der gespeicherte Refresh-Token trägt Ads-Scopes, keine Merchant-Scopes.
  Merchant-Account **116274940** ist bereits ermittelt und in der Config hinterlegt,
  `merchantCenter.enabled` steht **absichtlich auf `false`**, damit Läufe klar scheitern
  statt verwirrend. Freischalten: `/merchant-auth "Stay Cold Apparel"`, dann `/feed-auditor full`.
- **`offer-angles.md` existiert nicht.** Das LP-Audit fand punk/goth/metal/rocker **null Mal**
  auf der Non-Brand-Landingpage, während `brand.md` genau dieses Material belegt führt.
  Das Angebot ist stark (97 %) und schlicht nicht ausgespielt (LP 56 %). Route: `/offer-maker angles`.
- **Zwei N-Gram-Shared-Lists existieren nicht.** Die Config nannte früher drei Listen, von denen
  keine im Konto war — Schreibvorgänge wären still fehlgeschlagen. Real existieren genau zwei
  Sets: `EX I ALL` (78 Keywords, id 9606244993) und `EXCLUSIONS FOR BRAND` (3.135, id 11415316346).
  Die beiden N-Gram-Listen stehen in der Config auf `null`, damit ein Lauf laut scheitert.
  **Anlegen, bevor N-Gram-Push aktiviert wird** (Gap G20).
- **`competitors.domains` ist leer.** Die Marken sind dokumentiert (Killstar, DropDead, Disturbia,
  Sullen, Named Collective, Blackcraft Cult, Bad Monday), die Domains nicht verifiziert.
  Raten würde `/competitor-scraper` auf die falschen Advertiser schicken.
- **Offene Zahlen-Gaps:** G1 (brutto vs. netto verschiebt Break-even 1,6 ↔ 1,9 — die folgenreichste
  unverifizierte Zahl), G8 (2 % Zahlungsgebühr und 6 € Versand sind Annahmen, die direkt in den
  Break-even laufen), G2 (Wiederkaufrate/CLV nicht verfügbar, obwohl das Konto +16,46 € Neukunden-Bonus zahlt).
- **Governance-Widerspruch, ungelöst:** `business.md` §13 sagt „Martin schlägt vor, Jonas führt aus,
  keine Ausnahmen". Der Changelog zeigt: alle 5 Budget- und 3 Target-Änderungen der letzten 30 Tage
  kamen von `exmachina.agency@gmail.com` über die Web-UI, dazu 266 nicht zugeordnete Editor-Änderungen.
- **Consent Mode v2** ist vollständig implementiert, aber alle vier Signale defaulten auf `granted`.
  Für einen in Berlin registrierten Werbetreibenden ist das die einzige Feststellung mit
  rechtlichem Gewicht. Braucht eine saubere Inkognito-Gegenprobe.

### Kollabo

- **Auto-Apply-Recommendations:** Zwei maskierte `recommendation_subscription`-Einträge verursachen
  automatische Keyword-Entfernungen (30.07., 21.08., 27.08.). Über die API nicht abschaltbar
  (`BAD_RESOURCE_ID`), auf beiden MCCs existiert kein Override. **Nur über die UI abstellbar:**
  Tools → Empfehlungen → „Automatisch angewendet" → alle Haken raus. Nachkontrolle per GAQL,
  alle 12 müssen `status 3` tragen.
- **`search-terms-rules.md` ist veraltet.** Die Regel „fremdsprachig → NKL_Generisch" ist widerlegt:
  fremdsprachiger Traffic ist profitabel (1.195 CHF / 44,2 Conv / **CPA 27,04** gegen
  Non-Brand-Schnitt 31,99). Der N-Gram-Motor schlug genau diese Terms zur Negation vor.
  Regel korrigieren, bevor jemand den Vorschlägen folgt.
- **N-Gram-Engine rechnet mit `0,01` statt `0` Conversions** (Divisionsschutz) und erzeugt
  CPA-Artefakte bis 14.443 CHF. ST-D13 fiel dadurch fälschlich auf 0, ST-D14 auf 18 Flags.
- **Keine tragfähige Negationsbasis:** Kein einziger der 155 nicht konvertierenden Suchbegriffe
  erreicht 20 Klicks (Max 18) — Kollabos eigene Mindestentscheidungsbasis aus `business.md` §8.
  Es wurde bewusst nichts negiert.
- **Offene Chance, nicht umgesetzt:** `temporärbüro`-Cluster, 1.020 CHF / 46,19 Conv / **CPA 22,09**,
  verteilt über 26 Kampagnen per Broad-Zufall. Ein generisches `temporärbüro`-Keyword existiert nicht.
- **Zwei Minuten-Fixes auf der Website, offen:** „Facebook Rating 0" steht sichtbar neben
  „Google Rating 4.9"; und der abgebrochene Satz „Jeder dritte Bewerber findet den neuen direkt
  über kollabo" — es fehlt „Job" (korrekter Claim in `business.md` §12).
- **Lead-Wert wird nicht gemessen.** Cost-per-Lead ja, Vermittlungsquote / Umsatz pro Lead nein.
  Laut Executive Summary der größte offene Hebel.

---

## 3. Struktureller Unterschied der beiden Kontexte

Stay Cold ist deutlich vollständiger aufgebaut als Kollabo:

| | Stay Cold | Kollabo |
|---|---|---|
| `brand.md` | ✅ | ❌ |
| `brand-colours/palette.md` | ✅ | ❌ |
| `website/pages/` | ✅ 20 Seiten | ❌ |
| Feed-/PMax-/Placement-Audits | ✅ (Feed blockiert) | ❌ nicht anwendbar (Lead-Gen, kein Shopping) |
| `.logs/` vom Gatherer | ✅ | ❌ |

Das ist kein Versehen im Export — die Dateien existieren auf Kollabo-Seite schlicht nicht.
