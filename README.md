# zoukpirates.com

Website for the Zouk Pirates, an organization for Brazilian Zouk events in
Boston, MA. Built with [Eleventy (11ty)](https://www.11ty.dev/) and deployed to
GitHub Pages.

## Development

```bash
npm install       # install dependencies
npm start         # local dev server at http://localhost:8080 with hot reload
npm run build     # build to _site/
npm run format    # reformat all files with Prettier
```

## Stack

- **Static site generator:** Eleventy 3.x
- **Templating:** Nunjucks (`.njk`) and Markdown
- **Styling:** Vanilla CSS with design tokens (`src/assets/css/tokens.css`)
- **Deployment:** GitHub Pages via GitHub Actions on push to `main`

## Project structure

```
src/
  _data/          # Global data (site metadata, etc.)
  _includes/      # Layouts and partials
  assets/
    css/          # tokens.css → reset.css → base.css → components/
    fonts/        # Self-hosted web fonts
    images/
  *.njk / *.md    # Top-level pages
```
