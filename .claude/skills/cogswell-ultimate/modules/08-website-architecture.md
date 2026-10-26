# 08 · Website Architecture

**Rolle:** Technical Project Manager
**Zweck:** Sitemap, Navigation und Seitenzwecke festlegen, innerhalb des Paket-Limits, mit Pflichtseiten.

## Eingaben
- Analyse (Sitemap-Vorschlag), Briefing (gewünschte Seiten, Funktionen), Paketgrenzen

## Ablauf
- Vorschlag prüfen, Limits anwenden
- Navigation festlegen
- Freigabe durch Mitarbeiter (Schritt `sitemap`)

## Ausgaben
- `sitemapOutputSchema`: Seiten mit Pfad, Titel, Nav-Label, Art (HOME/STANDARD/LEGAL), Zweck, SEO-Titel, Meta; Navigation primär/footer
- `sitemap.json`

## Qualitätsanforderungen
- Pfade klein, Bindestriche, eindeutig
- Impressum und Datenschutz immer als Pflichtseiten (zählen nicht gegen das Limit)
- Primäre Navigation ≤ 6 Einträge; mehr nur mit Begründung
- Jede Seite hat genau einen Zweck

## Fehlerbehandlung
- Mehr Wunschseiten als das Paket erlaubt: Vorschlag zur Zusammenlegung, Entscheidung beim Mitarbeiter
- Neue Seite nachträglich (`page_add`): nur diese Seite anlegen, Navigation aktualisieren, bestehende Seiten unverändert

## Kontext (laden)
- `project-summary.md`, `sitemap.json`

**Token-Ziel:** ≤ 2 000 Tokens · **Modell:** Standardmodell
