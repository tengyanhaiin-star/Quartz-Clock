# Quartz Clock

A fully self-contained, real-time analog quartz clock rendered entirely in SVG, with a glowing digital time/date readout underneath. Ported from a Figma Make React prototype into a single dependency-free HTML file.

## Features

- **Vector everything** — the entire clock face, ticks, numerals, and hands are drawn with SVG primitives (no bitmap images), so it stays perfectly crisp at any size, from a small phone screen to a 4K display.
- **Smooth, drift-free motion** — hands are animated every frame via `requestAnimationFrame` and always rotate forward (never snap backward across the 12/60 boundary).
- **Digital readout** — an LCD-style panel below the analog face shows the current time (`HH:MM:SS`, 24-hour) and date, complete with a subtle scanline overlay and a soft green glow.
- **Fully responsive layout** — a small script measures the digital display's real rendered height and sizes the analog face to fill whatever space remains, so nothing gets cropped or squished no matter the window size or aspect ratio.
- **No fixed size cap** — the clock face scales up to fill large windows and high-resolution monitors rather than stopping at an arbitrary maximum.
- **Mobile / iPhone-ready** — respects iOS safe areas (notch, Dynamic Island, home indicator), uses `100dvh` to handle Safari's collapsing toolbar, disables pinch-zoom and rubber-band scrolling, and can be added to the Home Screen as a full-screen web app.
- **Zero build step, zero dependencies** — a single `.html` file. The only external resource is the Google Fonts stylesheet (Alata, DM Sans, DM Mono).

## Usage

Just open the HTML file in any modern browser — desktop or mobile.

On iPhone/iPad, open it in Safari and use **Share → Add to Home Screen** to run it full-screen like a native app.

## How it's built

| Layer | Technology |
|---|---|
| Clock face, ticks, numerals, hands | Inline SVG, generated and animated with vanilla JavaScript |
| Digital time/date panel | HTML + CSS (gradients, box-shadow, scanline overlay) |
| Fonts | Google Fonts — Alata (hour numerals), DM Sans (face labels), DM Mono (digital readout) |
| Responsive sizing | CSS (`dvh`, `vmin`, `clamp()`, safe-area insets) plus a small resize-aware script that measures the digital panel and fits the analog face to the remaining space |
| No frameworks | Plain JavaScript — no React, no build tools, no external libraries |

## Customization

All key visual parameters live near the top of the `<style>` block and are easy to tweak:

- `MAX_CLOCK_SIZE`-style caps have been removed — the face now scales freely with the window.
- Digital readout font sizes: `#timeStr` and `#dateStr` use `clamp(min, preferred-vmin, max)` so you can adjust the minimum, scaling rate, and maximum independently.
- Colors, glow, and letter-spacing for the digital display can be edited directly in the `#timeStr` / `#dateStr` rules.

## 📄 License

MIT — see [LICENSE](LICENSE) for details.
