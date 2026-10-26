# Medien und Lizenzen

Quelle im Code: `src/server/assets/service.ts`, Upload-Routen unter `src/app/api/projects/[id]/assets/`, Seite „Medien“ im Projekt. `asset-manifest.json` (Context Engine) führt jede Datei mit Pfad, Maßen, Alt-Text, Lizenz, Nachweis und Zuordnung.

## Ablauf

1. **Upload** (PNG, JPG, WebP, SVG, PDF, max. 15 MB): Prüfung über Magic Bytes, SVG wird bereinigt (keine Skripte, keine externen Verweise), Dateinamen werden normalisiert.
2. **Optimierung**: Bilder werden mit sharp zu WebP in Größenvarianten (z. B. 480/960/1600 px) umgerechnet; Logos mit Transparenz behalten zusätzlich PNG. Originale bleiben erhalten.
3. **Lizenz**: Pflichtfeld je Datei: Eigenes Material des Kunden, Stock lizenziert, Envato Elements (mit Lizenznachweis), Generiert, Unbekannt. „Unbekannt“ blockiert die Veröffentlichung (Modul 17).
4. **Alt-Text**: Pflicht vor Veröffentlichung. Claude darf einen Vorschlag erzeugen (Vision), der Mitarbeiter übernimmt oder ändert ihn; Vorschläge heißen `[Vorschlag]`.
5. **Zuordnung**: Seite und Sektion (Logo → Header, Hero-Bild → Startseite); ohne Zuordnung entscheidet der Code-Schritt anhand des Manifests.
6. **Verwendung**: Der Code-Schritt kennt nur Dateien aus dem Manifest und erfindet keine Bildpfade; das Logo erscheint über `site.logo` im Template-Header. Beim Bauen landet die Bibliothek unter `public/images/`.

## Designbezogene Empfehlungen

Aus Creative Direction und Layoutarchitektur leitet Claude ab, welche Bilder fehlen (z. B. „Image-Led braucht drei Querformate der Werkstatt mit einheitlichem Licht“) und schreibt sie als Liste `[Bildanweisung]` in den Content; Platzhalterflächen tragen diese Anweisung sichtbar, bis das Bild da ist.

## Stock-Anbieter

- **Envato Elements**: nur manueller Import. Der Mitarbeiter lädt die Datei herunter, lädt sie hoch, wählt Lizenz „Envato Elements“ und trägt den Lizenznachweis (Lizenz-ID/Download-Beleg) ein. Ohne Nachweis wird der Upload abgelehnt. Es gibt keinen automatisierten Zugriff auf Envato, keinen Scraper, keine Suche über die Suite.
- **Anbieter mit offizieller API** (Unsplash, Pexels u. a.): nicht eingebunden; die Provider-Schnittstelle ist vorbereitet, eine Anbindung braucht Lizenzprüfung und Freigabe durch den Administrator.
- **Generierte Bilder**: Lizenz „Generiert“, Kennzeichnung im Manifest; nie für Personen, Produkte oder Referenzen des Kunden.

## Was nie passiert

Keine Bilder von fremden Websites, keine Bildpfade ohne Manifest, keine Veröffentlichung mit Lizenz „Unbekannt“ oder ohne Alt-Text.
