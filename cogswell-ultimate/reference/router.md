# Skill Router

Ordne jede Anfrage genau einer Absicht zu. Lade nur die genannten Module (`modules/`) und Kontextdateien (`.cogswell/`). Bei Unsicherheit die kleinere Absicht wählen und nachfragen, nie „zur Sicherheit“ alles laden. Der Router der Suite (`src/server/ultimate/router.ts`) fällt ohne Treffer auf `section_restyle` zurück; in dem Fall stellt Claude vor der Änderung eine Rückfrage mit zwei konkreten Deutungen.

| Absicht | Erkennungsmerkmale | Deterministisch? | Module | Kontext aus `.cogswell/` |
| --- | --- | --- | --- | --- |
| `token_change` | Farbe, Schrift, Abstand, Radius, Schatten ändern („dunkler“, „mehr Luft“, „runder“) | **ja**, Token-Engine | keines | `brand-system.json`, `design-decisions.json` |
| `copy_change` | Text, Überschrift, Button-Label, Telefonnummer ändern | **ja**, wenn der Text eindeutig in genau einer Komponente steht | keines (sonst 10) | `component-index.json`, `sitemap.json` |
| `asset_change` | Logo größer/kleiner, Bild ersetzen, hochgeladene Bilder verwenden | teilweise (Zuordnung ja, Komposition nein) | 10, bei neuem Layout 06 | `asset-manifest.json`, `component-index.json`, `brand-system.json` |
| `section_add` | neue Sektion, neuer Bereich auf bestehender Seite | nein | 06, 09 (Bausteine), 10 | `design-decisions.json`, `component-index.json`, betroffene Seite in `sitemap.json` |
| `page_add` | neue Seite („Über uns“, „Karriere“) | nein | 08, 07, 09, 10 | `project-summary.md`, `sitemap.json`, `design-decisions.json`, `component-index.json` |
| `section_restyle` | „Header moderner“, „Hero hochwertiger“, „Animation dezenter“ | nein | 06, 11, 10 | betroffene Komponente, `brand-system.json`, `design-decisions.json` |
| `bug_mobile` | „auf dem Handy kaputt“, Menü, Überlappung | nein | 13, 10 | betroffene Komponente, `quality-results.json` |
| `bug_build` | Build fehlgeschlagen, Typfehler | nein | 15, 10 | Build-Log (gekürzt), betroffene Dateien |
| `seo_issue` | Titel, Meta, Sitemap, Ranking, strukturierte Daten | nein | 12 | `sitemap.json`, `quality-results.json`, betroffene Seite |
| `a11y_issue` | Kontrast, Tastatur, Screenreader | nein | 14, 10 | `quality-results.json`, betroffene Komponente |
| `redesign` | „komplett neu“, „ganz anderer Stil“, Kunde lehnt Richtung ab | nein, nur auf ausdrücklichen Auftrag | 03, 04, 05, 06, 16 | `project-summary.md`, `brand-system.json`, `design-decisions.json` |
| `new_project` | Briefing liegt vor, noch nichts generiert | nein | Pipeline 01 → 17 | wird angelegt |
| `finish` | „Website fertigstellen“, „was fehlt noch“ | Zustandsabgleich | nur die Module der offenen Schritte | `workflow-state.json`, `quality-results.json` |
| `question` | Erklärung, Status, „warum“ | ja (Cogswell Guide) | keines | `workflow-state.json`, `project-summary.md` |

## Regeln

- **Deterministisch zuerst.** Ergibt die Token- oder Text-Engine eine eindeutige Änderung, wird kein Modell gerufen. Erst wenn sie „nicht eindeutig“ meldet, geht die Anfrage an Modul 10.
- **Keine Doppelprüfungen.** Module 13, 14, 15 und 16 prüfen disjunkte Dinge. Nach einer gezielten Änderung laufen nur die Prüfungen, deren Gegenstand sich geändert hat (siehe `efficiency.md` § Relevante Tests).
- **Eine Komponente, eine Datei.** `component-index.json` sagt, welche Datei welche Sektion rendert. Lade diese Datei und ihre direkten Bausteine, nicht die Seite drumherum.
- **Kein Verlauf laden.** Frühere Chatnachrichten sind nicht Kontext; `project-summary.md` fasst Entscheidungen zusammen.
- **Eskalation nur mit Grund.** Wechsel von `section_restyle` zu `redesign` verlangt eine Rückfrage an den Mitarbeiter.
