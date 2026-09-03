# Tracking Audit Log

## 2026-08-10 — full
- Score: 48% (Critical, Konfiguration) | Completeness 27,5/80 (34%) | Tag Health 35/50 (70%)
- FAIL: D05 Zielkategorie, D06 Zaehlmethode, D09 Volumen Zero-Check
- PASS: D08 Status, D10 Anomalie, D11 Google Tag, D12 Conversion Linker
- SKIP: D13-D17 (Test-Conversion wuerde echten Lead erzeugen - ohne Freigabe nicht durchgefuehrt)
- Kernbefund: Live-Gebotspfad sauber (34/37 Kampagnen kampagnenspezifisch, nur QUALIFIED_LEAD biddable).
  Score spiegelt Konfig-Hygiene, nicht operatives Risiko.
- Top-Risiko: SF: New Lead (1) seit 01.07. bei 0 und aus Conversions-Metrik raus; Qualified steigt
  gegenlaeufig -> Mapping-Verdacht ungeklaert.
- Klick-Lookback 90 T vs. 98,5% Conversions innerhalb 30 T.
- Consent Mode v2 vorhanden aber nicht verdrahtet (npa=1 auf allen Requests).
- Korrigierte business.md 3.3 (4 Perspective-Aktionen sind inert, nicht gebotsverwaessernd).
- Report: context/analysis/tracking/tracking-audit.md
