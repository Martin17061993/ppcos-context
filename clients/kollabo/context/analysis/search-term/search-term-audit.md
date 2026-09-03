# Search Term Audit — Kollabo

**Datum:** 2026-08-18 · **Modus:** full (26 Diagnostiken, 5 Module) · **Account:** 1487707588 (Kollabo)
**Fenster:** 90 Tage (Haupt) / 120 Tage (N-Gram) · **Conversion-Lag:** 14 T · **Währung:** CHF
**Datenbasis:** 36.902 Suchbegriffs-Zeilen · 47.250 N-Gram-Zeilen · 386 aktive Keywords · Experimente ausgeschlossen
**Ziele:** targetCPA 50 · maxCPA 75 · targetROAS n/a (Lead-Gen ohne Conversion-Werte)

---

## Executive read

**81 % — und der Score sagt hier etwas Unbequemeres als „gut": die Suchbegriffs-Ebene dieses Kontos ist nicht das Problem, und sie hat auch kaum etwas anzubieten, das man reparieren könnte.** Von 36.902 Suchbegriffen über 90 Tage bleiben nach allen Filtern 155 nicht-konvertierende Terms mit zusammen 1.148 CHF übrig. Kein einziger davon erreicht 20 Klicks — Kollabos eigene, aus 149 bewerteten Änderungen validierte Mindestentscheidungsbasis. Der teuerste hat 18. Es gibt in diesem Konto derzeit **keine einzige statistisch tragfähige Negation.** Wer trotzdem negiert, rät.

Die wichtigste Zahl des Laufs ist eine, die der Report fast nicht produziert hätte: **fremdsprachiger Traffic kostet 1.195 CHF und liefert 44,2 Conversions — CPA 27,04.** Das ist besser als der Nicht-Brand-Schnitt des Kontos (31,99) und liegt 46 % unter dem Zielwert. Spanisch 27,73 · Italienisch 20,57 · Portugiesisch 24,66. Der N-Gram-Motor hat genau diese Terms als Negativ-Kandidaten geflaggt — `idioma`, `extranjeros`, `trabalho temporario`, `offerte lavoro`. Sie zu negieren hätte das effizienteste Segment des Kontos abgeschaltet. `business.md` §1 nennt Zuwanderer als Kern-Zielgruppe und „mehrsprachige Beratung" als USP; die Daten bestätigen das. **Diese Empfehlung ist damit dauerhaft vom Tisch** — sie stand schon im Lauf vom 10.08. als Widerspruch drin.

Die zweite Zahl ist die eigentliche Chance. **`temporärbüro*` liefert 1.020 CHF bei CPA 22,09** — verteilt über 26 Kampagnen, eingesammelt per Broad-Match-Zufall. Der gesamte `temporär*`-Cluster: 1.879 CHF, 65,87 Conversions, CPA 28,53, 28 Kampagnen. Die 16 existierenden `temporär`-Keywords sind **alle gewerkegebunden** („elektriker temporär", „temporärbüro maler"). Ein generisches `temporärbüro`-Keyword existiert nicht. Dieselbe Query läuft dadurch bis zu fünfmal parallel — `temporärbüro wädenswil` steht in 5 Kampagnen gleichzeitig.

Was **kein** Problem ist: die Negativ-Abdeckung. Alle 30 aktiven Kampagnen haben Negative und Shared-List-Anbindung, 0 Konflikte, 0 doppelte Ad-Group-Negative. Die vom Script gemeldeten „265 Kampagnen ohne Negative" sind **zu 100 % pausiert** — derselbe Fehlalarm wie am 10.08.

Frische Peer-Reports stützen die Diagnose geschlossen: `/strategy-specialist` (10.08., 55 %) hält als D13 FAIL fest — *„30 von 30 Kampagnen laufen Max Conversions ohne jede Zielvorgabe"*; genau das erscheint hier als `target_source=fallback` auf **155 von 155** geflaggten Datensätzen. `/competitive-analyst` (11.08., 41 %) misst den 90-Tage-CPA auf **27,25** statt 49,98 — der hier verwendete Zielwert 50 stammt aus einem messgeschädigten 30-Tage-Fenster und ist damit fast doppelt so lasch wie die Realität. `/lp-auditor` (11.08., 60 %) und `/quality-score-auditor` (10.08., 44 %) lokalisieren den Engpass unverändert bei der LP-Erfahrung.

