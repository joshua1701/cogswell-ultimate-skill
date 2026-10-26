# 14 · Accessibility

**Rolle:** QA Engineer
**Zweck:** Barrierefreiheit: axe-core prüft automatisch WCAG 2.1 A/AA (so meldet es die Suite); die zusätzlichen Punkte aus WCAG 2.2 (Fokus nicht verdeckt, Zielgröße 24 px, Ziehbewegungen mit Alternative, konsistente Hilfe) werden als manuelle Prüfpunkte benannt, nie als bestanden gemeldet.

## Eingaben
- Gebaute Version, betroffene Seiten

## Ablauf
- axe ausführen (Werkzeug)
- Befunde erklären und zuordnen
- Reparatur über Token-Engine oder Modul 10

## Ausgaben
- axe-core-Befunde je Seite (Regel, Element, Schwere)
- Manuelle Prüfpunkte: Fokusreihenfolge, Formular-Fehlermeldungen, Alt-Text-Qualität, Bewegung
- `quality-results.json` → `a11y`

## Qualitätsanforderungen
- Keine `critical`/`serious` Befunde vor Veröffentlichung
- Kontrast ≥ 4.5:1 (Text), ≥ 3:1 (große Schrift, UI)
- Jedes Formularfeld mit Label; sichtbarer Fokus

## Fehlerbehandlung
- Kontrastbefund durch Markenfarbe: Textfarbe anpassen (Token-Engine), Marke bleibt
- axe nicht lauffähig: `SKIPPED`, offen lassen

## Kontext (laden)
- `quality-results.json`, betroffene Komponente

**Token-Ziel:** ≤ 1 500 Tokens · **Modell:** Standardmodell
