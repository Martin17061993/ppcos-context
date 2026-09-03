---
id: kollabo.search-terms-rules
layer: customer
client: kollabo
status: canonical
triggers: [search-terms, keyword-optimization]
topics: [search-terms, negatives, tiering]
last_reviewed: 2026-05-20
---
# Kollabo – Search Terms Regeln

## Account-Kontext
- **Customer ID:** 148-770-7588
- **MCC:** 5591362086
- **Budget:** 235 CHF/Tag (~7.000 CHF/Monat)
- **Match Type:** Alle Keywords sind Broad Match
- **Branche:** Personalvermittlung Baugewerbe (Temporärarbeit)
- **Zielgruppe:** Deutschsprachige Bauarbeiter in der Schweiz, aktiv arbeitssuchend
- **Conversion:** Worker-Registrierung via "Jetzt bewerben"

---

## Kampagnenstruktur

Naming Convention: `EX | [Jahr] | [Land] | SEARCH | LEAD | [Gewerk]`

### Aktive Gewerke (Kampagnen)
Letzter API-Abgleich: 2026-04-21.

Elektroinstallateur, Sanitärinstallateur, Dachdecker, Zimmermann, Bauarbeiter, Baumaschinenführer, Metallbauer, Metallbaukonstrukteur, Gipser, Gerüstbauer, Polymechaniker, Grundbauer, Gärtner, Produktionsmechaniker, Strassenbauer, Abdichter, Heizungsinstallateur, Montage-Elektriker, Automatiker, Schweisser, Maler, Kranführer, Montage-Schreiner, Brand, Compeditor, DYN Catchall

Hinweis: Die Gewerke **Storenmonteur, Trockenbauer, Spengler** haben aktuell keine eigene Kampagne, tauchen aber in Search Terms auf. Sie werden über Overlap-Regeln (siehe unten) in die verwandten Kampagnen geroutet.

### Kampagnen-Logik
- Jede Kampagne deckt EIN spezifisches Gewerk ab
- Die **Brand-Kampagne** fängt alle Kollabo-Suchanfragen ab
- Die **Compeditor-Kampagne** bietet bewusst auf Competitor-Brand-Terms (jobs.ch, Adecco etc.). Hier sind Competitor-Terms RELEVANT, NICHT negativ. NKW_Compeditor wird auf diese Kampagne NICHT angewendet.
- Die **DYN Catchall-Kampagne** fängt restliche relevante Suchanfragen ab
- **UMLAND TEST** testet den DACH-Raum ausserhalb CH

---

## Negativ-Keyword-Listen (Shared Lists)

### Struktur der 6 Listen

| Liste | Keywords | Angewendet auf | Zweck |
|---|---|---|---|
| **NKL_Generisch** | 394 | 311 Kampagnen | Generische/irrelevante Suchbegriffe |
| **NKW_Compeditor** | 1026 | 34 Kampagnen | Alle Competitor-Brands |
| **NKW_Brand** | 48 | 34 Kampagnen | Kollabo Brand-Varianten (für Nicht-Brand-Kampagnen) |
| Negative KWs | 37 | 80 Kampagnen | Legacy-Liste (allgemein) |
| Negative KWs 1-Campaigns | 31 | 36 Kampagnen | Legacy-Liste (kampagnenspezifisch) |
| Negative KWs DE | 27 | 36 Kampagnen | Legacy-Liste (DE-Markt) |

### Zuordnungsregeln für neue Negativ-Keywords

**NKL_Generisch** – Hierhin gehören:
- Suchbegriffe ohne kommerziellen Job-Bezug (z.B. "was verdient ein dachdecker", "ausbildung maurer dauer")
- Fremdsprachige Suchbegriffe die nicht Deutsch sind (Italienisch, Französisch, Englisch) – AUSSER die UMLAND TEST Kampagne
- Berufe die NICHT in der Gewerk-Liste oben stehen
- Suchanfragen die auf Arbeitgeber/Auftraggeber-Seite abzielen ("personal finden", "mitarbeiter suchen", "temporärfirma gründen")
- Ausbildungs-/Lehr-Suchanfragen ("lehrstelle", "ausbildung", "lehrling", "lehre als")
- DIY/Hobby-Suchanfragen ("selber machen", "anleitung", "tutorial")
- Gehalt/Lohn-Recherche ohne Bewerbungsabsicht ("gehalt", "lohn", "verdienst", "salär" – NUR wenn ohne Jobbezug)
- Standorte ausserhalb der Schweiz (ausser UMLAND TEST)

