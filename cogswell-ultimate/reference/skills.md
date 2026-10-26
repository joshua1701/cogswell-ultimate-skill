# Externe Skills, Registry und Tariffreigabe

Der Master-Skill ist die Orchestrierung; externe Skills sind Werkzeuge, die nur nach Prüfung und mit protokolliertem Aufruf genutzt werden. Erwähnen zählt nicht, nur ein überprüfbarer Aufruf.

## Registry

Quelle: `src/server/skills/catalog.ts` (Startwerte) und `src/server/skills/inspect.ts` (Installationsstatus und Funktionstest zur Laufzeit). Jeder Eintrag beantwortet: verfügbar? (installiert, Version), geeignet? (welche Pipeline-Schritte), ausführbar? (Laufzeit: Claude Code, MCP, npm), Abhängigkeiten? (Node, Chromium, Binärdateien), tariflich freigegeben? (`tiers.ts` → `externalDesignSkills`, heute nur First). Der Status wird nicht behauptet, sondern gemessen; ein nicht installierter Skill erscheint als „nicht verfügbar“, nie als genutzt.

## Aufrufprotokoll

1. Vor dem Aufruf: Registry lesen; nicht verfügbar oder nicht freigegeben → ohne den Skill weiterarbeiten und das im Log vermerken.
2. Aufruf mit dem Mechanismus des Skills (Slash-Befehl in Claude Code, MCP-Tool, Skript) und minimalem Kontext (Komponentenindex, nicht das Repository).
3. Ergebnis in das Schrittprotokoll und, wenn es Design oder Code ändert, in `design-decisions.json` bzw. eine neue Version.
4. Kein Skill umgeht die Pflichtprüfungen (Modul 13–15, 17).

## Zuordnung

| Skill | Quelle | Schritte | Zweck | Tarif |
| --- | --- | --- | --- | --- |
| Taste (design-taste-frontend) | github:Leonxlnx/taste-skill | 04, 05, 09 | Art Direction, Anti-Slop-Prüfung an drei Breiten | First |
| Impeccable | npm:impeccable | 05, 09, 16 | Shape, Audit, Polish, Harden, Animate | First |
| Emil Kowalski (emil-design-eng, animate) | github:emilkowalski/skill | 09, 11 | UI-Polish, Animationsentscheidungen | First |
| Anthropic Frontend Design / anthropics/skills | github:anthropics/skills | 05, 09 | Frontend-Design-Leitlinien, Dokumenten-Skills | alle (Leitlinien), Aufruf protokolliert |
| Vercel Agent Skills | github:vercel-labs/agent-skills | 09, 15 | React/Next.js-Best-Practices, Deployment-Prüfungen | alle |
| Playwright | github:microsoft/playwright | 13, 15 | Browser-Tests, Screenshots, Labor-Performance | alle (Pflichtwerkzeug) |
| Claude SEO | github:AgriciDaniel/claude-seo | 12, 15 | SEO-Audits (technisch, Content, Schema, Local); Modul 12 nutzt die Ergebnisse | alle |
| imagegen-skills | github:Leonxlnx/imagegen-skills | Assets | generierte Bilder mit Kennzeichnung „Generiert“ | Business, First; nie für Personen/Produkte des Kunden |
| trailofbits/skills | github:trailofbits/skills | 15, 17 | Sicherheitsprüfung des generierten Codes | alle (Prüfung wird nie gekürzt) |
| Heimdall MCP | github:lcbcFoo/heimdall-mcp-server | – | projektübergreifendes Gedächtnis | geprüft, nicht aktiv (`efficiency.md`) |
| Caveman | github:JuliusBrussee/caveman | – | knappe Antworten | geprüft, nicht aktiv (`efficiency.md`) |

Die sieben Repositories ab „Anthropic Frontend Design“ sind die Standardausstattung des Studios; sie werden installiert, in der Registry geführt und erst nach bestandenem Funktionstest in den Schritten genutzt.
