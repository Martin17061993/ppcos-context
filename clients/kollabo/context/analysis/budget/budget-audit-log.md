# Budget Audit Log

## 2026-08-10 — Score: 86/100 (Good)
- Period: 30d | Campaigns: 30 | Experimente eingeschlossen
- Top hypothesis: Bid — Signal-Unterversorgung durch Fragmentierung, nicht Budgetknappheit
- Active blocking: M (tracking-audit), B (strategy-audit) — beide 2026-08-10
- Module: Allocation 100% | Limitation 65% | Pacing 100% | Sufficiency 73% | Shared 100%
- Top finding: BUD-D02 FAIL — 19 Kampagnen mit Lost IS (Budget) >= 25%, ABER Rang dominiert
  in 29/30 (Median Rang 55,7% vs Budget 27,5%).
- BUD-D06 WARN: 20 Kampagnen erreichen an >=50% der Tage ihr Tagesbudget -> Mittagsstopp.
- BUD-D08 WARN: 30/30 unter Conversion-Floor.
- Score nach oben verzerrt: D03/D04/D13/D14/D15 haengen an Rentabilitaetsklassifikation,
  die ohne Break-even nicht berechenbar ist. Fuenf Diagnostiken nur formal gruen.
- Pacing: MTD 2361, Projektion 8133 vs Ziel 8500 (-4,3%) — auf Kurs.

## 2026-08-18 — Score: 80/100 (Good)
- Period: 30d | Campaigns: 30 | Consumers: 30 | Shared budgets: 12 | Experiments: INCLUDED
- Top hypothesis: Competitive — Rang-Limitierung durch LP-Erfahrung, nicht Budget-Knappheit
- Active blocking: measurement (tracking 48%/Completeness 34%), business (GAP-1 Erloes je Vermittlung offen), bidding (BUD-D08)
- Module: Limitation 3,75/12,5 | Sufficiency 8,25/11,25 | Pacing 11,25/11,25 | Allocation 7,5/7,5 | Shared 15/15
- TOP FINDING: Engine meldet 29 budget-limitierte Kampagnen + 16 Raise-Opportunities. Gegenrechnung
  Budget- vs Rang-Verlust: bei 29 von 30 dominiert der RANG. Alle 16 Opportunities verworfen.
  Einzige budget-dominante Kampagne: Trockenbauer (32,9% vs 16,4%), 85 CHF Spend.
- UMLAND-FLIP (Engine findet ihn nicht): im 30d-Fenster 1,3% Budget / 78,2% Rang = rang-limitiert.
  7d vor vs 7d nach Throttle-Entfernung (11.08.): Rang 79,9 -> 47,1%, Budget 3,4 -> 31,5%.
  Limitierung hat GEWECHSELT. Einzige heute begruendbare Erhoehung. 30d-Fenster maskiert es.
- B-LAYER-GATING: D03/D04/D13/D14/D15 auf INFO gesetzt. breakEvenCPA 75 ist laut Config
  ausdruecklich NICHT margenbasiert (1,5x Konto-Oe). BUD-D04 stufte Gipser bei CPA 75,12 als
  "unprofitabel" ein = 0,16% ueber einer selbstgesetzten Linie.
- BUD-D08: 30 von 30 Kampagnen unter Smart-Bidding-Conversion-Floor (30/Mon). Montage-Elektriker 1,9.
- Pacing gesund: MTD 4.877 vs 4.935 Soll; Monatsende projiziert 8.893 vs 8.500 (+4,6%).
- HYGIENE: 2 stille UMLAND-Kampagnen ENABLED mit je 65,99 CHF/Tag, 0 Impressionen in 14 Tagen.
- Trend 86% (10.08.) -> 80%. Ueberwiegend Methodik (B-Layer-Gating), nicht Verschlechterung.
- Fresh peers integriert: /search-term-auditor (18.08.), /competitive-analyst (11.08. 41%),
  /lp-auditor (11.08. 60%), /offer-auditor (11.08. 78%), /tracking-specialist (10.08. 48%),
  /strategy-specialist (10.08. 55%), /account-auditor (10.08.).
  Stale (>7T): /quality-score-auditor, /keyword-auditor, /bidding-auditor.
- Config: businessMdHash auf 3fd67857455b6b63 aktualisiert, monthlyBudgetTotal 8500 rebestaetigt.

