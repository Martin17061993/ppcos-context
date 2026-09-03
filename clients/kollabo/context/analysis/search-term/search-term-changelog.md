# Search Term Optimizer Changelog

## 2026-08-18 — Search Term Optimizer

**Mode:** live | **Account:** 1487707588
**Result:** 3/3 applied
**Source:** context/analysis/search-term/search-term-audit.md

**Summary:** 3 × ST-E03

| # | Action | Type | Target | Status |
|---|--------|------|--------|--------|
| 1 | ST-E03 | create | stellenanzeigen sanitärinstallateur | OK |
| 2 | ST-E03 | create | gipser gesucht | OK |
| 3 | ST-E03 | create | automatikmonteur jobs | OK |


### Nachtrag (Verifikation gegen API, 2026-08-18)

Alle 3 Keywords verifiziert als ENABLED:

| Keyword | Match | Ad Group | Criterion ID |
|---|---|---|---|
| stellenanzeigen sanitaerinstallateur | PHRASE | AG \| RSA \| Sanitaerinstallateur | 190557736766~357116055264 |
| gipser gesucht | PHRASE | AG \| RSA \| Gipser | 194724430511~11686663918 |
| automatikmonteur jobs | PHRASE | AG \| RSA \| Automatikmonteur | 154000335045~614639898886 |

**FEHLER bei Op 3 — Duplikat nicht erkannt.**
`automatikmonteur jobs` existierte in derselben Ad Group `AG | RSA | Automatikmonteur` bereits als
**BROAD** (ENABLED, Criterion 154000335045~368569501197). Die Ad Group traegt den Begriff jetzt
doppelt (BROAD + PHRASE).

Ursache: Der Kandidat stand im Audit auf `AG | DSA | Automatikmonteur` (SEARCH_DYNAMIC_ADS, nicht
ENABLED). Die Umleitung auf die aktive Schwester-Ad-Group erfolgte NACH der Duplikatspruefung, die
auf dem Paar (Ad-Group-Name, Keyword-Text) basierte. Das neue Ziel wurde nicht erneut geprueft.

Bewertung: nicht schaedlich. Phrase ist eine Teilmenge von Broad; bei Smart Bidding regelt Google
die Auktion pro Query. Die Promotion ist damit aber **redundant** — der Begriff war in dieser Ad
Group bereits ueber Broad erreichbar. Ops 1 und 2 sind sauber, dort existierte kein Vorgaenger.

Weitere Vorkommen von `automatikmonteur jobs` im Konto (vorbestehend, nicht angefasst):
- `Automatiker_1_Job` (Kampagne Automatiker) — BROAD, ENABLED
- `AG | RSA | Automatiker` (Kampagne Automatiker) — BROAD, PAUSED

**Offen:** Rueckbau des neuen PHRASE-Keywords moeglich (Criterion 154000335045~614639898886),
Entscheidung beim Nutzer.

**Handelnder Account:** `change_event` zeigt den Push zum Zeitpunkt der Pruefung noch nicht
(bekannte API-Latenz). Letzter sichtbarer Eintrag: 2026-08-11 martinweingarten93@gmail.com
(GOOGLE_ADS_WEB_CLIENT). Identitaet des API-Tokens damit weiterhin unbestaetigt.
