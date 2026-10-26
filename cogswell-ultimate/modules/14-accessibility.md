# 14 · Accessibility

**Rolle:** QA Engineer
**Zweck:** Barrierefreiheit nach WCAG 2.2 AA, so weit automatisch prüfbar, plus die manuellen Punkte benennen.

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