**NKW_Compeditor** – Hierhin gehören:
- Alle erkannten Competitor-Marken und deren Varianten
- Bekannte Competitors: jobs.ch, jobup.ch, jobscout24.ch, Indeed, JobCloud, Adecco, Randstad, Manpower, Kelly Services, Coople, DasTeam, Dekra, Holcim, Gross Arbeit AG, Inova Personal, Job 3000, Interim Pro, All in One Personal, Bautech Personal
- Staffing-Firmen die nicht Kollabo sind
- Job-Portale die nicht Kollabo sind

**NKW_Brand** – Hierhin gehören:
- Alle Kollabo Schreibvarianten: kollabo, kolabo, collabo, kallabo, kollabo ag, kollabo.ch, kollabo app
- Wird auf alle Nicht-Brand-Kampagnen angewendet, damit Brand-Traffic nur in die Brand-Kampagne fliesst

---

## Relevanz-Regeln pro Kampagne

### Grundprinzip
Ein Suchbegriff ist nur dann relevant für eine Kampagne, wenn er das Gewerk der Kampagne betrifft. Beispiel: "elektriker job zürich" ist relevant für die Elektroinstallateur-Kampagne, aber NICHT für die Dachdecker-Kampagne.

### Cross-Kampagnen Negativierung
Wenn ein Suchbegriff zu einem bestimmten Gewerk gehört, aber in einer ANDEREN Gewerk-Kampagne auftaucht, soll er in der falschen Kampagne als Negativ hinzugefügt werden (Kampagnen-Ebene, nicht Shared List).

### Relevanzmatrix Gewerke (Synonyme & verwandte Begriffe)

| Kampagne | Relevante Begriffe (Synonyme) |
|---|---|
| Elektroinstallateur | elektriker, elektroinstallateur, elektromonteur, stromer, elektrofachmann, elektrik |
| Sanitärinstallateur | sanitär, sanitärinstallateur, sanitärmonteur, klempner, rohrleger |
| Heizungsinstallateur | heizung, heizungsinstallateur, heizungsmonteur, heizungsbauer, heizungstechniker |
| Montage-Elektriker | montage-elektriker, montageelektriker, elektromonteur montage, installationselektriker |
| Dachdecker | dachdecker, dach, steildach, flachdach, bedachung, spengler (Overlap!) |
| Zimmermann | zimmermann, zimmerer, holzbau, holzarbeiter |
| Montage-Schreiner | montage-schreiner, montageschreiner, schreiner, innenausbau, bankschreiner, möbelschreiner |
| Bauarbeiter | bauarbeiter, bau, bauhilfsarbeiter, bauhelfer, baufacharbeiter, maurer |
| Baumaschinenführer | baumaschinenführer, baumaschinenfuehrer, bagger, baggerfahrer, maschinenführer |
| Kranführer | kranführer, kranfuehrer, baukranführer, kranmonteur, turmdrehkran, mobilkran |
| Strassenbauer | strassenbauer, strassenbau, asphaltbauer, tiefbau strasse |
| Metallbauer | metallbauer, schlosser, metallarbeiter |
| Metallbaukonstrukteur | metallbaukonstrukteur, metallbau, konstrukteur, cad metall |
| Schweisser | schweisser, schweißer, welder, schweißfachmann, wig, mag, mig |
| Automatiker | automatiker, automatisierungstechniker, automation, steuerungstechniker |
| Polymechaniker | polymechaniker, cnc, fräser, dreher, mechaniker |
| Produktionsmechaniker | produktionsmechaniker, produktionsmitarbeiter, produktion |
| Gipser | gipser, verputzer, stuckateur, trockenbauer (Overlap!) |
| Maler | maler, anstreicher, lackierer, maler und lackierer |
| Abdichter | abdichter, abdichtung, bauwerksabdichtung, flachdachabdichter |
| Gerüstbauer | gerüstbauer, gerüstmonteur, gerüst |
| Grundbauer | grundbauer, spezialtiefbau, tiefbau, bohrpfahlbauer |
| Gärtner | gärtner, landschaftsgärtner, gartenbauer, gartenpflege |
| Brand | kollabo, kolabo, collabo, kallabo, kollbo |
| Compeditor | alle Competitor-Brand-Terms (siehe NKW_Compeditor-Liste); Sonderlogik: hier sind Competitor-Terms NICHT negativ, sondern RELEVANT |
| DYN Catchall | alle restlichen relevanten Job-Suchanfragen im Baugewerbe, die zu keinem spezifischen Gewerk passen |

