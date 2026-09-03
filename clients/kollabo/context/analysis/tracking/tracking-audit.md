# Tracking Audit — Kollabo

**Datum:** 2026-08-10 · **Modus:** full · **Account:** 1487707588 (Kollabo) · **Währung:** CHF
**Vertical:** Lead Gen (zweiseitiger Marktplatz, Bewerber-Akquise)
**Datenfenster:** Conversion-Inventar lifetime · Daily 2026-07-27 – 2026-08-09

---

## Executive read

Der Score von 48 % liest sich schlimmer als die Lage ist, und diese Diskrepanz ist selbst der wichtigste Befund. Das Konto trennt sauber zwischen einem aufgeräumten Live-Gebotspfad und einer chaotischen Konfigurationsschicht darunter. Alle 30 aktiven Kampagnen nutzen kampagnenspezifische Zielvorhaben, und in allen 30 ist genau eine Kategorie gebotswirksam: QUALIFIED_LEAD, bedient von `SF: Qualified (2)`. Der Steuerungs-KPI aus der business.md wird also konsistent und ohne Verwässerung angewendet. Das ist besser, als die Aktenlage vermuten ließ — und es korrigiert eine Annahme aus der business.md, die ich mit diesem Audit widerlegen konnte: die vier Perspective-Aktionen mit null Volumen sind zwar primär, ihre Kategorien (DEFAULT, PAGE_VIEW) sind aber nur in drei beendeten Experiment-Armen gebotswirksam. Sie verwässern nichts, was heute läuft.

Was wirklich zählt, ist Prio eins: `SF: New Lead (1)` steht auf `include_in_conversions_metric = false` und liefert seit dem 1. Juli null. Damit ist per Konfiguration bestätigt, was vorher nur Inferenz war — der Volumeneinbruch von ~476 auf ~176 Conversions pro Monat ist kein Performance-Verlust, sondern eine Kombination aus totem Import und bewusster Herausnahme aus der Conversions-Metrik. Prio zwei: das Klick-Lookback der drei Salesforce-Aktionen steht auf 90 Tagen, obwohl 98,5 % aller Conversions innerhalb von 30 Tagen eintreffen und 86,5 % noch am selben Tag. Ein 90-Tage-Fenster schreibt uralten Klicks Verdienst zu und macht jeden Zeitraumvergleich unschärfer. Prio drei: Consent Mode v2 ist technisch vorhanden, aber nicht verdrahtet — jeder Tag-Request geht mit `npa=1` raus, also nicht personalisiert. Für die UMLAND-Kampagne, die auf deutsche Grenzregionen zielt, ist das EEA-Gebiet und damit relevant.

Kein Problem sind: Tag-Installation (GTM, GA4, Google Ads alle sauber geladen), Conversion Linker (gclid wird korrekt in `gclaw` übernommen), Attributionsmodell (datengetrieben auf allen Primäraktionen) und der Status aller Aktionen. Volumen-Anomalie: keine, −3,9 % Woche über Woche.

Zu lesen ist der Score als Konfigurations-Hygiene, nicht als operatives Risiko. Die Punktabzüge kommen aus 8 toten Staging-Aktionen, falschen Zielkategorien und Zählmethoden auf Aktionen, die überwiegend inert sind. Keine frischen Peer-Reports vorhanden — dies ist der erste Audit-Lauf für diesen Client. Kein Score-Trend verfügbar.

---

## Score

| | Punkte | Prozent | Bewertung |
|---|---|---|---|
| **Gesamt** | **62,5 / 130** | **48 %** | **Critical** (Konfiguration) |
| Completeness (D01–D07) | 27,5 / 80 | 34 % | Critical |
| Tag Health (D08–D17) | 35 / 50 | 70 % | Good |

> 30 Punkte (D13–D17) sind SKIP und aus dem Nenner genommen.

---

## Kritische Befunde

