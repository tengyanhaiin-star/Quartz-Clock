# 💥 Comic Clock

A real-time analog clock built entirely in HTML5 Canvas, styled after classic American comic books — bold outlines, Ben-Day halftone dots, starburst rays, and onomatopoeia that pops on every beat.

![Comic Clock Preview](preview.png)

---

## ✨ Features

- **Real-time clock** — smooth second-hand sweep driven by `requestAnimationFrame` with millisecond interpolation
- **Comic book aesthetic** — thick black outlines, flat color zones, Ben-Day dot textures, and a rotating starburst background
- **Synchronized animations** — the 30-ray starburst rotates in perfect lockstep with the second hand; TICK!/TOCK! alternates and pops on every beat; speed lines pulse on a 1-second cycle
- **Dual typefaces** — [Rancho](https://fonts.google.com/specimen/Rancho) for clock numerals, [Bangers](https://fonts.google.com/specimen/Bangers) for display text, [LXGW WenKai Mono TC](https://fonts.google.com/specimen/LXGW+WenKai+Mono+TC) for the monospaced digital readout
- **Fully responsive** — scales fluidly to any screen size via `vmin`-based layout
- **iPhone / iOS Safari compatible** — `viewport-fit=cover`, `env(safe-area-inset-*)`, `-webkit-fill-available`, pinch-zoom disabled

---

## 🚀 Usage

No build tools, no dependencies, no installation required. Just open the file:

```bash
# Clone the repo
git clone https://github.com/tengyanhaiin-star/Comic-Clock.git

# Open in your browser
open Comic-Clock/comic_clock.html
```

Or simply download `comic_clock.html` and open it directly — it is a fully self-contained single file.

---

## 🎨 Design

**Halftone Thunder Timepiece** draws from mid-century American comic book printing:

- **Starburst background** — 30 radiating rays (orange / yellow alternating) that rotate synchronously with the second hand, one full revolution every 60 seconds
- **Ben-Day dot ring** — a cobalt dot-screened band between the starburst and the clock face, referencing Roy Lichtenstein's appropriation of four-color print artifacts
- **Clock face** — cream-toned disc with two concentric decorative rings; 12 tick marks and 48 minute dots sit precisely between the inner rings
- **Numerals** — Rancho at 76 px; cardinal positions (12, 3, 6, 9) presented in red badge cartouches with drop shadows
- **Hands** — tapered trapezoid silhouettes with offset drop shadows; hour hand in black, minute hand in cobalt blue, second hand in red with a counterbalance tail
- **TICK! / TOCK!** — alternates each second with a sharp-attack pop animation, cobalt blue speech-bubble styling

---

## 🛠 Technical Notes

| Concern | Approach |
|---|---|
| Smooth sweep | `secAngle = secs + ms / 1000` — sub-second interpolation |
| Starburst sync | CSS `transform` written each rAF frame; no CSS animation |
| Font rendering | `Promise.all([fonts.load(...)])` before first draw |
| Responsive scaling | `--clock-scale` CSS variable, updated on `resize` and `orientationchange` |
| iOS safe area | `viewport-fit=cover` + `env(safe-area-inset-*)` on all four edges |
| Pinch-zoom lock | `user-scalable=no` in viewport meta + `touchstart`/`touchmove` JS interception |

---

## 📄 License

[MIT License](LICENSE) © 2026 tengyanhaiin-star
