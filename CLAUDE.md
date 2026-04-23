# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static single-page website for **The Toshi Order** — a Bitcoin Ordinals NFT collection of 3,333 inscriptions. The site is hosted via GitHub Pages at `thetoshiorder.org` (configured by the `CNAME` file).

The entire site is a single self-contained file: `index.html`. There is no build system, no package manager, and no dependencies to install.

## Development

To preview the site locally, serve `index.html` with any static file server:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

Or open `index.html` directly in a browser. There are no build, lint, or test commands.

## Deployment

Pushing to the main branch automatically deploys via GitHub Pages. The `CNAME` file maps the custom domain `thetoshiorder.org` to the Pages site — do not delete or modify it.

## Architecture

Everything lives inside `index.html`:

- **CSS** — all styles are inline in `<style>` tags in `<head>`. CSS variables define the color palette (`--gold`, `--bg`, `--card`, `--border`, `--text`, `--dim`). Layout uses CSS Grid for the stats, species, and traits sections. All responsive breakpoints are at 900px and 600px.
- **HTML** — sections are: hero, lore/genesis (with stats grid), ethos quote, species grid, traits grid, fellowship, collect links, and footer. Sections use `.reveal` class for scroll animations.
- **JavaScript** — two small inline scripts at the bottom:
  1. An `IntersectionObserver` that adds `.visible` to `.reveal` elements as they scroll into view.
  2. A `tick()` function that polls `mempool.space/api` every 60 seconds to display live Bitcoin fee rate and USD price in the nav ticker (`#tf` and `#tp` elements).

## Key Conventions

- The gold/Bitcoin orange color is `#F7931A` (`--gold`). Use this consistently for all accent elements.
- All fonts are loaded from Google Fonts: `Cinzel` (headings/titles), `Rajdhani` (UI/labels), `EB Garamond` (body/lore text).
- Section labels use `.s-label` (small caps, gold), section headings use `.s-title` (Cinzel serif).
- The nav logo and hero glyph both embed the logo as a base64 JPEG data URI — update both if the logo changes.
- External links include: ordinals.com gallery, ordinalswallet.com, satflow.com, trio.xyz, X/Twitter accounts (`@thetoshiorder`, `@sat_toshis`), and Discord.
