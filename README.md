# 📱 Phone Mockup — Dynamic Island Music Player

> **A pixel-perfect iPhone-style phone mockup built entirely with HTML & CSS — no JavaScript.**  
> Features a hover-activated Dynamic Island music player, animated gradient screen backgrounds, and a 4-colour theme switcher.

---

## 🧠 What is this project?

This is a **pure CSS front-end experiment** that recreates an iPhone-style smartphone mockup in the browser. The goal is to push what vanilla CSS can do — using only HTML structure and CSS properties to achieve:

- A **3D-feeling phone chassis** with a metallic border, physical side buttons (silent switch, volume, power), a front camera pill, and a home indicator bar — all rendered without images or SVG.
- A **Dynamic Island** (the pill-shaped notch at the top of the screen) that **expands on hover/focus** to reveal a music player with album art, song name, artist, and a progress bar — using only CSS `:hover` and `:focus-within`.
- **4 animated colour themes** — Deep Purple, Gold, Space Black, and Silver — each applying its own radial-gradient wallpaper, border highlight, and button tint. Switching is driven by hidden `<input type="radio">` elements and the CSS sibling selector `~` (the "checkbox hack").
- **Ambient screen animation** — the active theme's gradient layer subtly pulses using `@keyframes`, giving the screen a living, glowing feel.

**No frameworks. No JavaScript. No images.**

---

## ✨ Features

| Feature | How |
|---------|-----|
| Phone chassis with buttons & camera | Pure CSS `box-shadow`, `border-radius`, pseudo-elements |
| Dynamic Island expand on hover | CSS `:hover` + `:focus-within` + `scale3d` |
| Music player (song, artist, progress) | CSS `::before` / `::after` content + transitions |
| 4 animated colour themes | Radio checkbox hack + CSS custom properties (`--c-h`) |
| Ambient gradient animation | `@keyframes ambientPulse` on active theme layer |
| Entrance animations | `@keyframes appear` with staggered `animation-delay` |
| Backdrop blur on notch expand | `backdrop-filter: blur()` |
| Accessible | ARIA labels, `role="region"`, keyboard-focusable notch |

---

## 🚀 Usage

No install, no build step — just open in a browser:

```
open index.html
```

Or with VS Code Live Server, just click **Go Live**.

---

## 🎨 Themes

| Theme | Hue | Vibe |
|-------|-----|------|
| 🟣 Deep Purple | 284° | Rich violet / indigo |
| 🟡 Gold | 38° | Warm amber / champagne |
| ⚫ Space Black | 215° | Cool dark steel / navy |
| ⚪ Silver | 254° | Soft lavender-grey |

---

## 🐛 Bugs Fixed (v2)

| # | Bug | Fix |
|---|-----|-----|
| 1 | `.gold`, `.deep-purple` used `var(gold)` without `--` prefix | → `var(--gold)` |
| 2 | `#silver:checked` showed `.space-black` layer | Fixed CSS selector |
| 3 | `space-black` & `silver` divs nested *inside* `gold` in HTML | Moved to `.bg` siblings |
| 4 | `pallette` / `pallete` class name mismatch | Unified to `.pallette` |
| 5 | `animation: appear … forwads` typo | → `forwards` |
| 6 | `mask-image` missing comma in gradient | Fixed syntax |
| 7 | `transition: … var(ease)` missing `--` | → `var(--ease)` |
| 8 | `position: left` on `.phone` | → `position: relative` |
| 9 | `fill: blur(...)` is not valid CSS | Removed |
| 10 | Font `'Inter'` used but never imported | Added Google Fonts `<link>` |

---

## 📁 File Structure

```
JUST CODE/
├── index.html   # Phone shell, Dynamic Island, colour swatches
├── style.css    # All styling, animations, and theme logic
└── README.md    # This file
```

---

## 🛠 How It Works

### Theme switching (no JS)
```css
/* Hidden radio inputs sit outside .phone */
#gold:checked ~ .phone .bg .gold { opacity: 1; }
#gold:checked ~ .phone { --c-h: var(--gold); }
#gold:checked ~ .pallette label[for=gold] { border-color: ...; }
```
Checking a radio button cascades three effects via `~`: shows the gradient layer, updates the phone's colour channel (`--c-h`), and highlights the active swatch.

### Dynamic Island expansion (no JS)
```css
.notch-container:hover .notch,
.notch-container:focus-within .notch {
    max-width: 100%;
    max-height: 100%;
    transform: scale3d(1, 1, 1);
}
```
The container tracks hover/focus and transitions `scale3d` + `max-height` on the inner pill.

---

## 📄 License

MIT — do whatever you like with it.
