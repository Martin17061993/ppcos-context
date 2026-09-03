# Geo-Schedule Audit Log

## 2026-08-11 — Score: 74% (Good)
- Mode: full | 30 aktive Kampagnen | 30T Geo/Schedule/Device, 90T Demografie, 6 Wochen Konsistenz
- Module: Geographic 29,4/35 (84%) | Schedule&Device 18,2/28 (65%) | Demographics 15,68/22,4 (70%)
- FAIL: GS-D07 Zeitplan — 513,80 CHF fuer 1 Conversion in 01:00-04:00 + 22:00-23:00 (CPA 514).
  00:00 (CPA 30,74) und 05:00 (19,07) sind gut — keine pauschale Nachtregel.
- WARN: GS-D02/D04/D14 Deutschland CPA 29,02 vs Schweiz 53,82 bei nur 9,1% Spend-Anteil.
  Selber Befund wie /bidding-auditor UMLAND-tCPA-Fehlableitung, aus anderer Richtung.
- WARN: GS-D06 Mobile 71,6% Spend, CVR 2,09% vs Desktop 4,11%. Wahrscheinlich das LP-Problem
  in mobiler Auspraegung, nicht Targeting -> erst LP-Audit.
- PASS: GS-D01 PRESENCE ueberall, GS-D08 699 bestaetigte Muster ueber 6 Wochen,
  GS-D09 null Modifikatoren, GS-D11 kein Smart-Bidding-Konflikt moeglich.
- GS-D13 COMPLIANCE-BLOCKIERT: FEMALE CPA 52,82 vs MALE 33,14 wuerde Ausschluss nahelegen.
  NICHT zulaessig — Diversity Statement kollabo ag, Swissstaffing Code of Conduct, AVG.
  Befund an /rsa-maker + /lp-auditor statt an Targeting.
- Einkommens-Targeting in der Schweiz nicht verfuegbar (100% UNDETERMINED).
