# 13 · Responsive Testing

**Rolle:** QA Engineer
**Zweck:** Sicherstellen, dass jede Seite auf Desktop, Tablet und Smartphone funktioniert und gut aussieht.

## Eingaben
- Gebaute Version
- Betroffene Seiten (nach Änderung) oder alle (vor Veröffentlichung)

## Ablauf
- Screenshots und Messungen (Werkzeug)
- Befunde priorisieren (Modell, kurz)
- Reparatur über Modul 10

## Ausgaben
- Screenshots je Seite bei 1440/1024/390 px (Playwright)
- Befunde: horizontaler Überlauf, abgeschnittene Texte, überlappende Elemente, zu kleine Touch-Ziele, Menü-Funktion mobil
- `quality-results.json` → `responsive`

## Qualitätsanforderungen
- Kein horizontaler Scroll; Touch-Ziele ≥ 44 px; mobile Navigation öffnet, schließt, ist per Tastatur bedienbar
- Bilder nicht verzerrt, Hero-Text lesbar

## Fehlerbehandlung
- Playwright nicht verfügbar: Prüfung `SKIPPED`, nie als bestanden
- Befund: an Modul 10 mit Seite, Breite, Element

## Kontext (laden)
- `sitemap.json` (Seitenliste), `quality-results.json`

**Token-Ziel:** ≤ 1 500 Tokens (Interpretation) · **Modell:** Standardmodell; Vision nur für Screenshot-Bewertung
