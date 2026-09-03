# LP Audit — Kollabo

**Datum:** 2026-08-18 · **Modus:** Page Quality — Structural (D01–D12) + Message Match (D13–D16) + Technical (D17–D24) · **Vertical:** Lead Gen
**Geprüfte URLs:**
- `https://kollabo.com/de-ch/jobs/` — Job-Hub, 570,52 CHF LP-Below-Spend, 9 Keywords
- `https://kollabo.com/de-ch/` — Startseite, 362,00 CHF LP-Below-Spend, 4 Keywords

> 📁 Der Report vom 11.08. zur **Gewerke-Vorlage** (`/de-ch/jobs/gipser-jobs/`, Score 60 %) wurde vor dem Überschreiben nach `lp-audit-2026-08-11-gewerke-vorlage.md` archiviert. Er wird von drei Audits vom 18.08. zitiert und bleibt gültig — dieser Lauf prüft **andere Seitentypen**, er ersetzt ihn nicht.

---

## Executive read

**55 % — und diese beiden Seiten sind schlechter als die Gewerke-Vorlage, die am 11.08. mit 60 % durchlief.** Das ist relevant, weil sie zusammen **932 CHF** Spend auf Keywords mit unterdurchschnittlicher LP-Erfahrung tragen — mehr als jede einzelne Gewerkeseite. `/quality-score-auditor` (heute, 44 %) hat sie als teuerste LP-Positionen identifiziert und festgestellt, dass sie noch nie geprüft wurden. Zu Recht.

**Der Kernbefund ist eine Zahl.** Auf dem Job-Hub steht das eigentliche Versprechen — *„Statt hunderte von Bewerbungen zu senden, bewirbst du dich bei kollabo nur 1x"* — bei **Pixel 5.832 einer 7.862 Pixel hohen Seite**. Das ist unterhalb des Bewerbungsformulars. Auf der Startseite steht es bei 3.632 von 5.862. Der 11.08.-Report kritisierte an der Gipser-Seite, das Versprechen stehe „erst bei 832 Pixel" — hier ist es **siebenmal tiefer**. Was oberhalb der Falz steht, ist auf beiden Seiten: Logo, Navigation, zwei Telefonnummern, E-Mail, Öffnungszeiten, eine Kategorie-Überschrift und Gewerke-Filter. Kein Nutzenargument, kein Grund, sich ausgerechnet hier zu bewerben.

**Zwei harte technische Defekte kommen dazu.** Erstens: `<meta name="viewport">` steht auf `maximum-scale=1, user-scalable=0` — **Pinch-Zoom ist auf Mobilgeräten vollständig deaktiviert.** Bei 71,6 % Mobile-Spend und einer Mobile-CVR von 2,09 % gegen 4,11 % auf Desktop ist das ein konkreter Kandidat für die Hälfte der fehlenden Conversions. Zweitens: **die Startseite hat überhaupt kein `<h1>`** — der Hero läuft über ein `<h2>`, und Lighthouse meldet entsprechend *„Heading elements are not in a sequentially-descending order"*.

**Kein Problem sind:** Message Match (80 %) — die Anzeigen versprechen „Jobs für Handwerker:innen" und die Seiten liefern genau diese Überschrift; Duz-Form durchgehend korrekt; HTTPS; CLS bei 0; Bildoptimierung; und die CTA-Formulierung „Jetzt bewerben". **Eine Korrektur zu meinem eigenen Zwischenbefund:** Der Text *„Wählen Sie Dateien aus"* im Formular ist **nicht** Kollabos Copy und keine Duz-Form-Verletzung — es ist die native Beschriftung des Browsers für `<input type="file">`. Das Feld trägt ein eigenes, korrektes Label: „Bewerbungsunterlagen". Geprüft und widerlegt.

**Kein Score-Trend** — erster Lauf für diese beiden URLs.

---

## Score

| Modul | Punkte | % | Bewertung |
|---|---|---|---|
| Structural (D01–D12) | 25 / 60 | 42 % | Critical |
| Message Match (D13–D16) | 16 / 20 | 80 % | Good |
| Technical (D17–D24) | 16 / 30 | 53 % | Needs Attention |
| **GEWICHTET** | | **55 %** | **Needs Attention** |