**So liest du den Score:** 81 % ist keine Aufforderung zum Aufräumen, sondern ein Beleg, dass hier nichts zu holen ist. Modul „Close Variants" ist SKIP — das Script liefert auf 100 % der Datensätze leere `match_types`, die Diagnostik ist nicht durchführbar. **Trend: 76 % (10.08.) → 81 %.** Der Anstieg ist überwiegend Methodik (Variants jetzt SKIP statt 15/15), nicht Verbesserung; nach der Methodik des Vorlaufs wären es 84 %.

---

## Diagnose

**Die Wurzel liegt zwei Ebenen über den Suchbegriffen — im Business-Layer, nicht im Traffic-Layer.** Alle 30 aktiven Kampagnen laufen Max Conversions ohne Zielvorgabe (`target_source=fallback` auf allen 155 Flags). Ein Konto ohne CPA-Ziel gibt sein Budget unabhängig vom CPA aus; jede „ineffizient"-Aussage in diesem Report ist deshalb gegen einen Wert gemessen, den das Konto selbst nirgends anstrebt — und dieser Wert (50 CHF) stammt zudem aus einem Fenster, dessen Messung laut `business.md` §3 defekt war. Das Richtige zuerst: **Ziele setzen, nicht Terms negieren.** Der einzige Eingriff, der unabhängig davon Rendite bringt, ist die Strukturierung des `temporärbüro`-Clusters — dort wird nachweislich profitable Nachfrage per Zufall eingesammelt statt bedient.

---

## Evidence Ladder

### Measurement-Layer
- `SF: New Lead (1)` liefert seit 01.07.2026 exakt null und steht auf `include_in_conversions_metric=false`; Gebotssignal −63 % gegenüber April. → **H1**
- Klick-Lookback der drei Salesforce-Aktionen steht auf 90 Tagen, obwohl 98,5 % der Conversions binnen 30 Tagen eintreffen — Attributions-Credit wird über ein Quartal verteilt. → **H1**
- 15 der 268 Promotion-Kandidaten zeigen **≥2 Conversions bei ≤1 Klick** (z. B. `montage arbeit schweiz`: 1 Klick, 2,00 Conv, 0,82 CHF). Auf Suchbegriffs-Ebene ist die Conversion-Zuordnung damit nicht belastbar. → **H1**
- Nur 310 von 36.902 Suchbegriffen tragen überhaupt eine Conversion; 36.580 Zeilen stehen auf exakt 0. → **H1**

### Business-Layer
- **155 von 155 geflaggten Datensätzen tragen `target_source=fallback`** — kein einziges Flag stammt aus einer zielgebundenen Kampagne. → **H2**
- 0 der 30 aktiven Kampagnen nutzt Portfolio-Bidding. Die 34 vom Script „portfolio-resolved" gemeldeten Kampagnen sind **sämtlich pausiert** (Altlast „Portfolio Test JM" + DE_GSN-Struktur). Kein Portfolio-Hinweis nötig. → **H2**
- Zielwert 50 CHF vs. gemessener 90-Tage-CPA 27,25 CHF (`/competitive-analyst`) bzw. 28,18 CHF über sichtbare Suchbegriffe. Die Schwelle ist ~1,8× zu lasch. → **H2**
- `targetROAS` ist null und `conversionActionValues` stehen auf 0 (GAP-1) — jede ROAS-basierte Diagnostik ist strukturell nicht bewertbar. → **H2**

