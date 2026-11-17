# Indie Hackers Puerto Rico

The indiehackerspr.com website, built with [Hugo](https://gohugo.io/) v0.170+ and Tailwind CSS v4, deployed on Netlify.

## Develop

```sh
npm install
npm run dev     # http://localhost:1313
npm run build   # production build into public/
```

## Editing content

Anyone can open a PR, and most people do it through a coding agent: [AGENTS.md](AGENTS.md) has the rules agents follow,
and [/contribuye](https://www.indiehackerspr.com/contribuye/) has the prompts to paste.

- **Members:** `data/miembros.yaml` (bio is Markdown) + photo in `assets/images/miembros/`
- **Remote-work places:** `data/lugares.yaml` + photo in `assets/images/lugares/`
- **Links** (Slack, Luma, X, YouTube, add-a-place form): `[params.links]` in `hugo.toml`
- **Weekly Mastermind** (time, platform, host): `[params.mastermind]` in `hugo.toml`

Photos are resized and converted to WebP at build time, so drop in originals.

**Icons and social images** (`static/favicon.ico`, `apple-touch-icon.png`, `icon-*.png`, `images/logo.png`,
`images/og*.png`) are drawn by `python3 scripts/og.py` from `static/favicon.svg`. To give a page its own OG image, add
it to `OG` in that script and set `images:` in the page's front matter.

## Layout

- `layouts/home.html` — home page sections
- `layouts/trabajo-remoto/section.html` — remote-work guide with type filters
- `layouts/contribuye/section.html` — "contribute with your agent" page with copyable prompts
- `layouts/_partials/` — header, footer, logo (SVG), member and place cards, CSS pipeline
- `assets/css/main.css` — Tailwind entry and color tokens (Puerto Rico flag: celeste, flamboyán, navy, plus adoquín)

## Deploy

Netlify reads `netlify.toml`. Bump `HUGO_VERSION` there when upgrading Hugo locally.
