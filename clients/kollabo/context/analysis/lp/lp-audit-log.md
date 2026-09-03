# LP Audit Log

## 2026-08-11 — Structural (LP-D01-D12) — Score: 58% (Needs Attention)
- URL: https://kollabo.com/de-ch/jobs/gipser-jobs/ (Vertreter der Vorlage /de-ch/jobs/{gewerk}-jobs/)
- FAIL: LP-D07 Social Proof ("Facebook Rating 0" sichtbar + abgebrochener Satz),
  LP-D09 Garantie fehlt, LP-D11 Ein-Ziel-Regel (114 Links, volle Navigation, 41 Footer-Links)
- WARN: LP-D01 (4/5, Risikoumkehr fehlt), LP-D02 Hero verkauft Gewerk statt Angebot,
  LP-D04 "Absenden" generisch, LP-D12 5 Abschnitte
- PASS: LP-D03 CTA ueber Falz, LP-D05 Nutzen, LP-D06 Vertrauen, LP-D08 Einwandbehandlung (4/4),
  LP-D10 CTA-Wiederholung
- STAERKEN: 68 echte gewerkespezifische Stellenanzeigen, konsequente Duz-Form, USP gut getextet,
  1.306 Woerter gewerkespezifischer Inhalt. Der INHALT ist nicht das Problem.
- KORREKTUR eines Zwischenbefunds: "70 leere Ueberschriften" war ein Extraktionsfehler meinerseits
  (innerText leer bei verschachtelten Ankern), kein Seitenfehler. Widerlegt und zurueckgezogen.
- Offene Frage an technical/performance: wenn der Inhalt gut ist, woher kommen die 76,9%
  unterdurchschnittliche LP-Erfahrung aus dem QS-Audit?
- Fresh peers integrated: /quality-score-auditor, /geo-schedule-auditor, /competitive-analyst,
  /keyword-auditor

## 2026-08-11 - Message Match (LP-D13-D16) - Score: 52% (Needs Attention)
- Datenbasis: 60 Live-RSAs, 29 Final URLs (alle extrahiert), 298 Keywords
- WARN: LP-D13, LP-D14, LP-D15 | SKIP: LP-D16 (keine Display-/Video-Kampagnen)
- TOP-BEFUND: 6 H1 tragen einen Trennstrich mitten im Gewerkenamen (Elektro-installateur,
  Heizungs-installateur, Sanitaer-installateur, Produktions-mechaniker, Metallbau-konstrukteur,
  Montage-elektriker). Der Keyword-String steht damit nicht mehr wortwoertlich in der H1.
  VIER der sechs Seiten gehoeren zu den teuersten Kampagnen: Montage-Elektriker CPA 231,81,
  Produktionsmechaniker 146,90, Heizungsinstallateur 80,44, Sanitaerinstallateur 68,61.
  Korrelation, kein Beweis - aber Minuten-Fix und in 14 Tagen messbar.
- ZWEITER BEFUND: kollabo.com/de-ch/ hat gar KEINE H1. Zielseite von UMLAND
  (STAN | HOME | BROAD) - effizienteste Kampagne des Kontos (CPA 15,33/90T), 72,7% Rangverlust.
- Anzeige verspricht Tempo, H1 nennt nur das Gewerk. Versprechen erst bei 832px eingeloest.
- Nebenbefunde: Tippfehler "Zuruecksetzten", CTA-Sprache in 5 Varianten, "Waehlen Sie Dateien aus"
  bricht die verbindliche Duz-Form.

## 2026-08-11 - Technical (LP-D17-D24) - Score: 82% (Good)
- Messbedingungen: Mobile 390x844, Slow 4G, 4x CPU-Drosselung
- PASS: LP-D17 Ladezeit (LCP 1.571ms), LP-D18 Core Web Vitals (CLS 0,00), LP-D23 SSL
- WARN: LP-D19 (user-scalable=0, 24 Tap-Ziele <44px), LP-D20 (Mobile-CVR 50,9% der Desktop-CVR),
  LP-D21 (10 sichtbare Formularfelder ueber 3 Formulare), LP-D24 (0 von 86 Bildern lazy)