### Traffic-Layer
- 155 nicht-konvertierende Terms / 1.148,46 CHF / 524 Klicks. **Maximum 18 Klicks pro Term — kein einziger erreicht die 20-Klick-Schwelle.** → **H3**
- Fremdsprachiger Traffic: 1.195,30 CHF, 44,20 Conv, **CPA 27,04** (ES 27,73 · IT 20,57 · PT 24,66 · RO 10,50). Besser als Nicht-Brand-Schnitt 31,99. → **H4**
- `temporär*`: 1.879,35 CHF, 65,87 Conv, **CPA 28,53**, 3.805 Terms, 28 Kampagnen. Sub-Cluster `temporärbüro*`: 1.020,30 CHF, 46,19 Conv, **CPA 22,09**, 26 Kampagnen. → **H5**
- Alle 16 vorhandenen `temporär`-Keywords sind gewerkegebunden; **kein generisches `temporärbüro`-Keyword existiert.** → **H5**
- 9 generische Ortsbegriffe konkurrieren kampagnenübergreifend; `temporärbüro wädenswil` läuft in **5 Kampagnen** parallel. → **H5**
- Abdeckungsquote **3,2 %** — 10 von 310 konvertierenden Begriffen sind Keyword (Vorlauf: 3,8 %). Bei 88 % Broad-Spend und Broad-CPA 50,59 < Phrase-CPA 65,74 ist das jedoch **strategiekonform**, kein Defekt. → **H5**
- Von 18 als „ineffizient" geflaggten N-Grams sind **14 unterpowert** (<20 Klicks). Die restlichen 4 (`ab`, `ab sofort`, `suche`, `offerte`) sind deutschsprachige Zielgruppensprache bzw. Teil eines konvertierenden Sprachclusters. → **H3**
- 2 Legacy-Negative mit `+`-Syntax in Montage-Schreiner: `+bankschreiner`, `+möbelschreiner`. Die Roadmap führt parallel T4 „Bankschreiner-Reaktivierung — Bankschreiner verschollen". → **H6**
- 3 Shared-Negativ-Listen ohne jede Kampagnen-Anbindung: `Negative KWs`, `Negative KWs 1-Campaigns`, `Negative KWs DE`. → **H6**

---

## Module Scores

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| 1 · Search Term Quality (D01–D05) | 21 / 25 | 84 % | Good |
| 2 · Negative Coverage (D06–D12) | 20,71 / 25 | 83 % | Good |
| 3 · N-gram Analysis (D13–D16) | 16 / 20 | 80 % | Good |
| 4 · Close Variants (D17–D19) | **SKIP** | — | keine Match-Type-Daten |
| 5 · Promotion & PMax (D20–D22) | 3,6 / 6 | 60 % | Needs Attention |
| **GESAMT** | **61,31 / 76** | **81 %** | **Good** |

> **Nenner-Reduktionen:** Modul 4 komplett SKIP (−15) — `match_types` ist auf **allen** 423 geprüften Datensätzen leer, D17/D18/D19 sind nicht durchführbar. D25/D26 SKIP (−6) — keine PMax-Kampagne im Konto (PMax-Pull: 0 Zeilen). D22 INFO (−3) — Abdeckungsquote ist bei Broad-geführter Strategie kein Defekt.
>
> **Trendvorbehalt:** Der Vorlauf (10.08., 76 %) wertete Variants als 15/15 statt SKIP und N-Gram über 15 statt 20 Punkte. Bei identischer Methodik läge dieser Lauf bei **84 %**.

---

## Actions

### 🔍 Investigate first — blockierende Upstream-Klärung

| # | Was | Warum | Wohin |
|---|---|---|---|
| 1 | **Salesforce-Import-Mapping klären** | `SF: New Lead (1)` seit 01.07. bei null, `Qualified` gegenläufig gestiegen. Solange offen ist, ob New-Lead-Datensätze als Qualified importiert werden, ist jede CPA-Zahl in diesem Report mit Vorbehalt. | **Bestehenden Report lesen:** `context/analysis/tracking/tracking-audit.md` (10.08., 48 %) — Top-Befund: *„`include_in_conversions_metric = false`, 0 Conversions seit 01.07.2026 — war die volumenstärkste Aktion des Kontos."* Kein Re-Run nötig. Offene Frage geht an Kollabo/Salesforce. |
| 2 | **Klick-Lookback 90 → 30 Tage** | 90 Tage erfassen nur 1,5 % zusätzliche Conversions, verteilen den Credit aber über ein Quartal. Das verunschärft jedes Fenster in diesem Report. | **Bestehenden Report lesen:** `tracking/tracking-audit.md` Befund 2. Umsetzung im UI. |
| 3 | **Attribution auf Suchbegriffs-Ebene prüfen** | 15 Kandidaten mit ≥2 Conv bei ≤1 Klick. Bis das erklärt ist, trägt **kein** Promotion-Vorschlag aus Modul 5. | Neuer Befund aus diesem Lauf → an Kollabo/Salesforce zusammen mit #1 |

