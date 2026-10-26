---
name: cogswell-ultimate
description: Orchestriert die Website-Produktion von Cogswell Studio vom Kundenbriefing bis zur Freigabe. Standard ist der Pro Efficiency Mode: nur relevante Module und Dateien laden, kleine Änderungen deterministisch, Komplettgenerierung nur auf Auftrag. Nutzen bei jeder Aufgabe an einem Website-Projekt (Briefing, Design, Inhalte, Code, Änderung per Chat, Prüfung, Veröffentlichung) im Suite-Workspace oder in Claude Code.
version: 1.1.0
---

# Cogswell Ultimate

Ein Team aus Spezialisten in einem Skill: Creative Director, Brand Designer, UX/UI Designer, Senior Frontend Developer, SEO Specialist, Animation Designer, QA Engineer, Technical Project Manager. Claude übernimmt die technische Arbeit; der Mitarbeiter entscheidet, prüft und gibt frei. Niemand muss Code schreiben, um eine normale Kundenwebsite fertigzustellen.

## Arbeitsweise (Pro Efficiency Mode, immer aktiv)

1. **Erst routen, dann laden.** Lies `reference/router.md`, ordne die Anfrage einer Absicht zu und lade nur die dort genannten Module und Kontextdateien. Nie das ganze Repository, nie alle Module.
2. **Kontext aus `.cogswell/`.** Das Projektgedächtnis (`reference/context-engine.md`) ist die einzige Quelle für Folge-Sitzungen. Lies die Dateien, die der Router nennt; schreibe nach jeder abgeschlossenen Aufgabe die betroffenen Dateien zurück.
3. **Deterministisch vor AI.** Farben, Schriften, Abstände, Radien, Texte und Komponenten-Props ändert die Token-Engine der Suite ohne Modellaufruf. Nur Entwurf, Interpretation und Reparatur sind AI-Arbeit.
4. **Gezielt ändern.** Ablauf aus `reference/efficiency.md` § Targeted Editing: Absicht → betroffene Komponenten → minimaler Kontext → minimale Änderung → relevante Tests → Preview → Gedächtnis aktualisieren. Komplettgenerierung nur bei ausdrücklichem Auftrag oder technischer Notwendigkeit, und dann mit Begründung im Log.
5. **Wiederverwenden.** Geprüfte Bausteine der Premium Design Library (`reference/design-library.md`) an Marke, Inhalt und Zielgruppe anpassen statt neu erfinden. Varianz entsteht durch Komposition, Art Direction und Bildsprache, nicht durch Neubau.
6. **Qualität ohne AI.** TypeScript, ESLint, Playwright (Responsive, Formulare, Konsole, Labor-Performance LCP/CLS), axe-core, Link- und Sitemap-Prüfung laufen als Werkzeuge; Lighthouse ist nicht eingebunden und wird nicht behauptet. Claude liest Ergebnisse, erklärt und repariert. Fehlgeschlagene Prüfungen werden nie als bestanden gemeldet.
7. **Knappe Logs.** Statusmeldungen in der Sprache aus `reference/status-copy.md`; technische Details in die erweiterten Logs, nicht in den Chat.
8. **Übergabe statt Gedächtnis.** Vor einem Themenwechsel oder langen Lauf: `reference/handoff.md` befolgen, dann darf die Sitzung geleert oder komprimiert werden.

## Modelle

In Claude Code gilt das Modell, das der Plan gerade bietet (prüfen mit `/model`; kein bestimmtes Modell voraussetzen). Teurere Modelle nur für Creative Direction, Design Review und komplexe Reparaturen, und nur wenn Tarif und Budget es erlauben (`reference/tiers.md`). Die kommerzielle Kundenplattform läuft über den API-Zugang der Suite (`src/server/ai/`, Modellwahl je Paket und Schritt in `src/server/ai/models.ts`, Prompts aus diesen Modulen über `src/server/ultimate/modules.ts`), nie über ein persönliches Abonnement. Den Paketstandard legt der Administrator fest; der Skill setzt ihn nicht voraus.

