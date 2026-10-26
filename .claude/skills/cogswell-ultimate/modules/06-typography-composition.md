# 06 · Typography & Composition

**Rolle:** UX/UI Designer
**Zweck:** Typografie und Komposition einer Seite oder Sektion so festlegen, dass Hierarchie, Rhythmus und Lesbarkeit stimmen.

## Eingaben
- `design-decisions.json` (Layout-Key, Stil-Key, Hero-Typ)
- Inhalt der Seite/Sektion (`sitemap.json` → Sektionen)
- Bibliothek der Layoutarchitektur

## Ablauf
- Architekturregeln lesen
- Plan für genau die angefragte Seite/Sektion schreiben
- An Modul 09/10 übergeben

## Ausgaben
- Kompositionsplan: Sektionsreihenfolge, Spalten, Bildplätze, Größenstufen, Weißraum, Umbrüche (balance), Mobile-Verhalten
- Typografische Skala als `clamp()`-Werte, Zeilenlängen (45–75 Zeichen), Zeilenhöhen

## Qualitätsanforderungen
- Eine dominante Überschrift pro Viewport
- Fließtext mobil ≥ 17 px, Überschriften fluid, keine abgeschnittenen Wörter
- Nie dieselbe Sektionsreihenfolge auf zwei Seiten
- Abstände aus dem Spacing-System, keine Einzelwerte

## Fehlerbehandlung
- Inhalt zu lang für die Komposition: kürzen vorschlagen (Modul 07), nicht Schrift verkleinern
- Bild fehlt: Platzhalter mit Bildanweisung im Alt-Text, kein Stock-Klischee

## Kontext (laden)
- `design-decisions.json`, betroffene Sektionen aus `sitemap.json`

**Token-Ziel:** ≤ 2 500 Tokens · **Modell:** Standardmodell
