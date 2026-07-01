# NEXT_SESSION — AJJ3-Site

> End-of-session handoff. Overwrite at the end of each working block, then commit + push.
> Next session on any machine: `git pull`, open this folder in Claude Code, ask Claude to read CLAUDE.md + NEXT_SESSION.md and continue.

## Last worked: 2026-07-01 on Linux Threadripper (home)
## What I just did
- Rebuilt the **home hero cube** (`index.html`) to echo the ajj3-brain product mark:
  - Cube-face letters (A/J/J/3) + the "AJJ³" wordmark now use the **Iceland** webfont (SIL OFL, the same face ajj3-brain uses), loaded via a `<head>` Google-Fonts `<link>`.
  - Letters are genuinely **3D-extruded** — a small inline `<script>` stacks 20 translateZ slices per glyph (13px depth: a bright front cap over dark side walls) so they stand off each face and show real depth as the cube spins.
  - Added a **moving cast shadow** (`@keyframes ajj3-shadow-sweep` on the base slice) — darkened/pronounced, per-face-phased to one fixed light above-right, synced to the 18s spin.
  - The **"3" is now brass** `#BE8A36` (ajj3-brain's logo-3 color); its face darkened to navy `#0A2540` for contrast (~5:1). The wordmark `<sup>3</sup>` matches.
  - The **J's top bar shortened to ~75%** via a measured `clip-path` (same trim ajj3-brain applies to its logo J).
- All changes are confined to `index.html`. Verified in-browser (fonts loaded, extrusion layers, colors, clip, shadow animation).

## Current state
- Branch: master; committed + pushed. No build/test suite (static site); smoke check = HTML tag balance (clean).

## Next task (the ONE thing)
- Optional: regenerate `images/AJJ3_logo_horizontal_1600x560.png` (the top-left nav logo) so its "3" is brass too — CSS can't touch the PNG, so the nav 3 is still blue.

## Open questions / blockers
- Deploy mechanism still TODO (no CNAME / GH-Pages / Netlify / Vercel config in repo; domain is ajj3.us).

## Resume commands
```
# Preview locally, then open http://localhost:8000/
python3 -m http.server 8000
# No build, no test suite, no linter configured.
# Deploy: TODO — confirm host/mechanism (domain is ajj3.us)
```
