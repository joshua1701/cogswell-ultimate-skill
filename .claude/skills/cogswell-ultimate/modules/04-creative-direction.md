# 04 · Creative Direction

**Rolle:** Creative Director
**Zweck:** Eine Leitidee, die alle weiteren Entscheidungen trägt: Layoutarchitektur, Stil, Hero-Typ, Navigation, Bildsprache, Bewegung.

## Eingaben
- Briefing-Zusammenfassung, Analyse, `brand-system.json`
- Referenzen aus Modul 03
- Layout- und Stilbibliothek (`layouts.ts`, `styles.ts`) als Datenblock
- Anti-Generic-Regeln

## Ablauf
- Bibliotheken und Referenzen lesen
- Richtung formulieren (Modell, strukturiert)
- Mitarbeiter gibt frei oder korrigiert (Freigabe-Schritt `direction`)

## Ausgaben
- `CreativeDirection` (Zod `creativeDirectionSchema`): Konzept in zwei Sätzen, Leitidee, `layoutKey`, `styleKey`, Hero-Typ, Navigationsmuster, Typografie-Richtung, Farbstrategie, Bildsprache mit Bildanweisungen, Raster/Spacing, Animationsregeln, Komponentencharakter, Mobile-Regeln, begründete Abweichungen von den Anti-Generic-Regeln
- `design-decisions.json` aktualisiert

## Qualitätsanforderungen
- Die Leitidee ist in einem Satz sagbar und aus dem Geschäft des Kunden hergeleitet
- Genau ein `layoutKey` und ein `styleKey`; Mischungen nur begründet
- Jede Anti-Generic-Regel, die bewusst gebrochen wird, steht mit Begründung im Ergebnis
- Kein Stil, der dem Kunden laut Briefing widerspricht

## Fehlerbehandlung
- Briefing zu dünn für eine Richtung: zwei kurze Fragen an den Mitarbeiter statt zu raten
- Kunde hat harte Farbvorgaben mit schlechtem Kontrast: Vorgabe behalten, Textfarben korrigieren, Hinweis dokumentieren
- Modell liefert Standardlösung (zentrierter Hero, drei Karten): einmal mit Verweis auf Regel 1 und 3 neu anfordern

## Kontext (laden)
- `project-summary.md`, `brand-system.json`
- Referenzen (Modul 03), Bibliotheken als Datenblock

**Token-Ziel:** ≤ 6 000 Tokens · **Modell:** stärkstes im Tarif erlaubtes Modell (Business/First), sonst Standard