> Gewichtung Lead Gen, auf die drei gelaufenen Module normalisiert: Structural 46,7 % · Message Match 26,7 % · Technical 26,7 %.
> **Nicht gelaufen:** Performance (D25–D31), URL Health (D32–D37) — beide am 11.08. mit 27 % bzw. 88 % bewertet. Ecommerce (D38–D40) entfällt.
> **SKIP:** D17 und D18 — `lighthouse_audit` liefert keine Performance-Metriken (LCP/TBT). CLS wurde mit **0** gemessen und ist sauber.

---

## Priorität 1 — Der Hero verkauft nichts (LP-D02 FAIL)

**Was oberhalb der Falz steht, auf beiden Seiten:**

| y-Position | Element |
|---|---|
| 49 | +41 44 202 26 26 · +41 79 807 77 07 · info@kollabo.com · Montag–Freitag 08–18h |
| 99–116 | ALLE JOBS · ÜBER UNS · Login Portal · Jetzt bewerben |
| 240 / 260 | „Jobs für Handwerker" (Hub: `<h1>` · Startseite: `<h2>`) |
| 378 / 384 | Gewerke-Filter: Alle · Elektro · Gebäudehülle · HLKS · Hoch & Tiefbau · Holz · Industrie · Innenausbau · Mechaniker |
| 669 | Cookie-Banner, 211 px hoch |

Das ist eine **Kategorieseite**, keine Landingpage. Ein Bewerber, der auf „handwerker jobs schweiz" klickt, sieht eine Überschrift, die seine Suchanfrage wiederholt, und danach eine Filterleiste. Warum Kollabo statt jobs.ch — die Antwort steht 5.832 Pixel weiter unten.

**Wo das Versprechen tatsächlich steht:**

| Seite | Seitenhöhe | Formular bei | USP bei | USP-Tiefe |
|---|---|---|---|---|
| `/de-ch/jobs/` | 7.862 px | 5.713 px (73 %) | **5.832 px** | **74 %** |
| `/de-ch/` | 5.862 px | 3.513 px (60 %) | **3.632 px** | **62 %** |

> Auf beiden Seiten steht das Nutzenargument **hinter** dem Formular. Wer sich entscheiden will, bevor er das Formular ausfüllt, findet den Grund erst danach.

**Fix:** Das bestehende USP-Modul („Statt hunderte von Bewerbungen zu senden, bewirbst du dich bei kollabo nur 1x" + „3 einfache Schritte") nach oben ziehen, direkt unter die Überschrift. Der Text existiert bereits und ist gut — er steht nur an der falschen Stelle. Kein Neutexten nötig.

---

## Priorität 2 — Pinch-Zoom auf Mobil deaktiviert (LP-D19 FAIL)

Gemessener Wert im DOM:

```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0">
```

`user-scalable=0` **und** `maximum-scale=1` schalten das Zoomen auf Mobilgeräten vollständig ab. Lighthouse meldet das als eigenen Fehlschlag.

**Warum das hier besonders zählt:**

| Gerät | Spend | Anteil | Conv | CPA | CVR |
|---|---|---|---|---|---|
| **Mobile** | 5.630,27 CHF | **71,6 %** | 95,94 | 58,68 | **2,09 %** |
| Desktop | 2.197,07 CHF | 27,9 % | 53,67 | 40,93 | **4,11 %** |
| Tablet | 37,03 CHF | 0,5 % | 0,00 | — | 0,00 % |

**Desktop konvertiert 1,97× besser, während 71,6 % des Geldes auf Mobil läuft.** Das ist der grösste einzelne Effizienzunterschied im Konto. Ein Zoomverbot ist nicht die einzige mögliche Ursache, aber es ist eine belegte, in Minuten behebbare — und Google führt Mobile-Usability explizit als Faktor der Landing-Page-Erfahrung.

**Fix:** `maximum-scale` und `user-scalable` aus dem Viewport-Meta entfernen. Ein Wort in der Theme-Konfiguration. Betrifft die **gesamte Website**, nicht nur diese zwei Seiten.

---

## Priorität 3 — Startseite ohne `<h1>` (LP-D12 FAIL)

Gemessen: `document.querySelectorAll('h1').length === 0` auf `https://kollabo.com/de-ch/`.

