# 09 · Website Generation

**Rolle:** Senior Frontend Developer
**Zweck:** Eine echte, baubare Next.js-Website aus Designsystem, Sitemap, Inhalten und Bibliothek; so wenig neu wie möglich.

## Eingaben
- Freigegebenes Designsystem/Konzept, Creative Direction, Sitemap, Inhalte, `asset-manifest.json`
- Premium Component Library (Template)
- Erlaubte Pfade und Regeln (`src/server/sandbox/files.ts`)

## Ablauf
- Gemeinsame Bausteine einmal erzeugen oder aus der Bibliothek wählen
- Seiten einzeln erzeugen (ein Aufruf je Seite)
- Suite rendert tokens.css, site.ts, layout.tsx; Validierung; Version; Build

## Ausgaben
- Dateien unter `src/app/**`, `src/components/generated/**`, `src/content/**`, `public/images/**`; jede Sektion mit `data-cs-id`
- Neue `ProjectVersion` (Quelle GENERATION)
- `component-index.json`, `workflow-state.json`

## Qualitätsanforderungen
- Bibliothek zuerst: Hero, Navigation, Sektionen aus den Premium-Bausteinen, konfiguriert über Props und Tokens
- Texte exakt aus dem Content, Bilder aus dem Manifest mit Alt-Texten
- TypeScript strict, semantisches HTML, eine H1 je Seite, Tastaturbedienung
- Keine externen Skripte/Fonts/Tracker, keine Node-APIs, keine Secrets
- Anti-Generic-Scan ohne `fail`-Befunde

## Fehlerbehandlung
- Validierung lehnt eine Datei ab: nur diese Datei neu anfordern, nicht die Seite
- Modell liefert eine Seite nicht: Schritt schlägt fehl mit klarer Meldung, Wiederholung nur für diese Seite
- Build scheitert: Modul 15 (max. 2 Reparaturrunden), danach letzte funktionierende Version bleibt aktuell

## Kontext (laden)
- `design-decisions.json`, `sitemap.json`, `asset-manifest.json`, Inhalt der jeweiligen Seite

**Token-Ziel:** ≤ 8 000 Tokens Bausteine + ≤ 6 000 je Seite · **Modell:** Standardmodell; komplexe Startseite im First-Tarif höher