### 1. `SF: New Lead (1)` — tot und aus der Conversions-Metrik entfernt
`include_in_conversions_metric = false`, `primary_for_goal = false`, **0 Conversions seit 01.07.2026**
(lifetime 12.653 — war die volumenstärkste Aktion des Kontos).

Monatsverlauf: Apr 388 · Mai 287 · Jun 179 · **Jul 0 · Aug 0**.

Damit ist der Einbruch der Zielvorhaben-Conversions von ~476 (April) auf ~176 (Juli) vollständig
erklärt: kein Performance-Verlust, sondern toter Import **plus** Herausnahme aus der Metrik.
Gleichzeitig stieg `SF: Qualified (2)` von 67 (Mai) auf 175 (Juli) bei konstantem
Bewerbungsaufkommen — der Verdacht, dass New-Lead-Datensätze jetzt als Qualified importiert
werden, bleibt offen und ist der kritischste Punkt für die Verlässlichkeit des Steuerungs-KPI.

**Aktion:** Salesforce-Import-Mapping prüfen. Ist New Lead absichtlich abgeschaltet oder defekt?
Wenn absichtlich — warum steigt Qualified gegenläufig?

### 2. Klick-Lookback 90 Tage vs. tatsächliche Conversion-Verzögerung
Alle drei Salesforce-Aktionen: `click_through_lookback_window_days = 90`.

Gemessene Verzögerung (01.05.–09.08.): **86,5 % < 1 Tag · 93,4 % ≤ 7 T · 95,9 % ≤ 14 T · 98,5 % ≤ 30 T.**

Ein 90-Tage-Fenster erfasst also 1,5 % zusätzliche Conversions, verteilt aber Attributions-Credit
über ein Vierteljahr. Jeder Zeitraumvergleich wird dadurch unschärfer, und Änderungen wirken
verzögert sichtbar. **Empfehlung: auf 30 Tage.**
*Hinweis: die Historie dokumentiert einen Wechsel 30 → 60 Tage am 30.10.2025. Heute stehen 90 —
also wurde seither erneut geändert, ohne Dokumentation. Als Messbruch behandeln.*

### 3. Consent Mode v2 vorhanden, aber nicht verdrahtet
Live geprüft auf `kollabo.com/de-ch/jetzt-bewerben/`:

- `google_tag_data.ics` existiert mit allen vier Signalen (ad_storage, analytics_storage,
  ad_user_data, ad_personalization) — die API ist da
- **aber:** `usedUpdate = false`, keine `default`- und keine `update`-Werte gesetzt
- **jeder Tag-Request geht mit `npa=1` raus** (nicht-personalisierte Anzeigen)
- Cookie-Banner im DOM vorhanden, **kein bekanntes CMP-Objekt** (kein Cookiebot, OneTrust,
  Usercentrics, Complianz, kein TCF `__tcfapi`)

Folge: Remarketing- und Audience-Signale werden unterdrückt. Für UMLAND (deutsche
Grenzregionen = EEA) ist das der Bereich, in dem Consent Mode v2 seit März 2024 Voraussetzung
für Audience-Features ist.

### 4. Zählmethode falsch auf Lead-Formular-Aktionen (D06 FAIL)
| Aktion | Ist | Soll |
|---|---|---|
| 4× `Perspective … generate_lead_*` | MANY_PER_CLICK | ONE_PER_CLICK |
| `SF - Closed Won (Final)` | MANY_PER_CLICK | ONE_PER_CLICK* |
| `Anrufe über Anzeigen` | MANY_PER_CLICK | ONE_PER_CLICK |

*Bei Closed Won ist MANY_PER_CLICK **möglicherweise beabsichtigt** — ein Temporär-Kandidat kann
mehrfach vermittelt werden. Das ist die einzige Zählmethode im Konto, die eine plausible
Geschäftslogik hat. **Vor Änderung mit Kollabo klären.** Betroffen ist nur `DYN Catchall`
(die einzige Live-Kampagne, in der CONVERTED_LEAD gebotswirksam ist).

