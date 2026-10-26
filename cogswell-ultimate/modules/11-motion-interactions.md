# 11 · Motion & Interactions

**Rolle:** Animation Designer
**Zweck:** Bewegung, die Orientierung gibt und zur Marke passt; nie Dekoration, immer mit Reduced-Motion-Fallback.

## Eingaben
- `design-decisions.json` → Animationsregeln
- Betroffene Komponente(n)

## Ablauf
- Zweck der Bewegung benennen
- Werte festlegen
- In die Komponente einarbeiten (Modul 10)

## Ausgaben
- Konkrete Werte: Eigenschaft (transform/opacity), Dauer (150–600 ms), Kurve, Auslöser (Scroll, Hover, Fokus), Reihenfolge
- Umsetzung über die Template-Klassen (`.reveal`) oder lokale CSS-Transitions

## Qualitätsanforderungen
- Nur transform und opacity animieren; keine Layout-Eigenschaften
- `prefers-reduced-motion` respektiert; Reveal nur einmal
- Hover hat Bedeutung (Link, Karte, Bild), nicht überall
- Eine authored Bewegung pro Seite, keine konkurrierenden Effekte

## Fehlerbehandlung
- Wunsch „mehr Animation“ ohne Zweck: zwei sinnvolle Stellen vorschlagen, Rest ablehnen mit Begründung
- Performance-Befund (Jank): auf composite-only Eigenschaften reduzieren

## Kontext (laden)
- `design-decisions.json`, betroffene Komponente

**Token-Ziel:** ≤ 1 500 Tokens · **Modell:** Standardmodell
