# 15 · Technical QA

**Rolle:** QA Engineer
**Zweck:** Build, Typen, Lint, Links, Formulare, Performance und Sicherheit als harte Fakten, mit begrenzter automatischer Reparatur.

## Eingaben
- Version (Dateien), Build-Log (gekürzt auf Fehlerzeilen), Artefakt

## Ablauf
- Werkzeuge laufen lassen (kein Modell)
- Nur bei Fehlern: Interpretation und Reparatur (Modell)
- Ergebnis speichern, Preview nur bei Erfolg

## Ausgaben
- `QualityCheck`-Zeilen: build, typescript, eslint, links, forms, console, performance, security
- Reparaturvorschlag mit betroffener Datei bei rotem Build (max. 2 Runden automatisch)
- `quality-results.json` → `qa`

## Qualitätsanforderungen
- Build grün ist Pflicht; nichts wird ohne grünen Build vorgeschaut oder veröffentlicht
- Fehlgeschlagene Prüfungen bleiben rot; keine Umdeutung
- Performance als Labordaten (LCP, CLS) aus dem Playwright-Lauf, als Labor gekennzeichnet; Lighthouse ist nicht eingebunden

## Fehlerbehandlung
- Build rot: Fehlerzeilen lesen, kleinste Reparatur, erneut bauen; nach 2 Runden Mitarbeiter mit verständlicher Erklärung (`status-copy.md`) und Rollback-Angebot
- Container nicht erreichbar: klarer Hinweis, keine Prüfung als bestanden markieren

## Kontext (laden)
- Build-Log (gekürzt), betroffene Dateien

**Token-Ziel:** ≤ 3 000 Tokens je Reparaturrunde · **Modell:** Standardmodell
