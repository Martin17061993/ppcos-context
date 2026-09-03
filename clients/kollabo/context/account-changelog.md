# Account Changelog — Kollabo

**Date range:** 2026-07-29 to 2026-08-27 (30 days)
**Total changes (change_event):** 10
**API-invisible changes (change_status):** 1.174

> **⚠️ Data source limitation — read this before relying on this changelog.**
> Built from the Google Ads API `change_event` resource, which does **NOT** include changes made via **Google Ads Editor** (documented API limitation) and can occasionally miss other events. Absence of a change here is not proof it didn't happen. The Google Ads UI change history (Tools → Change history) is the source of truth.
> **For downstream skills/agents:** if your analysis depends on the completeness of this changelog (e.g., "no changes were made, therefore…"), you must first ask the user: *"Were any changes made via Google Ads Editor in this period?"* — do not treat this file as exhaustive.

---

## ⚠️ Drei Befunde, die sofort zählen

### 1. Auto-Apply hat unseren eigenen Keyword-Push zurückgedreht — und die schlechtere Match-Type-Variante behalten

Am **18.08. 16:29:56** hat `/search-term-optimizer promote` in `AG | RSA | Automatikmonteur`
das Keyword `automatikmonteur jobs` als **PHRASE** angelegt (Criterion `154000335045~614639898886`).
Der Memory-Log vom 18.08. hat das als Duplikat markiert, weil derselbe Begriff dort schon als
**BROAD** existierte, und einen Rückbau als offenes Item geführt.

**Am 21.08. 03:21:53 hat Auto-Apply genau dieses Criterion entfernt.** Das Duplikat ist damit
weg — aber Google hat **PHRASE gelöscht und BROAD behalten**. Das ist die falsche Richtung:

- PHRASE war die engere, gewollte Variante — sie war der Grund für den Push.
- BROAD auf Smart Bidding verstösst gegen die eigene Regel „never Broad-on-Smart-Bidding"
  (`/search-term-optimizer`, 18.08.).
- Die Entscheidung fiel nachts um 03:21 ohne Freigabe.

**Das offene Item „Rückbau Criterion 154000335045~614639898886" ist erledigt — aber nicht durch
uns und nicht richtig.** Guardrail #6 („Auto-Apply = Münzwurf") hat hier einen negativen Fall
dazubekommen.

### 2. Auto-Apply greift jetzt häufiger ein — 2 der 3 Eingriffe fallen in die letzten 7 Tage

| Datum | Uhrzeit | Kampagne | Aktion |
|---|---|---|---|
| 2026-07-30 | 03:45:37 | Metallbauer | `stellenangebote metallbau` (EXACT) entfernt |
| 2026-08-21 | 03:21:53 | Automatikmonteur | `automatikmonteur jobs` (PHRASE) entfernt — unser Push vom 18.08. |
| **2026-08-27** | **03:50:34** | **Strassenbauer** | **`strassenbauer stellen` (BROAD) entfernt — heute** |

Der Eingriff von heute trifft eine **konvertierende** Kampagne: Strassenbauer liegt bei
CPA 34,20 (14 T, 12.–25.08.) und damit **unter** dem Konto-Ø von 44,13. Das ist kein
Aufräumen in einer toten Ecke.

#### Stand der Auto-Apply-Abschaltung (2026-08-27)

