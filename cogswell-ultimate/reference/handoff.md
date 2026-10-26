# Übergabe zwischen Sitzungen

Bevor eine Sitzung geleert (`/clear`) oder komprimiert (`/compact`) wird, muss alles Nötige in Projektdateien stehen. Danach darf keine Information verloren sein, die Anforderungen oder Freigaben betrifft.

## Vor `/clear` oder `/compact`

1. `.cogswell/project-summary.md` aktualisieren: Stand, offene Entscheidungen, letzte Änderungen, bestätigte Fakten.
2. `.cogswell/workflow-state.json` prüfen: Ist der aktuelle Schritt korrekt markiert? Offene Freigaben eingetragen?
3. `component-index.json` nach Dateiänderungen neu schreiben (die Suite tut das nach jeder Version automatisch; manuell nur in Claude Code ohne Suite).
4. Eine kurze Übergabe in die Antwort schreiben (max. 8 Zeilen):

```
Übergabe
Projekt: <Name> · Schritt: <Schlüssel> · Version: v<n>
Erledigt: <1–3 Punkte>
Offen: <1–3 Punkte, mit Datei/Komponente>
Entscheidungen: <was der Mitarbeiter festgelegt hat>
Nächster Befehl: <konkret>
```

## Wann `/clear`, wann `/compact`

- **`/clear`** bei Themenwechsel (anderes Projekt, von Design zu SEO ohne Zusammenhang).
- **`/compact`** bei langen zusammenhängenden Aufgaben (Konzeptrunde, mehrstufige Reparatur).
- In beiden Fällen gilt: `.cogswell/` ist die Wahrheit, nicht die Erinnerung der Sitzung.

## Was nie nur im Gedächtnis bleiben darf

Freigaben, abgelehnte Vorschläge, bestätigte Fakten des Kunden, Budgetentscheidungen, geänderte Anforderungen.
