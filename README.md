# Step Solar Website

Public marketing website for Step Solar Energy, split out of the original
`StepSolar` monorepo. This is a pure static site (HTML/CSS/JS + city landing
pages). The CRM lives in the separate `StepSolar-CRM` repo.

## Contents

- `index.html` — homepage (solar panel installation in UP & Bihar)
- `track.html` — customer tracking portal (`/track/:token`)
- `solar-panel-installation-*/` — per-city SEO landing pages
- `privacy-policy/` — privacy policy pages
- `Invoice.html`, `letterhead.html` — printable document templates
- `sitemap.xml`, `robots.txt`, `_headers`, `_redirects`

## Run locally

Any static file server works, e.g.:

```bash
python3 -m http.server 8080
```

For full API behaviour (lead form, tracking portal), proxy `/api/*` to the CRM
backend (see `netlify.toml` / `_redirects`).

## Deploy

The repo is Netlify-ready — `netlify.toml` publishes the repo root with no build
step and forwards `/api/*` to the CRM backend on Render.

## Repo split notes

- Admin subdomain (`admin.stepsolar.in`) redirects to the CRM — point
  `CRM_ORIGIN` in `index.html` and the `/api/*` + admin redirects in
  `_redirects`/`netlify.toml` at the deployed CRM.
- `crm.html` was moved to the `StepSolar-CRM` repo.
