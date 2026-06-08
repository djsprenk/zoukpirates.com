# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with
code in this repository.

## Commands

```bash
npm install          # install dependencies
npm start            # dev server at http://localhost:8080 with hot reload
npm run build        # build to _site/
npm run format       # reformat all files with Prettier
npm run format:check # check formatting without writing
```

## Stack

- **Eleventy 3.x** — static site generator configured in
  [.eleventy.js](.eleventy.js)
- **Nunjucks** (`.njk`) — primary templating language
- **Markdown** — used for policy pages under `src/policies/`
- **Vanilla CSS** — no build pipeline; files are passed through as-is
- **Deployment** — GitHub Pages via GitHub Actions on push to `main`

## Architecture

All source is under `src/`. Eleventy outputs to `_site/` (not committed).

**Data layer** (`src/_data/`): JSON files are automatically available as global
template variables by filename — `site.json` → `{{ site.title }}`, `crew.json` →
`{{ crew }}`, `events.json` → `{{ events }}`.

**CSS load order**: `tokens.css` (CSS custom properties) → `reset.css` →
`base.css`. All three are linked from the base layout. Add component styles as
additional files linked in the layout or inline per-page.

**Layout**: Every page uses `layout: layouts/base.njk` in its frontmatter. The
base layout renders `{{ content | safe }}` inside `<main>` and uses a
`{% year %}` shortcode for the footer copyright year.

**Pages with data**: `src/crew.njk` and `src/events.njk` iterate over their
respective `_data` JSON arrays. To add/update crew members or events, edit the
JSON files directly.