### 5. Zielkategorien semantisch falsch (D05 FAIL)
| Aktion | Kategorie ist | sollte sein |
|---|---|---|
| `Perscpective - Sanitär (web) generate_lead_sanitär` | **PAGE_VIEW** | SUBMIT_LEAD_FORM |
| `Perspective - Allgemein (web) generate_lead_allg` | **DEFAULT** | SUBMIT_LEAD_FORM |
| `Perspective - Elektro (web) generate_lead_elektro` | **DEFAULT** | SUBMIT_LEAD_FORM |
| `Perspective - Montage-Schreiner (web) generate_lead_montage` | **DEFAULT** | SUBMIT_LEAD_FORM |

Alle vier sind primär **und** in `include_in_conversions_metric`. Ihre Kategorien sind aber nur
in 3 beendeten Experiment-Armen gebotswirksam → **kein Einfluss auf laufende Kampagnen.**
Zusätzlich: Tippfehler „Perscpective".

### 6. Primäraktionen ohne Volumen (D09 FAIL)
Zero in beiden 7-Tage-Fenstern: `Perspective - Allgemein` (**lifetime 0 — nie ausgelöst**),
`Perspective - Elektro` (**lifetime 0**), `Folgeaufrufe auf YouTube` (**lifetime 0**),
`Perscpective - Sanitär` (lifetime 2), `Perspective - Montage-Schreiner` (lifetime 1),
4× GOOGLE_HOSTED „Lokale Aktionen" / Click-to-Call.

---

## Der Live-Gebotspfad — was tatsächlich Gebote steuert

Dies ist der wichtigste Abschnitt und der Grund, warum der Score die Lage überzeichnet.

| Ebene | Befund |
|---|---|
| Zielvorhaben-Konfiguration | **34 von 37 aktiven Kampagnen auf `goal_config_level = CAMPAIGN`** (kampagnenspezifisch). Die 3 auf Kontostandard sind beendete Experiment-Arme aus 2019. |
| Gebotswirksam in allen 30 Live-Kampagnen | **QUALIFIED_LEAD (WEBSITE)** → `SF: Qualified (2)` |
| Zusätzlich gebotswirksam in 1 Live-Kampagne | **CONVERTED_LEAD** → `SF - Closed Won (Final)`, nur in `DYN Catchall` |
| Inert (Kategorie nicht biddable in Live-Kampagnen) | DEFAULT, PAGE_VIEW, SUBMIT_LEAD_FORM, CONTACT, PHONE_CALL_LEAD, PURCHASE, DOWNLOAD, BEGIN_CHECKOUT, ENGAGEMENT, GET_DIRECTIONS, YOUTUBE_FOLLOW_ON_VIEWS |

**Konsequenz:** Der Steuerungs-KPI ist sauber implementiert. `thank_you_page_view` ist korrekt
sekundär und aus der Conversions-Metrik ausgeschlossen — genau wie in business.md §2.1 gewollt.

**Einzige Inkonsistenz:** `DYN Catchall` bietet als einzige Live-Kampagne zusätzlich auf Closed
Won. Entweder für alle vereinheitlichen oder bewusst dokumentieren.

---

## Ergebnisse — Completeness (D01–D07)

