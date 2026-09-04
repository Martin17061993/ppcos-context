# Website-Anpassungen kollabo.com — Umsetzungsauftrag

**Datum:** 18.08.2026 · **Von:** Martin Weingarten (Google Ads) · **An:** Kollabo Web/Dev
**Kontext:** Analyse der Landingpages aus Google-Ads-Sicht. Alle Befunde sind am Live-System gemessen, nicht vermutet.

---

## Warum das zählt — in drei Sätzen

Google bewertet jede Landingpage mit einer „Landing Page Experience". Bei **79 % der Keywords im Kollabo-Konto steht diese Bewertung auf unterdurchschnittlich** — und sie ist bei 125 Keywords der *einzige* Grund, warum Anzeigen schlechter platziert werden. Konkret: **29 von 30 Kampagnen verlieren Sichtbarkeit an den Anzeigenrang, nicht am Budget.** Mehr Werbebudget löst das nicht; die Seiten lösen es.

Die fünf Punkte unten sind nach Aufwand-Wirkung sortiert. Punkt 1 ist eine Zeile Code und wirkt auf die gesamte Website.

---

## 1. Zoom-Sperre auf Mobilgeräten aufheben

**Priorität: hoch · Aufwand: Minuten · Wirkung: gesamte Website**

### Was ist