- SKIP: LP-D22 Formular-Test (wuerde echten Lead erzeugen)
- DIE LADEZEIT IST NICHT DAS PROBLEM. Dritter Erwartungsbruch in Folge.
- Lighthouse mobile: SEO 92, Accessibility 71, Best Practices 58, Agentic 67. 14 Fehlschlaege:
  13 Kontrastverstoesse, 68 Listenelemente nicht in ul/ol, 2 Formularfelder ohne Label,
  3 Links ohne Namen, user-scalable=no.
- 173 Netzwerkanfragen: ~20 Schriftdateien (mehrere doppelt als .otf/.ttf UND woff2),
  ~30 CSS, ~50 JS, volles Google-Maps-SDK, WordPress-Emoji-Skript.
- GAP-9 (Cross-Channel) GESCHLOSSEN: Bing Ads UET (bat.bing.com), Jooble (Jobboersen-
  Aggregator), ActiveCampaign (prism.app-us1.com, trackcmp.net) nachgewiesen.

## 2026-08-11 - Performance (LP-D25-D31) - Score: 27% (Critical)
- Datenbasis: 28 Zielseiten, Ad-Group-Ebene auf Final URLs aggregiert
- Konto-Referenz: Spend 7.576,08 | Conv 144,12 | CPA 52,57 | CVR 2,53%
- FAIL: LP-D25 (7 Seiten unter 50% der Konto-CVR), LP-D29 (8 Seiten ueber 150% Konto-CPA)
- PASS: LP-D30 (Mobile CPA 143,4% von Desktop, knapp unter Schwelle)
- WARN: LP-D31 (UMLAND auf Startseite ohne H1)
- SKIP: LP-D26/D27/D28 (erfordern GA4)
- KORREKTUR AN MODUL 2: Die Trennstrich-Hypothese haelt der Pruefung NICHT stand.
  Mit Trennstrich: 6 Seiten, CVR 2,29%. Ohne: 17 Seiten, CVR 2,96%. Getragen von zwei
  Ausreissern. elektroinstallateur MIT Trennstrich ist die viertbeste Seite (CVR 4,78%),
  gaertner OHNE Trennstrich die schlechteste (0,60%). Sechs Datenpunkte tragen die Aussage nicht.
- HAUPTBEFUND: 12,4x CVR-Spanne bei IDENTISCHER Vorlage (maurer 7,46% bis gaertner 0,60%).
  Waere die Vorlage die Ursache, muessten alle Seiten aehnlich schlecht konvertieren.
  -> Der Rangverlust ist ein LP-Problem (Navigation/Barrierefreiheit -> QS -> Ad Rank).
     Die CVR-Unterschiede sind ein Markt-/Angebotsproblem. Beides gleichzeitig wahr.
- 4 Seiten mit NULL Conversions: abdichter (114 Klicks), montage-schreiner (81),
  kranfuehrer (77), geruestbauer (40).

## 2026-08-11 - URL Health (LP-D32-D37) - Score: 88% (Good)
- 109 URLs geprueft (Anzeigen + Keywords + Assets)
- PASS: LP-D32 (0 von 109 auf AKTIVEN Ketten defekt), LP-D33 (1 Weiterleitung, Schraegstrich),
  LP-D35 (Keyword-URLs sauber)
- WARN: LP-D37 (Final-URL-Expansion auf UMLAND aktiv, Qualitaet nicht verifizierbar)
- SKIP: LP-D34 (DSA-Ziele nicht im Pull), LP-D36 (assets.csv fuehrt nur Bild-URLs, keine
  Sitelink-Ziel-URLs -> gads-context assets.gaql erweitern)
- ZWEITER FEHLALARM ENTKRAEFTET: 29 kaputte URLs klingt nach Notfall, ist keiner -
  ALLE 29 liegen auf pausierten Kampagnen, null auf aktiven Ketten.
- NEUER KONTEXT: 22 der 29 toten URLs sind /de-de/-Seiten - Beleg fuer einen vollstaendigen,
  wieder eingestellten Markteintritt in Deutschland (de-tischler-sea, de-stuckateur-sea,
  DE_GSN_DE_Brand, DE_GSN_DE_Meister_Stuttgart). UMLAND ist also nicht der erste DE-Versuch.
  NEUER GAP: Warum wurde der erste Anlauf beendet? Steht in keiner Quelle.

