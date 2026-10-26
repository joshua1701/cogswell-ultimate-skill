# Tarife: Economy, Business, First

Der Tarif steuert Gestaltungsfreiheit, Modellwahl, Skills und Freigaben. Sicherheits-, Datenschutz- und Qualitätsprüfungen sind nie tarifgebunden. Quelle im Code: `src/server/ultimate/tiers.ts`.

| | Economy | Business | First |
| --- | --- | --- | --- |
| Für wen | Self-Service-Kunden | Self-Service mit mehr Freiheit | Projekt wird von einem Cogswell-Mitarbeiter übernommen |
| Designrichtung | kuratierte Stile, 1 Konzept zur Bestätigung | 3 Konzepte, Kombination erlaubt | volle Art Direction, Referenzrecherche, 3 Konzepte + Refinement |
| Layout | Bibliothek, feste Dramaturgie | Bibliothek + Anpassung | Bibliothek + eigene Komponenten |
| Änderungen per Chat | deterministisch + einfache Revisionen | alle Revisionsarten | alle, plus Design-Chat mit Critic |
| Modelle | effizientes Standardmodell | Standard, komplexe Schritte höher | Standard, Creative Direction/Review mit stärkstem erlaubtem Modell |
| Skills | Kernmodule 01, 07–10, 12–15, 17 | + 05, 06, 11, 16 | alle, plus externe Design-Skills (Taste, Impeccable, Emil) |
| Prüfungen | Standard-QA | erweiterte QA | erweiterte QA + Design Review mit Rubrik + menschliche Designfreigabe |
| Freigabe | Kunde | Kunde | Mitarbeiter, dann Kunde |

## Regeln

- Ein Modul, das der Tarif nicht freigibt, wird nicht geladen; der Guide erklärt, was First zusätzlich bietet (ein Satz, kein Verkaufsdruck).
- First verlangt vor Veröffentlichung eine dokumentierte Designfreigabe durch einen Menschen (`workflow-state.json` → `approvals.design`).
- Das persönliche Claude-Pro-Abonnement eines Mitarbeiters ist nie das Kontingent für Kundenprojekte; die Kundenplattform läuft über den API-Adapter mit eigenem Budget.
