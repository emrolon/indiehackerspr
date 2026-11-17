# Indie Hackers Puerto Rico

The indiehackerspr.com website, built with [Hugo](https://gohugo.io/) v0.170+ and Tailwind CSS v4, deployed on Netlify.

## Develop

```sh
npm install
npm run dev     # http://localhost:1313
npm run build   # production build into public/
```

## Editing content

- **Members:** `data/miembros.yaml` (bio is Markdown) + photo in `assets/images/miembros/`
- **Remote-work places:** `data/lugares.yaml` + photo in `assets/images/lugares/`
- **Links** (Slack, Luma, X, YouTube, add-a-place form): `[params.links]` in `hugo.toml`
- **Weekly Mastermind** (time, platform, host): `[params.mastermind]` in `hugo.toml`

Photos are resized and converted to WebP at build time, so drop in originals.

## Layout

- `layouts/home.html` — home page sections
- `layouts/trabajo-remoto/section.html` — remote-work guide with type filters
- `layouts/_partials/` — header, footer, logo (SVG), member and place cards, CSS pipeline
- `assets/css/main.css` — Tailwind entry and color tokens (celeste, mango, flamboyán, adoquín, navy)

## Deploy

Netlify reads `netlify.toml`. Bump `HUGO_VERSION` there when upgrading Hugo locally.
