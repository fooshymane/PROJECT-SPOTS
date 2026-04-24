# Spots

Spots is a small front-end image sharing app. It renders a user profile and a gallery of “cards” (posts), with common interactions like editing profile info/avatar, adding a new post, liking, deleting, and previewing images in a modal.

- Live site: https://fooshymane.github.io/se-project-spots/

## Features

- **Profile**
  - Edit profile name + description
  - Update avatar
- **Cards**
  - Render initial cards from an API
  - Add a new card (post)
  - Like/unlike a card
  - Delete a card
  - Preview a card image in a modal
- **Forms + UX**
  - Client-side validation
  - Loading states for submit actions
  - Modal close on overlay click / Escape

## Tech stack

- **UI**: HTML, CSS (BEM-style “blocks”), vanilla JavaScript
- **Tooling**: Webpack 5, Babel, PostCSS (Autoprefixer + cssnano)
- **CSS bundling**: CSS is imported from the JS entrypoint and extracted into a bundle via `mini-css-extract-plugin`

## Getting started

### Prerequisites

- Node.js + npm

### Install

```bash
npm install
```

### Run locally (development)

Starts webpack-dev-server and opens the app.

```bash
npm run dev
```

The dev server runs on `http://localhost:8080`.

### Build (production)

Builds into the `dist/` folder.

```bash
npm run build
```

## Project structure

High-level layout (key files/folders):

- `src/index.html`: HTML template used by HtmlWebpackPlugin
- `src/pages/index.js`: JS entrypoint (imports `./index.css` and bootstraps the app)
- `src/pages/index.css`: main stylesheet that `@import`s vendor + block styles
- `src/blocks/`: component-level CSS (BEM blocks)
- `src/scripts/validation.js`: form validation utilities
- `src/utils/Api.js`: API client wrapper
- `src/utils/helpers.js`: small shared helpers (button loading state, submit helper, etc.)
- `webpack.config.js`: build/dev configuration

## API

This project uses the TripleTen “Around” API.

- Base URL: `https://around-api.en.tripleten-services.com/v1`
- Auth: configured in `src/pages/index.js` via an `authorization` header

## Notes on CSS “not showing”

With this setup, CSS is bundled by webpack. If you open `src/index.html` directly in the browser, you’ll likely see unstyled HTML because the CSS bundle isn’t being generated/linked.

- Use `npm run dev` and visit `http://localhost:8080`, or
- Run `npm run build` and open `dist/index.html`

## Deployment

GitHub Pages should serve the **built output** from `dist/` (not the `src/` folder). If you use a GitHub Actions workflow, it should run `npm ci` + `npm run build` and then publish `dist/`.

## Demo video

Loom walkthrough: https://www.loom.com/share/d4aabd432445417983530611080bf86e
