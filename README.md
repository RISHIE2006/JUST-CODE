# 📱 Phone Mockup — Dynamic Island Music Player

A pure CSS iPhone-style phone mockup with an animated **Dynamic Island** music player notch and a **4-theme color switcher** — no JavaScript required.

## ✨ Features

- **Dynamic Island notch** — hover or focus to expand and reveal the music player
- **4 color themes** — Deep Purple, Gold, Space Black, Silver (switched via CSS radio inputs)
- **Ambient background gradients** — each theme has its own animated radial-gradient screen
- **Physical button details** — silent switch, volume, power button rendered in CSS
- **Home indicator bar** — subtle pill at the bottom of the screen
- **Album art thumbnail** with CSS music note icon
- **Progress bar** with timestamps
- **Entrance animation** — phone and swatches fade/scale in on load
- **Accessible** — ARIA labels, screen-reader text, keyboard focusable notch

## 🚀 Usage

Just open `index.html` in any modern browser — no build step needed.

```
open index.html
```

## 🐛 Bugs Fixed

| # | Bug | Fix |
|---|-----|-----|
| 1 | `.gold`, `.deep-purple` used `var(gold)` without `--` prefix | Changed to `var(--gold)` etc. |
| 2 | `#silver:checked` was showing `.space-black` layer instead of `.silver` | Fixed selector |
| 3 | `.space-black` and `.silver` were nested *inside* `.gold` in HTML | Moved to siblings inside `.bg` |
| 4 | `pallette` / `pallete` class name mismatch | Unified to `.pallette` |
| 5 | `animation: appear … forwads` typo | Fixed to `forwards` |
| 6 | `mask-image` missing comma in gradient shorthand | Fixed syntax |
| 7 | `transition: … var(ease)` missing `--` prefix | Fixed to `var(--ease)` |
| 8 | `position: left` on `.phone` | Changed to `position: relative` |
| 9 | `fill: blur(...)` is not valid CSS | Removed invalid property |
| 10 | Font `'Inter'` referenced but never imported | Added Google Fonts `<link>` |

## 📁 File Structure

```
JUST CODE/
├── index.html   # Markup — phone shell, notch, swatches
├── style.css    # All styling, animations, and theme logic
└── README.md    # This file
```

## 🎨 Themes

| Theme | Hue | Feel |
|-------|-----|------|
| Deep Purple | 284° | Rich violet/indigo |
| Gold | 38° | Warm amber/gold |
| Space Black | 215° | Cool dark steel |
| Silver | 254° | Soft lavender-grey |

## 🛠 How It Works

Themes are driven entirely by CSS custom properties and the **checkbox hack**:

```css
#gold:checked ~ .phone .bg .gold { opacity: 1; }
```

The Dynamic Island expands using `:hover` / `:focus-within` on a positioned container — no JS.