### 🔧 Structural fix needed — Ziel- und Conversion-Ebene

| # | Was | Warum | Wohin |
|---|---|---|---|
| 4 | **Zielvorgaben setzen (30/30 Kampagnen)** | `target_source=fallback` auf allen 155 Flags. Ohne Ziel ist „ineffizient" nicht definiert — und dieser Report kann seine Kernfrage nicht beantworten. | **Bestehenden Report lesen:** `context/analysis/strategy/strategy-audit.md` (10.08., 55 %) — D13 FAIL: *„30 von 30 Kampagnen laufen Max Conversions ohne jede Zielvorgabe, obwohl der Primär-KPI CPA-Steuerung ist."* |
| 5 | **Zielwert von 50 auf ~27–30 CHF korrigieren** | Der 90-Tage-CPA liegt bei 27,25 (competitive) / 28,18 (dieser Lauf). Der Config-Wert 50 stammt aus dem messgeschädigten 30-Tage-Fenster und macht jede Schwelle zu lasch. | `config/ads-context.config.json → searchTermAnalysis.targetCPA` — **erst nach #1**, danach `/strategy-specialist` |
| 6 | **`ab sofort` / `suche` sind ein Conversion-Problem, kein Traffic-Problem** | 135 Klicks / 132 CHF / 0 Conv bzw. 63 Klicks / 62 CHF / 0 Conv. Beides ist Zielgruppensprache („temporär jobs ab sofort", „ich suche arbeit in schweiz"). Wer hier negiert, schaltet Nachfrage ab statt sie zu bedienen. | **Bestehende Reports lesen:** `lp/lp-audit.md` (11.08., 60 %) — *„das hier ist keine Landingpage, es ist eine Website-Seite. 114 Links… jeder ist ein Ausgang aus dem Bewerbungsprozess."* · `offer/offer-audit.md` (11.08., 78 %) — *„12,4× CVR-Spanne bei identischer Vorlage."* |

### ✅ Act now (safe) — überlebt die Kaskade

| # | Was | Umfang | Wohin |
|---|---|---|---|
| 7 | **`temporärbüro`-Struktur bauen** | 1.020 CHF bei CPA 22,09 über 26 Kampagnen eingesammelt, ohne dass ein generisches Keyword existiert. Dazu 9 Ortsbegriffe in bis zu 5 Kampagnen parallel. Eigene Ad Group oder Kampagne beendet die Kannibalisierung und macht den Cluster steuerbar. | `/search-term-optimizer promote` — **einziger Eingriff, der unabhängig von #1–#6 trägt** |
| 8 | **2 Legacy-`+`-Negative bereinigen** | `+bankschreiner`, `+möbelschreiner` in Montage-Schreiner. Prüfen, ob sie die Roadmap-Aufgabe T4 „Bankschreiner verschollen" verursachen — das wäre die Erklärung. | `/search-term-optimizer conflicts` |
| 9 | **3 verwaiste Shared-Listen klären** | `Negative KWs`, `Negative KWs 1-Campaigns`, `Negative KWs DE` — 0 Kampagnen-Anbindung. Entweder anbinden oder löschen. | manuell im UI / `/account-auditor` |
| 10 | **Auto-Apply abschalten** | Am 30.07. hat Google selbstständig ein negatives Keyword in Metallbauer angelegt. Solange das läuft, ist jede Negativ-Arbeit in diesem Konto nicht attribuierbar — und dieser Report nicht reproduzierbar. | manuell im UI — **nicht über API prüfbar** |

