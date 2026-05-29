# CVPR 2026 Workshop on Foundation Models for Medical Vision

The official website for the **CVPR 2026 Workshop on Foundation Models for Medical Vision**.

This is a static website built on the [Start Bootstrap "Agency"](https://startbootstrap.com/theme/agency) theme (Bootstrap 5.1.3) and served via GitHub Pages from [`fmv-cvpr26workshop.github.io`](https://fmv-cvpr26workshop.github.io). There is no build step — the files are served as-is, so the `main` branch is the live deployment.

## Project structure

```
.
├── index.html                  # Current edition — single-page site
├── css/styles.css              # Vendored Agency theme (Bootstrap 5.1.3)
├── js/scripts.js               # Navbar shrink-on-scroll, ScrollSpy, mobile collapse
├── assets/img/                 # Images: speakers/, organizers/, logos/
├── template/index_template.html# Starting point for a new edition
├── previous/                   # Archived past editions + list.html index
└── MigrationNotes.md           # Notes for archiving / starting an edition
```

`index.html` is organized into `<section>` blocks: `#about`, `#schedule` (with a Presentations subsection), `#speakers`, `#organizers`, and `#map`. Editing the site means editing this HTML directly.

## Developing & previewing

Open `index.html` directly in a browser, or serve the repo root with a static server:

```bash
python3 -m http.server
# then visit http://localhost:8000
```

A VS Code launch config (`.vscode/launch.json`, "Open index.html", Chrome) is also provided.

> **Note on paths:** the root page uses root-absolute paths (`/css/styles.css`, `/assets/...`). These resolve on GitHub Pages and when served from the repo root, but break when opened via `file://` from a subdirectory. Pages under `previous/` use relative paths (`../css/...`) instead.

## Common workflows

**Start a new edition** — copy `template/index_template.html` and fill in the content.

**Archive the current edition** (see `MigrationNotes.md`):

1. Add an entry to `previous/list.html`.
2. Move the current `index.html` and its `assets/` into `previous/`.
3. Add the cross-links to the navbar (a "Previous" link and a "Current Edition" link).

## Deployment

Push to `main`. GitHub Pages serves the repository root automatically.

## Previous editions

- [CVPR 2025](https://fmv-cvpr25workshop.github.io/)
- [CVPR 2024](https://fmv-cvpr24workshop.github.io/)
