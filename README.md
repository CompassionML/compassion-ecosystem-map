# The Compassion AI Ecosystem — share-ready page

Standalone, self-contained static site for the Compassion AI Ecosystem map.
Co-branded as a collaboration between Sentient Futures and CaML. Deploys to
any static host (Cloudflare Pages, Netlify, GitHub Pages, etc.) without a
backend.

## What's in here

```
share/
├── index.html        # the whole page (HTML + CSS + JS inlined)
├── aimapBlank.png    # the parchment-style background map
├── logos/            # logo files for each org
└── README.md         # this file
```

## Local preview

Any simple static server. From this folder:

```bash
# Python
python -m http.server 8080
# then open http://localhost:8080
```

## Deploy to Cloudflare Pages (free)

### Easiest: drag-and-drop in the dashboard

1. Go to https://dash.cloudflare.com → **Workers & Pages** → **Create application** → **Pages** → **Upload assets**
2. Project name: e.g. `compassion-ecosystem` (becomes `compassion-ecosystem.pages.dev`)
3. Drag this whole `share/` folder into the upload area
4. Click **Deploy site** — done in ~30 seconds

The public URL is `<project-name>.pages.dev`. Custom domain optional.

### Alternative: Wrangler CLI

If `wrangler` is installed (it already is in the leaderboard repo):

```bash
cd share
wrangler pages deploy . --project-name=compassion-ecosystem
```

First run will open a browser for Cloudflare auth.

### Alternative: connect a GitHub repo

1. Push this `share/` folder (or its contents) to a new GitHub repo
2. In Cloudflare Pages, **Create a project** → **Connect to Git** → pick the repo
3. Build settings: leave build command empty, output directory `/`
4. Every push to main auto-redeploys

## Updating the org list

Org data lives in the `<script>` block near the bottom of `index.html`,
in the `ORGS` array. Each org is one object — edit/add/remove there.
Pin positions are in `x` and `y` as percentages of the bitmap.

The submission CTA is a `mailto:` link in the `<section class="submit">`
block — change the address as needed.
