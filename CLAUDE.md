# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Snowdrop is a no-build CSS/HTML boilerplate and styleguide — a single `index.html`
demonstrating modern, semantic HTML with clean vanilla CSS. There is no package
manager, no build step, and no JavaScript.

Serve locally with any static file server, e.g. `python3 -m http.server`.

## File structure

| File | Role |
|------|------|
| `reset.css` | CSS reset (based on "The New CSS Reset" v1.11.3). Rarely touched. |
| `base.css` | Default styles for all semantic HTML elements — the core of the project. |
| `local.css` | Application-specific utility classes (color helpers, navigation layout). |
| `index.html` | Single-page styleguide demonstrating every standard HTML element. |

## Architecture

**Three-layer stylesheet model:**
1. `reset.css` — neutralise browser defaults.
2. `base.css` — opinionated defaults for every semantic element (typography,
   form controls, tables, media, interactive elements).
3. `local.css` — utility classes layered on top.

**Color system** (defined in `base.css` `:root`):
- Named hues: `red`, `orange`, `yellow`, `green`, `blue`, `purple`, `black`, `white`.
- Abstract grays: `loud`, `hushed`, `whisper`, `quiet`, `silent`.
- Display-P3 overrides inside `@media (color-gamut: p3)`.
- `fg-*` and `bg-*` utility classes in `local.css` expose colors as classes.
- Light/dark mode is handled with the native `light-dark()` function — no
  separate media query blocks needed for most color values.

**Typography** — three font stacks set as CSS variables:
- `--font-sans`, `--font-serif`, `--font-mono`.

**Responsive sizing** — nearly all spacing, type sizes, and layout dimensions
use `rem`/`em`/`vw` with `calc()` on shared variables. Avoid introducing `px`
values for layout.

**Custom form/interactive elements** (no JS):
- `<details>`/`<summary>` chevron animated with CSS transforms.
- Range, progress, meter, and select elements styled via vendor pseudo-elements
  and modern CSS.
