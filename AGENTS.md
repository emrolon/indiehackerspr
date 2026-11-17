# Contributing with an agent

You're probably here because someone from the Indie Hackers Puerto Rico community asked you (Claude Code, Codex, Cursor or
another coding agent) to change indiehackerspr.com for them. The site is a public repo, anyone can open a pull request,
and a maintainer reviews every one before it goes live. Netlify builds a preview for each PR.

## Make it easy for them

The person may not know Git, YAML or Hugo, and shouldn't have to. You do the work; they answer questions.

1. **Ask what they want**, if their prompt didn't say: join as a member, update their profile, add a place to work
   remotely, or fix something. One question at a time, in Spanish unless they wrote in English.
2. **Gather what you need** (see the rules below). Accept whatever is easiest for them: a LinkedIn or website link to
   read their bio from, a photo as a file path or a URL you download. Never ask them to edit a file.
3. **Write it for them** and show the bio or place note before committing. Change it until they're happy.
4. **Handle GitHub yourself.** If the GitHub CLI (`gh`) isn't installed, install it or tell them the one command to run.
   If it isn't logged in, have them run `gh auth login` and follow the browser steps. If they have no GitHub account,
   tell them it's free at github.com/signup, or that they can ask in the community Slack and a maintainer adds them.
5. **Finish with the PR link** and tell them a maintainer will review it, usually within a few days.

## What contributors can change

1. **Add or update their own member profile:** an entry in `data/miembros.yaml` and a photo in `assets/images/miembros/`.
2. **Add or update a place to work remotely:** an entry in `data/lugares.yaml` and a photo in `assets/images/lugares/`.
   The comments at the top of that file list the allowed values.
3. **Write a guest post for the blog** (`/blog/`): anyone can, member or not. See "Guest posts" below.
4. **Fix something on the site:** a typo, a broken link, a place that closed, a bug in a template.

Anything bigger (a new section, a redesign, new dependencies), open an issue first instead of a PR.

## Rules

- **Only change your own profile.** Don't edit, reorder or remove other members. Don't set `founder`. To update a
  profile, find the entry by the name the person gives you (the "update my profile" prompt on each member card includes
  it) and say in the PR how they're connected to it (for example, their GitHub account is linked in the bio), so the
  maintainer can tell it's really them.
- **Site content is in Spanish** (Puerto Rico). Write the bio or place note in Spanish, even if the person asked in English.
- **Member bio:** 2 to 4 sentences of Markdown about what the person builds or does, with at most 4 links (their
  product, site, LinkedIn, X, GitHub). Third person or first person, either is fine. No made-up facts: if you don't know
  something, ask the person.
- **Member photo:** square, at least 320×320, JPG or PNG, a clear face. Name it after the person in lowercase with dashes
  (`maria-rivera.jpg`) and set `photo` to that file name. Hugo resizes it at build time, so commit the original. If the
  person didn't give you a photo, ask for one; don't use a placeholder.
- **Place:** a real spot in Puerto Rico you or the person has worked from. `directions` is a Google Maps link. The
  photo is landscape, at least 640×400. `rating` is the person's honest score out of 10.
- Append new entries at the end of the YAML file. Keep the existing formatting.
- Don't touch `hugo.toml`, `netlify.toml`, `package.json` or the layouts unless the fix is about them.

## Guest posts

A post is a folder, `content/blog/<slug>/`, with an `index.md` and any images it uses next to it:

```markdown
---
title: "Cómo conseguí mis primeros 10 clientes desde Mayagüez"
date: 2026-11-20
description: One or two sentences on what the reader gets from it. Shows in the list, search results and link previews.
autor: María Rivera             # exactly as in data/miembros.yaml if they're a member: their photo and bio fill in
autorBio: Fundadora de Ejemplo.  # optional; one line, Markdown. Needed if they're not a member
autorLink: https://ejemplo.com  # optional; their site, LinkedIn or X
---
```

- **Interview the author, then write in their voice.** Ask what happened, what they learned, the numbers, what they'd do
  differently. Show the draft and change it until they say it sounds like them. Never invent facts, numbers, quotes or
  results: if something is missing, ask.
- **What fits:** first-hand stories of building something independent from or for Puerto Rico: first customers,
  pricing, failures, tools, taxes and laws, working from the Island. Doesn't fit: generic advice lists, press releases,
  thinly veiled ads, anything they didn't live. A link to their product is fine; a sales pitch isn't.
- **Spanish**, 500 to 2,000 words, `##` headings, short paragraphs. Use concrete numbers and dates where they have them.
- **Images:** optional, in the post folder, referenced by file name (`![Descripción](foto.jpg)`) with real alt text.
  Name one `cover.jpg` (landscape, ideally 1200×630) to use it at the top of the post and in link previews. A photo of
  the author that isn't a member's goes in the folder as `autor.jpg`.
- `slug`: lowercase, dashes, no accents (`primeros-10-clientes`). `date` is the day they open the PR.
- PR title: `Post: <title>`.

## Check your change

```sh
npm install
npm run build   # must finish without errors
npm run dev     # http://localhost:1313: look at the card you added
```

## Open the pull request

- Fork `gabrieljoel/indiehackerspr` (with `gh repo fork --clone` if you have the GitHub CLI), work on a branch, push and
  open the PR against `main`.
- Title: `Miembro: <name>`, `Lugar: <place>` or `Fix: <what>`.
- Fill in the PR template, and say which agent made the change.
