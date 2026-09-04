# Fragen an Kollabo — Stand 27.08.2026

> **Für Martin:** Anredeform ist auf „ihr/euch" gesetzt — bei Bedarf auf „Sie" umstellen.
> Block A ist der Teil, der eine Entscheidung blockiert. Block B und C können nachlaufen.
> Wenn nur eine Frage gestellt werden kann, dann **A1**.

---

## Worum es geht (Kurzfassung für die Mail)

Das Konto läuft aktuell auf **8.512 CHF/Monat** und liefert **~193 qualifizierte Bewerber/Monat**
zu **44 CHF pro Stück**. Wir sehen genug ungenutzte Nachfrage, um auf **10.000 CHF/Monat**
zu gehen — technisch ist das 2,7-fach durch profitable, aktuell am Budget scheiternde Suchanfragen
gedeckt.

**Wir können aber nicht beurteilen, ob das für euch profitabel ist.** Uns fehlt eine einzige Zahl:
was eine Vermittlung wirtschaftlich wert ist. Ohne sie ist jede Budgetempfehlung geraten.

Dazu kommen vier Messfragen, bei denen wir seit Juli im Blindflug sind.

---

## Block A — blockiert die 10k-Entscheidung 🔴

### A1 · Was bringt euch eine erfolgreiche Vermittlung an Deckungsbeitrag?

**Die Frage ist binär:** liegt der Deckungsbeitrag je Vermittlung (Provision minus direkte
Kosten für Betreuung, Personalberatung, Admin) über oder unter **500 CHF**?

Warum diese Schwelle: aus unseren Daten kostet eine Vermittlung über Google Ads derzeit
zwischen **244 und 485 CHF** — die Bandbreite hängt daran, welche Vermittlungsquote gilt (siehe A2).

| Vermittlungsquote | Kosten je Vermittlung über Google Ads |
|---|---|
| 18,1 % (13-Monats-Mittel) | 244 CHF |
| 15 % (Viabilitätsschwelle) | 294 CHF |
| **9,1 % (Juli, gemessen)** | **485 CHF** |

**Was es freischaltet:** die 10k-Entscheidung. Der zusätzliche Aufwand von 1.488 CHF/Monat
bringt rechnerisch **+3 bis +6 Vermittlungen/Monat**, also **240 bis 496 CHF je zusätzliche
Vermittlung**. Liegt euer Deckungsbeitrag darüber, ist 10k klar richtig. Liegt er darunter,
müssen wir über 8.500 nochmal reden — nicht über 10k.

*Eine Bandbreite genügt uns („zwischen X und Y"). Wir brauchen keine Buchhaltung, nur die
Größenordnung.*

---

### A2 · Wie hoch ist die tatsächliche Vermittlungsquote im Juli und August?

Wir messen, was aus Salesforce zu uns zurückkommt — und das ist seit Juli lückenhaft (A3, A4).
Deshalb brauchen wir die Quote aus **euren** Zahlen, nicht aus unseren.

Konkret: von den qualifizierten Bewerbern eines Monats — wie viele wurden am Ende vermittelt?

Was wir sehen: die Quote ist von **20,2 % (Juni)** auf **9,1 % (Juli)** gefallen. Das ist
vermutlich die erwartbare Folge der gesenkten Qualifikationsschwelle zum 01.07. (vorher 2 Jahre
Erfahrung Schweiz, jetzt 6 Monate EU) — mehr Leute kommen durch, entsprechend weniger davon
werden vermittelt.

**Wichtig:** unsere 9,1 % sind eine **Untergrenze**. Die Juli-Bewerber hatten noch keine Zeit,
abzuschliessen — belastbar ist der Wert erst Ende Oktober. Wenn ihr eine bessere Zahl habt,
ändert das unsere Rechnung erheblich.

**Was es freischaltet:** A1 überhaupt beantwortbar zu machen. Ohne die Quote kennen wir die
Kosten je Vermittlung nur als Bandbreite von 244 bis 485 CHF — ein Faktor 2.

---

### A3 · Wurde die Stufe „New Lead" mit der Kriterienänderung abgeschafft, oder ist der Import defekt?

`SF: New Lead (1)` liefert seit dem **01.07.2026 exakt null**. Vorher waren es 179–388 pro Monat.

Zwei mögliche Erklärungen, und die Konsequenz ist völlig verschieden:
- **Abgeschafft:** die Stufe existiert im neuen Prozess nicht mehr → wir löschen sie und alles ist gut.
- **Defekt:** der Import bricht → wir verlieren Daten, die wir für die Gebotssteuerung brauchen.

**Was es freischaltet:** Sauberkeit der Messung. Solange wir das nicht wiss, steht hinter jeder
CPA-Zahl ab Juli ein Fragezeichen.

---

### A4 · Warum kommen aus Salesforce 63 % weniger Datensätze an als im April?

| Monat | Bewerbungen (unsere Messung) | Datensätze aus Salesforce |
|---|---|---|
| April | 556 | 472 |
| Mai | 504 | 354 |
| Juni | 527 | 293 |
| **Juli** | **527** | **175** |

Die Bewerbungen sind **stabil**. Was zurückkommt, hat sich mehr als halbiert.

Warum das für euch teuer ist: Googles Gebotsautomatik lernt aus genau diesen Rückmeldungen.
Sie arbeitet aktuell mit **rund einem Drittel** des Signals von April und verteilt euer Budget
entsprechend schlechter. Das ist eine plausible Mitursache dafür, dass wir bei den Anzeigen-
Platzierungen an Boden verlieren.

**Frage konkret:** hat sich zum 01.07. etwas am Salesforce-Setup, an der Schnittstelle oder am
Feldmapping geändert? Und: wer bei euch ist der richtige Ansprechpartner für die
Salesforce-Google-Ads-Verbindung?

**Was es freischaltet:** die Gebotssteuerung. Das ist der grösste einzelne Effizienzhebel im
Konto — grösser als jede Budgetentscheidung.

---

## Block B — verbessert die Steuerung 🟡

### B1 · Was ist für euch ein „guter" Lead?

Wir optimieren aktuell auf `SF: Qualified (2)`. **Das ist unsere Annahme, nicht eure Vorgabe** —
es gibt bis heute keine abgestimmte Definition.

Unsere Logik: „Bewerbung abgeschickt" wäre zu früh (dann optimiert Google auf Masse, auch auf
Ausschuss), „Abschluss" mit ~14/Monat zu dünn zum Steuern. `Qualified` ist der Mittelweg.

