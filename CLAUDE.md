# AJJ3-Site

**What it is.** Static marketing/brand website for AJJ³ (Arthur J. Jenkins III) — a top-level brand site (RF · Systems · Software) plus per-product landing pages for AJJ³ products under `apps/`. Pure HTML + CSS, no framework, no backend.
**Status.** Commercial — live brand/product marketing site (domain ajj3.us, ongoing commits marketing real product features).

## Stack & layout
- Plain HTML5 + a shared `styles.css`; page-specific CSS lives inline in `<style>` blocks. No JS framework, no build step.
- Top-level brand pages: `index.html` (home), `antenna.html`, `junction.html`, `joinery.html`, `contact.html`; plus `ajj3_animated_logo.html`.
- `apps/` — product landing pages, one folder each: `ajj3-brain/`, `WealthBuilder/`, `thrift/`, `my_llm/` (a redirect stub → `apps/ajj3-brain/`).
- `images/` — brand logos and cube favicons (PNG, multiple sizes).
- No entry point / no Python — open the `.html` files directly. Build/dist: files are served as-is (static hosting).

## How to run / build / test
```
# Preview locally (any static server), then open http://localhost:8000/
python3 -m http.server 8000
# No build, no test suite, no linter configured.
# Sanity check before commit: HTML tag balance (all pages currently balanced).
# Deploy: TODO — confirm host/mechanism (no CNAME / GH-Pages / Netlify / Vercel config in repo; domain is ajj3.us)
```

## Conventions (match existing code)
- Shared design tokens as CSS custom properties in `styles.css` `:root`; each product page redefines its own `:root` palette inline for a distinct aesthetic.
- Brand: "AJJ³" wordmark uses `<sup>3</sup>`; accessibility attributes present (`aria-label`, `role`, `aria-current`).
- Contact form posts via `mailto:` (`action="mailto:support@ajj3.us"`, `enctype="text/plain"`) — no server endpoint.
- Product pages marketed with explicit tiers/pricing in `<meta name="description">` and headings; keep copy consistent with the product's real features.

## Fragile / do-NOT-touch
- `apps/my_llm/index.html` is a meta-refresh + JS redirect stub to `/apps/ajj3-brain/`; don't turn it into a real page without intent.
- `index.html` inline cube CSS has hard-won fixes (comments mark `position`/`flex` tweaks that stop faces escaping / text pushing the cube out) — change cautiously.

## How I want you to work on this project
- Walk me through consequences before any destructive or behavior-changing edit: what the code does today, what changes, your confidence, and what could break — then wait for my yes/no. Batch only clearly-safe sweeps.
- Edit files directly on disk (I reload in PyCharm); don't hand me paste-in patches unless I ask.
- Prefer completing a half-built feature over deleting it, when that's a real option.
- After each change, run the smoke/compile check and report a clean state before moving on.
- I'm cautious about breaking working/production behavior — when in doubt, ask.

## Git
- Branch: master; remote: origin → https://github.com/king-aj3/AJJ3-Site.git
- Commit/push only when I ask.

## Pointers
- Product pages correspond to separate code projects (e.g. AJJ³ Brain, WealthBuilder, Thrift Reseller Tracker) — marketing copy should track those products' real capabilities.