| ID | Diagnostik | Status | Punkte | Befund |
|---|---|---|---|---|
| D01 | Conversion-Abdeckung | WARN | 7,5/15 | Alle Geschäfts-Events vorhanden und feuernd (Bewerbung 7.699 · Qualified 4.448 · Closed Won 699 lifetime). Aber 8 Staging-Aktionen mit 0 und 1 Makro (`New Lead`) seit Juli flatline. |
| D02 | Primär/Sekundär | WARN | 7,5/15 | 11 Primäraktionen, davon nur 2 mit Substanz. Vanity-Primäre (YOUTUBE_FOLLOW_ON_VIEWS, PAGE_VIEW) vorhanden, aber in Live-Kampagnen inert. `thank_you_page_view` sekundär = bewusste Entscheidung, kein Fehler. |
| D03 | Duplikate | WARN | 5/10 | SUBMIT_LEAD_FORM 3× (1 LIVE + 2 Staging), CONTACT 4×, PHONE_CALL_LEAD 3×. Keine zwei Primäraktionen für dasselbe Event in Live-Kampagnen. New Lead vs. Qualified = verschiedene Funnel-Stufen, kein Duplikat. |
| D04 | Namenskonsistenz | WARN | 2,5/5 | Keine Platzhalter-Namen. Aber: Tippfehler „Perscpective", gemischt DE/EN, auto-generierte GA4-Namen. Staging/LIVE ist immerhin explizit benannt. |
| D05 | Zielkategorie | **FAIL** | 0/10 | 4 Lead-Aktionen als PAGE_VIEW / DEFAULT kategorisiert (siehe Befund 5). |
| D06 | Zählmethode | **FAIL** | 0/15 | 4 Lead-Formular-Aktionen + 1 Call-Aktion auf MANY_PER_CLICK (siehe Befund 4). |
| D07 | Konto-Standardziele | WARN | 5/10 | Kontostandard ist unsauber (11 Primäre inkl. Vanity), wird aber durch kampagnenspezifische Ziele in 34/37 Kampagnen neutralisiert. Genau der dokumentierte WARN-Fall. |

---

## Ergebnisse — Tag Health (D08–D17)

| ID | Diagnostik | Status | Punkte | Befund |
|---|---|---|---|---|
| D08 | Aktionsstatus | PASS | 15/15 | Alle 23 Aktionen ENABLED, alle Primäraktionen ENABLED. |
| D09 | Volumen Zero-Check | **FAIL** | 0/15 | 7+ Primäraktionen mit 0 in beiden 7-Tage-Fenstern, davon 3 mit lifetime 0 (nie ausgelöst). |
| D10 | Volumen-Anomalie | PASS | 10/10 | `SF: Qualified` 28,98 → 27,85 (−3,9 %). Keine Anomalie. 08.–09.08. ohne Daten = erwarteter Offline-Import-Lag (Lauf täglich 03–04 Uhr), nicht als Ausfall gewertet. |
| D11 | Google-Tag-Präsenz | PASS | 5/5 | GTM-5WM63B5 · GA4 G-4V0XDR0GY9 · Google Ads AW-794335319 · `gtag` als Funktion vorhanden. |
| D12 | Conversion Linker | PASS | 5/5 | Test-gclid wurde korrekt als `gclaw=` in `/ccm/collect` übernommen. `_gcl_au` gesetzt. |
| D13 | Tag-Firing-Verifikation | SKIP | — | Erfordert Test-Conversion → würde einen echten Lead in Kollabos Salesforce erzeugen. Nicht ohne Freigabe. |
| D14 | Transaction-ID | SKIP | — | wie D13 |
| D15 | Dynamischer Wert | SKIP | — | wie D13. Hinweis: alle Aktionen haben `default_value = 0` bzw. `1` — es wird **kein Conversion-Wert** übergeben. Hängt an [GAP-1] Erlös pro Vermittlung. |
| D16 | Währung | SKIP | — | API-seitig: 22 Aktionen CHF, **`Anrufe über Anzeigen` steht auf `XXX`** (undefinierte Währung). Sekundär und inert, daher kein Scoring-Abzug. |
| D17 | Backend-Abgleich | SKIP | — | Immer manuell. → Import-Volumen wöchentlich gegen Salesforce prüfen. |

---

## Attribution (Beobachtungen, nicht gescored)

| Aktion | Modell | Klick-Fenster | View-Fenster | in Conversions-Metrik |
|---|---|---|---|---|
| `SF: Qualified (2)` | Data-Driven | **90 T** | 1 T | ✅ |
| `SF - Closed Won (Final)` | Data-Driven | **90 T** | 1 T | ✅ |
| `SF: New Lead (1)` | Data-Driven | 90 T | 1 T | ❌ |
| `thank_you_page_view` (LIVE) | UNKNOWN (GA4) | 90 T | 1 T | ❌ |
| 4× `Perspective generate_lead_*` | Data-Driven | 90 T | 1 T | ✅ |

