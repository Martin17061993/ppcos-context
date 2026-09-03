# Budget Optimizer Changelog

## 2026-08-18 — Budget Optimizer

**Mode:** live | **Customer:** 1487707588 | **Currency:** CHF
**Result:** 3/3 applied
**Override:** breakEvenCPA 75 dokumentierter Proxy. Reduktionen treffen CPA 152 und 130 = 2,99x bzw 2,56x Konto-Oe.

| # | Type | Target | Old/day | New/day | Rationale |
|---|------|--------|---------|---------|-----------|
| 1 | — | `—` | CHF 0 | CHF 4 | CPA 152,16 = 2,99x Konto-Oe (50,92). Guardrail #5 Schwelle 76,38 ueberschritten. Reduktion auf 4,00 haelt das 3-4-CHF-Minimum aus Guardrail #10 (keine Profession pausieren). |
| 2 | — | `—` | CHF 0 | CHF 6 | CPA 130,31 = 2,56x Konto-Oe. Dreifach belegt: QS faellt 7->5 (DECLINING_SHARP), CPC steigt 1,84->2,30->2,54 (BID-D23). Schritt exakt -20% (Guardrail #8). |
| 3 | — | `—` | CHF 0 | CHF 29 | Einzige Kampagne mit belegtem Limitierungs-Wechsel: Rang-Verlust 79,9->47,1%, Budget-Verlust 3,4->31,5% (7T vor/nach Throttle-Entfernung 11.08.). Zugleich eine von nur zwei Kampagnen ueber der Smart-Bidding-Lernschwelle (16 Conv/30T). Saettigungsdeckel Guardrail #1 bei ~85 CHF/Tag. Schritt +10%, unter dem 20%-Cap. |

