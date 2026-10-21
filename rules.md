---
layout: default
title: Coding rules — AlphaPost.io replica
permalink: /docs/rules/
---

# Coding rules

These standards, dependencies, security requirements, and error-handling boundaries apply to anyone (human or AI) working on the AlphaPost.io replica site and platform code.

## Coding standards
- HTML5 semantic markup; accessible form controls, labels, and heading hierarchy.
- Responsive, mobile-first layout using the Bootstrap 3 grid plus `css/custom.css`.
- No inline styles except where unavoidable; prefer utility/component classes.
- JavaScript: unobtrusive, event-delegated, ES5-compatible where supporting older browsers; jQuery used only where already present.
- All user-facing strings in English; keep copy consistent with the platform overview.
- Images optimized; provide `alt` text; lazy-load offscreen images.

## Dependencies
- Jekyll (GitHub Pages), jQuery, Bootstrap 3.3.2, Font Awesome, Animate.css, WOW.js.
- Do not add new client-side dependencies without recording them in `rules.md`.
- Platform-side: use official OAuth flows and documented platform APIs; no unofficial scraping.

## Security requirements
- AI keys and posting tokens encrypted with AES-256 at rest; decrypted in memory only at publish time.
- Never expose secrets in the UI, logs, or client-side JavaScript.
- Server-side role checks on every protected action (owner/admin/editor/reviewer/viewer).
- Every workspace-owned record includes `workspace_id`; enforce workspace isolation.
- Email/password authentication requires email verification.
- Google OAuth supports account linking where email addresses match.
- Content publishing blocked if mandatory fields are missing.
- Generated text marked as AI-assisted until edited or approved by a user.
- X/Twitter session-token (`auth_token`) model, where used, must carry a prominent security and account-risk disclosure.
- Rate-limit provider adapters; surface "unavailable" for unsupported/restricted platform actions rather than simulating them.

## Error handling
- Publishing must be idempotent: retrying must not create duplicate posts.
- Each channel delivery recorded separately; partial success visible when one destination succeeds and another fails.
- Delivery state exposed: queued, publishing, published, partially published, failed.
- Provider errors normalized and shown in plain language; retries use backoff.
- Failed publishes never silently swallowed; always logged to `audit_log` and shown to the user.

## Boundaries the AI must follow
- Do not use AlphaPost trademarks, logos, copy, visual assets, or proprietary code beyond what is publicly described.
- Do not claim native cross-platform analytics (impressions, engagement, clicks, followers, revenue) — v1 links to native platform analytics only.
- Do not promise guaranteed reach, revenue, or engagement.
- Do not scrape credentials, cookies, or session tokens unless explicitly documented by the platform with risk disclosure.
- Do not simulate platform actions the provider does not support.
