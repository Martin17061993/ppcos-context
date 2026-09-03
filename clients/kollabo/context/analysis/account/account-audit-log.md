# Account Audit Log

## 2026-08-10 — full
- Score: 77% (Good) | Structure 45/75 | Naming 8/8 | Settings 44/48 | AdGroups 22/25 | Defaults 5/5
- FAIL: D04 Kampagnenanzahl (30 Kampagnen, 0 mit >=30 Conv), D05 Budget-Fragmentierung
  (18/30 unter 10 CHF/Tag), D07 Null-Conversion (4 Kampagnen, 467 CHF)
- WARN: D06 Keyword-Overlap 1,4%, D12 Suchpartner 29/30 ohne Begruendung,
  D19 TEXT_ASSET_AUTOMATION OPTED_IN auf UMLAND TEST, D21 8 AdGroups mit nur 1 RSA
- PASS: D01 D02 D03 D08 D09 D10 D11 D13 D14 D16 D18 D20 D22 D23 D24
- SKIP: D15 Sprache, D17 Anzeigenplan (Felder nicht im Pull)
- Kernbefund: Datenfragmentierung ist die strukturelle Ursache der Rang-Limitierung.
- Nebenbefund: Match-Types sind NICHT mehr durchgehend Broad (162/139/85), aber 88% des
  Spends laeuft weiter ueber Broad; Phrase-CPA (65,74) schlechter als Broad (50,59).
- Peer integriert: /tracking-specialist 2026-08-10 (bestaetigt D24, widerspricht D07).
- Report: context/analysis/account/account-audit.md
