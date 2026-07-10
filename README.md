# Kolkata Metro Guide

A single-page, client-side Kolkata Metro route planner — no backend, no build step. Pure HTML/CSS/JS (Tailwind via CDN).

## Files in this repo
- `index.html` — the app (this is your old `metrooooo.html`, renamed — hosts require `index.html` as the entry point)
- `vercel.json` — config for Vercel deploys
- `netlify.toml` — config for Netlify deploys
- `.gitignore` — standard ignores

## Deploy — pick one

### GitHub Pages (simplest, free forever)
1. Push this folder to a GitHub repo.
2. Repo → **Settings → Pages** → Source: `main` branch, `/ (root)` folder → Save.
3. Live in ~1 min at `https://<username>.github.io/<repo-name>/`.

### Vercel
1. Push to GitHub.
2. [vercel.com/new](https://vercel.com/new) → import the repo → Deploy (no settings needed, it auto-detects static HTML).

### Netlify
1. Push to GitHub.
2. [app.netlify.com/start](https://app.netlify.com/start) → import the repo → Deploy.

All three are free and auto-redeploy on every `git push`.
