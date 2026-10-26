# 02 · Brand Intelligence

**Rolle:** Brand Designer
**Zweck:** Die vorhandene Marke verstehen und als Regeln festhalten, bevor etwas gestaltet wird.

## Eingaben
- Logo-Datei(en) aus dem Asset-Manifest
- Briefing-Felder Farben, Stil, Tonalität, Referenzen
- Bestehende Website des Kunden (nur Beschreibung durch den Mitarbeiter, kein Scraping)

## Ablauf
- Logo prüfen und Farben messen (Suite)
- Palette ableiten, Kontraste berechnen
- Regeln schreiben, in `brand-system.json` ablegen

## Ausgaben
- `brand-system.json`: Logofarben (gemessen), empfohlene Palette mit Kontrastwerten, Logo-Regeln (Mindesthöhe, Freiraum, Hintergrund hell/dunkel), Tonalität in drei Adjektiven
- Hinweis, ob das Logo Dark- und Light-Variante braucht

## Qualitätsanforderungen
- Farben aus dem Logo werden gemessen (Bitmap-Analyse der Suite), nicht geschätzt
- Jede Text-/Hintergrund-Kombination ≥ 4.5:1 (WCAG AA); Ausnahmen begründet
- Keine Markenaussagen erfinden; was der Kunde nicht sagt, steht als offene Frage

## Fehlerbehandlung
- Kein Logo: Wortmarke aus der Schriftpaarung vorschlagen, als `[zu bestätigen]` markieren
- SVG mit Skripten oder externen Referenzen: ablehnen, Mitarbeiter informieren
- Logo zu klein/unscharf: Hinweis an Kunden, Platzhalter mit korrekter Größe

## Kontext (laden)
- `asset-manifest.json`
- Briefing-Felder Farben/Stil/Tonalität

**Token-Ziel:** ≤ 2 000 Tokens · **Modell:** deterministisch (Farbanalyse) + Standardmodell für die Regeln
