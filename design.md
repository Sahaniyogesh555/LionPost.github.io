---
layout: default
title: Design system — AlphaPost.io replica
permalink: /docs/design/
---

# Design system

Specifies colours, typography, spacing, components, responsive behaviour, accessibility, and interaction patterns for the AlphaPost.io replica.

## Colours
| Role | Hex | Usage |
|------|-----|-------|
| Primary | `#2563eb` | Buttons, links, icons, accents |
| Primary dark | `#1d4ed8` | Hover states |
| Background | `#ffffff` | Page surfaces |
| Background (alt) | `#f8fafc` | Secondary sections |
| Text (heading) | `#0f172a` | Headings, brand |
| Text (body) | `#334155` | Body copy |
| Text (muted) | `#64748b` | Captions, helper text |
| Border | `#e2e8f0` | Card borders, dividers |
| Success | `#10b981` | Published / connected states |
| Warning | `#f59e0b` | Partially published |
| Error | `#ef4444` | Failed / rejected |

## Typography
- Headings: `Catamaran`, Helvetica, Arial, sans-serif; font-weight 600–800; letter-spacing ~0.4px.
- Body: `Muli`, Helvetica, Arial, sans-serif; font-size 18px; line-height 1.6–1.7.
- Small/muted: 0.86–0.92rem; colour `#64748b`.

## Spacing
- Section padding: 70px vertical.
- Container max-width with `px-4 px-lg-5` gutters.
- Component padding: 18–26px; border-radius 10–12px on cards.
- Gap between flex items: 8–16px.

## Components
- **Navbar:** white, fixed-top, thin bottom border, brand mark + links + "Start free" CTA button; mobile hamburger toggle.
- **Buttons:** rounded (6–8px), font-weight 600, transition on hover; primary blue, outline, and hero variants.
- **Cards:** 1px border `#e2e8f0`, white background, border-radius 12px, subtle lift + shadow on hover.
- **Feature / step / trust boxes:** icon (42px circle or 2rem), heading, muted body text; centered.
- **Tools grid:** 4 columns on desktop, 2 on tablet, 1 on mobile; uniform card height.

## Responsive behaviour
- Navbar collapses to hamburger below the Bootstrap grid breakpoint.
- Grid columns stack: 4 → 2 → 1 as width decreases.
- Hero title scales down on smaller screens (3rem → ~2rem).
- Padding and font sizes reduce on mobile for comfortable tap targets (≥44px).

## Accessibility
- Semantic HTML: `<header>`, `<nav>`, `<section>`, `<footer>`.
- Heading hierarchy (h1 → h2 → h4) without skipping levels.
- All images include `alt` text; decorative icons hidden from assistive tech where appropriate.
- Colour contrast meets WCAG AA for text on primary/background colours.
- Focus states visible on interactive elements.
- Keyboard navigable; anchor links scroll smoothly to sections.

## Interaction patterns
- Hover lift on cards/tools; subtle shadow increase.
- Active states on buttons; disabled look when an action is unavailable.
- "Go to top" button fixed bottom-right; appears on scroll.
- Smooth scroll for in-page anchor links.
- External links open in same tab by default; social links open in new tab.