### ⚠️ Do NOT negate

| Cluster | Umfang | Begründung |
|---|---|---|
| **Fremdsprachige Suchbegriffe gesamt** | 1.195,30 CHF · 44,20 Conv · **CPA 27,04** | Effizienter als der Nicht-Brand-Schnitt (31,99). `business.md` §1 nennt Zuwanderer als Kern-Zielgruppe, „mehrsprachige Beratung" als USP. **Der Widerspruch zu `search-terms-rules.md` („fremdsprachig → NKL_Generisch") ist zugunsten der Daten aufzulösen — die Regel ist veraltet.** |
| `idioma` · `sin idioma` · `extranjeros` · `temporario` · `trabalho temporario` · `offerte lavoro` · `lavori svizzera` · `electrician` | 8 der 18 N-Gram-Flags | Sämtlich <20 Klicks **und** Bestandteil der oben konvertierenden Sprachcluster. Der N-Gram-Motor hat sie nur geflaggt, weil er intern mit 0,01 statt 0 Conversions rechnet (siehe Datenqualität). |
| `ab sofort` · `suche` | 135 + 63 Klicks, 194 CHF | Deutsche Zielgruppensprache mit Existenzdruck-Signal. 0 Conversions ist ein LP-Befund, kein Relevanz-Befund → Aktion #6. |
| `montage elektriker` | 13 Klicks | Kerngewerk mit eigener Kampagne. Unterpowert, nicht irrelevant. |
| **Competitor-Terms in der Compeditor-Kampagne** | `dasteam ag`, `adecco basel`, `manpower olten`, `coople` u. a. | `business.md` §13: dort **bewusst relevant**. `NKW_Compeditor` wird auf diese Kampagne nicht angewendet. |
| **Alle 155 nicht-konvertierenden Terms** | 1.148,46 CHF | Kein einziger erreicht 20 Klicks (Max: 18). `business.md` §8: „Mindestentscheidungsbasis: 20 Klicks, 30 Tage" / „Pause-Kandidat: ≥30 CHF, 0 Conv, ≥20 Klicks". **Keiner qualifiziert.** |

---

## Module Details

### Modul 1 — Search Term Quality (21 / 25)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| ST-D01 | Irrelevanter Spend-Anteil | WARN | 3/5 | 11,8 % (1.148,46 von 9.748,60 CHF). Das Script setzt „irrelevant" = „nicht konvertierend"; echte semantische Irrelevanz liegt deutlich darunter. |
| ST-D02 | Nicht-konvertierende Terms | WARN | 3/5 | 155 Terms, 524 Klicks. **Alle unter 20 Klicks**, alle `target_source=fallback`. Ø 7,41 CHF je Term. Nicht entscheidbar. |
| ST-D03 | Unterperformende Terms | PASS | 5/5 | 0 Terms über 75 CHF CPA bei ≥50 CHF Spend und ≥3 Klicks. |
| ST-D04 | Fremdsprachige Terms | PASS | 5/5 | 4.219 Terms / 1.195,30 CHF / CPA **27,04** — besser als der Konto-Schnitt. Kein Defekt, sondern **ungenutzte Chance**: DE-only-Website bedient nachweislich nicht-deutschsprachige Nachfrage. |
| ST-D05 | Trending Terms | PASS | 5/5 | 148 Terms mit Periodenveränderung erkannt (u. a. `trockenbauer` 0 → 22,48 CHF, `manpower bern` 0 → 16,85 CHF). Erkennung funktioniert. |

**Hinweis zu D04 als Chance:** Spanisch (545 CHF / 19,66 Conv), Italienisch (267 / 13,00), Portugiesisch (186 / 7,52) konvertieren auf einer rein deutschsprachigen Seite. Der `jobs emploi lavoro`-Präfix in 983 Terms ist ein Portal-Titelmuster (jobs.ch), keine italienische Query — die dahinterliegenden Suchbegriffe sind deutsch.

