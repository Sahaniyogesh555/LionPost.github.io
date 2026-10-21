---
layout: default
title: Project history — AlphaPost.io replica
permalink: /docs/memory/
---

# Project history

Records completed work, important decisions, known bugs, current progress, and the next task. Helps a new session resume work without guessing.

## Completed work
- Explored the two reference PDFs (`give.pdf` and `AlphaPost.io_ Platform Overview.pdf`) to understand the requested replica and platform content.
- Audited the existing Jekyll repo (`LionPost.github.io`): layouts, includes, CSS/JS assets, Bootstrap 3.3.2, Font Awesome, existing AlphaPost marketing content.
- Updated `_config.yml` for the AlphaPost.io replica (title, description, social, SEO, platform tagline).
- Rewrote `_includes/nav.html` — responsive AlphaPost.io navigation (Tools, How it works, Platforms, Community, Blog, Start free).
- Rewrote `_layouts/front.html` — complete replica landing page: hero, purpose & positioning, 16 tools grid, how-it-works steps, platforms, community, security, CTA signup, footer, go-to-top.
- Rewrote `css/custom.css` — modern design system (colours, typography, buttons, cards, sections, responsive overrides).
- Created planning docs: `prd.md`, `architecture.md`, `rules.md`, `phases.md`, `design.md`, `memory.md`.

## Important decisions
- Kept the Jekyll/GitHub Pages stack already present in the repo rather than introducing a new build toolchain.
- Used Bootstrap 3 classes (matching the vendored `bootstrap.min.js` v3.3.2 and jQuery) for grid/nav collapse, with a custom design system in `css/custom.css` for the modern look.
- Did not load external fonts or CDN assets (only hosts allowed in the sandbox); relied on vendored Bootstrap + Font Awesome + system font stacks.
- The replica presents AlphaPost.io branding/content per the Platform Overview PDF; planning docs follow `give.pdf`'s structure without claiming to be a pixel-for-pixel branded clone.

## Known bugs / limitations
- Bootstrap 3.3.2 is dated; newer component classes (e.g. Bootstrap 5 `data-bs-*`) will not work — use `data-toggle` / BS3 markup.
- `head.html` loads both `/js/bootstrap.min.js` and `/vendor/bootstrap/js/bootstrap.min.js` plus jQuery twice — harmless but redundant; leave as-is to avoid breaking existing pages.
- No live publishing backend exists yet; the site is the marketing/front-end replica only (platform SaaS is described in `architecture.md`).
- The X/Twitter `auth_token` session model described in the overview is sensitive; any implementation must carry a risk disclosure (see `rules.md`).

## Current progress
Phase 1 (marketing site) complete. Replica landing page live at `/`; planning docs at `/docs/prd/`, `/docs/architecture/`, etc.

## Next task
- Build and preview the Jekyll site locally to verify rendering, then deploy to GitHub Pages / custom domain.
