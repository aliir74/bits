# bits

Ali Irani's one-page experiments — diagrams, recipes, micro-tools. Deployed at [bits.aliirani.com](https://bits.aliirani.com).

Each "bit" is its own folder under the repo root containing a single `index.html` (plus any assets it needs). No build step — Vercel serves the structure as-is.

## Layout

```
bits/
├── index.html                    # landing page (hand-maintained list)
├── animal-classification/
│   └── index.html
└── <slug>/                       # add more here
    └── index.html
```

## Add a new bit

1. Create `<slug>/index.html` with your page.
2. Add a `<li>` to the root `index.html` linking to `/<slug>/`.
3. Commit & push — Vercel auto-deploys.

## Deploy

Hosted on Vercel as a static site. `vercel.json` enables clean URLs and trailing slashes, so `/animal-classification/` works without `.html`.

## Conventions

- **Self-contained:** each bit's `index.html` should include all its styles/scripts inline or via CDN. Avoid shared assets unless really needed.
- **No build step:** if a bit needs bundling, it probably belongs in its own repo instead.
- **External APIs welcome:** Wikipedia, GBIF, etc. are fine — they're called client-side.