### Modul 2 — Negative Coverage (20,71 / 25)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| ST-D06 | Kampagnen ohne Negative | PASS | 3,57 | **0 von 30 aktiven.** Die 265 Meldungen sind zu 100 % PAUSED — Fehlalarm, identisch zum 10.08. |
| ST-D07 | Kampagnen ohne Shared List | PASS | 3,57 | **0 von 30 aktiven.** Gleicher Fehlalarm. |
| ST-D08 | Negativ-Konflikte | PASS | 3,57 | 0 Konflikte — kein Negativ blockiert ein aktives Keyword. |
| ST-D09 | Doppelte Ad-Group-Negative | PASS | 3,57 | 0. |
| ST-D10 | Doppelte Kampagnen-Negative | WARN | 2,14 | 42 Terms in 3–12 Kampagnen. **39 davon tragen `likely_routing=true`** mit Beleg (z. B. `maler job` EXACT-negativ in Dachdecker/Zimmermann/Maurer, während `job` als Positiv-Keyword in Brand steht) — also **gewollte Kampagnen-Steuerung, kein Defekt.** *Revision gegenüber dem 10.08., wo D10 als FAIL gewertet wurde.* Verbleiben 3 ungeklärte. |
| ST-D11 | Legacy `+modified` Broad | WARN | 2,14 | 2: `+bankschreiner`, `+möbelschreiner` (Montage-Schreiner). Mögliche Ursache für Roadmap-Punkt T4. |
| ST-D12 | Katalog-Vollständigkeit | WARN | 2,14 | Aktive Abdeckung gut (`NKL_Generisch` 466 KWs / 312 Kampagnen · `NKW_Compeditor` 1.035 / 35 · `NKW_Brand` 48 / 35). Aber **3 Legacy-Listen ohne jede Kampagnen-Anbindung.** |

### Modul 3 — N-gram Analysis (16 / 20)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| ST-D13 | Nicht-konvertierende N-Grams | WARN | 3/5 | Script meldet 0 (Artefakt, s. u.). Eigene Nachrechnung mit Wortgrenzen: **4 entscheidbare** — `ab` (138 Klicks / 135,91 CHF), `ab sofort` (135 / 132,19), `suche` (63 / 62,17), `offerte` (42 / 39,78), alle 0 Conv. `ab` und `ab sofort` überlappen fast vollständig. **Alle 4 sind Zielgruppensprache → keine Negation.** |
| ST-D14 | Ineffiziente N-Grams | PASS | 5/5 | 18 geflaggt, davon **14 unter 20 Klicks**. Nach Bereinigung bleibt keine belastbare Ineffizienz. |
| ST-D15 | Shared-List-Aktualität | WARN | 3/5 | `listStaleness` leer. `ngramNonConverting` / `ngramInefficient` stehen bewusst auf `null` (korrekt — die Template-Listen existieren nicht). Dazu 3 verwaiste Listen. |
| ST-D16 | Volumen-Konzentration | PASS | 5/5 | 67,8 % des geflaggten Spends in wenigen N-Grams. Bei 1.148 CHF Gesamtvolumen informativ, nicht handlungsauslösend. |

> **⚠️ Datenqualität — CPA-Werte im N-Gram-Output sind unbrauchbar.** Das Script rechnet mit einer Untergrenze von `0,01` Conversions statt `0`, um Division durch null zu vermeiden. Daraus entstehen Werte wie „CPA 14.443 CHF" für `ab` oder „CPA 9.972 CHF" für `suche`. Die Rohdaten zeigen: **36.580 von 36.902 Zeilen tragen exakt 0 Conversions.** Diese N-Grams sind nicht *ineffizient*, sie sind *nicht-konvertierend* — und deshalb landete D13 fälschlich bei 0 und D14 bei 18. Alle Zahlen in diesem Modul stammen aus eigener Nachrechnung, nicht aus dem Script-Output.

### Modul 4 — Close Variants (SKIP)

