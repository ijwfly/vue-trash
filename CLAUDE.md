# CLAUDE.md

## Project Overview

**vue-trash** is a collection of standalone Vue.js utility applications and demos. Each HTML file is a self-contained single-page application that loads Vue.js (and other dependencies) via CDN — there is no build system, bundler, or package manager.

## Repository Structure

```
vue-trash/
├── index.html             # Landing page with navigation links
├── counter.html           # Counter app (3 counters, Vue 2)
├── counter2.html          # Counter variant (2 counters, Vue 2)
├── base_render.html       # Matrix-style text animation (Vue 2 + jQuery)
├── factorisation.html     # Number factorization calculator (Vue 3)
├── excelcalc.html         # Centimeters-to-pixels converter (Vue 3)
├── vuetify.html           # Vuetify Material Design demo (Vue 2 + Vuetify)
└── image_measurer.html    # Image measurement/scaling tool (~1400 lines, vanilla JS + Font Awesome)
```

## Tech Stack

- **Vue.js 2** — `counter.html`, `counter2.html`, `base_render.html`, `vuetify.html` (uses `new Vue({el, data, methods})`)
- **Vue.js 3** — `factorisation.html`, `excelcalc.html` (uses `Vue.createApp().mount()`)
- **Vuetify** — `vuetify.html` only
- **jQuery 3.3.1** — `base_render.html` only
- **Font Awesome 6.4.2** — `image_measurer.html` only
- All dependencies loaded via CDN (jsdelivr, cdnjs, googleapis) — no `node_modules` or `package.json`

## Development Workflow

### No build step
Open any HTML file directly in a browser. No compilation, transpilation, or dev server required.

### No tests, linting, or CI
There is no test suite, linter configuration, or CI/CD pipeline. Validate changes by opening files in a browser.

### Git conventions
- Commit messages are short and descriptive in English (e.g., "Add excelcalc", "new vue version fixes")
- The repository uses a flat structure — all app files live at the root

## Code Conventions

- **Language**: User-facing text and some comments are in **Russian**
- **Inline everything**: CSS is in `<style>` tags, JS in `<script>` tags — no external `.js` or `.css` files
- **State management**: Global variables or Vue instance `data` — no Vuex/Pinia
- **Mixed Vue versions**: Vue 2 and Vue 3 coexist across files; there is no single standard
- **Theming**: `image_measurer.html` uses CSS custom properties for dark/light theme toggle
- **No abstractions**: Each file is independent with no shared code between apps

## Key Application: image_measurer.html

The most complex file (~1400 lines). Despite importing Vue via CDN, it is implemented in vanilla JavaScript. Features include:
- Image upload and clipboard paste (Ctrl/Cmd+V)
- Interactive zoom/pan with mouse and touch support
- Scale calibration (pixel-to-unit conversion)
- Distance measurement with visual overlays
- Measurement export to JSON
- Dark/light theme toggle
- Responsive/mobile layout

## Guidelines for AI Assistants

- Each HTML file is fully self-contained — changes to one file should not affect others
- Preserve CDN-based dependency loading (do not introduce npm/build tooling unless asked)
- Keep user-facing strings in Russian to match existing conventions
- When modifying `image_measurer.html`, be aware it uses vanilla JS patterns despite importing Vue
- There are no tests to run — verify correctness by reviewing code logic
- Do not add unnecessary abstractions, documentation files, or tooling beyond what is requested
