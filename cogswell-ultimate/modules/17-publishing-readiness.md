# 17 · Publishing Readiness

**Rolle:** Technical Project Manager
**Zweck:** Entscheiden, ob die Website veröffentlicht werden darf, und alles Nötige für Freigabe und Übergabe bereitstellen.

## Eingaben
- Alle Prüfergebnisse (`quality-results.json`), `workflow-state.json`, `unconfirmedClaims` aller Seiten, Rechtsseiten-Status, Asset-Lizenzen

## Ablauf
- Blocker deterministisch sammeln (Suite)
- Bericht formulieren
- Freigabe anfordern; nach Freigabe Export/Deploy

## Ausgaben
- Readiness-Bericht: harte Blocker (roter Build, kritische a11y-Befunde, fehlende Pflichtseiten, unbestätigte Aussagen, fehlende Lizenzen, offener Consent), weiche Hinweise, To-do-Liste für Menschen
- Freigabe-Anforderung an Projektmanager/Kunde (First: zusätzlich Designfreigabe)
- Übergabepaket: ZIP/Git-Export, Übergabebericht

## Qualitätsanforderungen
- Kein Blocker wird übersprungen; Veröffentlichung nie automatisch
- Rechtstexte bleiben Entwürfe bis zur fachlichen Freigabe
- Alle `[zu bestätigen]`-Stellen sind bestätigt oder entfernt
- Jedes Bild hat Lizenz und Alt-Text

## Fehlerbehandlung
- Blocker vorhanden: Liste mit Verantwortlichem (Kunde, Mitarbeiter, Claude) und nächstem Schritt
- Freigabe verweigert: Projekt bleibt in REVIEW, Gründe dokumentiert

## Kontext (laden)
- `workflow-state.json`, `quality-results.json`, `asset-manifest.json`, `sitemap.json`

**Token-Ziel:** ≤ 2 000 Tokens · **Modell:** Standardmodell
