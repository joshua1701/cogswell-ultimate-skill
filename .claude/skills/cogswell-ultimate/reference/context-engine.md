# Smart Context Engine: `.cogswell/`

Das Projektgedächtnis liegt im Workspace jedes Projekts (`WORKSPACES_DIR/<projectId>/.cogswell/`) und in der Datenbank (`ProjectMemory`). Die Suite schreibt es nach jedem abgeschlossenen Schritt; Claude liest nur die Dateien, die der Router nennt.

| Datei | Inhalt | Wer schreibt | Größe (Ziel) |
| --- | --- | --- | --- |
| `project-summary.md` | Kunde, Branche, Ziel, Zielgruppe, Tonalität, Stand, offene Entscheidungen, letzte drei Änderungen | Suite nach jedem Schritt; Claude ergänzt „Entscheidungen“ | ≤ 1 500 Zeichen |
| `brand-system.json` | Palette, Schriften, Logo-Pfade, Logo-Regeln, Kontrastwerte | Brand Intelligence, Token-Engine | ≤ 2 KB |
| `design-decisions.json` | Creative Direction (Leitidee, Layout-Key, Stil-Key, Hero-Typ, Navigation, Bildsprache, Animationsregeln), gewähltes Konzept, Review-Verdikt | Creative Direction, Konzeptauswahl, Design Critic | ≤ 4 KB |
| `sitemap.json` | Seiten mit Pfad, Titel, Zweck, Status, Sektionen (ids) | Website Architecture, Content | ≤ 4 KB |
| `component-index.json` | je Sektion: Datei, Exportname, verwendete Bausteine, Design-Token-Bindungen, Assets, Seite | Website Generation, Editing (nach jeder Version) | ≤ 8 KB |
| `asset-manifest.json` | Logo, Bilder mit Pfad, Maßen, Lizenz, Alt-Text, Zuordnung zu Seiten/Sektionen | Asset-Verwaltung | ≤ 4 KB |
| `workflow-state.json` | Schritte mit Status, Version, Zeitstempel, Modell, Tokens, offenen Freigaben, Metriken | Workflow-Engine | ≤ 4 KB |
| `quality-results.json` | letzte Ergebnisse je Prüfung (Status, Anzahl Befunde, Top-Befunde), Design-Review-Scores | QA, SEO, Design Critic | ≤ 4 KB |

## Leseprotokoll

- Lies zuerst `workflow-state.json` (wo stehen wir), dann die vom Router genannten Dateien.
- Lade eine Komponentendatei erst, wenn `component-index.json` sie als betroffen ausweist.
- Lade nie `quality-results.json` vollständig für eine Designfrage und nie `component-index.json` für eine SEO-Frage.

## Schreibprotokoll

- Nach jeder abgeschlossenen Aufgabe: betroffene Dateien aktualisieren, `project-summary.md` → „Letzte Änderungen“ um eine Zeile ergänzen (älteste fällt heraus).
- Entscheidungen des Mitarbeiters (gewähltes Konzept, abgelehnte Vorschläge, bestätigte Fakten) stehen in `project-summary.md` → „Entscheidungen“ und gehen nie verloren, auch nicht bei `/compact`.
- Freigaben werden nur von der Suite geschrieben (`workflow-state.json` → `approvals`), nie von Claude.

## Beispiel: „Mach den Header moderner.“

Laden: `component-index.json` (→ `src/components/generated/SiteHeaderNav.tsx`), diese Datei, `brand-system.json`, `design-decisions.json` (Navigation, Layout-Key). Nicht laden: Blog, andere Seiten, Chatverlauf, SEO-Berichte.