**Frage:** passt das, oder gibt es bei euch eine Stufe dazwischen, die besser abbildet, wann ein
Bewerber wirtschaftlich interessant wird?

---

### B2 · Was passiert zwischen 500 Bewerbungen und 158 qualifizierten?

Rund **zwei Drittel** fallen in diesem Schritt heraus. Wir wissen nicht, warum.

Unsere Vermutungen, alle unbestätigt: Doppelbewerbungen · unvollständige Profile · falsches
Gewerk · fehlende Arbeitsbewilligung.

**Was wir bräuchten:** eine Aufstellung der Ablehnungsgründe, gerne grob („40 % unvollständig,
30 % falsches Gewerk, …"). Ein Salesforce-Export mit dem Ablehnungsgrund-Feld über 3 Monate
würde völlig genügen.

**Was es freischaltet:** wenn ein grosser Teil aus einem Grund wegfällt, den wir im Targeting
adressieren können (z. B. falsches Gewerk, keine Arbeitsbewilligung), sparen wir Geld an der
Quelle statt es nachträglich zu filtern. Das ist der Unterschied zwischen 44 CHF und deutlich
weniger pro qualifiziertem Bewerber.

---

### B3 · Habt ihr für alle Gewerke überhaupt genug Arbeitgeberseite?

Das ist die unangenehme Frage, aber die wichtigste in diesem Block.

Wir bewerben ~30 Gewerke separat. Die Ergebnisse gehen extrem auseinander — bei **identischer
Landingpage-Vorlage** liegt der beste Bereich beim **12-fachen** des schlechtesten.

Vier Gewerke haben in den letzten 14 Tagen **183 CHF ausgegeben und null** qualifizierte
Bewerber gebracht:

| Gewerk | Ausgaben 14 Tage | Qualifizierte |
|---|---|---|
| Kranführer | 51 CHF | 0 |
| Trockenbauer | 47 CHF | 0 |
| Baumaschinenführer | 44 CHF | 0 |
| Metallbaukonstrukteur | 41 CHF | 0 |

Bei so einer Streuung ist die Ursache normalerweise nicht die Werbung, sondern das **Angebot**:
Wenn ihr für ein Gewerk keine offenen Stellen habt, springt niemand — egal wie gut die Anzeige ist.

**Frage:** für welche Gewerke habt ihr aktuell wirklich Bedarf, und wo eher nicht? Eine simple
Ampel-Liste (viel Bedarf / etwas / kaum) über die Gewerke wäre extrem wertvoll.

**Was es freischaltet:** wir schichten Budget von Gewerken ohne Arbeitgeberbedarf zu denen mit
Bedarf. Auf Wunsch pausieren wir nichts — wir fahren die Schwachen nur auf Minimum. Nach unserer
Rechnung sind das rund **400 CHF/Monat**, die aktuell in Gewerken ohne Nachfrage liegen.

---

### B4 · Die vier gewerkespezifischen Perspective-Landingpages liefern null Conversions

Wir sehen vier separate Landingpages (Perspective-Funnels), deren Conversion-Messung **nichts**
zurückgibt. Entweder werden sie nicht mehr genutzt, oder das Tracking darauf ist tot.

**Frage:** sind die noch im Einsatz? Wenn ja, schicken wir das ans Tracking-Setup.

---

## Block C — Kontext, kann warten ⚪

### C1 · Wie ist euer Geschäftsjahr saisonal?

Wir sehen in unseren eigenen Daten, dass **August und September historisch die teuersten Monate**
sind (Bewerber teurer als im Frühjahr). Was wir nicht wissen: wie sich das mit **eurer**
Saisonalität überlagert — Bau-Hochsaison, Ferienwirkung auf offene Stellen, Winterpause.

**Warum es zählt:** wenn im Herbst euer Stellenangebot zurückgeht, sollten wir das Budget nicht
gerade dann hochfahren.

---

### C2 · Welche anderen Kanäle speisen die ~500 Bewerbungen im Monat?

Wir wissen von euch nur: GTM, GA4, Salesforce, Cookie-Banner. Ob und wie stark SEO, Social,
Meta Ads, Jobportale oder Offline-Recruiting beitragen, ist uns unbekannt.

**Warum es zählt:** wenn ein anderer Kanal einen relevanten Teil der Bewerber liefert, ist der
Google-Ads-Anteil an den qualifizierten Bewerbern in unseren Zahlen **überschätzt** — und damit
auch die Wirtschaftlichkeit, die wir uns selbst zuschreiben. Wir würden das gerne ehrlich rechnen.

---

### C3 · Freigabe für 10.000 CHF/Monat — grundsätzlich denkbar?

Rein zur Planung: **wenn** A1 positiv beantwortet ist, wäre eine Erhöhung von 8.500 auf 10.000
CHF/Monat grundsätzlich im Rahmen? Wir würden in zwei Schritten über zwei Wochen hochfahren,
nicht auf einmal.

Für Beträge darüber (der früher diskutierte 15k-Pfad) sehen wir aktuell **keine tragfähige
Grundlage** — dazu müsste zuerst die Anzeigenqualität auf den Landingpages besser werden.
Das ist der Punkt aus dem separaten Dokument `kollabo-website-fixes-2026-08-18.md`.

---

## Was wir konkret brauchen — Kurzliste

| # | Was | Format | Priorität |
|---|---|---|---|
| A1 | Deckungsbeitrag je Vermittlung | eine Zahl oder Bandbreite | 🔴 blockiert |
| A2 | Vermittlungsquote Juli + August | zwei Prozentwerte | 🔴 blockiert |
| A3 | Status der Stufe „New Lead" | abgeschafft oder defekt? | 🔴 blockiert |
| A4 | Ansprechpartner Salesforce-Schnittstelle + was sich zum 01.07. geändert hat | Name + kurze Antwort | 🔴 blockiert |
| B1 | Bestätigung oder Korrektur des Gebotsziels | kurze Antwort | 🟡 |
| B2 | Ablehnungsgründe Bewerbung → qualifiziert | Salesforce-Export, 3 Monate | 🟡 |
| B3 | Ampel-Liste Arbeitgeberbedarf je Gewerk | Liste | 🟡 |
| B4 | Status der 4 Perspective-Landingpages | in Betrieb ja/nein | 🟡 |
| C1 | Saisonalität des Geschäfts | Stichpunkte | ⚪ |
| C2 | andere Recruiting-Kanäle | Stichpunkte | ⚪ |
| C3 | Budgetrahmen 10k | ja / nein / später | ⚪ |

---

## Interne Notizen (nicht mit rausschicken)

- **A1 = GAP-1**, A2 = die Quotenhälfte von GAP-1, A3 = GAP-4, B1 = GAP-2, B2 = GAP-3,
  B3 = GAP-7, C1 = GAP-8, C2 = GAP-9, C3 = GAP-6 (offen für >8,5k).
- **Die Break-even-Schwelle in `business.md` §2.3 (278 CHF) ist überholt.** Sie basiert auf der
  alten Vermittlungsquote von 18,1 %. Bei der Juli-Quote von 9,1 % liegt sie bei **485 CHF**
  (eigene Rechnung 27.08.: Konto-CPA 44,13 über 14 T ÷ 0,091). `business.md` muss nachgeführt werden.
- **B3 ist die Frage mit dem grössten Sprengstoff:** Guardrail #10 („keine Profession pausieren",
  Kundenwunsch) hält die vier Nullkampagnen am Leben. Wenn Kollabo bestätigt, dass dort kein
  Arbeitgeberbedarf besteht, ist das die Freigabe, den Guardrail für diese Gewerke aufzuheben.
- **A4 nicht als Vorwurf formulieren** — die Ursache kann genauso gut bei uns oder im
  Google-Import liegen. Ziel ist der Ansprechpartner, nicht die Schuldfrage.
- Nicht gefragt, weil unsere Baustelle: Auto-Apply, Budgetumschichtung, Keyword-Struktur.