Die Hero-Überschrift „JOBS FÜR HANDWERKER" ist ein `<h2>`. Lighthouse bestätigt: *„Heading elements are not in a sequentially-descending order"* und *„Accessibility tree is not well-formed"*.

Der Job-Hub hat zwar ein korrektes `<h1>`, aber insgesamt nur **drei Überschriften auf 7.862 Pixel** (H1 „Jobs für Handwerker", H2 „WARUM KOLLABO", H3 „JETZT ANMELDEN"). Für eine Seite dieser Länge ist das keine Struktur.

---

## Weitere Befunde

### „Facebook Rating 0" ist auch hier (LP-D07 FAIL)

Auf der Startseite gemessen. Damit ist der Prio-1-Befund aus dem 11.08.-Report **nicht auf die Gewerke-Vorlage beschränkt, sondern site-weit**. Der abgebrochene Satz („findet den neuen direkt über kollabo") wurde hier **nicht** gefunden — der ist vorlagenspezifisch.

### Der Job-Hub hat gar keine Vertrauenssignale (LP-D06 WARN)

| Signal | `/de-ch/` | `/de-ch/jobs/` |
|---|---|---|
| Google Rating 4.9 | ✅ | ❌ **fehlt** |
| Facebook Rating 0 (Defekt) | ⚠️ vorhanden | — |
| Telefonnummern | ✅ | ✅ |
| Öffnungszeiten | ✅ | ✅ |
| Testimonials mit Namen/Foto | ❌ | ❌ |
| FAQ | ❌ | ❌ (0 Elemente) |

Die teuerste der beiden Seiten (570 CHF) trägt **kein einziges Bewertungssignal**. `business.md` §12 führt „4.9 Google Rating" als erlaubten quantitativen Claim — er wird hier nicht genutzt.

### Ausgangsdichte (LP-D11 FAIL)

| Seite | Links gesamt | Navigation | Fusszeile |
|---|---|---|---|
| `/de-ch/jobs/` | **129** | 30 | 48 |
| `/de-ch/` | **85** | — | 48 |
| *(Vergleich 11.08.: `/gipser-jobs/`)* | *114* | — | *41* |

Der Job-Hub hat **mehr Ausgänge als die am 11.08. kritisierte Gewerkeseite**. Jeder Link ist ein Weg aus dem Bewerbungsprozess heraus.

### Keine Risikoumkehr (LP-D09 FAIL)

Weder Garantie noch Zusicherung noch „unverbindlich" auf einer der beiden Seiten. Deckt sich mit `/offer-auditor` (11.08., 78 %): *„Die erste Lücke ist Risikoumkehr, und sie ist die wichtigste… erfährt mein aktueller Arbeitgeber davon, und wohin gehen meine Daten? Beides wird nirgends adressiert."* Für eine Stellenplattform ist **Diskretion** das eigentliche Risikoargument.

### Lighthouse (Mobil, Startseite)

| Kategorie | Score |
|---|---|
| SEO | **100** |
| Accessibility | 81 |
| Best Practices | 77 |
| Agentic Browsing | 67 |

**9 fehlgeschlagene Audits**, die relevanten:

| Befund | LP-Bezug |
|---|---|
| `[user-scalable="no"]` im Viewport-Meta | **LP-D19 — Prio 2** |
| Heading elements not in sequentially-descending order | LP-D12 — fehlendes H1 |
| Form elements do not have associated labels | LP-D22 — 1 Feld ohne Label |
| Background/foreground contrast insufficient | Lesbarkeit, besonders mobil |
| Links do not have a discernible name | Accessibility |
| Uses third-party cookies (4) | Consent — siehe `/tracking-specialist` |

---

## Diagnostik-Ergebnisse

### Structural (25 / 60)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D01 | Offer Section Completeness | WARN | 3/5 | Alle Komponenten vorhanden (nur 1x bewerben · kostenlos · wir übernehmen den Rest · 3 Schritte), aber bei 62–74 % Seitentiefe |
| LP-D02 | Hero 5-Second Test | **FAIL** | 0/5 | Hero = Kategorie-Überschrift + Gewerke-Filter. Kein Nutzenargument oberhalb der Falz |
| LP-D03 | Above-Fold CTA Presence | PASS | 5/5 | „Jetzt bewerben" bei y=99 in der Navigation |
| LP-D04 | CTA Button Quality | PASS | 5/5 | „Jetzt bewerben" — klar, handlungsorientiert, Duz-Form |
| LP-D05 | Benefits Section Quality | WARN | 3/5 | „3 EINFACHE SCHRITTE" (y=1.278) und „WARUM KOLLABO" vorhanden, aber tief |
| LP-D06 | Trust/Authority Section | WARN | 3/5 | Startseite: Google 4.9 ✅ · **Job-Hub: kein Rating** |
| LP-D07 | Social Proof Quality | **FAIL** | 0/5 | „Facebook Rating 0" sichtbar; keine Testimonials mit Namen/Foto; Hub ohne jedes Rating |
| LP-D08 | Objection Handling | WARN | 3/5 | kostenlos, AGB/Datenschutz, Telefon, „ohne Anschreiben" — aber **0 FAQ** |
| LP-D09 | Guarantee Presence | **FAIL** | 0/5 | Keine Garantie, keine Zusicherung, kein „unverbindlich" |
| LP-D10 | CTA Repetition | WARN | 3/5 | 3 sichtbare „Jetzt bewerben" auf 7.862 px — dünn für die Länge |
| LP-D11 | One-Page-One-Goal | **FAIL** | 0/5 | 129 bzw. 85 Links, je 48 in der Fusszeile |
| LP-D12 | Section Hierarchy | **FAIL** | 0/5 | Startseite **ohne H1**; Hub mit 3 Überschriften auf 7.862 px |

### Message Match (16 / 20)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D13 | Ad-to-LP Headline Match | WARN | 3/5 | Anzeige „Jobs für Handwerker:innen" ↔ LP „Jobs für Handwerker" — starke Deckung. Abzug: Startseite liefert sie als `<h2>` statt `<h1>` |
| LP-D14 | Ad-to-LP Offer Match | WARN | 3/5 | Anzeigen versprechen „Bewerben ohne Anschreiben", „In unter einer Minute bewerben", „Nur 1x bewerben" — die Seite löst das erst bei 62–74 % Tiefe ein |
| LP-D15 | Keyword-to-LP Relevance | PASS | 5/5 | Generische Hub-Seiten für generische Suchanfragen — passend. Hub wird von der Brand-Ad-Group „Kollabo Name" bedient, Startseite von `STAN \| HOME \| BROAD` (UMLAND) |
| LP-D16 | Visual Consistency | PASS | 5/5 | Logo, Farbwelt, Tonalität konsistent; Duz-Form in Anzeigen („Dich", „Deiner") und auf der Seite durchgehend |

### Technical (16 / 30)

| ID | Diagnostik | Status | Pts | Befund |
|---|---|---|---|---|
| LP-D17 | Page Load Speed | SKIP | — | `lighthouse_audit` liefert keine Performance-Metriken. Für LCP/TBT wäre ein Performance-Trace nötig |
| LP-D18 | Core Web Vitals | SKIP | — | **CLS = 0 gemessen (sauber)**; LCP und TBT nicht verfügbar |
| LP-D19 | Mobile Responsiveness | **FAIL** | 0/5 | `maximum-scale=1, user-scalable=0` — Pinch-Zoom deaktiviert |
| LP-D20 | Mobile vs Desktop CVR Gap | **FAIL** | 0/5 | Mobile 2,09 % vs. Desktop 4,11 % = **1,97× Lücke** bei 71,6 % Mobile-Spend |
| LP-D21 | Form Field Count | WARN | 3/5 | 6 sichtbare Eingaben + Datei-Upload + 2 Checkboxen. Für eine Bewerbung vertretbar, der Upload ist Reibung |
| LP-D22 | Form Functionality | WARN | 3/5 | 1 Feld ohne Label (Lighthouse). Absenden nicht getestet — kein Test-Submit ohne deine Freigabe |
| LP-D23 | SSL/HTTPS | PASS | 5/5 | HTTPS aktiv |
| LP-D24 | Image Optimization | PASS | 5/5 | 78 Bilder, keine Lighthouse-Beanstandung zu Grösse/Format |

---

## Routing

| Priorität | Was | Wohin |
|---|---|---|
| 1 | **USP-Modul nach oben ziehen** — Text existiert, steht nur bei 62–74 % Tiefe | `/lp-optimizer elements` |
| 2 | **Viewport-Meta korrigieren** (`user-scalable`, `maximum-scale` entfernen) — site-weit, Minuten | `/lp-optimizer mobile` |
| 3 | **`<h1>` auf der Startseite setzen** | `/lp-optimizer elements` |
| 4 | **„Facebook Rating 0" entfernen** — site-weit, nicht nur die Gewerke-Vorlage | **Bestehenden Report lesen:** `lp-audit-2026-08-11-gewerke-vorlage.md` Prio 1 — Fix ist dort bereits beschrieben |
| 5 | **Google Rating 4.9 auf den Job-Hub bringen** | `/lp-optimizer elements` |
| 6 | **Risikoumkehr formulieren** (Diskretion gegenüber aktuellem Arbeitgeber, Datenschutz) | **Bestehenden Report lesen:** `offer/offer-audit.md` (11.08., 78 %) — *„Für eine Stellenplattform ist Diskretion das eigentliche Risikoargument, und es ist ungenutzt."* |
| 7 | **Ausgangsdichte reduzieren** (129 Links auf dem Hub) | `/lp-optimizer elements` |

**Nicht nötig:** `/rsa-maker`. `/quality-score-auditor` (heute) misst Ad Relevance bei 8,9 % — die Anzeigen treffen. Message Match liegt hier bei 80 %.

---

## Cross-Skill-Kontext

| Peer | Datum | Score | Was es für diesen Report bedeutet |
|---|---|---|---|
| `/quality-score-auditor` | 18.08. | 44 % | *„LP-Erfahrung bei 176/223 Keywords BELOW_AVG (78,9 %), bei 125 die allein limitierende Komponente."* Hat diese zwei URLs als teuerste ungeprüfte Position identifiziert — dieser Lauf schliesst die Lücke |
| `/lp-auditor` (Vorlauf) | 11.08. | 60 % | Gewerke-Vorlage. *„Die Inhalte sind gut… die Vermutung verschiebt sich auf Ausgangsdichte und Technik."* **Bestätigt** — hier sind es 129 Links und ein Zoomverbot |
| `/offer-auditor` | 11.08. | 78 % | *„Erste Lücke ist Risikoumkehr… Diskretion ist das eigentliche Risikoargument."* Auf beiden Seiten unadressiert |
| `/competitive-analyst` | 11.08. | 41 % | *„Aggressiv konkurrieren — aber über Quality Score, nicht über Gebote."* LP ist der QS-Hebel |
| `/budget-auditor` | 18.08. | 80 % | 29/30 Kampagnen rang-limitiert — LP drückt den Ad Rank |
| `/bidding-auditor` | 18.08. | 65 % | 28/30 unter Lernschwelle — LP-Fixes erhöhen Conversions und lösen mittelbar auch das |
| `/tracking-specialist` | 10.08. | 48 % | **Vorbehalt:** Consent Mode v2 nicht verdrahtet, `npa=1`. CVR-Zahlen in D20 stehen unter Messvorbehalt |

**Kein Widerspruch zwischen den Peers.** Alle sechs zeigen auf dieselbe Ursache.

---

## Datenlage

| Punkt | Bedeutung |
|---|---|
| Messung Desktop 1440×900 | Erste Messungen liefen versehentlich auf Mobilbreite (docHeight 18.234 px) und wurden auf Desktop wiederholt. Die Zahlen im Report sind Desktop-Werte |
| Lighthouse: Mobil, Navigation-Modus, Startseite | Job-Hub nicht separat gelighthoused — gleiche WordPress-Vorlage, Viewport-Meta ist site-weit |
| D17/D18 unvollständig | `lighthouse_audit` schliesst Performance aus. CLS = 0 verfügbar, LCP/TBT nicht |
| Formular nicht abgesendet | Kein Test-Submit ohne deine Freigabe — D22 daher nur strukturell bewertet |
| Cookie-Banner aktiv | 211 px hoher Overlay bei y=669 während der Messung. Beeinflusst die reale Sichtbarkeit oberhalb der Falz zusätzlich negativ |