| ID | Diagnostik | Status | Befund |
|---|---|---|---|
| ST-D17 | Variant-Performance-Drift | SKIP | `match_types` ist auf **allen** 155 nicht-konvertierenden und **allen** 268 Promotion-Datensätzen ein leeres Array. Die Zuordnung Suchbegriff → auslösendes Keyword fehlt vollständig. |
| ST-D18 | Variant-Spend-Anteil | SKIP | s. o. |
| ST-D19 | Unbeabsichtigte Expansion | SKIP | s. o. Qualitativ: Expansion findet statt (88 % Broad-Spend, fremdsprachige Queries in DE-Kampagnen) — sie ist aber **profitabel** (CPA 27,04) und damit kein Schadensbefund. |

> Um dieses Modul zu bewerten, müsste der Pull `search_term_view.keyword` bzw. das auslösende Kriterium mitziehen. Bis dahin bleibt es SKIP — der Vorlauf vom 10.08. hat es mit 15/15 bewertet, was mangels Datengrundlage nicht belegbar war.

### Modul 5 — Promotion & PMax (3,6 / 6)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| ST-D20 | Top-Performer ohne Keyword | WARN | 1,8/3 | 268 Kandidaten. Aber nur **1** erfüllt Kollabos Top-Performer-Schutz (≥3 Conv **und** CPA ≤ 0,8× Konto-Ø). 15 zeigen ≥2 Conv bei ≤1 Klick → Attribution fraglich. Nur 6 haben ≥2 Conv bei ≥3 Klicks. **Der belastbare Teil ist der `temporärbüro`-Cluster, nicht die Einzelkandidaten.** |
| ST-D21 | Duplikate über Kampagnen | WARN | 1,8/3 | **9 Terms konkurrieren kampagnenübergreifend.** `temporärbüro wädenswil` in 5 Kampagnen (Montage-Elektriker, Maler, Sanitärinstallateur, Automatiker, Schweisser); `temporärbüro winterthur` in 3. Durchweg **generische Orts-/Temporär-Begriffe ohne Gewerksbezug** — genau die Lücke aus H5. |
| ST-D22 | Abdeckungsquote | INFO | — | 3,2 % (10 von 310). Bei 88 % Broad-Spend und Broad-CPA 50,59 < Phrase-CPA 65,74 ist eine niedrige Quote **strategiekonform**. Aus der Wertung genommen. |
| ST-D25 | PMax Brand-Query-Anteil | SKIP | — | Keine PMax-Kampagne (PMax-Pull: 0 Zeilen). |
| ST-D26 | PMax Search-Overlap | SKIP | — | s. o. |

---

## Datengrundlage & Vorbehalte

| Punkt | Bedeutung |
|---|---|
| **Fenster überspannt den Stichtag 01.07.2026** | Die Qualifikationskriterien wurden von „2 Jahre CH" auf „6 Monate EU" gesenkt (`business.md` §3.1a). Conversion-Zahlen vor und nach diesem Datum sind **nicht absolut vergleichbar**. Alle Cluster-CPAs hier sind 90-Tage-Mittel über diesen Bruch. |
| **Auto-Apply aktiv** | Google hat am 30.07. selbstständig ein negatives Keyword angelegt. Negativ-Befunde in diesem Report sind nicht sicher Martin zuzuordnen. |
| **Changelog 7 Tage alt** | `context/account-changelog.md` steht auf 2026-08-11 (Schwelle 5 Tage). Vor dem nächsten Push mit `/account-changelog` refreshen. |
| **1.649 API-unsichtbare Änderungen** | In 30 Tagen, davon 554 in zwei Nacht-Clustern. Attribution über Juli/August ist generell eingeschränkt. |
| **Sichtbarkeitslücke** | 10.366,86 CHF sind sichtbaren Suchbegriffen zugeordnet — von 13.011,60 CHF Konto-Spend im Fenster (79,7 %). Rund 2.645 CHF sind nicht auf Suchbegriffsebene analysierbar. |
| **Keine Self-Learning-Historie** | `evidence/search-term-decisions.json` existiert noch nicht. Wenn du Terms freigibst oder N-Grams ablehnst, wird die Datei angelegt und filtert sie beim nächsten Lauf. |
