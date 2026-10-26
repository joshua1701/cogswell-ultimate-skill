# Employee Mode und Expert Mode

Die Suite hat zwei Ansichten derselben Daten. Der Modus hängt am Nutzer (Cookie `cs-mode`, Standard nach Rolle: Mitarbeiter und Betrachter im Employee Mode, Administratoren und Projektmanager im Expert Mode; umschaltbar in der Kopfzeile).

## Employee Mode: elf geführte Schritte

Ziel: Eine Aushilfe ohne Vorkenntnisse bringt eine normale Kundenwebsite bis zur Kundenfreigabe. Jeder Schritt hat einen Status-Text (`status-copy.md`) und eine nächste Aktion im Cogswell Guide.

1. **Kunde auswählen oder anlegen** – Name, Rechtsform, Adresse, Ansprechpartner. Platzhalter heißen `[zu bestätigen]`.
2. **Briefing ausfüllen** – Formular (Modul 01); unvollständige Pflichtfelder blockieren den Start, der Guide nennt sie.
3. **Logo und Bilder hochladen** – Medienbibliothek (`assets.md`): Logo zuerst, dann Fotos; Lizenz und Alt-Text je Datei.
4. **Website erstellen** – startet die Pipeline. Der Mitarbeiter sieht Fortschritt, Kosten und den aktuellen Schritt, keine Logs.
5. **Designkonzept wählen** – drei Konzepte mit Vorschau (Economy: eines bestätigen), eine Wahl oder eine Kombination (Business/First).
6. **Seiten bestätigen** – Sitemap mit Navigationsbezeichnungen; Seiten hinzufügen, umbenennen, entfernen.
7. **Inhalte prüfen** – Texte mit `[zu bestätigen]`-Markierungen; Mitarbeiter ersetzt oder lässt beim Kunden nachfragen.
8. **Vorschau ansehen** – Desktop, Tablet, Mobil; Screenshots aller Seiten.
9. **Änderungen per Chat** – natürliche Sprache (Modul 10, Router); die Suite sagt vorab, was sie tut und ob ein Modell nötig ist.
10. **Prüfberichte einsehen** – Qualität, SEO, Barrierefreiheit, Design-Review in einfachem Deutsch; rote Punkte mit Empfehlung.
11. **Kundenfreigabe anfordern** – Readiness-Check (Modul 17) muss grün oder mit begründeten Ausnahmen sein; danach Freigabe-Link an den Kunden, Veröffentlichung erst nach menschlicher Freigabe.

Regeln: Kein Schritt zeigt Code, Dateipfade oder Tokenzahlen; Fehler erscheinen als verständlicher Satz mit nächstem Schritt; technische Details liegen im Protokoll. „Website fertigstellen“ führt die offenen Schritte 4–10 in Folge aus.

## Expert Mode

Zeigt zusätzlich: Workflow-Schritte mit Modell, Tokens und Kosten; Versionen mit Dateien, Build-Log und Diff; Komponentenindex; `.cogswell/`-Dateien; Prüfberichte mit Rohdaten (axe-Regeln, LCP/CLS, Überläufe); Modell- und Paketeinstellungen; Skill-Registry mit Installationsstatus. Schreibrechte ändern sich dadurch nicht, nur die Sichtbarkeit.
