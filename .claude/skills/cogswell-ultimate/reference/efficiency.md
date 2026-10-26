# Pro Efficiency Mode

Tokens, Kontextfenster, Tool-Aufrufe und Modellnutzung sind begrenzt. Ziel: höchste Designqualität je verbrauchter Ressource. Qualitäts- und Sicherheitsprüfungen werden nie gekürzt.

## Regeln

1. Nur relevante Dateien lesen; `component-index.json` sagt welche. Kein Repository-Dump, kein `cat` ganzer Ordner.
2. Keine wiederholten Analysen: Was in `.cogswell/` steht, wird nicht neu hergeleitet.
3. Keine Komplettgenerierung ohne Auftrag oder technischen Grund. Gründe sind: Wechsel der Creative Direction, defekte Projektstruktur, ausdrücklicher Wunsch.
4. Keine Subagenten für Aufgaben, die eine Sitzung sequentiell erledigt. Parallelität nur für unabhängige Prüfungen (z. B. drei Konzepte bauen).
5. Keine identischen Analysen parallel.
6. Logs knapp: eine Zeile pro Entscheidung. Erklärungen gehören in die Antwort an den Mitarbeiter, nicht ins Log.
7. Nur die vom Router genannten Module laden.
8. Kleine Änderungen deterministisch (Token-Engine, Text-Engine).
9. Bestehende Bausteine und Vorlagen zuerst; neue Komponenten nur, wenn die Bibliothek nichts Passendes hat.
10. Große Tool-Ausgaben kürzen (Build-Logs auf Fehlerzeilen, Screenshots statt DOM-Dumps).

## Targeted Editing

1. Absicht erkennen (Router).
2. Betroffene Komponenten aus `component-index.json` bestimmen.
3. Nur diese Dateien plus `brand-system.json` laden.
4. Minimale Änderung planen: welche Datei, welche Zeilen, was bleibt unberührt.
5. Änderung durchführen (vollständige Datei zurückgeben, keine Platzhalter).
6. Relevante Tests ausführen (unten).
7. Ergebnis in der Preview zeigen.
8. `project-summary.md`, `component-index.json`, `workflow-state.json` aktualisieren.

## Relevante Tests nach Änderung

| Änderung | Pflicht | Nicht nötig |
| --- | --- | --- |
| Token (Farbe, Schrift) | Build, Kontrastprüfung (axe) der betroffenen Seiten | Link-, SEO-, Formular-Tests |
| Text | Build, SEO der Seite (Titel/Meta, wenn geändert) | Responsive-Screenshots aller Seiten |
| Sektion/Komponente | Build, Typecheck, Responsive der Seite, axe der Seite | SEO-Gesamtlauf |
| Neue Seite | Build, Typecheck, Links, SEO der Seite, Responsive, axe | Komplett-Performance |
| Navigation/Layout | Build, Responsive aller Seiten, axe | SEO-Inhalte |
| Vor Veröffentlichung | alles (Modul 17) | – |

## Was nie gespart wird

Build-Prüfung, Secret-Scan, Pfadprüfung, Consent- und Rechtsprüfung, menschliche Freigabe.

## Messung

Jeder Lauf zählt: AI-Aufrufe, Eingabe-/Ausgabetokens, geladene Dateien, Tool-Aufrufe, Komplettregenerationen, fehlgeschlagene Generierungen, wiederverwendete Komponenten, bestandene Prüfungen. Die Suite schreibt diese Werte in `workflow-state.json` → `metrics`. Es werden keine prozentualen Einsparungen behauptet, die nicht gemessen wurden.

## Validierung mit drei Beispielwebsites

Die Szenarien liegen in `scripts/ultimate/scenarios/{handwerk,architektur,beratung}.json` (Schreinerei, Architekturbüro, Beratungsunternehmen), jeweils mit Briefing, Tarif und drei Chat-Änderungen. Ablauf je Szenario: Projekt anlegen → Briefing → Pipeline bis Freigabe (`pnpm ultimate:drive` oder `pnpm ultimate:scenario`) → Chat-Änderungen (`pnpm ultimate:chat <projectId> "<Anweisung>" …`) → Messwerte (`pnpm ultimate:measure`, `scripts/ultimate/report-data.ts`). Ergebnisse und Befunde stehen in `docs/ultimate-efficiency-report.md`. Noch offen: ein Vergleichslauf ohne Sparmodus (volle Dateiladung, Komplettregeneration je Änderung), ohne den keine Ersparnis beziffert wird.

## Geprüfte Zusatzwerkzeuge: Heimdall, Caveman

- **Heimdall MCP** (projektübergreifendes Gedächtnis): geprüft, nicht eingebunden. Die Smart Context Engine (`.cogswell/`, acht Dateien) deckt das Projektgedächtnis ab; ein zweiter Speicher wäre redundant und müsste synchron gehalten werden. Einbindung nur, wenn eine Messung an den drei Szenarien weniger geladene Tokens bei gleicher Ergebnisqualität zeigt.
- **Caveman** (knappe Antwortform): geprüft, nicht eingebunden. Die Status-Texte (`status-copy.md`) sind bereits knapp; Kundentexte dürfen nicht verkürzt werden. Einbindung nur für interne Logs, wenn eine Messung weniger Ausgabetokens ohne Informationsverlust zeigt.
- Beide bleiben in der Registry (`reference/skills.md`) als „geprüft, nicht aktiv“ geführt; die Messung ist ein offener Auftrag, kein Versprechen.
