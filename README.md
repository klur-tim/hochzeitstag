# Handoff: Hochzeitstag-Grußkarten-Hero „Liebe ist Alles" (Tim & Tobias)

## Overview
Animierter Mobile-Hero (100vw × 100vh) für eine Online-Grußkarte zum 3. Hochzeitstag eines schwulen Brautpaars (Tim & Tobias, verheiratet 12.08.2023). Doodle-/Handzeichnungs-Stil auf hellem Papier-Hintergrund mit Körnung. **Die gewählte finale Variante ist 1c („Der Kuss")** — Varianten 1a und 1b liegen als verworfene Explorationen mit im File.

## About the Design Files
Die Dateien in diesem Bundle sind **Design-Referenzen in HTML** — Prototypen, die Look und Verhalten zeigen, kein Produktionscode. Aufgabe: die Variante 1c im Ziel-Codebase-Umfeld (React, Vue, Svelte, natives Web …) mit dessen etablierten Patterns nachbauen. Existiert noch kein Environment, freie Framework-Wahl (ein statisches HTML/CSS-Snippet reicht — es gibt keinen JS-State).

`Hochzeitstag Hero.dc.html` öffnet direkt im Browser (benötigt `support.js` daneben). Die Variante 1c ist der Block `<div id="1c" data-screen-label="1c Der Kuss">` — der 390×844-Screen darin ist der eigentliche Hero; im Zielprojekt auf 100vw/100vh (mobil, `100dvh`) skalieren.

## Fidelity
**High-fidelity.** Farben, Typografie, Abstände, SVG-Illustrationen und Animationen sind final und sollen pixelgenau übernommen werden.

## Screens / Views

### Hero „Der Kuss" (Variante 1c)
- **Purpose**: Emotionaler Einstieg der Online-Grußkarte; keine Interaktion außer Ansehen.
- **Canvas**: mobil, Referenzgröße 390×844, im Ziel 100vw × 100dvh, `overflow:hidden`, `position:relative`.
- **Hintergrund**: `#f2eee2` + Körnungs-Overlay über die volle Fläche (siehe Design Tokens → Papier-Körnung), `pointer-events:none`.

**Layout (von oben nach unten):**
1. **Headline-Block** — absolut, `top:76px; left:36px; right:36px`, Spalten-Flex.
   - Drei Zeilen „LIEBE" / „IST" / „ALLES": Gaegu Bold, 96px, `line-height:.9`, Farbe `#1c1c1c`.
   - Danach Textblock mit `margin-top:44px`, linksbündig:
     - „TIM & TOBIAS" — Gaegu Bold 40px, `line-height:1`, `#1c1c1c`
     - „Verheiratet seit dem 12. August 2023" — Courier Prime 13px, `letter-spacing:1px`, `margin-top:10px`
     - „3 Jahre & für immer!" — Caveat Bold 28px, `transform:rotate(-1.5deg)`, `margin-top:16px`
2. **Küssendes Paar** — absolut, `left:0; right:0; bottom:-4px`, Inline-SVG `viewBox="0 0 340 260"`, `width:100%`. Handgezeichneter Doodle-Stil: Strich `#1c1c1c`, `stroke-width:2.5`, runde Caps/Joins. Dunkelhaariger, größerer Mann gefüllt (`#1c1c1c`-Anzug), blonder, kleinerer Mann als Outline mit Hintergrund-Füllung `#f2eee2`. Am unteren Rand beschnitten (bewusst). SVG-Pfade 1:1 aus der Datei übernehmen.
   - Darüber: pulsierendes Herz (`left:50%; top:14%`, 20px, Rot) und zwei funkelnde Sterne (`left:24%; top:6%`, 16px / `left:74%; top:2%`, 13px, `#1c1c1c`).
3. **Aufsteigende Herzen** — 6 kleine Herz-SVGs (10–18px, abwechselnd Rot `oklch(0.6 0.17 25)` und `#1c1c1c`), Start bei `bottom:-30px` auf `left: 9% / 26% / 42% / 58% / 76% / 88%`, Animation `riseFull` mit Dauern 10–15s und Delays 0–8s, `linear infinite`.

## Interactions & Behavior
Keine Klick-Interaktionen. Nur Animationen (alle CSS-only):
- `popIn` — Einstiegsanimation: Headline-Block `.9s ease-out both`; Paar-Illustration `1.1s .3s ease-out both`. (Scale/Fade von ~0.94/0 auf 1/1, siehe @keyframes im File.)
- `riseFull` — Herzen steigen von unten (`bottom:-30px`) über die volle Höhe auf, mit leichtem seitlichem Pendeln und Ausfaden; `linear infinite`, Dauer/Delay je Herz s.o.
- `kissPop` — Herz überm Paar skaliert weich auf/ab, `3s ease-in-out infinite`.
- `twinkle` — Sterne Opacity/Scale-Flackern, `2.4s .5s` bzw. `2.8s 1.2s ease-in-out infinite`.
- `prefers-reduced-motion`: Animationen deaktivieren (im Prototyp nicht umgesetzt — bitte ergänzen).

## State Management
Keiner. Rein statisch/CSS-animiert.

## Design Tokens
- Farben: Papier `#f2eee2` (Varianten nutzten auch `#f4f1e8`/`#fbf9f2`), Tinte `#1c1c1c`, Akzent-Rot `oklch(0.6 0.17 25)`.
- Typografie (Google Fonts): **Gaegu 700** (Display/Headline), **Caveat 700** (Handschrift-Akzent), **Courier Prime 400** (Mono-Meta). Größen: 96 / 40 / 28 / 13 px auf 390px-Breite — auf anderen Breiten proportional skalieren.
- Abstände: Seitenrand 36px, Headline-Top 76px, Headline→Namensblock 44px, Name→Datum 10px, Datum→Handschrift 16px.
- Radius/Schatten: keine im Hero selbst (28px-Radius + Schatten im File gehören zum Präsentations-Rahmen, nicht zum Design).
- Papier-Körnung: SVG `feTurbulence` (fractalNoise, baseFrequency 0.8, 2 Oktaven) als data-URI-Background, 240×240 Kachel, Alpha ≈ 0.06 — als Overlay über der Papierfarbe.

## Assets
Keine externen Assets. Alle Illustrationen sind Inline-SVGs im File; Fonts via Google Fonts (`<link>` im `<helmet>`-Bereich der Datei).

## Files
- `Hochzeitstag Hero.dc.html` — alle drei Varianten; **finale Variante: Block `id="1c"`**. `@keyframes` (popIn, riseFull, kissPop, twinkle) stehen im `<style>` am Dateianfang.
- `support.js` — nur Laufzeit für die Prototyp-Vorschau, nicht übernehmen.
