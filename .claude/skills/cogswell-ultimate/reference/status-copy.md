# Statusmeldungen und Fehlertexte (Employee Mode)

Einfaches Deutsch, du-Form, ein Satz, keine Fachbegriffe. Technische Details in die erweiterten Logs.

## Status

| Schlüssel | Text |
| --- | --- |
| `efficiency_on` | Sparmodus aktiv |
| `reusing_components` | Vorhandene Komponenten werden verwendet |
| `targeted_edit` | Nur die ausgewählte Sektion wird geändert |
| `testing` | Website wird automatisch getestet |
| `change_done` | Änderung erfolgreich |
| `review_required` | Manuelle Prüfung erforderlich |
| `approval_required` | Deine Freigabe ist nötig |
| `building` | Website wird gebaut |
| `preview_ready` | Vorschau ist bereit |
| `waiting_customer` | Wartet auf Informationen vom Kunden |
| `ai_offline` | Automatische Erstellung ist gerade nicht verbunden |
| `budget_paused` | Das Kontingent dieses Projekts ist aufgebraucht, ein Projektmanager kann es erhöhen |

## Fehler (verständlich → technisch bleibt im Log)

| Technisch (Muster) | Anzeige |
| --- | --- |
| `TypeError`, `ReferenceError`, `Cannot read properties` | Die Website konnte aufgrund eines Komponentenfehlers nicht vollständig erstellt werden. Claude kann eine automatische Reparatur versuchen. |
| `TS\d{4}`, `Type '.*' is not assignable` | Ein Baustein passt nicht zusammen. Claude kann das automatisch korrigieren. |
| `Module not found`, `Cannot find module` | Ein Baustein fehlt. Claude kann ihn ergänzen. |
| `ELIFECYCLE`, `exit code 1` im Build | Der Bau der Website ist abgebrochen. Claude prüft die Ursache und schlägt eine Reparatur vor. |
| `UnsafeFileError`, `geschützte Datei` | Eine vorgeschlagene Änderung würde einen geschützten Bereich berühren. Bitte formuliere den Wunsch anders. |
| `Token-Budget erschöpft` | Das Kontingent dieses Projekts ist aufgebraucht. Ein Projektmanager kann es erhöhen. |
| `ANTHROPIC_API_KEY fehlt`, `nicht verbunden` | Die automatische Erstellung ist gerade nicht verbunden. Ein Administrator muss die Verbindung einrichten. |
| `refusal` | Claude hat diese Anfrage abgelehnt. Bitte formuliere sie anders oder frag deinen Projektmanager. |
| `max_tokens` | Die Antwort war zu lang. Claude teilt die Aufgabe in kleinere Schritte. |
| `ECONNREFUSED`, Docker, Container | Die Bau-Umgebung ist nicht erreichbar. Ein Administrator muss sie starten. |
| Playwright/axe/Lighthouse-Fehler | Die automatische Prüfung konnte nicht laufen. Das Ergebnis gilt als offen, nicht als bestanden. |
| alles andere | Etwas ist schiefgegangen. Claude kann eine Reparatur versuchen; die Details stehen im Protokoll. |

## Cogswell Guide, Satzmuster

- Was passiert: „Gerade wird … Das dauert etwa …“
- Entscheidung: „Du musst jetzt … Empfehlung: … weil …“
- Fehlt: „Vom Kunden fehlt noch: … Ohne das kann … nicht …“
- Problem: „… hat nicht funktioniert. Am schnellsten: … Alternativ: …“
- Offene Prüfungen: „Vor der Abnahme fehlen noch: …“
- Bereit: „Die Website ist bereit zur Kundenabnahme. Noch zu prüfen durch Menschen: …“
