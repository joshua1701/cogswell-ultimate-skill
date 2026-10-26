# 01 · Customer Briefing

**Rolle:** Technical Project Manager
**Zweck:** Ein vollständiges, widerspruchsfreies Briefing, aus dem alle weiteren Schritte ohne Rückfragen arbeiten können.

## Eingaben
- Formulardaten des Mitarbeiters (`Briefing.data`, Zod `briefingDataSchema`)
- Kundendaten aus CXHUB, falls verbunden
- Hochgeladene Assets (Logo, Bilder) aus `asset-manifest.json`

## Ablauf
- Pflichtfelder prüfen (deterministisch, kein Modell)
- Nur bei Vollständigkeit: eine Lückenprüfung per Modell (`gapCheckSchema`)
- Ergebnis dem Mitarbeiter als Liste zeigen; blockierende Fragen stoppen die Pipeline

## Ausgaben
- Briefing mit Status `SUBMITTED`
- Lückenliste: Feld, Frage an den Kunden, blockierend ja/nein, Bereitschaft (`ready` / `minor_gaps` / `major_gaps`)
- Eintrag „Kunde & Ziel“ in `project-summary.md`

## Qualitätsanforderungen
- Pflichtfelder vollständig (Unternehmen, Branche, Beschreibung ≥ 40 Zeichen, Zielgruppe, Ziele, Leistungen, Sprachen)
- Keine Annahmen: Fehlendes wird gefragt, nicht ergänzt
- Fragen sind konkret und vom Kunden in einem Satz beantwortbar
- Max. 8 Fragen; blockierende zuerst

## Fehlerbehandlung
- Briefing im Entwurf: Mitarbeiter bitten, einzureichen; nichts generieren
- Widersprüche (z. B. „seriös“ und „verspielt“): als Entscheidung an den Mitarbeiter, nicht raten
- CXHUB nicht verbunden: Felder manuell, Status „nicht verbunden“ sichtbar lassen

## Kontext (laden)
- `workflow-state.json`
- Briefing-Formular (direkt aus der Datenbank)

**Token-Ziel:** ≤ 3 000 Tokens (Lückenprüfung) · **Modell:** effizientes Standardmodell des Pakets (kleine, günstige Klasse reicht)
