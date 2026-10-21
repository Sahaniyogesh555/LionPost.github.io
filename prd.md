---
layout: default
title: Product Requirements Document — AlphaPost.io replica
permalink: /docs/prd/
---

# Product Requirements Document

## Product name
**AlphaPost.io (replica)** — free creator-publishing platform.

## One-line summary
A free, no-card, no-subscription creator-publishing platform that combines AI-assisted content production, scheduled distribution, blogging automation, research utilities, and a creator community under one account.

## Who will use it
- **Solo creator** — publishes short videos, posts, and blog articles; wants a low-cost workflow.
- **Blogger / affiliate publisher** — publishes SEO-oriented articles; wants to schedule blog content and auto-share to social.
- **Small content team** — needs shared drafts, review states, scheduled publishing, and activity tracking.
- **Community member** — wants to ask questions, share workflows, and learn from other creators.

## Product vision
Enable a creator to move from a topic idea to reviewed, scheduled, and published content across multiple destinations — all from a single free account, with no subscription or payment card.

## Core capabilities (v1)
1. Account creation (email/password or Google OAuth; email verification).
2. Secure AI-key configuration (user-supplied Google Gemini API key, encrypted at rest).
3. Platform connection (official OAuth / documented APIs where available).
4. Content generation or import (AI drafts, manual posts, blog articles, repurposing).
5. Editing and review (drafts, variants, approval workflow).
6. Scheduling (timezone-aware, UTC storage, durable job queue).
7. Publishing (idempotent, per-channel delivery, retry without duplicates).
8. Delivery-status monitoring (queued, publishing, published, partially published, failed).
9. Native-platform analytics links or imported metrics (no built-in cross-platform analytics dashboard in v1).
10. Community participation (discussions, comments, reactions, reports).

## Non-goals for v1
- Rebuilding every feature of every social network.
- Guaranteed reach, revenue, rankings, or engagement.
- Scraping credentials, browser cookies, or session tokens (except where the platform explicitly documents a session-token model, e.g. X, with clear risk disclosure).
- Circumventing social-platform APIs, rate limits, review processes, or payment requirements.
- Full video-editing software comparable to desktop NLEs.
- Deep multi-touch marketing attribution.
- Native post-performance analytics dashboard (impressions, engagement, clicks, followers, revenue).

## Success looks like
- First-time setup understandable in under 10 minutes.
- A scheduled post creatable in under 5 minutes after connecting an account.
- Unreviewed content never publishes by default.
- Publishing status, errors, retries, and connected-account health are clearly visible.
- User secrets are encrypted and never exposed in the UI or logs.

## Requirements reference
See `architecture.md` (technical structure), `rules.md` (coding rules), `phases.md` (roadmap), `design.md` (design system), and `memory.md` (project history).
