# Premium Design Library

Geprüfte Bausteine, die Claude an Marke, Inhalt und Zielgruppe anpasst, statt sie neu zu entwickeln. Quelle im Code: `src/server/design/` (Layouts, Stile, Anti-Generic-Regeln) und `templates/website/src/components/site/premium/`.

## Bestandteile

- **Designsysteme**: zehn Stilrichtungen (`styles.ts`), jede mit Palette, Schriftpaarung, Skala, Radius, Schatten, Button-/Kartenstil, Header-Variante, Animationsregel, Bildsprache.
- **Layoutarchitekturen**: zwölf Architekturen (`layouts.ts`) mit Raster, Abständen, Sektionsdramaturgie, Responsive-Regeln, Navigation, Footer, CTA.
- **Hero-Varianten**: Editorial, Cinematic, Full-Bleed, Split, Typographic, Stage (Film/Bild mit einem Satz).
- **Navigationsmuster**: Minimal, Sticky, Transparent→Opak, Mega (nur bei > 8 Seiten), Vollbild-Overlay mobil.
- **Komponenten**: Editorial Feature, Asymmetric Grid, Process Timeline, Testimonials (nur belegte), Pricing (nur mit bestätigten Preisen), Image Reveal, Statement, FAQ, Kontaktbereich mit Formular, Editorial Footer.
- **Seitenlayouts**: Start, Leistung, Über uns, Projekt/Referenz, Kontakt, Rechtliches.
- **Animationen**: Reveal (einmalig), Hover mit Bedeutung, Zahlen zählen, Bildwechsel; alle mit `prefers-reduced-motion`.
- **Typografiekombinationen**: siehe Stilrichtungen; nur lokal eingebettete Variable Fonts.

## Regeln der Wiederverwendung

1. Zuerst Bibliothek, dann Anpassung, zuletzt Neubau. Neubau wird im Log begründet.
2. Jede Website bekommt eine eigene Komposition: Hero-Typ, Sektionsreihenfolge, Bildsprache und Schriftpaarung aus der Creative Direction. Zwei Projekte dürfen nicht dieselbe Kombination aus Stil + Layout + Hero tragen, wenn sie in derselben Branche liegen.
3. Anti-Generic-Regeln (`anti-generic.ts`) gelten für Bibliothek und Neubau gleichermaßen.
4. Bausteine sind token-gesteuert: Farben, Schriften, Radien kommen aus `tokens.css`, nie hart in der Komponente.
5. Jede Komponente trägt `data-cs-id="<sektion>"`, damit `component-index.json` und gezielte Änderungen funktionieren.

## Was die Bibliothek nicht ersetzt

Bildauswahl, Texte, Markenentscheidungen und die Freigabe durch Menschen.