### Overlap-Warnung
Folgende Gewerke haben Begriffsüberschneidungen die besondere Aufmerksamkeit brauchen:
- **Dachdecker ↔ Spengler**: "spengler" kann beides meinen (Spengler hat keine eigene Kampagne → Routing zu Dachdecker)
- **Gipser ↔ Trockenbauer**: "trockenbau", "rigips", "gipskarton" (Trockenbauer hat keine eigene Kampagne → Routing zu Gipser)
- **Zimmermann ↔ Montage-Schreiner**: "schreiner" kann beides meinen. Bei reiner Holz-/Dachstuhl-Arbeit → Zimmermann; bei Innenausbau/Möbel → Montage-Schreiner
- **Metallbauer ↔ Schweisser**: "schweisser" früher Synonym von Metallbauer, jetzt eigene Kampagne → "schweisser" ausschliesslich Schweisser-Kampagne
- **Baumaschinenführer ↔ Kranführer**: "kranführer" früher Synonym von Baumaschinenführer, jetzt eigene Kampagne → "kranführer" ausschliesslich Kranführer-Kampagne
- **Elektroinstallateur ↔ Montage-Elektriker ↔ Automatiker**: drei elektrotechnische Gewerke. "elektriker" generisch → Elektroinstallateur. "montage" / "installation" → Montage-Elektriker. "automation" / "steuerung" → Automatiker.
- **Sanitärinstallateur ↔ Heizungsinstallateur**: "heizung sanitär" / "HLKS" → bessere CPA-Kampagne; allein "heizung" → Heizungsinstallateur, allein "sanitär" → Sanitärinstallateur.

Bei Overlaps: CPA pro Kampagne vergleichen und in der besseren Kampagne belassen. In der anderen Kampagne als Exact-Match-Negativ auf Kampagnen-Ebene hinzufügen (NICHT in Shared List).

---

## Schwellenwerte für Kollabo

Da das Budget relativ klein ist (7.000 CHF/Monat), gelten angepasste Schwellenwerte:

| Metrik | Schwellenwert | Aktion |
|---|---|---|
| Spend ohne Conversion | > 30 CHF | Als WASTED flaggen |
| CPA vs. Account-Durchschnitt | > 2x | Als INEFFICIENT flaggen |
| Min. Klicks für Entscheidung | 20+ | Unter 20 Klicks = MONITOR |
| Min. Datenzeitraum | 30 Tage | Keine Entscheidung unter 30 Tagen |
| Irrelevanz-Spend | > 5 CHF | Sofort als Negativ vorschlagen |

---

## Sprachregeln

- **Primärsprache:** Deutsch (Schweizer Hochdeutsch)
- **Akzeptiert:** Deutschschweizer Dialektbegriffe ("Büez", "Stifti" etc.) wenn Job-relevant
- **Negativ:** Italienische, französische, englische Suchbegriffe → NKL_Generisch
- **Ausnahme:** UMLAND TEST Kampagne darf auch DE-Begriffe enthalten
