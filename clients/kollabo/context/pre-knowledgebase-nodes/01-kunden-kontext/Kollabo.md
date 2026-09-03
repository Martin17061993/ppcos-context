# Kollabo

## Kunden-Card

| Feld | Wert |
|---|---|
| Branche | Personalvermittlung / Stellenvermittlung Handwerker & Fachkräfte |
| Geschäftsmodell | Zweiseitiger Marktplatz (Bewerber kostenlos, Auftraggeber zahlt) |
| Customer ID | 1487707588 (148-770-7588) |
| MCC | 5591362086 (Jonas Makki) |
| Website | https://kollabo.com/ |
| Firmensitz | kollabo ag, Blegi 5, 6343 Rotkreuz (Kanton Zug) |
| Swissstaffing | Ja |
| Was beworben wird | Bewerber-Akquise (Lead-Gen) |
| Monatsbudget | 7.500 CHF |
| Tagesbudget aktuell | 249 CHF |
| Account-Ø-CPA | 14,53 CHF |

## Zielgruppe

Handwerker und Fachkräfte in der Deutschschweiz auf aktiver Jobsuche. Starker Anteil Zuwanderer/Neuankömmlinge (laut Google-Reviews).

### Abgedeckte Gewerke
Elektro, Holz (inkl. Schreiner/Bankschreiner), Gebäudehülle (Dach/Fassade/Spengler), HLKS (Heizung/Lüftung/Klima/Sanitär), Industrie (Schweisser/Produktion), Mechaniker, Innenausbau, Hoch- & Tiefbau

## USPs Kollabo

- Nur 1× bewerben — Kollabo übernimmt den Rest
- Kostenlos für Bewerber
- Persönliche Personalberater
- Matching-Technologie + menschliche Beratung
- Großes Arbeitgebernetzwerk Baubranche
- Blitzschnelle Vermittlung
- Google Rating 4.9
- Mehrsprachige Beratung (relevant für Einwanderer)

## Tonalität

Persönlich, direkt, ermutigend, niederschwellig. **Konsequente Duz-Form.** Kurze, klare Sätze. „Nur 1× bewerben", „Wir übernehmen den Rest". Sehr service- und menschenorientiert.

## Compliance

- Schweizer DSG
- Swissstaffing Code of Conduct
- Arbeitsvermittlungsgesetz AVG
- Diversity Statement (kollabo ag)

**Keine** falschen oder übertriebenen Jobversprechen. **Keine** diskriminierenden Formulierungen.

## Mitbewerber

- Allgemeine Jobportale: jobs.ch, jobup.ch, jobscout24.ch, Indeed, JobCloud
- Klassische Personalvermittler Baubereich: Adecco, Randstad, Manpower, Kelly Services
- Temporär-/Flex: Coople
- Branchenspezifische Vermittler / kleine regionale Personalbüros

## Tracking

- **Hauptkonversion:** Bewerber-Registrierung auf `kollabo.com/de-ch/jetzt-bewerben/`
- **CRM:** Bewerber-Plattform `app.kollabo.com`
- **Tools:** GTM, GA4, UTM/GCLID, Salesforce
- **Cookie-Banner:** aktiv, Opt-In für Analytics/Marketing

## Aktive Kampagnen (28 total)

**TOP-Performer:** Bauarbeiter, UMLAND TEST, Brand, DYN Catchall, Maler, Produktionsmech, Strassenbauer, Polymech
**Mittelfeld:** Elektroinstallateur, Compeditor, Schweisser, Abdichter, Gipser, Montage-Elektriker, Heizungsinst, Automatiker, Gärtner, Grundbauer
**Schwach:** Maurer, Kranführer, Sanitärinst, Metallbauer, Metallbaukonstr, Dachdecker, Baumaschin, Zimmermann, Gerüstbauer (CPA 88!)

## Pausiert für Re-Aktivierung

- Bankschreiner (Test 7-10.4., aktuell nicht im Account findbar)
- Trockenbauer (Test 14-20.4., CPA 61,86)
- Montage-Schreiner (Test 22-27.4., CPA 98,47)
- Automatikmonteur (gerade im Test, Auswertung in 3-4 Tagen)

## Konfiguration im Code-Stack

Customer-Files unter `ppc-workspace-v2/system-prompts/frameworks/customer/kollabo/`:
- `account-info.md` — Master-Kontext
- `search-terms-rules.md` — Negativ-Listen-Routing
- `ad-copy-rules.md` — RSA-Compliance
- `keyword-rules.md` — Match-Type-Switches, Pause-Schwellen

## Review-Sheets

- Search-Terms: in Shared Drive `ppc-reports/Kollabo/search-terms/`
- Ad-Copy: in Shared Drive `ppc-reports/Kollabo/ad-copy/`
- Keywords: ID `17mZOvrbheBUNsfdpmSfZicGn396GprWju6-EC97wlDs`, in `ppc-reports/Kollabo/keywords/`

## Open Items

- Bankschreiner verschollen — im Account suchen (Filter „alle Status" inkl. entfernt)
- Auto-Apply-Empfehlungen ausschalten
- Trockenbauer-Optimierung umsetzen (Match-Types verengen)
- Maler-Anzeigen-Ablehnung beheben
