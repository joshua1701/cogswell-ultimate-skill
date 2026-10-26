# 16 · Design Critic

**Rolle:** Creative Director
**Zweck:** Die gebaute Website mit Augen prüfen: Screenshots gegen Rubrik und Creative Direction, ehrlich bewertet.

## Eingaben
- Desktop- und Mobile-Screenshots der Startseite und einer Unterseite
- `design-decisions.json` (Leitidee, Regeln)
- Anti-Generic-Scan-Befunde

## Ablauf
- Screenshots lesen
- Rubrik ausfüllen
- Plan an Modul 10 oder Freigabe an Mitarbeiter

## Ausgaben
- `DesignReview`: Scores 1–10 je Kriterium (Typografie, Komposition, Marke, Bildsprache, Konsistenz, Responsive, Interaktion) mit Begründung, Befunde mit Stelle, Verbesserungsplan (max. 5 gezielte Änderungen), Verdikt `pass` / `refine` / `fail`
- `quality-results.json` → `designReview`

## Qualitätsanforderungen
- Bewertet wird gegen die eigene Creative Direction, nicht gegen Geschmack
- Unter Schwelle (Gesamt < 7 oder ein Kriterium < 5) folgt `refine` über Modul 10, max. 2 Runden
- Verbesserungen sind konkret (Datei, Element, Änderung), nicht „hochwertiger machen“

## Fehlerbehandlung
- Screenshots fehlen: Review nicht möglich, Status offen
- Zwei Runden ohne `pass`: Mitarbeiter entscheidet mit Begründung; nie automatisch als fertig markieren

## Kontext (laden)
- Screenshots, `design-decisions.json`

**Token-Ziel:** ≤ 4 000 Tokens je Review · **Modell:** Vision-fähiges Modell; im First-Tarif das stärkste erlaubte