## GEWICHTETER GESAMTSCORE LP-AUDIT: 60% (Needs Attention)
- Structural 58% (35%) | Message Match 52% (20%) | Technical 82% (20%) |
  Performance 27% (15%) | URL Health 88% (10%)
- KERNAUSSAGE: Die Vorlage ist mittelmaessig, nicht kaputt. Sie kostet AD RANK (114 Ausgaenge,
  gesperrter Zoom, 13 Kontrastverstoesse) - das erklaert 37-73% Rangverlust.
  Sie erklaert NICHT die CVR-Spreizung von Faktor 12,4 zwischen den Gewerken.
  Zwei getrennte Baustellen: LP-Vorlage -> /lp-optimizer. Gewerke-Passung -> /offer-auditor.

## 2026-08-18 — Score: 55% (Needs Attention)

- **Modus:** Page Quality (Structural D01-D12 + Message Match D13-D16 + Technical D17-D24)
- **URLs:** https://kollabo.com/de-ch/jobs/ (570,52 CHF LP-Below) + https://kollabo.com/de-ch/ (362,00 CHF)
  = die 932 CHF, die /quality-score-auditor am 18.08. als teuerste UNGEPRUEFTE LP-Position fand
- **Module:** Structural 25/60 (42%) · Message Match 16/20 (80%) · Technical 16/30 (53%)
- **TOP FINDING:** USP steht auf dem Job-Hub bei Pixel 5.832 von 7.862 (74% Tiefe) — UNTERHALB des
  Formulars (5.713). Startseite: USP bei 3.632 von 5.862 (62%), Formular bei 3.513.
  Zum Vergleich 11.08. Gipser-Seite: USP bei 832 px. Hier siebenmal tiefer.
- **PRIO 2:** viewport meta = "maximum-scale=1, user-scalable=0" -> Pinch-Zoom auf Mobil komplett
  deaktiviert. SITE-WEIT. Bei 71,6% Mobile-Spend und Mobile-CVR 2,09% vs Desktop 4,11% (1,97x Luecke)
  ein konkreter Ursachenkandidat. Fix = ein Wort in der Theme-Konfiguration.
- **PRIO 3:** Startseite hat GAR KEIN h1 (h1count=0), Hero laeuft ueber h2. Lighthouse bestaetigt
  "Heading elements are not in a sequentially-descending order".
- "Facebook Rating 0" auch auf der Startseite -> der 11.08.-Befund ist SITE-WEIT, nicht
  vorlagenspezifisch. Der abgebrochene Satz dagegen ist vorlagenspezifisch (hier nicht gefunden).
- Job-Hub hat KEIN Google Rating — die teuerste Seite traegt kein einziges Bewertungssignal.
- Ausgangsdichte: Hub 129 Links (30 Nav, 48 Footer) — MEHR als die am 11.08. kritisierte
  Gipser-Seite (114). Startseite 85.
- KORREKTUR eines eigenen Zwischenbefunds: "Waehlen Sie Dateien aus" ist NICHT Kollabos Copy und
  keine Duz-Form-Verletzung — es ist die native Browser-Beschriftung fuer input[type=file].
  Das Feld hat ein eigenes korrektes Label "Bewerbungsunterlagen". Geprueft und widerlegt.
- Lighthouse mobil (Startseite): SEO 100 · Accessibility 81 · Best Practices 77 · Agentic 67.
  9 Fehlschlaege, u.a. user-scalable, Heading-Reihenfolge, Form-Label, Kontrast.
- SKIP: D17/D18 — lighthouse_audit liefert keine Performance-Metriken. CLS = 0 (sauber).
- **Routing:** /lp-optimizer elements (USP hochziehen, h1, Google Rating, Ausgangsdichte),
  /lp-optimizer mobile (Viewport-Meta). NICHT /rsa-maker — AR liegt bei 8,9%.
- **Archiviert:** der 11.08.-Report zur Gewerke-Vorlage (60%) liegt jetzt unter
  lp-audit-2026-08-11-gewerke-vorlage.md — er wird von drei Audits vom 18.08. zitiert und
  waere sonst ueberschrieben worden.
- Report: context/analysis/lp/lp-audit.md