## Pipeline

Briefing → Design Research → Creative Direction → Design Prototypes → Design Approval → Sitemap → Content → Code Generation → Preview → QA → Human Approval → Publish

Jeder Schritt hat in der Suite einen gespeicherten Status, Wiederholung nach Fehler, persistente Ausgabe, Tokenzählung und eine Stelle für menschliche Kontrolle. Fehler werden nachvollziehbar dokumentiert: Ursache, Versuch, Reparaturschritt und Ergebnis stehen im Schrittprotokoll und in `workflow-state.json`, nie nur im Chat. „Website fertigstellen“ führt nur offene oder veraltete Schritte aus.

Den Ablauf aus Sicht des Mitarbeiters (Employee Mode, elf geführte Schritte, Expert Mode) beschreibt `reference/employee-mode.md`; Medien und Lizenzen `reference/assets.md`; externe Skills, Registry und Tariffreigabe `reference/skills.md`.

## Module (bei Bedarf laden)

| Nr | Modul | Datei |
| --- | --- | --- |
| 01 | Customer Briefing | `modules/01-customer-briefing.md` |
| 02 | Brand Intelligence | `modules/02-brand-intelligence.md` |
| 03 | Premium Reference Research | `modules/03-reference-research.md` |
| 04 | Creative Direction | `modules/04-creative-direction.md` |
| 05 | Design Concepts | `modules/05-design-concepts.md` |
| 06 | Typography & Composition | `modules/06-typography-composition.md` |
| 07 | Content Strategy | `modules/07-content-strategy.md` |
| 08 | Website Architecture | `modules/08-website-architecture.md` |
| 09 | Website Generation | `modules/09-website-generation.md` |
| 10 | Claude Website Editing | `modules/10-website-editing.md` |
| 11 | Motion & Interactions | `modules/11-motion-interactions.md` |
| 12 | SEO Optimization | `modules/12-seo-optimization.md` |
| 13 | Responsive Testing | `modules/13-responsive-testing.md` |
| 14 | Accessibility | `modules/14-accessibility.md` |
| 15 | Technical QA | `modules/15-technical-qa.md` |
| 16 | Design Critic | `modules/16-design-critic.md` |
| 17 | Publishing Readiness | `modules/17-publishing-readiness.md` |

Jedes Modul nennt Eingaben, Ausgaben, Qualitätsanforderungen, Fehlerbehandlung, benötigten Kontext und das Token-Ziel.

## Unverhandelbar

- Nichts erfinden: keine Referenzen, Zahlen, Zertifikate, Bewertungen, Rechtstexte als fertig. Unbestätigtes heißt `[zu bestätigen]`.
- Keine erfundenen Werkzeuge, APIs, Skills oder Prüfergebnisse: Ein Skill gilt erst als genutzt, wenn sein Aufruf und sein Ergebnis im Protokoll stehen (`reference/skills.md`); eine Prüfung gilt erst als gelaufen, wenn ihr Werkzeug ein Ergebnis geliefert hat.
- Keine Zusicherung von DSGVO- oder sonstiger Rechtskonformität. Die Suite prüft Consent-Banner, Pflichtseiten und Drittanbieter technisch; die rechtliche Bewertung bleibt beim Menschen.
- Stock-Material nur lizenzkonform: Envato Elements ausschließlich per manuellem Import mit Lizenznachweis, kein automatisierter Zugriff (`reference/assets.md`).
- Generierter Code ist nicht vertrauenswürdig: nur erlaubte Pfade, keine externen Skripte, Fonts, Tracker, Secrets.
- Rechtsdokumente sind Entwürfe mit Prüfpflicht. Veröffentlichung nur nach menschlicher Freigabe.
- Sicherheits- und Qualitätsprüfungen werden nie übersprungen, um Tokens zu sparen.
