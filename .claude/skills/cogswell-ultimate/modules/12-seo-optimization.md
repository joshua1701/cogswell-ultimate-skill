# 12 · SEO Optimization

**Rolle:** SEO Specialist
**Zweck:** Technische und inhaltliche SEO-Grundlagen als messbare Ergebnisse, Empfehlungen getrennt davon.

## Eingaben
- Gebaute Version (Artefakt), `sitemap.json`, Seiteninhalte
- Prüfregeln der Suite (`src/server/quality/rules.ts`)

## Ablauf
- Automatische Prüfung (kein Modell)
- Interpretation und Priorisierung der Befunde (Modell, kurz)
- Reparaturen über Modul 07/10

## Ausgaben
- `SEOReport`: automatische Prüfungen je Seite (Titel, Meta, H-Struktur, Canonical, lang, Open Graph, Structured Data, Alt-Texte, interne Links, Wortzahl) und Site (robots, sitemap, Abdeckung), Score
- Empfehlungen (Modell) klar als „menschliche Bewertung nötig“ markiert
- `quality-results.json` → `seo`

## Qualitätsanforderungen
- Nur echte Messwerte; was nicht gemessen werden kann, ist `SKIPPED` mit Grund
- Keine Ranking-Versprechen
- Core Web Vitals nur mit Labordaten der Suite, als solche gekennzeichnet

## Fehlerbehandlung
- Seite nicht gebaut: Prüfung überspringen, Build anfordern
- Befund auf Inhalt (zu kurz, kein Keyword): an Modul 07 mit genauer Stelle

## Kontext (laden)
- `sitemap.json`, `quality-results.json`, betroffene Seite

**Token-Ziel:** ≤ 2 000 Tokens (nur Interpretation) · **Modell:** Standardmodell
