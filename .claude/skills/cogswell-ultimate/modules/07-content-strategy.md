# 07 · Content Strategy

**Rolle:** Creative Director + SEO Specialist
**Zweck:** Texte, die aus dem Briefing kommen, in der Tonalität des Kunden, mit SEO-Grundlagen und ohne erfundene Aussagen.

## Eingaben
- Briefing, Analyse (Keywords, Suchintention), Sitemap
- Kompositionsplan (Modul 06) für Längenvorgaben

## Ablauf
- Nur angefragte Seiten bearbeiten
- Ergebnis validieren (Längen, Markierungen)
- In `ProjectPage.content` speichern

## Ausgaben
- Je Seite `pageContentSchema`: SEO-Titel (≤ 60), Meta-Description (≤ 155), H1, Sektionen mit Überschrift und Text, CTAs, interne Links, Schema.org-Typ, `unconfirmedClaims`
- Statusaktualisierung in `sitemap.json`

## Qualitätsanforderungen
- Jede Zahl, jedes Zertifikat, jede Bewertung, jede Öffnungszeit ohne Beleg steht in `unconfirmedClaims` und im Text als `[zu bestätigen]`
- Pro Seite ein Hauptkeyword, natürlich eingebettet; keine Keyword-Wiederholungen
- Rechtstexte nur als Struktur mit `[PRÜFEN]`
- Texte in der Tonalität aus `brand-system.json`

## Fehlerbehandlung
- Briefing liefert zu wenig für eine Seite: kurze Struktur mit Fragen statt Füllsätze
- Kunde liefert eigene Texte: übernehmen, nur SEO-Elemente ergänzen, nichts umschreiben ohne Auftrag

## Kontext (laden)
- `project-summary.md`, `sitemap.json`, betroffene Seite(n)

**Token-Ziel:** ≤ 3 000 Tokens je Seite · **Modell:** Standardmodell