Im `<head>` jeder Seite steht:

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=0">
```

`user-scalable=0` und `maximum-scale=1` verbieten Nutzern das Zoomen. Auf dem Handy lässt sich auf kollabo.com **nirgends** mit zwei Fingern vergrößern.

### Was soll sein

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Nur die beiden Parameter entfernen, sonst nichts ändern.

### Warum

- Google führt Mobile-Bedienbarkeit ausdrücklich als Faktor der Landing-Page-Bewertung. Google Lighthouse meldet die Sperre als eigenen Fehler.
- **71,6 % der Werbeausgaben laufen über Mobilgeräte** — und Mobil konvertiert mit **2,09 %** nur halb so gut wie Desktop mit **4,11 %**.
- Zielgruppe sind Handwerker, oft auf der Baustelle, bei Sonnenlicht, mit Arbeitshandschuhen. Wer ein Formularfeld nicht vergrößern kann, bricht ab.
- Es ist zusätzlich ein Barrierefreiheits-Verstoß (WCAG 1.4.4).

### Prüfen

Handy → kollabo.com öffnen → mit zwei Fingern aufziehen. Muss zoomen.

---

## 2. Nutzenversprechen nach oben ziehen

**Priorität: hoch · Aufwand: Umsortieren, kein neuer Text · Betrifft: 2 Seiten**

### Was ist

Auf beiden Seiten steht der Satz, der erklärt *warum Kollabo*, ganz unten — hinter dem Bewerbungsformular:

| Seite | Seitenhöhe | Formular bei | Nutzenversprechen bei |
|---|---|---|---|
| `kollabo.com/de-ch/jobs/` | 7.862 px | 5.713 px | **5.832 px (74 %)** |
| `kollabo.com/de-ch/` | 5.862 px | 3.513 px | **3.632 px (62 %)** |

Gemeint ist dieser Block:

> „Statt hunderte von Bewerbungen zu senden, bewirbst du dich bei kollabo nur 1x."
> „Du bewirbst dich nur 1x – wir übernehmen den Rest."
> Dazu die Sektion „3 EINFACHE SCHRITTE".

Oberhalb des sichtbaren Bereichs stehen dagegen: Logo, Navigation, zwei Telefonnummern, E-Mail, Öffnungszeiten, die Überschrift „Jobs für Handwerker" und die Gewerke-Filterleiste.

### Was soll sein

Den bestehenden Nutzen-Block **direkt unter die Hauptüberschrift** verschieben — vor die Gewerke-Filter und vor die Job-Kacheln. **Der Text bleibt wortgleich**, es geht ausschließlich um die Reihenfolge der Sektionen.

### Warum

Ein Besucher kommt über eine Google-Anzeige, die „Bewerben ohne Anschreiben" und „Nur 1x bewerben" verspricht. Er landet auf einer Seite, die eine Überschrift und eine Filterleiste zeigt — dasselbe Bild wie bei jobs.ch oder Indeed. Das Alleinstellungsmerkmal erfährt er erst nach sieben Bildschirmhöhen, und da hat er das Formular schon passiert.

---

## 3. „Facebook Rating 0" entfernen

**Priorität: hoch · Aufwand: Widget-Einstellung · Betrifft: gesamte Website**

### Was ist

Im Vertrauens-Block steht wörtlich:

> „Die unabhängigen Bewertungen von kollabo auf Google sind hervorragend. Und mit Grund: Jeder dritte Bewerber findet den neuen direkt über kollabo. **Google Rating 4.9 — Facebook Rating 0**"

Ein Bewertungs-Widget, das **0** anzeigt — direkt neben der 4.9. Gefunden auf der Startseite und auf den Gewerke-Seiten, also site-weit.

### Was soll sein

Das Facebook-Widget entweder mit echten Daten befüllen oder **ausblenden**. Die Google-Bewertung 4.9 bleibt.

### Warum

Das ist der Abschnitt, in dem die Seite Vertrauen aufbaut. Eine sichtbare Null ist dort kein neutrales Element, sondern ein aktives Misstrauenssignal — direkt neben dem stärksten Argument.

---

## 4. Fehlende Hauptüberschrift auf der Startseite

**Priorität: mittel · Aufwand: eine Zeile · Betrifft: `kollabo.com/de-ch/`**

### Was ist

Die Startseite hat **kein `<h1>`-Element**. Gemessen: `document.querySelectorAll('h1').length === 0`. Die Hero-Überschrift „JOBS FÜR HANDWERKER" ist als `<h2>` ausgezeichnet.

Google Lighthouse meldet dazu: *„Heading elements are not in a sequentially-descending order"* und *„Accessibility tree is not well-formed"*.

### Was soll sein

Die Hero-Überschrift von `<h2>` auf `<h1>` ändern. Rein semantisch — das Aussehen bleibt, falls die Formatierung über CSS-Klassen läuft.

### Warum

Das `<h1>` ist das Feld, über das Suchmaschinen und Screenreader erkennen, worum es auf einer Seite geht. Auf der Startseite fehlt dieses Signal komplett.

---

## 5. Abgebrochener Satz auf den Gewerke-Seiten

**Priorität: niedrig · Aufwand: Tippfehler · Betrifft: Gewerke-Vorlagen**

### Was ist

> „Jeder dritte Bewerber findet den **neuen** direkt über kollabo."

Dem Satz fehlt das Wort „Job". Gefunden auf `kollabo.com/de-ch/jobs/gipser-jobs/`, betrifft die Vorlage `/de-ch/jobs/{gewerk}-jobs/` — also 14+ Seiten.

### Was soll sein

> „Jeder dritte Bewerber findet den neuen **Job** direkt über kollabo."

---

## Nachrangig, aber erwähnenswert: Ausgangsdichte

Die Job-Hub-Seite enthält **129 Links** (30 in der Navigation, 48 in der Fusszeile), die Startseite 85. Jeder davon ist ein Weg aus dem Bewerbungsprozess heraus.

Das ist kein Fehler, sondern eine bewusste Website-Architektur — für Seiten, auf die bezahlte Anzeigen führen, ist sie aber teuer. **Kein Auftrag, sondern ein Gesprächsthema:** ob es sinnvoll ist, für Google-Ads-Traffic reduzierte Varianten dieser zwei Seiten anzulegen (ohne Kopfnavigation, mit verkürzter Fusszeile).

---

## Was ausdrücklich gut ist

Damit die Liste nicht falsch ankommt — folgendes wurde geprüft und ist in Ordnung:

- **Die Texte selbst.** Markenstimme, Duz-Form, die drei Schritte, das Nutzenversprechen — sprachlich gut gemacht.
- **Message Match zu den Anzeigen: 80 %.** Was die Anzeigen versprechen, liefern die Seiten inhaltlich auch.
- **SEO-Grundlage: Lighthouse 100/100.**
- **HTTPS, Bildoptimierung, Layoutstabilität (CLS 0)** — alles sauber.
- **68 echte, tagesaktuelle Stellenanzeigen** je Gewerkeseite. Inhaltliche Relevanz auf einem Niveau, das die meisten Landingpages nicht erreichen.

Es geht in dieser Liste nicht um Qualität der Inhalte, sondern um **Reihenfolge, ein Meta-Tag und ein defektes Widget**.

---

## Zusammenfassung für die Planung

| # | Was | Aufwand | Reichweite |
|---|---|---|---|
| 1 | Zoom-Sperre entfernen | Minuten | gesamte Website |
| 2 | Nutzenversprechen nach oben | Umsortieren | 2 Seiten |
| 3 | „Facebook Rating 0" entfernen | Widget-Einstellung | gesamte Website |
| 4 | `<h1>` auf Startseite | eine Zeile | 1 Seite |
| 5 | Fehlendes Wort „Job" | Tippfehler | 14+ Seiten |

**Rückmeldung erbeten:** Welche der fünf Punkte sind bis wann machbar? Punkt 1 hat mit Abstand das beste Verhältnis von Aufwand zu Wirkung.

---

*Messgrundlage: Chrome DevTools und Google Lighthouse am 18.08.2026, Desktop 1440×900 und Mobil-Emulation. Google-Ads-Kennzahlen aus dem Konto 148-770-7588, Zeitraum 30 Tage.*
