# AJJ3-Site

**What it is.** Static marketing/brand website for AJJ³ (Arthur J. Jenkins III) — a top-level brand site (RF · Systems · Software) plus per-product landing pages for AJJ³ products under `apps/`. Pure HTML + CSS, no framework, no backend.
**Status.** Commercial — live brand/product marketing site (domain ajj3.us, ongoing commits marketing real product features).

## Stack & layout
- Plain HTML5 + a shared `styles.css`; page-specific CSS lives inline in `<style>` blocks. No JS framework or build step (the only script anywhere is a small inline vanilla `<script>` at the end of `index.html`'s `<body>` that builds the hero cube's 3D-extruded letters).
- Top-level brand pages: `index.html` (home), `antenna.html`, `junction.html`, `joinery.html`, `contact.html`; plus `ajj3_animated_logo.html`.
- `apps/` — product landing pages, one folder each: `ajj3-brain/`, `WealthBuilder/`, `thrift/`, `my_llm/` (a redirect stub → `apps/ajj3-brain/`). `ajj3-brain/` also has `vs-local-ai.html` — a neutral "vs the local-AI apps" comparison (Ollama/LM Studio/Open WebUI/AnythingLLM/Odysseus), linked from its index nav + footer, reusing the product page's inline design.
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
- `index.html` **hero cube** is a hand-built CSS 3D system — change cautiously:
  - Faces carry `data-glyph` + per-face `--cap`/`--side`/`--sweep-delay`; the inline `<script>` stacks `LAYERS` translateZ slices per letter to extrude it `DEPTH`px (needs `transform-style: preserve-3d` on `.ajj3-face`). Letters use the **Iceland** webfont (loaded via a `<head>` `<link>`), matching ajj3-brain's mark.
  - The extruded "3" is brass `#BE8A36` on a darkened navy face (`#0A2540`, for contrast — brass on the old light-blue was ~1.2:1); the wordmark `<sup>3</sup>` matches. A/J/J faces stay blue.
  - `@keyframes ajj3-shadow-sweep` on the base (z=0) slice casts a per-face-phased moving shadow synced to the 18s spin (fixed light above-right).
  - The J's top bar is trimmed to ~75% by a measured `clip-path` on `[data-glyph="J"]` layers (Iceland J: stem right at x≥98, top bar reaches left; notch clips only x<79 & y<88).
  - Original hard-won `position`/`flex` fixes (marked in comments) still stop faces escaping / text pushing the cube out.
  - The top-left **nav** "AJJ³" is a PNG (`images/AJJ3_logo_horizontal_1600x560.png`), so its 3 is still blue — recoloring it to brass needs the image regenerated, not CSS.

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