Datengetriebene Attribution auf allen Primäraktionen ist korrekt. Das 90-Tage-Klickfenster ist
der einzige Problempunkt (Befund 2).

---

## Empfehlungen — priorisiert

| # | Aktion | Wer | Aufwand |
|---|---|---|---|
| 1 | **Salesforce-Import prüfen:** Warum liefert `New Lead` seit 01.07. null, während `Qualified` gegenläufig steigt? Mapping-Fehler ausschließen. | Kollabo / SF-Admin | — |
| 2 | **Klick-Lookback 90 → 30 Tage** auf den drei SF-Aktionen. Erfasst 98,5 % und schärft jeden Zeitraumvergleich. Als Messbruch dokumentieren. | Google Ads UI | 5 Min |
| 3 | **Consent Mode v2 verdrahten.** CMP mit `gtag('consent','default'/'update')` verbinden. Relevant für UMLAND/EEA. | Web-Dev | — |
| 4 | **Zählmethode** der 4 Perspective-Aktionen auf ONE_PER_CLICK. Closed Won **vorher mit Kollabo klären** (Mehrfachvermittlung plausibel). | Google Ads UI | 10 Min |
| 5 | **Zielkategorien** der 4 Perspective-Aktionen auf SUBMIT_LEAD_FORM. Tippfehler „Perscpective" korrigieren. | Google Ads UI | 10 Min |
| 6 | **8 Staging-GA4-Aktionen archivieren** — alle 0 Conversions, reine Verwirrung. | Google Ads UI | 10 Min |
| 7 | **`DYN Catchall` vereinheitlichen** oder dokumentieren — einzige Live-Kampagne, die zusätzlich auf Closed Won bietet. | Google Ads UI | 5 Min |
| 8 | **Wöchentlicher Import-Check** als feste Routine (Guardrail aus business.md §3.3). | Martin | laufend |

### Routing zu Peer-Skills
Keine frischen Peer-Reports vorhanden — erster Audit-Lauf für diesen Client. Sobald verfügbar,
gegenprüfen. Wichtig für nachfolgende Audits:

> **Alle conv-abhängigen Bewertungen der übrigen Audits stehen unter Vorbehalt**, solange
> Befund 1 offen ist. Der Gebotspfad selbst ist sauber (nur QUALIFIED_LEAD), aber ob die
> gelieferten Qualified-Datensätze wirklich qualifiziert sind, ist ungeklärt.

---

## Manuelle Prüfungen erforderlich

- **D17 Backend-Abgleich:** Salesforce-Conversion-Zahlen gegen Google Ads abgleichen
- **Auto-Apply-Status** — nicht über API auslesbar, seit 30.06.2026 unbestätigt
- **Import-Autorisierung:** letzte dokumentierte Autorisierung der SF-Datenquelle war 05.09.2024
- **HTTP-503 auf allen Google-Endpunkten** während des Live-Checks — mit hoher Wahrscheinlichkeit
  lokale Browser-Umgebung (Extension/Proxy), **nicht** als Defekt gewertet. In sauberer Umgebung
  gegenprüfen.

## Datenfrische

| Quelle | Stand |
|---|---|
| `conversions-audit.csv` (23 Aktionen) | 2026-08-10 |
| `conversions-daily.csv` (14 T) | 2026-07-27 – 2026-08-09 |
| `conversion-goal-config.csv` (319) · `campaign-goals.csv` (5.423) | 2026-08-10 |
| `conversions-attribution.csv` (23) | 2026-08-10 |
| `custom-conversion-goals.csv` | 0 Zeilen — keine benannten Custom Goals |
| Live-Seiten-Check | 2026-08-10, `kollabo.com/de-ch/jetzt-bewerben/` |
| `context/account-changelog.md` | **fehlt** — Änderungskontext nicht verfügbar |
