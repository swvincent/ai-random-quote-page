# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file static web page (`index.html`) that displays a random inspirational quote on load and cycles through quotes on button click.

## Development

No build step, package manager, or server required. Open `index.html` directly in a browser, or use any static file server:

```bash
npx serve .
# or
python -m http.server
```

## Architecture

- **`style.css`**: Dark theme using CSS custom properties (`--ink`, `--cream`, `--gold`, `--muted`). Decorative corner marks via `body::before/::after`. Card fade-in on load via `@keyframes fadeUp`.
- **`quotes.json`**: Array of quote objects with `text`, `author`, and `source` fields. Sources include attribution context and year in parentheses.
- **`index.html`**: Markup and JS logic. Loads quotes via `fetch('quotes.json')` on page load. `getRandomQuote()` avoids repeating the last shown quote. `nextQuote()` fades out the three text elements, swaps content, then fades in.
- **External dependencies** (CDN only): Bootstrap 5.3.3 (CSS + JS bundle), Google Fonts (Playfair Display, Lato).

> Because quotes are loaded via `fetch`, the page must be served over HTTP — opening `index.html` directly as a `file://` URL will fail due to CORS restrictions.

## Styling Conventions

- Dark background (`#0d0d0d`) with light text (`#e8e2d9`) — variable names (`--cream`, `--ink`) reflect an inverted paper metaphor.
- Silver/muted accent color (`#c0c0c8`) used for decorative elements and borders.
- Quote text uses Playfair Display italic; UI labels use Lato.
