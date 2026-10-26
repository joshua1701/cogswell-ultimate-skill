# Premium Design Library

Geprüfte Gestaltungsregeln, die Claude an Marke, Inhalt und Zielgruppe anpasst, statt sie neu zu entwickeln. Die Bibliothek besteht aus Regelwerken im Code und aus den Template-Bausteinen; einen Katalog fertiger Premium-Komponenten gibt es nicht, Komponenten entstehen projektbezogen unter `src/components/generated/` und werden über den Komponentenindex wiederverwendet.

## Bestand (so wie er im Code existiert)

- **Stilrichtungen** (`src/server/design/styles.ts`, zehn): Palette, Schriftpaarung, Skala, Radius, Schatten, Button-/Kartenstil, Header-Variante, Animationsregel, Bildsprache.
- **Layoutarchitekturen** (`src/server/design/layouts.ts`, zwölf: editorial, asymmetric, swiss, minimal-luxury, modern-corporate, image-led, typography-led, architectural, cinematic, creative-studio, premium-saas, …): Raster, Abstände, Sektionsdramaturgie, Responsive-Regeln, Hierarchie, Bildplatzierung, Navigation, Footer, CTA, Eignung und Tabus je Branche.
- **Typografie** (`src/server/design/typography.ts`): Paarungen, Skalen, Zeilen- und Buchstabenabstände; nur lokal eingebettete Variable Fonts aus dem Template (`TEMPLATE_FONT_NAMES`).
- **Anti-Generic-Regeln** (`src/server/design/anti-generic.ts`): was eine Website austauschbar macht und deshalb abgelehnt wird (zentrierte Standard-Heros, dreispaltige Icon-Cards, Gradient-Flächen, Stock-Klischees).
- **Template-Bausteine** (`templates/website/src/components/site/`): Header (Logo aus der Medienbibliothek, mobiles Menü ohne JavaScript), Footer, ContactForm, ConsentBanner, Reveal. Header, Footer und Reveal darf ein Projekt überschreiben (Modul 10).
- **Token-System** (`templates/website/src/styles/tokens.css`, erzeugt aus dem Designsystem): Farben, Schriften, Skala, Abstände, Radius, Bewegung. Alle Bausteine sind token-gesteuert.
- **Projektbausteine**: je Website 3–6 Bausteine, die der Code-Schritt zuerst erzeugt (Hero, SectionHeading, Feature-/Leistungsraster, CTA-Band, Kontaktbereich mit ContactForm) und die alle Seiten importieren; `component-index.json` führt sie mit `data-cs-id`.

## Regeln der Wiederverwendung

1. Zuerst Regelwerk und vorhandene Projektbausteine, dann Anpassung, zuletzt Neubau. Neubau wird im Log begründet.
2. Jede Website bekommt eine eigene Komposition: Hero-Typ, Sektionsreihenfolge, Bildsprache und Schriftpaarung aus der Creative Direction. Zwei Projekte derselben Branche tragen nicht dieselbe Kombination aus Stil + Layout + Hero.
3. Anti-Generic-Regeln gelten für Bibliothek und Neubau gleichermaßen.
4. Farben, Schriften, Radien kommen aus `tokens.css`, nie hart in der Komponente.
5. Jede Komponente trägt `data-cs-id="<sektion>"`, damit `component-index.json` und gezielte Änderungen funktionieren.
6. Testimonials nur belegt, Preise nur bestätigt, Zahlen nur aus dem Briefing; sonst `[zu bestätigen]`.

## Was die Bibliothek nicht ersetzt

Bildauswahl, Texte, Markenentscheidungen und die Freigabe durch Menschen.
