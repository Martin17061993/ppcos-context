# LP Audit — Kollabo

**Datum:** 2026-08-11 · **Module:** Structural (D01–D12) + Message Match (D13–D16) + Technical (D17–D24) + Performance (D25–D31) + URL Health (D32–D37) · **Vertical:** Lead Gen
**Geprüfte URL:** `https://kollabo.com/de-ch/jobs/gipser-jobs/`
**Repräsentativ für:** die Vorlage `/de-ch/jobs/{gewerk}-jobs/` — 14+ URLs identischer Bauart

---

## Executive read

58 % — und das Ergebnis ist differenzierter, als fünf vorangegangene Audits erwarten ließen. Diese Seite ist **kein schlechtes Stück Arbeit.** Der Text trifft die Markenstimme punktgenau, die Duz-Form ist konsequent durchgehalten, die drei Schritte („Nur 1× bewerben – ohne Anschreiben. Wir übernehmen die Jobsuche und das Anschreiben für dich.") formulieren den USP so klar, wie man es sich wünscht, und die Seite zeigt **68 echte, gewerkespezifische Stellenanzeigen** — `Gipser (m/w) in Thalwil`, `Gipser EFZ in Aesch`. Das ist inhaltliche Relevanz auf einem Niveau, das die meisten Landingpages nicht erreichen.

Der Punktverlust kommt aus drei Stellen, und zwei davon sind in Minuten behebbar. **Erstens: die Seite zeigt sichtbar „Facebook Rating 0".** Direkt neben „Google Rating 4.9". Ein sichtbar auf null stehendes Bewertungs-Widget ist kein neutrales Element — es ist ein aktives Misstrauenssignal an genau der Stelle, an der die Seite Vertrauen aufbauen soll. Im selben Block steht ein abgebrochener Satz: „Jeder dritte Bewerber findet den neuen direkt über kollabo" — dem Satz fehlt das Wort „Job". Das ist der Social-Proof-Abschnitt, und er ist an beiden Stellen beschädigt.

**Zweitens: das hier ist keine Landingpage, es ist eine Website-Seite.** 114 Links, vollständige Kopfnavigation, 41 Fußzeilen-Links, drei Social-Icons. Jeder dieser Links ist ein Ausgang aus dem Bewerbungsprozess. Bei einem Konto, dessen dokumentierter Engpass die Landing-Page-Erfahrung ist, ist das der strukturell teuerste Befund.

**Drittens: die Überschrift verkauft das Gewerk, nicht Kollabo.** „Gipser Jobs" plus „Als Gipser verleihst du Wänden den perfekten Schliff" ist sympathisch, aber es ist Schmeichelei. Das eigentliche Versprechen — einmal bewerben statt zwanzigmal — steht erst bei 832 Pixel, unterhalb des Sichtbereichs.

Kein Problem sind: Vertrauenssignale (Google 4.9, Telefonnummern, Öffnungszeiten), Einwandbehandlung (FAQ, kostenlos, Datenschutz, „ohne Anschreiben"), die Nutzenargumentation und die CTA-Formulierung „Jetzt bewerben".

Der `/quality-score-auditor`-Report von gestern (44 %) hält fest: *„170 von 221 Keywords mit unterdurchschnittlicher LP-Erfahrung; LP ist bei 123 Keywords die allein limitierende Komponente."* Dieses Audit erklärt das Warum nur teilweise — die Inhalte sind gut. Die Vermutung verschiebt sich damit auf **Ausgangsdichte und Technik**; die Module `technical` und `performance` laufen als nächstes.

Kein Score-Trend — erster Lauf.

---

## Score

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| Structural (LP-D01–D12) | 46 / 80 | 58 % | Needs Attention |
| Message Match (LP-D13–D16) | 13 / 25 | 52 % | Needs Attention |
| Technical (LP-D17–D24) | 41,8 / 51 | 82 % | Good |
| Performance (LP-D25–D31) | 8 / 30 | 27 % | Critical |
| **URL Health (LP-D32–D37)** | **37,8 / 43** | **88 %** | **Good** |
| **GEWICHTETER GESAMTSCORE** | | **60 %** | **Needs Attention** |

> Alle fünf für Lead-Gen relevanten Module gelaufen. Ecommerce (D38–D40) entfällt — kein Ecommerce-Vertical.

---

## ⚠️ Wichtige Korrektur an einem eigenen Zwischenbefund

Meine erste DOM-Extraktion meldete „70 von 75 Überschriften leer". **Das war ein Extraktionsfehler
meinerseits, kein Seitenfehler.** Die Überschriften enthalten echte Inhalte — es sind die 68
Stellenanzeigen im `job_listings`-Widget, alle gerendert und sichtbar. `innerText` lieferte leere
Strings, weil die Elemente in Anker-Tags verschachtelt sind. Nachgeprüft und widerlegt.

---

## Prioritäre Fixes

### 1. „Facebook Rating 0" entfernen (LP-D07 FAIL)

Der Social-Proof-Block zeigt wörtlich:

> „Die unabhängigen Bewertungen von kollabo auf Google sind hervorragend. Und mit Grund:
> Jeder dritte Bewerber findet den neuen direkt über kollabo. **Google Rating 4.9 — Facebook Rating 0**"

**Zwei Defekte in vier Zeilen:**

| Defekt | Wirkung |
|---|---|
| „Facebook Rating 0" sichtbar | Aktives Misstrauenssignal direkt neben dem stärksten Vertrauenssignal |
| „findet den **neuen** direkt über kollabo" | Abgebrochener Satz — es fehlt „Job". Wirkt unfertig. |

Beides ist ein Widget-/Textfix, kein Redesign. Das Facebook-Widget entweder befüllen oder
ausblenden. **Aufwand: Minuten. Betrifft alle 14+ Seiten der Vorlage.**

> `business.md` §12 listet die erlaubten quantitativen Claims abschließend auf. Darunter:
> `jeder dritte Bewerber findet einen Job` — die korrekte Formulierung steht dokumentiert,
> sie ist auf der Seite nur falsch umgesetzt.

### 2. Ausgänge reduzieren (LP-D11 FAIL)

| Element | Anzahl |
|---|---|
| Links gesamt | **114** |
| Fußzeilen-Links | 41 |
| Kopfnavigation | ALLE JOBS · ÜBER UNS · Login · Portal · Sprachwahl |
| Social-Icons | 3 |
| Formulare auf der Seite | 3 |

Das ist die Struktur einer Website-Unterseite, nicht einer Landingpage. Für den bezahlten
Traffic bedeutet jeder Link einen möglichen Ausstieg vor der Bewerbung.

**Das ist zugleich der Befund mit der größten Hebelwirkung** — und der einzige, der Dev-Support
braucht (`business.md` Known Constraints: 2 Wochen Vorlauf).

### 3. Hero auf das Versprechen umstellen (LP-D02 WARN)

**Ist:**
> „Gipser Jobs" → „Als Gipser verleihst du Wänden den perfekten Schliff. Möchtest du in einem
> Job arbeiten, der deine Handwerkskunst schätzt? Hier findest du passende Stellenangebote für
> Gipser."

**Das Versprechen steht erst bei 832 px:**
> „Nur 1× bewerben – ohne Anschreiben. Wir übernehmen die Jobsuche und das Anschreiben für dich."

Der Text ist markengetreu und in korrekter Duz-Form — aber er verkauft das *Gewerk*, nicht
*Kollabo*. Der Grund, warum jemand Kollabo statt jobs.ch nutzt, steht unterhalb der Falz.
**Der USP gehört nach oben.** → `/rsa-maker` und `/offer-maker` haben denselben Rohstoff.

---

## Diagnostik-Ergebnisse — Structural

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D01 | Angebots-Vollständigkeit | WARN | 5/10 | 4 von 5 Komponenten: Was/für wen ✓, Nutzen ✓, Beleg ✓, CTA ✓ — **Risikoumkehr fehlt** |
| LP-D02 | Hero-5-Sekunden-Test | WARN | 5/10 | H1 „Gipser Jobs" = 2 Wörter, aber Kategorie-Label statt Ergebnis. Sub-Headline lobt das Gewerk statt das Angebot. USP erst bei 832 px. |
| LP-D03 | CTA über der Falz | PASS | 10/10 | 2× „Jetzt bewerben" im Sichtbereich (Desktop). *Mobil nicht geprüft — Modul `technical`.* |
| LP-D04 | CTA-Qualität | WARN | 3/5 | „Jetzt bewerben" ist konkret und handlungsstark ✓. **„Absenden" ist generisch** ✗ |
| LP-D05 | Nutzen-Abschnitt | PASS | 5/5 | „In 3 einfachen Schritten zum neuen Job" — ergebnisorientiert, deckt Aufwand **und** Geschwindigkeit ab |
| LP-D06 | Vertrauen/Autorität | PASS | 5/5 | Google 4.9, Telefon (2 Nummern), Öffnungszeiten Mo–Fr 08–18h, Impressum |
| LP-D07 | Social Proof | **FAIL** | 0/5 | **„Facebook Rating 0" sichtbar** + abgebrochener Satz. Keine namentlichen Testimonials mit Foto. |
| LP-D08 | Einwandbehandlung | PASS | 5/5 | 4 von 4: FAQ ✓, kostenlos ✓, Datenschutz ✓, „ohne Anschreiben" (Aufwand) ✓ |
| LP-D09 | Garantie / Risikoumkehr | **FAIL** | 0/5 | Keine Garantie, kein Risikoumkehr-Statement. „kostenlos" ist Preisangabe, keine Zusicherung. |
| LP-D10 | CTA-Wiederholung | PASS | 5/5 | 3 wirksame CTAs (99 px, 3.845 px, 5.888 px) auf 7.136 px Seitenhöhe. Zählt, aber **Lücke von 3.700 px** zwischen erstem und zweitem. |
| LP-D11 | Ein Ziel je Seite | **FAIL** | 0/10 | 114 Links, volle Navigation, 41 Fußzeilen-Links, 3 Social-Icons, 3 Formulare |
| LP-D12 | Abschnitts-Hierarchie | WARN | 3/5 | 5 Abschnitte: Hero → 3 Schritte → Social Proof → offene Stellen → Allgemeine Infos. Reihenfolge stimmig, aber Urgency und Garantie fehlen. |

---

## Was gut ist — ausdrücklich

Diese Seite hat Stärken, die in einem Fix-Plan nicht untergehen sollten:

| Element | Bewertung |
|---|---|
| **68 gewerkespezifische Stellenanzeigen** | Konkrete Orte (Thalwil, Aesch, Schlieren, Glattbrugg), echte Titel (`Gipser EFZ`). Sehr starkes Relevanzsignal. |
| **Duz-Form** | Konsequent. Die einzigen zwei „Sie"-Fundstellen sind Fremdkomponenten: Datei-Upload-Widget („Wählen Sie Dateien aus") und Cookie-Banner. |
| **USP-Formulierung** | „Nur 1× bewerben – ohne Anschreiben. Wir übernehmen die Jobsuche und das Anschreiben für dich." — exakt die Kernbotschaft aus `business.md` §12, gut getextet. |
| **Markenstimme** | Persönlich, direkt, ermutigend. Trifft die dokumentierte Tonalität. |
| **Inhaltstiefe** | 1.306 Wörter, gewerkespezifisch, nicht generisch. |

**Der Inhalt ist nicht das Problem.** Das ist relevant für die Ursachenfrage aus dem QS-Audit.

---

## Routing

| Befund | Aktion | Aufwand |
|---|---|---|
| „Facebook Rating 0" + abgebrochener Satz | Widget ausblenden oder befüllen; Satz korrigieren auf den freigegebenen Claim `jeder dritte Bewerber findet einen Job` | **Minuten**, wirkt auf 14+ Seiten |
| „Absenden" → konkreter CTA | Formular-Button umbenennen | Minuten |
| Garantie / Risikoumkehr ergänzen | Rohstoff vorhanden: „kostenlos", „unverbindlich", „nur 1× bewerben" | → `/offer-maker` |
| Hero auf USP umstellen | Versprechen über die Falz ziehen | → `/offer-maker`, `/lp-optimizer elements` |
| 114 Links / volle Navigation | Dedizierte LP-Variante für bezahlten Traffic | → `/lp-optimizer`, Dev-Support (2 Wochen) |

**Peer-Reports, die hier einzahlen:**

| Peer | Stand | Befund |
|---|---|---|
| `/quality-score-auditor` | 2026-08-11, 44 % | *„LP-Erfahrung bei 76,9 % der Keywords unterdurchschnittlich; LP bei 123 Keywords allein limitierend."* Dieses Audit erklärt das nur teilweise → `technical` und `performance` prüfen. |
| `/geo-schedule-auditor` | 2026-08-11, 74 % | *„Mobile 71,6 % des Spends bei CVR 2,09 % vs Desktop 4,11 %."* Verdacht auf mobiles LP-Problem → Modul `technical`. |
| `/competitive-analyst` | 2026-08-11, 41 % | *„Rangverlust 37–73 % QS-getrieben."* Der Hebel liegt hier. |
| `/keyword-auditor` | 2026-08-10, 57 % | *„B3 Core-Term-Konzentration 91,3 % — das Problem liegt hinter den Keywords."* Bestätigt die Route hierher. |

---

## Datenfrische

| Quelle | Stand |
|---|---|
| Live-Seiten-Prüfung `gipser-jobs` | 2026-08-11, Chrome DevTools |
| `context/business.md` | 2026-08-10 |
| Module `message-match`, `technical`, `performance`, `urls` | folgen in diesem Durchgang |

> **Geltungsbereich:** Geprüft wurde eine Seite als Vertreter der Vorlage. Die Befunde
> LP-D07 (Facebook-Widget), LP-D09 (Garantie) und LP-D11 (Navigation) sind Template-Eigenschaften
> und gelten mit hoher Wahrscheinlichkeit für alle 14+ Gewerke-Seiten. LP-D02 (Hero) ist
> je Seite getextet und muss stichprobenartig gegengeprüft werden.

---

# Modul 2 — Message Match (LP-D13–D16)

**Score: 13 / 25 = 52 % — Needs Attention**
**Datenbasis:** 60 Live-RSAs · 29 eindeutige Final URLs (alle extrahiert) · 298 Keywords

## Der Befund mit der größten Erklärkraft: Trennstriche in den H1

Sechs Gewerke-Seiten tragen einen **Trennstrich mitten im Gewerkenamen** in der H1. Der
Keyword-String steht damit nicht mehr wortwörtlich auf der Seite:

| Seite | H1 ist | müsste sein | Keyword im Konto |
|---|---|---|---|
| `/elektroinstallateur-jobs/` | `Elektro-installateur Jobs` | Elektroinstallateur Jobs | `elektroinstallateur jobs` |
| `/heizungsmonteur-jobs/` | `Heizungs-installateur Jobs` | Heizungsinstallateur Jobs | `heizungsinstallateur jobs` |
| `/sanitaer-jobs/` | `Sanitär-installateur Jobs` | Sanitärinstallateur Jobs | `sanitär jobangebote` |
| `/produktionsmechaniker-jobs/` | `Produktions-mechaniker Jobs` | Produktionsmechaniker Jobs | `produktionsmechaniker` |
| `/metallbaukonstrukteur-jobs/` | `Metallbau-konstrukteur Jobs` | Metallbaukonstrukteur Jobs | `jobs metallbaukonstrukteur` |
| `/montage-elektriker-jobs/` | `Montage-elektriker Jobs` (kleines e) | Montage-Elektriker Jobs | `montage elektriker jobs` |

Das sieht nach CSS-Silbentrennung aus, die als **harter Trennstrich in den Text gewandert ist** —
vermutlich ein `&shy;`, das beim Rendern zum sichtbaren Bindestrich wird, oder manuell gesetzt,
um lange Wörter im Layout umzubrechen.

**Warum das zählt:** Die H1 ist eines der stärksten Relevanzsignale einer Seite. Wer auf
`heizungsinstallateur jobs` bietet und dessen Seite `Heizungs-installateur Jobs` in der
Überschrift trägt, verliert die wortwörtliche Übereinstimmung.

### Die Korrelation, die auffällt

| Seite mit Trennstrich | CPA (30 T) | Rang im Konto |
|---|---|---|
| Montage-Elektriker | **231,81** | schlechtester CPA |
| Produktionsmechaniker | **146,90** | drittschlechtester |
| Heizungsinstallateur | 80,44 | über Schwelle |
| Sanitärinstallateur | 68,61 | knapp unter Schwelle |
| Metallbaukonstrukteur | 44,25 | unauffällig |
| Elektroinstallateur | 40,54 | unauffällig |

**Vier der sechs betroffenen Seiten gehören zu den teuersten Kampagnen des Kontos.**

Das ist eine **Korrelation, kein Beweis** — sechs Seiten sind eine kleine Stichprobe, und zwei
davon sind unauffällig. Aber der Fix kostet Minuten und ist sofort messbar. **Als Test
formuliert:** Trennstriche entfernen, 14 Tage messen, gegen die beiden unauffälligen Seiten
und gegen die 23 Seiten ohne Trennstrich vergleichen.

## Die UMLAND-Zielseite hat gar keine H1

`https://kollabo.com/de-ch/` — Zielseite der Ad Group `STAN | HOME | BROAD` (UMLAND TEST) —
liefert **eine leere H1**. Die Seite trägt nur eine Sub-Headline (`JOBS FÜR HANDWERKER`).

UMLAND ist laut `/competitive-analyst` (2026-08-11) mit **CPA 15,33 über 90 Tage die
effizienteste Kampagne des Kontos** und verliert gleichzeitig 72,7 % ihrer Impressionen an den
Rang. Eine fehlende H1 auf ihrer Zielseite ist eine plausible Mitursache — und der billigste
denkbare Fix.

## Anzeige verspricht Tempo, Seite nennt das Gewerk

**Anzeigen-Headlines (repräsentativ):**
> „Kollabo: Die Jobplattform" · „Handwerkerjobs in der Schweiz" · „**Bewerben ohne Anschreiben**" ·
> „**In unter einer Minute bewerben**" · „Temporär oder Festanstellung" · „**Heute bewerben, morgen Job**"

**Zugehörige LP-H1:**
> „Gipser Jobs" · „Zimmermann Jobs" · „Maurer Jobs"

Die Anzeige verkauft **Geschwindigkeit und Aufwandsersparnis**. Die Landingpage bestätigt das
**Gewerk**. Beides gehört zum selben Thema, aber das Versprechen der Anzeige wird oben auf der
Seite nicht eingelöst — es steht laut Structural-Modul erst bei 832 px („Nur 1× bewerben – ohne
Anschreiben").

Wer auf „Bewerben ohne Anschreiben" geklickt hat, sieht zuerst „Gipser Jobs" und darunter einen
Absatz über das Gipserhandwerk. Die Bestätigung kommt — aber zu spät.

## Weitere Beobachtungen

| Befund | Detail |
|---|---|
| **Tippfehler im Formular** | Button `Zurücksetzten` (statt „Zurücksetzen") auf allen Gewerke-Seiten |
| **CTA-Sprache uneinheitlich** | `Jetzt bewerben` (Header) · `Jetzt anmelden` (Seite) · `Absenden` (Formular) · `Weiter` · `Suchen` — fünf verschiedene Handlungsaufforderungen auf einer Seite |
| **Sie-Form in Fremdkomponente** | `Wählen Sie Dateien aus` (Upload-Widget) — bricht die verbindliche Duz-Form |
| **Schwache Keyword-Abdeckung** | `Baumaschinenführer` (H1 deckt `fahrer jobs`, `staplerfahrer arbeit` nicht) · `Abdichter` (deckt `bauwerksabdichter jobs`, `isoleur jobs` nicht) |
| **Ad-Versprechen ohne Entsprechung** | Anzeige: „Top-Lohn & faire Verträge" — auf der Seite nicht bestätigt |

## Diagnostik-Ergebnisse — Message Match

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D13 | Anzeige-zu-LP Headline-Match | WARN | 5/10 | Gleiches Thema, anderer Winkel: Anzeige verspricht Tempo/Aufwand, H1 nennt das Gewerk. Versprechen erst bei 832 px eingelöst. **6 H1 mit Trennstrich-Artefakt**, 1 H1 komplett leer. |
| LP-D14 | Anzeige-zu-LP Angebots-Match | WARN | 5/10 | 3-Schritte-Prozess und 68 Stellenanzeigen lösen die Anzeigenzusage ein ✓. Aber „Top-Lohn & faire Verträge" fehlt auf der Seite, und die CTA-Sprache streut über fünf Varianten. |
| LP-D15 | Keyword-zu-LP-Relevanz | WARN | 3/5 | Überwiegend gut (2–3 von 3 Top-Keywords in der H1). Ausnahmen: Trennstrich-Seiten verlieren die wortwörtliche Übereinstimmung; `Baumaschinenführer` und `Abdichter` decken ihre Top-Keywords nicht ab. |
| LP-D16 | Visuelle Konsistenz | SKIP | — | Keine Display- oder Video-Kampagnen im Konto — alle 30 sind Search. |

## Priorisierte Fixes aus diesem Modul

| # | Aktion | Aufwand | Erwartete Wirkung |
|---|---|---|---|
| 1 | **Trennstriche aus 6 H1 entfernen** | Minuten | Stellt wortwörtliche Keyword-Übereinstimmung her; 4 der 6 Seiten gehören zu den teuersten Kampagnen |
| 2 | **H1 auf `kollabo.com/de-ch/` ergänzen** | Minuten | Zielseite der effizientesten Kampagne des Kontos (UMLAND, CPA 15,33) |
| 3 | **Tippfehler `Zurücksetzten` korrigieren** | Minuten | Vorlagenweit |
| 4 | **CTA-Sprache vereinheitlichen** | gering | Fünf konkurrierende Handlungsaufforderungen auf einer Seite |
| 5 | **USP über die Falz ziehen** | mittel | Löst das Anzeigenversprechen dort ein, wo es ankommt → deckt auch Structural LP-D02 |
| 6 | **Upload-Widget auf Duz-Form** | gering | `business.md` §12 — Duz-Form ist verbindlich |

---

# Modul 3 — Technical (LP-D17–D24)

**Score: 41,8 / 51 = 82 % — Good**
**Messbedingungen:** Mobile-Emulation 390×844, **Slow 4G**, **4× CPU-Drosselung** · Lighthouse mobile

## Die Ladezeit ist nicht das Problem

| Kennzahl | Wert | Bewertung |
|---|---|---|
| **LCP** | **1.571 ms** | gut (Schwelle 2.500 ms) |
| **CLS** | **0,00** | ausgezeichnet |
| Horizontales Scrollen | keins | ✓ |
| TTFB | 2 ms | *Cache-Treffer — Kaltstart nicht gemessen* |
| LCP-Aufschlüsselung | Ladeverzögerung 944 ms · Renderverzögerung 625 ms | Optimierungsspielraum, kein Defekt |

Nach drei Audits, die auf die Landing Page zeigen, ist das der dritte Erwartungsbruch:
**der Inhalt ist gut, die Message-Match hat behebbare Fehler, und die Ladezeit ist in Ordnung.**
Was bleibt, ist Struktur — die 114 Ausgänge und die Trennstriche in den H1.

## Was die Technik trotzdem belastet

### 173 Netzwerk-Anfragen für eine Landingpage

| Kategorie | Anzahl | Auffälligkeit |
|---|---|---|
| **Schriftdateien** | **~20** | HelveticaNowDisplay als `.otf` **und** `.woff2` (Doppel-Download) · TrimMono als `.ttf` **und** `.woff` · TrimPoster als `.otf` + `.woff2` · FontAwesome ×2 |
| CSS-Dateien | ~30 | Elementor, Elementor Pro, Bootstrap, FontAwesome, Gravity Forms, WP Job Manager, Select2, GDPR, Business Reviews … |
| JS-Dateien | ~50 | inkl. **Google Maps SDK** (`maps.googleapis.com/maps/api/js` + `map.js`) auf einer Job-Landingpage |
| WordPress-Emoji | 1 Skript + 6 SVGs | von `s.w.org` — nicht benötigt |

**Die Schriften sind der auffälligste Posten.** `.otf` und `.ttf` sind unkomprimierte Formate und
zwei- bis fünfmal größer als `woff2`. Mehrere Familien werden **in beiden Formaten** geladen —
das ist doppelte Übertragung ohne Nutzen.

Dass LCP und CLS trotzdem gut sind, liegt am Caching (WP Rocket) und daran, dass die Schriften
nicht renderblockierend sind. Bei einem Erstbesucher über Mobilfunk sieht die Rechnung anders aus.

### 86 Bilder, 0 davon Lazy-Loading

WP Rocket lädt `lazyload.min.js`, aber **kein einziges der 86 Bilder** trägt `loading="lazy"`.
Neun Bilder haben keine Größenangaben. Dass CLS trotzdem 0 ist, spricht für das Layout —
aber die Bilder werden alle sofort geladen.

### `user-scalable=0` — Zoom auf Mobilgeräten gesperrt

```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0">
```

Nutzer können auf dem Smartphone **nicht heranzoomen**. Lighthouse flaggt das als
Barrierefreiheits-Verstoß. Bei einer Zielgruppe, die laut `business.md` §1 einen hohen Anteil
Zuwanderer umfasst — also Menschen, die den Text womöglich genauer lesen wollen — ist das
mehr als eine Formalie.

Dazu: **24 Tap-Ziele unter 44 px**. Die Haupt-CTAs sind mit 167 × 50 px in Ordnung, aber zwei
Dutzend kleinere Elemente nicht.

## Lighthouse Mobile

| Kategorie | Score |
|---|---|
| SEO | **92** |
| Accessibility | **71** |
| Agentic Browsing | 67 |
| Best Practices | **58** |

**14 fehlgeschlagene Prüfungen**, die relevantesten:

| Befund | Anzahl | Warum es zählt |
|---|---|---|
| Kontrastverhältnis unzureichend | **13 Elemente** | Lesbarkeit — besonders mobil bei Sonnenlicht |
| Listenelemente nicht in `<ul>`/`<ol>` | **68** | Das Stellenanzeigen-Widget — semantisch unsauber |
| Formularfelder ohne Label | **2** (+1 Submit) | Direkt auf dem Conversion-Pfad |
| Links ohne erkennbaren Namen | 3 | Barrierefreiheit + Crawling |
| Überschriften nicht absteigend sortiert | 2 | Semantik |
| `user-scalable=no` | 1 | siehe oben |
| Veraltete APIs / Drittanbieter-Cookies | 1 / 4 | Best Practices |

## Nebenbefund: Cross-Channel-Lücke [GAP-9] geschlossen

Der Netzwerk-Mitschnitt zeigt, welche Marketing-Kanäle tatsächlich mitlaufen:

| Dienst | Nachweis |
|---|---|
| **Microsoft Bing Ads (UET)** | `bat.bing.com/bat.js`, `bat.bing.com/p/action/355016996.js`, `bat.bing.net/action/0?ti=355016996` |
| **Jooble** (Jobbörsen-Aggregator) | `jooble.org/js/conversion.js` |
| **ActiveCampaign** | `diffuser-cdn.app-us1.com`, `prism.app-us1.com`, `trackcmp.net` |
| Google Ads / GA4 / GTM | `AW-794335319`, `G-4V0XDR0GY9`, `GTM-5WM63B5` |

**Kollabo betreibt also mindestens einen zweiten bezahlten Kanal (Bing Ads), eine
Jobbörsen-Distribution (Jooble) und E-Mail-Marketing-Automation (ActiveCampaign).**
Das war in `business.md` §14 als offene Lücke geführt. Für die Attribution heißt das: der
Google-Ads-Anteil an den 158 qualifizierten Leads ist nicht der Gesamtanteil.

## Diagnostik-Ergebnisse — Technical

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D17 | Ladegeschwindigkeit | PASS | 15/15 | LCP 1.571 ms unter Slow 4G + 4× CPU. *Lighthouse-Performance-Score nicht verfügbar (Tool schließt ihn aus); Bewertung stützt sich auf Trace-Metriken.* |
| LP-D18 | Core Web Vitals | PASS | 10/10 | LCP 1.571 ms ✓ · CLS 0,00 ✓ · **INP nicht gemessen** (erfordert Interaktion) |
| LP-D19 | Mobile Responsiveness | WARN | 6/10 | Kein horizontales Scrollen ✓, CTA erreichbar (167×50 px) ✓. Aber **`user-scalable=0`** und **24 Tap-Ziele < 44 px** |
| LP-D20 | Mobile-vs-Desktop-CVR-Lücke | WARN | 3/5 | Mobile CVR **2,09 %** = **50,9 %** der Desktop-CVR (4,11 %). Schwelle WARN: 40–59 % |
| LP-D21 | Formularfeld-Anzahl | WARN | 3/5 | **10 sichtbare Felder** auf der Seite — verteilt auf 3 Formulare (Jobsuche-Filter + Bewerbung). Das Bewerbungsformular allein ist damit nicht sauber isoliert; separate Messung nötig. |
| LP-D22 | Formular-Funktionalität | SKIP | — | Testabsendung würde einen **echten Lead** in Kollabos Salesforce erzeugen. Nicht ohne Freigabe. |
| LP-D23 | SSL/HTTPS | PASS | 3/3 | HTTPS, kein Mixed Content in 173 Anfragen |
| LP-D24 | Bild-Optimierung | WARN | 1,8/3 | Format gut (WebP/SVG), aber **0 von 86 Bildern mit Lazy-Loading** trotz geladenem WP-Rocket-Lazyload; 9 ohne Größenangaben |

## Priorisierte Fixes aus diesem Modul

| # | Aktion | Aufwand | Wirkung |
|---|---|---|---|
| 1 | **`user-scalable=0` und `maximum-scale=1` entfernen** | Minuten | Behebt einen Lighthouse-Accessibility-Verstoß; relevant für die Zielgruppe |
| 2 | **Schriften auf woff2 vereinheitlichen** | gering | ~20 Schriftdateien, mehrere doppelt in `.otf`/`.ttf` **und** `woff2` |
| 3 | **Lazy-Loading aktivieren** | gering | 86 Bilder, aktuell keins verzögert — Plugin ist bereits geladen |
| 4 | **13 Kontrastverstöße beheben** | gering | Lesbarkeit mobil |
| 5 | **2 Formularfelder labeln** | Minuten | Direkt auf dem Conversion-Pfad |
| 6 | **Google Maps SDK prüfen** | mittel | Voller Maps-SDK auf einer Job-Landingpage — nur laden, wenn die Karte sichtbar wird |
| 7 | **WordPress-Emoji-Skript deaktivieren** | Minuten | 1 Skript + 6 externe SVGs ohne Nutzen |

---

# Modul 4 — Performance (LP-D25–D31)

**Score: 8 / 30 = 27 % — Critical**
**Datenbasis:** 28 Zielseiten mit ≥ 10 Klicks · Ad-Group-Ebene auf Final URLs aggregiert
**Konto-Referenz:** Spend 7.576,08 CHF · Conv 144,12 · **CPA 52,57** · **CVR 2,53 %**

---

## ⚠️ Korrektur an Modul 2 — die Trennstrich-Hypothese hält nicht

In Modul 2 habe ich sechs Seiten mit Trennstrich in der H1 gefunden und darauf hingewiesen, dass
vier davon zu den teuersten Kampagnen gehören. Ich habe das ausdrücklich als „Korrelation, kein
Beweis" markiert und einen Test vorgeschlagen. **Die Performance-Daten dieses Moduls sind dieser
Test — und sie stützen die Hypothese nicht.**

| Gruppe | Seiten | Ø CVR | Ø CPA | Ø CPC |
|---|---|---|---|---|
| **Mit** Trennstrich | 6 | **2,29 %** | 102,09 | 1,60 |
| **Ohne** Trennstrich | 17 | **2,96 %** | 69,50 | 1,50 |

Der Unterschied ist da, aber er wird von zwei Ausreißern getragen: `montage-elektriker` (CVR
0,93 %) und `produktionsmechaniker` (0,61 %). Gleichzeitig ist `elektroinstallateur` **mit**
Trennstrich die viertbeste Seite (CVR 4,78 %, CPA 40,54) und `metallbaukonstrukteur` unauffällig
(2,88 %, 44,25). Umgekehrt haben `gaertner` (0,60 %) und `baumaschinenfuehrer` (1,08 %) **keinen**
Trennstrich und performen genauso schlecht.

**Sechs Datenpunkte tragen diese Aussage nicht.** Der Trennstrich bleibt ein echter
Relevanzdefekt und gehört behoben — aber er erklärt die Performance-Unterschiede **nicht**.

## Der eigentliche Befund: 12,4× Spanne bei identischer Vorlage

Alle 28 Seiten laufen auf **derselben Vorlage** — gleicher Aufbau, gleiche drei Schritte,
gleiches Formular, gleiche Navigation, gleiche Technik.

| | Seite | CVR |
|---|---|---|
| **Beste** | `/maurer-jobs` | **7,46 %** |
| | `/automatiker-jobs` | 5,53 % |
| | `/automatikmonteur-jobs` | 4,91 % |
| | `/elektroinstallateur-jobs` | 4,78 % |
| … | | |
| | `/montage-elektriker-jobs` | 0,93 % |
| | `/produktionsmechaniker-jobs` | 0,61 % |
| **Schlechteste** | `/gaertner-jobs` | **0,60 %** |
| **Null** | `/abdichter-jobs` (114 Klicks) · `/kranfuehrer-jobs` (77) · `/montage-schreiner` (81) · `/geruestbauer-jobs` (40) | **0 %** |

**Faktor 12,4 zwischen bester und schlechtester Seite bei identischer Seitenarchitektur.**

Das ist die wichtigste Aussage dieses Moduls, und sie **relativiert die LP-Hypothese der
gesamten Audit-Serie.** Wäre die Vorlage die Ursache, müssten alle Seiten ähnlich schlecht
konvertieren. Sie tun es nicht. Was zwischen 7,46 % und 0,60 % unterscheidet, ist **nicht** die
Seite — es ist die Passung zwischen Suchintention, Gewerk und Angebot.

### Was das für die Ursachenkette bedeutet

`/quality-score-auditor` misst LP-Erfahrung bei 76,9 % der Keywords als unterdurchschnittlich.
Das bleibt richtig — Googles LP-Bewertung stützt sich auf Navigation, Ausgänge, Barrierefreiheit
und Relevanz, nicht auf die Conversion-Rate. **Beide Befunde können gleichzeitig wahr sein:**

- Die Vorlage ist aus Googles Sicht mittelmäßig (114 Ausgänge, `user-scalable=0`,
  13 Kontrastverstöße) → drückt Quality Score → drückt Ad Rank → **erklärt den Rangverlust**.
- Die Vorlage ist aber **nicht** der Grund für die CVR-Unterschiede zwischen Gewerken →
  **erklärt die CPA-Spreizung nicht**.

Der Rangverlust ist ein LP-Problem. Die schlechten Gewerke sind ein **Markt- und Angebotsproblem**.

## Zielseiten-Performance im Detail

| Zielseite | Spend | Klicks | Conv | CPA | CVR | Bewertung |
|---|---|---|---|---|---|---|
| `/de-ch/` (UMLAND) | 596 | 595 | 16,00 | 37,23 | 2,69 % | ✓ |
| `/jobs` (Hub) | 950 | 1.230 | 35,04 | **27,10** | 2,85 % | ✓ |
| `/maurer-jobs` | 141 | 107 | 7,98 | **17,73** | **7,46 %** | ✓✓ |
| `/automatikmonteur-jobs` | 116 | 81 | 3,98 | 29,26 | 4,91 % | ✓✓ |
| `/automatiker-jobs` | 246 | 145 | 8,02 | 30,73 | 5,53 % | ✓✓ |
| `/zimmermann-jobs` | 142 | 86 | 3,50 | 40,47 | 4,07 % | ✓ |
| `/elektroinstallateur-jobs` | 585 | 302 | 14,42 | 40,54 | 4,78 % | ✓ |
| `/metallbaukonstrukteur-jobs` | 88 | 69 | 1,99 | 44,25 | 2,88 % | ✓ |
| `/dachdecker-jobs` | 88 | 76 | 1,98 | 44,52 | 2,61 % | ✓ |
| `/schweisser-jobs` | 228 | 175 | 4,48 | 50,87 | 2,56 % | ✓ |
| `/metallbauer-jobs` | 255 | 163 | 4,95 | 51,49 | 3,04 % | ✓ |
| `/grundbauer-jobs` | 359 | 219 | 5,50 | 65,28 | 2,51 % | über Konto-CPA |
| `/sanitaer-jobs` | 274 | 161 | 4,00 | 68,61 | 2,48 % | über Konto-CPA |
| `/strassenbauer-jobs` | 343 | 205 | 4,98 | 68,83 | 2,43 % | über Konto-CPA |
| `/trockenbauer-jobs` | 73 | 27 | 1,00 | 73,48 | 3,70 % | dünne Datenbasis |
| `/gipser-jobs` | 447 | 250 | 5,98 | 74,83 | 2,39 % | über Konto-CPA |
| `/heizungsmonteur-jobs` | 507 | 307 | 6,30 | **80,44** | 2,05 % | **> 150 %** |
| `/baumaschinenfuehrer-jobs` | 89 | 93 | 1,00 | **88,64** | 1,08 % | **> 150 %**, CVR < 50 % |
| `/bauarbeiter-jobs` | 502 | 342 | 5,49 | **91,46** | 1,61 % | **> 150 %** |
| `/maler-jobs` | 313 | 212 | 3,00 | **104,39** | 1,42 % | **> 150 %** |
| `/polymechaniker-jobs` | 180 | 102 | 1,50 | **120,31** | 1,47 % | **> 150 %** |
| `/produktionsmechaniker-jobs` | 147 | 164 | 1,00 | **146,90** | 0,61 % | **> 150 %**, CVR < 50 % |
| `/gaertner-jobs` | 202 | 168 | 1,00 | **202,17** | 0,60 % | **> 150 %**, CVR < 50 % |
| `/montage-elektriker-jobs` | 236 | 110 | 1,02 | **231,81** | 0,93 % | **> 150 %**, CVR < 50 % |
| `/abdichter-jobs` | 146 | **114** | **0** | — | 0 % | **null Conversions** |
| `/montage-schreiner` | 115 | 81 | 0 | — | 0 % | **null Conversions** |
| `/kranfuehrer-jobs` | 120 | 77 | 0 | — | 0 % | **null Conversions** |
| `/geruestbauer-jobs` | 85 | 40 | 0 | — | 0 % | null Conversions, dünn |

> **Vorbehalt:** `/tracking-specialist` (2026-08-10, 48 %) hält fest, dass der Salesforce-Import
> seit 01.07. kein `New Lead` mehr liefert. Alle Conversion-Zahlen dieses Fensters stehen unter
> diesem Vorbehalt. `/competitive-analyst` (2026-08-11) zeigt, dass über 90 Tage derselbe
> Kontostand bei **CPA 27,25** liegt statt 52,57 — die 30-Tage-Werte sind messverzerrt.
> **Die Rangfolge der Seiten untereinander ist davon aber nicht betroffen**, weil der Messverlust
> alle gleichmäßig trifft.

## Diagnostik-Ergebnisse — Performance

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D25 | CVR vs. Benchmark | **FAIL** | 0/10 | **7 Seiten mit ≥ 50 Klicks unter 50 % der Konto-CVR** (1,27 %): gaertner 0,60 %, produktionsmechaniker 0,61 %, montage-elektriker 0,93 %, baumaschinenfuehrer 1,08 % + abdichter/kranfuehrer/montage-schreiner mit 0 % |
| LP-D26 | Bounce Rate | SKIP | — | Nicht über die Google-Ads-API verfügbar |
| LP-D27 | Scroll-Tiefe | SKIP | — | Erfordert GA4-Scroll-Events |
| LP-D28 | Verweildauer | SKIP | — | Erfordert GA4-Engagement-Metriken |
| LP-D29 | CPA je Zielseite | **FAIL** | 0/10 | **8 Seiten über 150 % des Konto-CPA** (78,86), Spitzenwert 231,81. Dazu 4 Seiten mit null Conversions bei 40–114 Klicks. |
| LP-D30 | Geräte-Performance | PASS | 5/5 | Mobile CPA 58,68 / Desktop 40,93 = **143,4 %** — knapp unter der 150-%-Schwelle |
| LP-D31 | Traffic-Source-Match | WARN | 3/5 | Gewerke-Kampagne → passende Gewerke-Seite: durchgehend sauber ✓. **Ausnahme UMLAND** → Startseite `kollabo.com/de-ch/` ohne H1 — für grenzüberschreitenden Traffic eine generische Seite statt einer passenden. |

## Was daraus folgt

| # | Erkenntnis | Konsequenz |
|---|---|---|
| 1 | **12,4× CVR-Spanne bei identischer Vorlage** | Die Vorlage erklärt die Performance-Unterschiede nicht. LP-Fixes heben den Ad Rank, nicht die Gewerke-CVR. |
| 2 | **4 Seiten mit 0 Conversions bei 40–114 Klicks** | `/abdichter-jobs` (114 Klicks!), `/kranfuehrer-jobs`, `/montage-schreiner`, `/geruestbauer-jobs`. Deckt sich mit `/account-auditor` D07 — dort blockiert durch den Tracking-Befund. |
| 3 | **Die stärksten Seiten sind nicht die größten** | `/maurer-jobs` liefert CVR 7,46 % bei 141 CHF Spend. `/bauarbeiter-jobs` liefert 1,61 % bei 502 CHF. Das ist ein Allokations-, kein Seitenproblem. |
| 4 | **UMLAND landet auf einer Seite ohne H1** | Effizienteste Kampagne (CPA 15,33/90 T) auf der generischsten Zielseite. |

## Routing aus diesem Modul

| Befund | Route |
|---|---|
| 7 Seiten mit CVR < 50 % der Konto-CVR | **`/offer-auditor`** — wenn dieselbe Seite bei einem Gewerk 7,46 % und beim anderen 0,60 % liefert, liegt es am Angebot/Markt, nicht am Layout |
| 4 Seiten mit null Conversions | Erst Tracking klären: `context/analysis/tracking/tracking-audit.md` |
| Allokation: starke Seiten unterfinanziert | `/budget-auditor`, `/account-auditor` (Konsolidierung) |
| UMLAND auf Startseite ohne H1 | H1 ergänzen (Modul 2, Fix 2) — oder dedizierte UMLAND-Zielseite |

---

# Modul 5 — URL Health (LP-D32–D37)

**Score: 37,8 / 43 = 88 % — Good**
**Datenbasis:** 109 eindeutige URLs aus Anzeigen, Keywords und Assets · HEAD-Prüfung mit Weiterleitungsverfolgung

## Das Rohergebnis sieht schlimmer aus, als es ist

| | Anzahl |
|---|---|
| Geprüfte URLs | 109 |
| **404 / fehlerhaft** | **29** |
| Mit Weiterleitung | 25 |
| Fehlerfrei | 80 |

**29 kaputte URLs klingt nach einem Notfall. Es ist keiner:**

| Zuordnung | Anzahl |
|---|---|
| Kaputt auf **aktiven** Ketten | **0** |
| Kaputt nur auf pausierten Kampagnen | **29** |
| Weiterleitungen auf aktiven Ketten | **1** |

**Keine einzige ausliefernde Anzeige zeigt auf eine tote Seite.** Alle 29 gehören zu pausierten
Kampagnen.

> Das ist der zweite Fehlalarm dieser Audit-Serie, den die Statusprüfung entkräftet — nach den
> „265 Kampagnen ohne Negative" im Search-Term-Audit, von denen ebenfalls null aktiv waren.
> Rohzahlen aus Google-Ads-Exporten enthalten pausiertes Inventar; ohne Statusabgleich erzeugen
> sie regelmäßig Scheinbefunde.

## Was die toten URLs trotzdem erzählen

| Muster | Anzahl | Beispiele |
|---|---|---|
| `/de-de/` — **deutscher Markt** | **22** | `de-tischler-sea`, `de-stuckateur-sea`, `de-trockenbaumonteur-sea`, `DE_GSN_DE_Meister_Stuttgart`, `DE_GSN_DE_Brand` |
| `/de-ch/aktueller-job/…` | 5 | Einzelstellen-Seiten, die es nicht mehr gibt |
| `kollabo.ch` (Altdomain) | 2 | `maurer-schaler-per-sofort`, `heizungsmonteur-per-sofort-luzern` |

**Der interessante Teil ist der deutsche Markt.** 22 tote Seiten belegen einen **vollständigen
Markteintritt in Deutschland**, der wieder eingestellt wurde — mit eigenen Gewerke-Landingpages
(`de-tischler`, `de-stuckateur`, `de-trockenbaumonteur`), einer Brand-Kampagne
(`DE_GSN_DE_Brand`) und sogar einer Stadt-Kampagne (`DE_GSN_DE_Meister_Stuttgart`).

Das ist relevanter Kontext für die UMLAND-Diskussion: **Deutschland wurde bereits einmal im
großen Stil versucht.** UMLAND — die Grenzregionen-Kampagne mit CPA 15,33 über 90 Tage — ist
also nicht der erste DE-Versuch, sondern der überlebende. Bevor jemand „Deutschland ausbauen"
sagt, gehört die Frage geklärt, **warum der erste Anlauf beendet wurde.** Das steht in keiner
Quelle. **Neuer Gap.**

## Diagnostik-Ergebnisse — URL Health

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D32 | HTTP-Statuscodes | PASS | 15/15 | **0 von 109 URLs auf aktiven Ketten defekt.** Die 29 Fehler liegen sämtlich auf pausierten Kampagnen → Hygiene, kein Auslieferungsproblem. |
| LP-D33 | Weiterleitungsketten | PASS | 10/10 | Genau **1** Weiterleitung auf aktiver Kette: `kollabo.com/de-ch/jobs` → `…/jobs/` (1 Hop, Schrägstrich-Normalisierung). Fällt unter die zulässige Ausnahme. |
| LP-D34 | DSA-Ziel-URLs | SKIP | — | `DYN \| Catchall` ist die DSA-Kampagne (3.496 Impressionen, 5,5 Conv). DSA arbeitet mit Seiten-Feeds/Auto-Zielen, die im Anzeigen-Pull nicht enthalten sind. **Nicht prüfbar mit den vorliegenden Daten.** |
| LP-D35 | Keyword-Ziel-URLs | PASS | 5/5 | Keyword-Ebene-URLs vorhanden und fehlerfrei auf aktiven Ketten. |
| LP-D36 | Asset-URLs | SKIP | — | `assets.csv` führt nur `asset.image_asset.full_size.url` (Bild-Dateien). **Sitelink-Ziel-URLs sind im Pull nicht enthalten** — der `assets.gaql` fragt `asset.sitelink_asset.final_urls` nicht ab. Datenlücke, kein Befund. |
| LP-D37 | Final-URL-Expansion | WARN | 7,8/13 | `/account-auditor` (2026-08-10) fand `TEXT_ASSET_AUTOMATION = OPTED_IN` auf **UMLAND TEST** und 10 weitere Kampagnen ohne gesetzten Wert (Google-Default). Erweiterte Ziel-URLs sind damit aktiv, ihre Qualität ist **nicht verifizierbar**. |

## Was daraus folgt

| # | Aktion | Priorität |
|---|---|---|
| 1 | **Nichts Dringendes.** Keine aktive Anzeige zeigt auf eine tote Seite. | — |
| 2 | 29 tote URLs auf pausierten Kampagnen bereinigen — bevor eine davon reaktiviert wird | niedrig, aber vor jeder Reaktivierung |
| 3 | **Klären, warum der deutsche Markteintritt beendet wurde** — bevor UMLAND ausgebaut wird | **hoch**, betrifft die Skalierungsstrategie |
| 4 | Sitelink-Ziel-URLs in den `gads-context`-Pull aufnehmen (`asset.sitelink_asset.final_urls`) | Tooling |
| 5 | Final-URL-Expansion auf UMLAND prüfen — dieselbe Einstellung, die auch Anzeigentexte automatisch umschreibt | mittel |

---

# Gesamtergebnis LP-Audit

| Modul | Score | Gewicht | Beitrag |
|---|---|---|---|
| Structural (D01–D12) | 58 % | 35 % | 20,3 |
| Message Match (D13–D16) | 52 % | 20 % | 10,4 |
| Technical (D17–D24) | 82 % | 20 % | 16,4 |
| Performance (D25–D31) | 27 % | 15 % | 4,1 |
| URL Health (D32–D37) | 88 % | 10 % | 8,8 |
| **Gewichteter Gesamtscore** | | | **60 % — Needs Attention** |

## Die Kernaussage nach fünf Modulen

Die Landingpage-Vorlage ist **mittelmäßig, nicht kaputt**. Inhalt und Ladezeit sind gut,
URL-Hygiene ist sauber, die Technik hat behebbare Mängel. Was sie kostet, ist **Ad Rank** —
über 114 Ausgänge, gesperrten Zoom, 13 Kontrastverstöße und semantische Fehler. Das erklärt
den Rangverlust von 37–73 %.

**Was sie nicht erklärt, ist die Conversion-Rate.** Bei identischer Vorlage spreizt sich die
CVR um Faktor 12,4 zwischen den Gewerken. Diese Differenz entsteht vor der Seite — in der
Passung zwischen Suchintention, Gewerk und Angebot.

**Zwei getrennte Baustellen, zwei getrennte Adressaten:**

| Problem | Wirkung | Adressat |
|---|---|---|
| Vorlage: Ausgänge, Zoom, Kontrast, Semantik | Ad Rank → Sichtbarkeit | `/lp-optimizer` + Dev |
| Gewerke-Passung: CVR 0,60 % bis 7,46 % | Conversion-Rate | **`/offer-auditor`** |
