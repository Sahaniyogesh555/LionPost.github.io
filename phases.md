---
layout: default
title: Development roadmap — AlphaPost.io replica
permalink: /docs/phases/
---

# Development roadmap

Splits the project into manageable stages, with clear tasks and acceptance criteria for each phase.

## Phase 1 — Marketing site (this repository)
**Goal:** Publish a public-facing AlphaPost.io replica landing site on GitHub Pages.

Tasks:
- [x] Replica homepage: hero, purpose/positioning, 16 tools, how-it-works, platforms, community, security, CTA, footer.
- [x] Responsive navigation with scroll-to sections and mobile toggle.
- [x] Design system in `css/custom.css` (typography, buttons, cards, colors).
- [x] Site config (`_config.yml`) with title, description, social links, SEO.
- [x] Additional pages: blog, privacy, 404.
- [ ] Deploy to GitHub Pages / custom domain.

Acceptance criteria:
- Site loads on mobile and desktop; all anchor links scroll to sections.
- No broken images or links; SEO meta tags present.

## Phase 2 — Platform foundation
**Goal:** Authentication, workspaces, and encrypted AI-key storage.

Tasks:
- Implement email/password registration with verification.
- Implement Google OAuth with account linking.
- Create personal workspace on signup.
- Implement encrypted AI-key storage (AES-256) with add/test/remove/rotate.
- Server-side workspace role checks on all protected actions.

Acceptance criteria:
- First-time setup understandable in under 10 minutes.
- Secrets never appear in UI or logs; encrypted at rest.

## Phase 3 — Channel connections
**Goal:** Connect publishing destinations via official provider flows.

Tasks:
- Build provider adapters (Facebook Pages, Instagram, X, Pinterest, Telegram, TikTok, YouTube, Dailymotion, Blogger).
- OAuth connect / disconnect; show connection state, scopes, expiration, last successful post.
- Store tokens encrypted; refresh per adapter rate-limit policy.
- Show unsupported platform actions as unavailable, not simulated.

Acceptance criteria:
- User can connect at least one destination and see its health.

## Phase 4 — Content creation
**Goal:** Manual posts, AI drafts, blog articles, repurposing.

Tasks:
- Create parent content item with title, body, caption, hashtags, CTA, media.
- AI draft generation server-side via user's Gemini key; mark AI-assisted until edited/approved.
- Platform-specific variants derived from a parent item.
- Character-limit warnings per channel.
- Draft version history preserved.

Acceptance criteria:
- Scheduled post creatable in under 5 minutes after connecting an account.

## Phase 5 — Review and approval
**Goal:** Optional review workflow for teams.

Tasks:
- Submit draft for review; reviewer approves, rejects, or requests changes.
- Approved content becomes schedulable.
- Audit log records each change and publishing action.

Acceptance criteria:
- Unreviewed content never publishes by default.

## Phase 6 — Scheduling and publishing
**Goal:** Reliable, timezone-aware scheduled publishing.

Tasks:
- Store all schedule timestamps in UTC; display in workspace timezone.
- Durable job queue; worker publishes at scheduled time.
- Idempotent publishing; no duplicate posts on retry.
- Per-channel delivery recorded separately; partial success visible.

Acceptance criteria:
- Delivery state shown: queued, publishing, published, partially published, failed.

## Phase 7 — Community and measurement
**Goal:** Community and guidance to native analytics.

Tasks:
- Community discussions, comments, reactions, reports, moderation.
- Link to each destination's native analytics (no built-in cross-platform dashboard in v1).
- Keyword research and AEO checker tooling.

Acceptance criteria:
- Users can ask questions and share workflows; performance reviewed via native platform analytics.

## Current progress
Phase 1 complete (replica marketing site in this repo). Next: Phase 2.
