# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`bits` is a static-site umbrella repo for one-off HTML demos — diagrams, recipes, interactive toys, micro-tools. Each "bit" lives in its own subfolder as a self-contained `index.html`. Deployed to Vercel at `bits.aliirani.com`.

This is the third leg of Ali's personal web triangle:

- **personal-site** (Next.js + Contentful) → identity, writing, journey at `aliirani.com`
- **talks** (Slidev decks) → presentations at `talks.aliirani.com`
- **bits** (static one-pagers) → small standalone HTML pages at `bits.aliirani.com`

## Layout

```
bits/
├── index.html        # landing page (hand-maintained list of bits)
├── vercel.json       # static config (clean URLs, trailing slashes)
├── README.md
└── <slug>/           # one folder per bit
    └── index.html
```

No build step. Vercel serves files directly.

## Adding a new bit

1. Create `<slug>/index.html` (kebab-case slug).
2. Add a `<li>` to the root `index.html` linking to `/<slug>/`. Keep the order most-recent-first.
3. Commit and push — Vercel auto-deploys.

## Conventions

- **Self-contained HTML:** styles/scripts inline or via CDN. No shared assets unless absolutely needed.
- **External APIs are fine:** Wikipedia REST, GBIF, etc. — called client-side, no backend.
- **No bundler / no framework:** if a bit grows complex enough to need one, promote it to its own repo.
- **Persian content welcome:** set `lang="fa" dir="rtl"` and use Vazirmatn via CDN (see `animal-classification/index.html`).
- **Always include Vercel Analytics + Speed Insights** in the `<head>` of every new bit. The scripts 404 harmlessly in local dev and auto-resolve on the deployed bits.aliirani.com domain:

  ```html
  <script defer src="/_vercel/insights/script.js"></script>
  <script defer src="/_vercel/speed-insights/script.js"></script>
  ```

## Deploy

- Hosted on Vercel as a static site.
- `vercel.json` enables `cleanUrls: true` (so `/foo/` works without `.html`) and `trailingSlash: true`.
- Subdomain: `bits.aliirani.com` (configure DNS + Vercel domain on first deploy).
