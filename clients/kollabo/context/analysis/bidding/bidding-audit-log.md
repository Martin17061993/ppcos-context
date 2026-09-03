# Bidding Audit Log

## 2026-08-10 — Score: 66/100 (Needs Attention)
- Period: 30d | Campaigns: 30 (Experimente ausgeschlossen)
- Top hypothesis: Vol — Conversion-Volumen unter Smart-Bidding-Minimum durch Fragmentierung
- Active blocking: M (SF-Import, tracking-audit 2026-08-10), B (Break-even offen, strategy-audit 2026-08-10)
- Module: Target 4,8/9 | Strategy 6,0/20 | Learning 8/8 | Portfolio 5,8/7 | CPC 9,33/10 |
  ValueRules SKIP | Adjustments 5/5
- Top finding: 28 von 30 Kampagnen unter dem 15-Conv-Minimum fuer Smart Bidding (3-5 Conv/30T).
- UMLAND: PAR 0,33 und 259% Zielabweichung — bestaetigt die tCPA-Fehlableitung unabhaengig.
- 5 verwaiste Portfolio-Strategien ENABLED an 0 Kampagnen, 3 davon mit aktiven CPC-Caps.
- 0 Data Exclusions trotz dokumentiertem Tracking-Ausfall 10.05.-03.06.2026.

## 2026-08-18 — Score: 65/100 (Needs Attention)
- Period: 30d | Campaigns: 30 (Experimente ausgeschlossen) | Posture: efficiency (PAR 2,0)
- Top hypothesis: Volume — Signal-Aushungerung, 28/30 Kampagnen unter Smart-Bidding-Lernschwelle
- Active blocking: measurement (tracking 48%), business (GAP-1 offen)
- Module: TargetValidation SKIP | Strategy 5/15 | Learning 7,5/7,5 | Portfolio 4,8/6 | CPC 4,0/6,67 | ValueRules SKIP | Adjustments 5/5
- TOP FINDING: 28 von 30 Kampagnen unter 15 Conv/30T (Google-Minimum fuer Search). Median 3-4.
  Geruestbauer und Kranfuehrer bei NULL. Nur Brand (23) und UMLAND (16) ueber der Schwelle.
- KONVERGENZ MIT BUDGET-AUDIT (heute, 80%): beide Audits landen unabhaengig auf UMLAND als
  einziger begruendbarer Massnahme. UMLAND ist zugleich lernfaehig (16 Conv) UND seit 11.08.
  budget-limitiert statt rang-limitiert. Budget-Uplift trifft die einzige Stelle, die zusaetzliches
  Volumen verarbeiten kann. KEIN tCPA setzen — das war der Fehler vom 24.07.
- ERLEDIGT seit 10.08.: BID-D08 (UMLAND 259% Ziel-Abweichung) und BID-D07 (PAR 0,33) sind weg,
  weil der Ziel-CPA am 11.08. entfernt wurde. Preis: 30/30 jetzt ohne Ziel, Modul 1 komplett SKIP.
- NEU: BID-D23 8 Kampagnen mit CPC-Anstieg ueber 3 Perioden (Montage-Elektriker 1,84->2,30->2,54).
  BID-D22 2 Spitzen (Baumaschinenfuehrer +37%, Geruestbauer +32% bei 0 Conversions).
- OFFEN: 5 verwaiste Portfolios ENABLED an 0 Kampagnen, 3 davon mit aktivem CPC-Cap (latentes Risiko).
- Trend 66% (10.08.) -> 65%. Praktisch unveraendert.
- Config: biddingAudit-Block erstmals geschrieben. breakEvenCPA 75 ausdruecklich als PROXY markiert.
- Fresh peers integriert: /budget-auditor (18.08. 80%), /search-term-auditor (18.08. 81%),
  /competitive-analyst (11.08. 41%), /lp-auditor (11.08. 60%), /offer-auditor (11.08. 78%),
  /tracking-specialist (10.08. 48%), /strategy-specialist (10.08. 55%), /account-auditor (10.08.).
  Stale (>7T): /quality-score-auditor, /keyword-auditor.

