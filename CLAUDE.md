# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static website for the CVPR 2026 Workshop on Foundation Models for Medical Vision. It is a GitHub Pages site served from the repo `fmv-cvpr26workshop.github.io`, so the `main` branch is the live deployment — pushing publishes directly. There is no build step, package manager, or test suite; files are served as-is.

## Developing & previewing

- Open `index.html` directly in a browser, or use the VS Code launch config `.vscode/launch.json` ("Open index.html", Chrome). A simple static server (e.g. `python3 -m http.server`) also works.
- Asset/CSS/JS links use **relative paths** (`css/styles.css`, `assets/...`, `js/scripts.js`). These resolve correctly on GitHub Pages, when served from the repo root, and when opening `index.html` directly via `file://`. Pages under `previous/` use `../`-prefixed relative paths (`../css/styles.css`). The only intentionally absolute URLs are the Open Graph / Twitter `<meta>` image and URL tags in `<head>`, which require a full `https://fmv-cvpr26workshop.github.io/...` URL.

## Architecture & structure

- `index.html` — the current edition's single-page site. Content is hard-coded HTML organized into `<section>` blocks (`#about`, `#schedule`, `#speakers`, `#organizers`, `#map`). Editing the site means editing this HTML directly; speakers/organizers are repeated Bootstrap card blocks, schedule rows are table rows. Sections not yet ready (e.g. `#schedule`) are kept in the file but commented out.
- `css/styles.css` and `js/scripts.js` — vendored from the **Start Bootstrap "Agency" v7.0.11** theme (Bootstrap 5.1.3). `styles.css` is the full compiled theme (~12k lines); do not hand-edit it for content changes — override with page-level `<style>` blocks or by adding rules at the end. `scripts.js` handles navbar shrink-on-scroll, ScrollSpy, and mobile navbar collapse.
- `assets/img/` — organized into `speakers/`, `organizers/`, `logos/`. Add new headshots here and reference them from the card blocks.
- `template/index_template.html` — pristine starting point for a **new edition**. Copy it and fill in the `TITLE` placeholder and content.
- `previous/` — archived past editions (their own `index.html` copies, plus `list.html` which is the index of all past editions). `extra` is a scratch file of unused theme markup (portfolio, team modals) kept for reference.

## Common workflows (per `MigrationNotes.md`)

**Archiving the current edition when starting a new one:**
1. Add an entry to `previous/list.html`.
2. Move the current `index.html` and its `assets/` into `previous/`.
3. Add the cross-links to the navbar (a "Previous" link and a "Current Edition" link).

**Starting a new edition:** copy `template/index_template.html` and edit accordingly.

## Conventions

- The navbar "Competition" and "Previous" dropdowns use Bootstrap dropdown markup and link out to external URLs (Codabench competitions, prior workshop sites). Keep these in sync when editions/competitions change.
- Always use forward slashes in `<img src>` and other paths (`assets/img/...`). Older archived pieces occasionally used Windows backslashes (`assets\img\...`); these happen to work but should be normalized to forward slashes when touched.
