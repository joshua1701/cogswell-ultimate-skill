# 10 · Claude Website Editing

**Rolle:** Senior Frontend Developer
**Zweck:** Gezielte Änderungen an bestehenden Dateien auf Zuruf, versioniert, nach Build in der Preview.

## Eingaben
- Anweisung des Mitarbeiters (Chat)
- Router-Ergebnis (Absicht, betroffene Komponenten)
- Betroffene Dateien, `brand-system.json`, ggf. `asset-manifest.json`

## Ablauf
- Absicht und Komponenten bestätigen (Router)
- Deterministisch, wenn möglich; sonst Modell mit minimalem Kontext
- Patch validieren, Version, Build, relevante Tests, Preview, Gedächtnis

## Ausgaben
- Patches (`revisionOutputSchema`): vollständige Dateien für geänderte/neue Dateien, Löschungen nur auf Auftrag, Zusammenfassung in 1–3 Sätzen
- Neue `ProjectVersion` (Quelle REVISION) → Build → Preview
- `component-index.json`, `project-summary.md` → Letzte Änderungen

## Qualitätsanforderungen
- Nur die betroffenen Dateien ändern; unveränderte nicht zurückgeben
- Geschützte Template-Dateien (layout.tsx, globals.css, site.ts, tokens.css, Pflichtseiten) bleiben tabu; wenn nötig, in `notes` erklären
- Die Template-Bausteine `src/components/site/Header.tsx`, `Footer.tsx`, `Reveal.tsx` sind überschreibbar: vollständige Datei unter demselben Pfad zurückgeben, das Projekt überlagert das Template. Header-, Navigations-, Logo- und Footer-Anweisungen werden so umgesetzt, nie abgelehnt
- Gezielte Änderung (Ziele bekannt): nur Zieldateien, deren Verwender und Pfadtreffer laden (max. 6 Dateien, 40k Zeichen); Template-Bausteine zählen dazu
- Nach der Änderung nur die relevanten Tests (`efficiency.md`)
- Keine stillen Nebenänderungen (Texte, Farben, Reihenfolge) außerhalb der Anweisung

## Fehlerbehandlung
- Anweisung mehrdeutig („mach es schöner“): eine Rückfrage mit zwei konkreten Vorschlägen
- Änderung bräuchte eine geschützte Datei: Alternative vorschlagen (Token-Engine, Props)
- Build nach Änderung rot: automatische Reparatur (max. 2), sonst Rollback-Angebot
- Revisionslimit erreicht: Mitarbeiter informieren, Projektmanager kann erhöhen

## Kontext (laden)
- Router-Ergebnis; `component-index.json`; betroffene Dateien; `brand-system.json`

**Token-Ziel:** ≤ 4 000 Tokens je Änderung · **Modell:** Standardmodell; strukturelle Umbauten höher