Über `recommendation_subscription` (v24) sind die Abos lesbar und teilweise schreibbar. Die
Notiz vom 18.08. („über die API gar nicht abschaltbar, nur UI") war **falsch**. Ausgangslage:
**3 von 12 Abos ENABLED**.

| Typ | Status | Weg |
|---|---|---|
| `OPTIMIZE_AD_ROTATION` (type 10) | ✅ **am 27.08. per API auf PAUSED gesetzt** | API, verifiziert |
| **Redundante Keywords entfernen** | ⚠️ **weiterhin AKTIV** | nur UI |
| Optimiertes Targeting | ⚠️ weiterhin aktiv, aber **wirkungslos** | nur UI |
| 9 weitere (`KEYWORD`, `SEARCH_PARTNERS_OPT_IN`, `MAXIMIZE_CONVERSIONS_OPT_IN`, `MAXIMIZE_CONVERSION_VALUE_OPT_IN`, `RESPONSIVE_SEARCH_AD_IMPROVE_AD_STRENGTH` u. a.) | PAUSED | — |

**Warum die letzten zwei nicht per API gehen:** Google maskiert deren Typ. Beide melden
`type = 1` (UNKNOWN) und `resource_name = customers/1487707588/recommendationSubscriptions/UNKNOWN`.
Ein Update darauf lehnt der Server ab — bei `validate_only` und live identisch:
`{"request_error":"BAD_RESOURCE_ID"} 'UNKNOWN' part of the resource name is invalid.`
Die Zuordnung der Klarnamen kommt aus der UI (Martin, 27.08.), nicht aus der API.

**Von den beiden ist nur eines gefährlich:**
- **„Redundante Keywords entfernen"** ist die Ursache aller drei Entfernungen oben. Genau dieses
  Muster: `automatikmonteur jobs` (PHRASE) war redundant gegen ein vorhandenes BROAD — Google
  hat die engere Variante gelöscht.
- **„Optimiertes Targeting"** ist ein Display-/Demand-Gen-/Video-Feature. Geprüft am 27.08.:
  `ad_group.optimized_targeting_enabled` ist auf **allen 34** aktiven Ad Groups leer, alle 34
  sind `SEARCH` (33 × `SEARCH_STANDARD`, 1 × `SEARCH_DYNAMIC_ADS`). Es hat derzeit nichts,
  worauf es greifen kann — latent, nicht wirksam. Trotzdem abschalten, sobald Display/Demand Gen
  dazukommt.

> **Kein MCC-Override:** auf beiden Verwaltungskonten (Jonas Makki 5591362086 und
> Ex Machina Agency 8152735088) existiert **keine einzige** `recommendation_subscription`.
> Geprüft am 27.08. Die Abschaltung muss also im Kundenkonto erfolgen, nicht im MCC.

### 3. Die „1.174 unsichtbaren Änderungen" sind mit hoher Wahrscheinlichkeit Google-Metadaten, keine Editor-Sessions

Die Vorversion dieses Changelogs (11.08.) hat 1.649 `change_status`-Treffer als „viel Bewegung"
und mutmassliche Editor-Sessions gelesen. **Diese Deutung ist nach der heutigen Prüfung
wahrscheinlich falsch.** Belege:

1. Am **27.08. 19:59:42** meldet `change_status` **23 `CAMPAIGN_BUDGET`-Ressourcen gleichzeitig
   als CHANGED** — in einem einzigen Sekunden-Batch, plus 3 weitere um 07:59:43 und 2 am 26.08.
   Zusammen: **alle 30 Live-Budgets innerhalb von ~36 Stunden.**
2. **Die Budgetbeträge haben sich nicht geändert.** Direkt gegen die API verifiziert (27.08.):
   Tagesbudget-Summe unverändert **280,00 CHF über 30 Live-Kampagnen**, alle Einzelwerte auf
   dem Stand vom 18.08.
3. `change_event` — die Ressource *mit* Detailangaben — zeigt seit dem 18.08. **keine einzige**
   Budgetänderung.

Die plausibelste Erklärung: `campaign_budget` trägt Google-gepflegte Felder
(`recommended_budget_amount`, `has_recommended_budget`), deren Aktualisierung die Ressource als
CHANGED markiert. Analog auf Kampagnenebene (Optimierungsfaktor o. Ä.) — dort sind alle
29 Live-Kampagnen am 27.08. zwischen 14:05 und 19:57 einzeln als CHANGED gemeldet, was für
30 separate menschliche Edits an einem Nachmittag unrealistisch ist.

> **Nicht bewiesen, aber gut belegt.** Für die Praxis heisst das: `change_status`-Zahlen sind
> **kein** Indikator für Eingriffe ins Konto. Die frühere Frage „waren die Cluster vom 21.07.
> und 14.07. deine Editor-Sessions?" ist damit entwertet — sie lässt sich aus diesen Daten
> nicht beantworten und sollte keine Analyse mehr blockieren.

---

## Summary

### By Resource Type (change_event)

| Typ | Anzahl |
|---|---|
| AD_GROUP_CRITERION | 6 |
| CAMPAIGN_BUDGET | 3 |
| CAMPAIGN | 1 |
| **Summe** | **10** |

### By Source

| client_type | Anzahl |
|---|---|
| GOOGLE_ADS_API | 6 |
| GOOGLE_ADS_RECOMMENDATIONS_SUBSCRIPTION | 3 |
| GOOGLE_ADS_WEB_CLIENT | 1 |

### By User

| user_email | Anzahl | Was |
|---|---|---|
| `ads@jonas-makki.com` | 6 | unsere API-Pushes vom 18.08. (3 Keywords + 3 Budgets) |
| `Recommendations Auto-Apply` | 3 | 30.07., 21.08., 27.08. — alle Keyword-Entfernungen |
| `martinweingarten93@gmail.com` | 1 | 11.08. UMLAND tCPA entfernt (UI) |

---

## Change Log

### 2026-08-27

- **03:50:34 · `Recommendations Auto-Apply` · AD_GROUP_CRITERION REMOVE**
  Kampagne `EX | 26 | CH | SEARCH | LEAD | Strassenbauer`, Ad Group `AG | RSA | Strassenbauer`
  Keyword `strassenbauer stellen` (BROAD) entfernt. Criterion `193437338762~298317241381`.
  → Kampagne konvertiert (CPA 34,20 in 14 T, unter Konto-Ø 44,13). Wirkung unbewertet.

### 2026-08-21

- **03:21:53 · `Recommendations Auto-Apply` · AD_GROUP_CRITERION REMOVE**
  Kampagne `EX | 25 | CH | SEARCH | LEAD | Automatikmonteur`, Ad Group `AG | RSA | Automatikmonteur`
  Keyword `automatikmonteur jobs` (PHRASE) entfernt. Criterion `154000335045~614639898886`.
  → **Das ist unser eigener Push vom 18.08.** Siehe Befund 1.

### 2026-08-18

- **18:55:10 · `ads@jonas-makki.com` · CAMPAIGN_BUDGET UPDATE ×3** (GOOGLE_ADS_API)
  | Kampagne | alt | neu |
  |---|---|---|
  | `EX \| 26 \| CH \| SEARCH \| LEAD \| Abdichter` | 5,00 | 4,00 |
  | `EX \| 25 \| CH \| SEARCH \| LEAD \| Montage-Elektriker` | 8,00 | 6,40 |
  | `EX \| DE \| DACH \| SEARCH \| LEAD \| UMLAND TEST` | 26,00 | 28,60 |
  → Netto ±0. Unsere Umschichtung, `/budget-optimizer reallocate`.
  History: `tmp/budget-optimizer/mutations-2026-08-18T16-55-10-603Z.json`

- **16:29:56 · `ads@jonas-makki.com` · AD_GROUP_CRITERION CREATE ×3** (GOOGLE_ADS_API)
  | Keyword | Match | Ad Group |
  |---|---|---|
  | `stellenanzeigen sanitärinstallateur` | PHRASE | `AG \| RSA \| Sanitärinstallateur` |
  | `gipser gesucht` | PHRASE | `AG \| RSA \| Gipser` |
  | `automatikmonteur jobs` | PHRASE | `AG \| RSA \| Automatikmonteur` |
  → `/search-term-optimizer promote`. Das dritte wurde am 21.08. von Auto-Apply entfernt.

### 2026-08-11

- **16:07:07 · `martinweingarten93@gmail.com` · CAMPAIGN UPDATE** (GOOGLE_ADS_WEB_CLIENT)
  `EX | DE | DACH | SEARCH | LEAD | UMLAND TEST`:
  `maximize_conversions.target_cpa_micros` 11.000.000 → **entfernt**.
  → Phase 0 des Budgetplans. Ergebnis siehe unten unter Insights.

### 2026-07-30

- **03:45:37 · `Recommendations Auto-Apply` · AD_GROUP_CRITERION REMOVE**
  Kampagne `EX | 25 | CH | SEARCH | LEAD | Metallbauer`, Ad Group `AG | RSA | Metallbauer KW Testing`
  Keyword `stellenangebote metallbau` (EXACT) entfernt. Criterion `191429218741~2831004360`.

---

## API-Invisible Changes

### 1.174 invisible changes detected

> ⚠️ Über `change_status` erkannt, **kein Detail** in der API. **Lies Befund 3 oben, bevor du
> diese Zahlen interpretierst** — die Evidenz spricht dafür, dass der Grossteil
> Google-Metadaten-Refreshes sind, keine Eingriffe.

**Nach Ressourcentyp:**

| Typ | Anzahl |
|---|---|
| AD_GROUP_CRITERION | 1.045 |
| AD_GROUP_AD | 68 |
| CAMPAIGN_BUDGET | 30 |
| CAMPAIGN | 30 |
| AD_GROUP | 1 |
| **Summe** | **1.174** |

**Cluster nach Grösse:**

| Zeitpunkt | Ressourcen | Einschätzung |
|---|---|---|
| 2026-08-22 14:32:14 | 282 | nachmittags |
| 2026-08-12 04:55:14 | 230 | nachts — mutmasslich automatisiert |
| 2026-07-29 01:47:44 | 215 | nachts — mutmasslich automatisiert |
| 2026-08-05 04:23:16 | 174 | nachts — mutmasslich automatisiert |
| 2026-08-15 14:02:31 | 134 | nachmittags |
| **2026-08-27 19:59:42** | **23** | **alle CAMPAIGN_BUDGET — Beträge nachweislich unverändert (Befund 3)** |
| 2026-08-25 11:35:44 | 15 | |
| 2026-08-27 16:04:03 | 11 | |

**Tagesverteilung:**

| Datum | Ressourcen |
|---|---|
| 2026-07-29 | 218 |
| 2026-08-05 | 174 |
| 2026-08-12 | 231 |
| 2026-08-15 | 134 |
| 2026-08-22 | 287 |
| 2026-08-25 | 28 |
| 2026-08-26 | 9 |
| 2026-08-27 | 68 |
| *übrige Tage* | je 1–7 |

---

## Insights

- **Auto-Apply ist das dringendste offene Item im Konto.** 3 Eingriffe in 30 Tagen, 2 davon in
  den letzten 7 Tagen, einer heute, alle nachts zwischen 03:21 und 03:50. Einer hat einen
  eigenen, begründeten Push zurückgedreht und dabei die schlechtere Match-Type-Variante behalten.
  Nur über die UI abschaltbar — die API bietet es nicht an.
- **Phase 0 (tCPA-Entfernung 11.08.) hat funktioniert.** UMLAND, Fenster 19.–25.08.:
  Ausnutzung 111,2 %, Budget-Lost-IS 14,0 %, Qualified-CPA 44,54. Alle drei Gates aus
  `tmp/bidding-optimizer/follow-ups-UMLAND-2026-08-11.md` erfüllt. 14-Tage-Wert 12.–25.08.:
  413,75 CHF / 11,00 Qualified / **CPA 37,61** — unter Konto-Ø 44,13.
- **Der Schnitt an Montage-Elektriker vom 18.08. war gegen die Datenlage.** 14 T nach dem
  Schnitt: 107,18 CHF / 4,96 Qualified / **CPA 21,60** = 0,49× Konto-Ø, bei 22,0 %
  Budget-Lost-IS und 120 % Ausnutzung des reduzierten Budgets. Die Begründung damals
  (CPA 130,31) stammte aus einem 30-Tage-Fenster, das den Juli-Signalabsturz mitschleppte.
- **Die Budget-Schnitte vom 18.08. haben nur ~29 % ihres Nominalwerts realisiert.**
  Ist-Spend/Tag vorher → nachher: Montage-Elektriker 8,25 → 7,69 (−0,56 statt −1,60),
  Abdichter 5,08 → 4,88 (−0,20 statt −1,00). Google überliefert auf budgetlimitierten
  Kampagnen bis 2× Tagesbudget. **Regel für künftige Umschichtungen: ein kleiner Schnitt auf
  einer gedrosselten Kampagne setzt kein echtes Geld frei.**
- **`change_status`-Zahlen taugen nicht als Eingriffs-Indikator** (Befund 3). Von
  1.184 Gesamtänderungen sind 10 im Detail sichtbar — aber die restlichen 1.174 sind
  überwiegend keine Eingriffe, sondern Metadaten. Die frühere Lesart „0,2 % Sichtbarkeit,
  also blinder Fleck" überschätzt das Problem.
- **Konto-Pacing ist exakt auf Plan.** 12.–25.08.: 3.932,37 CHF in 14 T = 8.539 CHF auf
  30,4 Tage, gegen ein Nominalbudget von 8.512 CHF (280,00 CHF/Tag). Der Kundenauftrag
  „8.500 CHF/Monat" ist erfüllt.

---
*Last updated: 2026-08-27*
*Date range: 30 days (2026-07-29 to 2026-08-27)*
*Raw: `context/google-ads/data/account-changelog.csv` (10 events) · `context/google-ads/data/account-changelog-invisible.csv` (1.174 rows)*
