---
layout: default
title: Architecture — AlphaPost.io replica
permalink: /docs/architecture/
---

# Architecture — Technical structure

## Overview
AlphaPost.io is a server-rendered Jekyll marketing site (this repository) that documents the free creator-publishing platform. The platform itself (the SaaS behind alphapost.io) is conceptually composed of the following layers, described here for implementation reference.

## Tech stack
- **Frontend:** HTML5, CSS3 (Bootstrap 3 grid + custom design system), vanilla JavaScript, jQuery, Font Awesome.
- **Static site:** Jekyll (GitHub Pages), Liquid templates, kramdown Markdown, SEO and sitemap plugins.
- **Backend (platform concept):** API server, durable job queue for scheduling, worker for publishing, database, object storage for media references.
- **AI:** Server-side calls to Google Gemini using the user's own API key (never pooled by the platform).
- **Auth:** Email/password with verification; Google OAuth with account linking on matching email.
- **Encryption:** AES-256 for stored API keys and posting tokens.

## App flow
1. Visitor lands on the marketing site (this repo) → reads platform overview → signs up.
2. User registers / signs in → personal workspace created → onboarding checklist.
3. User optionally adds a Gemini API key (stored encrypted).
4. User connects publishing destinations via official provider OAuth flows.
5. User creates content (manual, AI draft, blog article, repurpose) → parent content item + channel variants.
6. (If approvals enabled) draft submitted for review → approved → schedulable.
7. User selects channels + publish-now or future time → durable job scheduled in UTC.
8. At publish time, worker calls provider adapters → records per-channel delivery → surfaces status.

## Database (platform concept)
- `users` — id, email, password hash, OAuth provider ids, email_verified, created_at.
- `workspaces` — id, owner_id, name, timezone, default_language, created_at.
- `workspace_members` — workspace_id, user_id, role (owner/admin/editor/reviewer/viewer).
- `ai_keys` — id, user_id, encrypted_key, key_provider, created_at, last_tested_at.
- `connected_accounts` — id, workspace_id, provider, provider_account_id, scopes, encrypted_token, expires_at, last_successful_at.
- `content_items` — id, workspace_id, title, body, caption, hashtags, cta, media_urls, status (draft/queued/scheduled/published/failed), created_by, approved_by, created_at.
- `content_variants` — id, content_item_id, channel, channel-specific body/caption/media, status.
- `schedules` — id, variant_id, publish_at_utc, status, created_at.
- `deliveries` — id, variant_id, channel, status (queued/publishing/published/partially_published/failed), provider_response, error, attempted_at, completed_at.
- `audit_log` — id, workspace_id, actor_id, action, target_type, target_id, metadata, created_at.
- `community_posts` / `community_comments` — discussion and moderation records.

## Folder structure (this repo)
```
/                         — Jekyll site root
  _config.yml             — site settings
  index.html              — homepage (uses front layout)
  _layouts/front.html     — replica landing page layout
  _includes/nav.html      — top navigation
  _includes/head.html     — HTML <head>
  _includes/scripts.html  — JavaScript assets
  css/custom.css          — replica design system
  js/                     — jQuery, Bootstrap 3, custom plugins
  vendor/bootstrap/       — Bootstrap 3.3.2 (CSS/JS/fonts)
  vendor/font-awesome/    — Font Awesome icons
  img/                    — brand and mockup images
  prd.md / architecture.md / rules.md / phases.md / design.md / memory.md  — planning docs
  _posts/                 — blog posts
  blog.html / privacy.html / 404.html — additional pages
```

## How components connect
- Marketing site → Jekyll → static HTML served by GitHub Pages.
- Platform API → authenticated user → content_item → variants → schedule → worker → provider adapter → destination platform → delivery record → audit log.
- User secrets (AI key, OAuth tokens) flow server-side only; decrypted in memory at publish time, never logged or returned to the UI.
