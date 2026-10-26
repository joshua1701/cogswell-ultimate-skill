# 05 · Design Concepts

**Rolle:** UX/UI Designer
**Zweck:** Drei klar unterschiedliche, renderbare Konzepte zur Auswahl; danach genau eines weiterbauen.

## Eingaben
- Freigegebene Creative Direction
- `brand-system.json`
- Tarif (Economy: 1 Konzept, Business/First: 3)

## Ablauf
- Konzepte erzeugen (ein Modellaufruf pro Konzept, parallel erlaubt)
- Deterministische Vorschau rendern, Validierung (Kontrast, Anti-Generic)
- Auswahl durch Mitarbeiter (Freigabe-Schritt `concepts`)

## Ausgaben
- Je Konzept: Name, Designsystem (`designSystemOutputSchema` erweitert um Hero, Navigation, Beispielsektionen), Begründung, Desktop- und Mobile-Vorschau
- Vorschau-Rendering: Sparmodus = deterministische Konzeptkarte aus den Tokens (Hero, Navigation, Typografie-Probe, Buttons, Karte) ohne Build; First = zusätzlich echter Build der Startseite
- Auswahl oder Kombination des Mitarbeiters in `design-decisions.json` → `concept`

## Qualitätsanforderungen
- Die drei Konzepte unterscheiden sich in mindestens zwei von: Layoutarchitektur, Hero-Typ, Schriftpaarung, Farbstrategie
- Alle drei erfüllen Kontrast und Anti-Generic-Regeln; ein Konzept, das sie verletzt, wird nicht angeboten
- Jede Vorschau zeigt echte Texte aus dem Briefing, keine Lorem-ipsum-Flächen

## Fehlerbehandlung
- Ein Konzept scheitert an der Validierung: nur die anderen anbieten, Fehler loggen, nicht stillschweigend ein Standardkonzept einsetzen
- Mitarbeiter will Eigenschaften mischen: Kombination deterministisch zusammenführen (Tokens), nur bei Layoutwechsel Modell
- Build einer Konzept-Startseite schlägt fehl (First): Konzept als „Vorschau ohne Build“ zeigen, Fehler ins Log

## Kontext (laden)
- `design-decisions.json`, `brand-system.json`

**Token-Ziel:** ≤ 4 000 Tokens je Konzept · **Modell:** Standardmodell
