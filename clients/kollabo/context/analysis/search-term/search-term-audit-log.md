# Search Term Audit Log

## 2026-08-10 — Score: 76% (Good)
- Period: 60d main / 120d n-gram | Lag: 14d | 26.797 ST-Zeilen | Experimente ausgeschlossen
- Top hypothesis: Struktur — konvertierende Nachfrage wird zufaellig eingesammelt statt bedient
- Module: Quality 19/25 | Coverage 18,56/25 | N-gram 13/15 | Variants 15/15 | Promotion 1,8/9
- TOP FINDING: 36 temporaer*-Suchbegriffe liefern 38,3 Conv fuer 108,31 CHF = CPA 2,83.
  Kein Keyword, keine Kampagne. Verteilt auf 9+ Gewerke-Kampagnen per Broad-Zufall.
- Abdeckungsquote 3,8% — nur 7 von 185 konvertierenden Begriffen sind Keyword. 164 Kandidaten.
- WIDERSPRUCH offengelegt: search-terms-rules.md sagt "fremdsprachig -> NKL_Generisch",
  business.md nennt Zuwanderer als Kern-Zielgruppe, trabalhar na suica konvertiert bei CPA 5,47.
- FALSCHALARM neutralisiert: 265 Kampagnen ohne Negative gemeldet — 0 davon aktiv.
- ST-D10 FAIL: 42 Negative individuell in 3-12 Kampagnen statt Shared List.
- Fresh peers integrated: /keyword-auditor, /tracking-specialist, /strategy-specialist (alle heute)

## 2026-08-18 — Score: 81% (Good)
- Period: 90d main / 120d n-gram | Lag: 14d | 36.902 ST-Zeilen | Experimente ausgeschlossen
- Top hypothesis: Business — 155/155 Flags auf target_source=fallback (30/30 Kampagnen ohne Zielvorgabe)
- Module: Quality 21/25 | Coverage 20,71/25 | N-gram 16/20 | Variants SKIP | Promotion 3,6/6
- KERNBEFUND: KEINE tragfaehige Negation im Konto. Kein einziger der 155 nicht-konvertierenden
  Terms erreicht 20 Klicks (Max 18) = Kollabos eigene Mindestentscheidungsbasis.
- FREMDSPRACHIG BESTAETIGT PROFITABEL: 1.195,30 CHF / 44,20 Conv / CPA 27,04 (ES 27,73 IT 20,57
  PT 24,66) vs Nicht-Brand-Schnitt 31,99. N-Gram-Motor hatte genau diese Terms zur Negation
  vorgeschlagen. Widerspruch aus dem 10.08.-Lauf endgueltig zugunsten der Daten aufgeloest:
  search-terms-rules.md ("fremdsprachig -> NKL_Generisch") ist VERALTET.
- CHANCE (90d bestaetigt + vergroessert): temporaer* 1.879,35 CHF / 65,87 Conv / CPA 28,53 ueber
  28 Kampagnen. Sub-Cluster temporaerbuero* 1.020,30 CHF / 46,19 Conv / CPA 22,09 ueber 26 Kampagnen.
  Alle 16 vorhandenen temporaer-Keywords sind gewerkegebunden - kein generisches KW existiert.
- ST-D21: 9 generische Ortsbegriffe kampagnenuebergreifend, temporaerbuero waedenswil in 5 Kampagnen.
- FALSCHALARM erneut neutralisiert: 265 Kampagnen ohne Negative gemeldet - alle 265 PAUSED, 0 aktiv.
- SCRIPT-DEFEKT dokumentiert: N-Gram-Engine rechnet mit 0,01 statt 0 Conversions -> CPA-Artefakte
  bis 14.443 CHF. D13 fiel dadurch faelschlich auf 0, D14 auf 18. Alle Modul-3-Zahlen nachgerechnet.
- MODUL 4 auf SKIP gesetzt: match_types ist auf allen 423 Datensaetzen leer. Der 10.08.-Lauf
  wertete es mit 15/15 ohne Datengrundlage. Bei alter Methodik waere dieser Lauf 84%.
- REVISION ST-D10: 39 von 42 doppelten Negativen tragen likely_routing=true mit Beleg = gewollte
  Steuerung. Am 10.08. als FAIL gewertet, hier WARN.
- Portfolio-Fehldeutung vermieden: 34 "portfolio-resolved" Kampagnen sind saemtlich PAUSED,
  0 von 30 aktiven nutzt Portfolio-Bidding.
- ZIELWERT-KONFLIKT: config targetCPA 50 (30d-Fenster) vs 90d-CPA 27,25 (competitive) / 28,18.
- Fresh peers integriert: /tracking-specialist (10.08. 48%), /strategy-specialist (10.08. 55%),
  /lp-auditor (11.08. 60%), /offer-auditor (11.08. 78%), /competitive-analyst (11.08. 41%),
  /account-auditor (10.08.). Stale (>7T): quality-score, keyword, bidding, budget.
