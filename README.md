# Opal-Enablement---Skills

# Optimizely Opal: Skills Guide — Interactive Training Walkthrough

A polished, gamified single-page training guide that teaches teams how to configure, deploy, and manage **Opal Skills** (formerly Instructions) across an Optimizely organization.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)

![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)

![Vanilla JS](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

![License](https://img.shields.io/badge/License-Internal-lightgrey)

## Overview

A zero-dependency, self-contained HTML page designed as an internal enablement resource for Optimizely teams and customers. It walks users through the complete Skills lifecycle — from understanding what skills are to creating, scoping, and managing them — with embedded knowledge checks that gate lesson completion.

## Features

### Content & Structure

- **7 guided sections** — Overview → Anatomy → Scopes → Activation & Relevancy → Implementation Walkthroughs → Management → Reference Examples
- **Session Recap pipeline** — Visual 4-step summary with responsive horizontal/vertical layout
- **3 creation methods** documented with step-by-step screenshots (Conversational, Manual Org, Manual Personal)
- **Scoping keywords table** — Best practices for trigger precision with Do/Don't patterns

### Gamification & Interactivity

- **5 knowledge checks** distributed across sections, gating the completion button
- **Quiz retry system** — Wrong answers only disable that option; the correct answer stays clickable with a "Try again" prompt
- **Score tracker** (fixed bottom-left) — 5 pip indicators showing green (correct), red (wrong), or empty (unanswered)
- **Completion gate** — "Complete Training Session" button stays disabled until all 5 checks are answered
- **Confetti celebrations** — Fires on correct answers and final completion (lazy-loaded, not bundled)
- **Interactive skill pills** — Click to toggle active/disabled state in the demo card
- **Copy-to-clipboard** on reference examples with visual feedback and fallback for older browsers

### UX & Performance

- **Scroll-reveal animations** via `IntersectionObserver` (no scroll-event jank)
- **Glass-effect sticky navbar** with scroll spy, active section highlighting, and reading progress bar
- **Mobile hamburger menu** with slide-down animation and auto-close on navigation
- **Back-to-top button** — Appears after 600px scroll with smooth behavior
- **Image lightbox** — Click any screenshot to zoom; close via click-outside, close button, or `Escape`
- **Lazy-loaded images** with `loading="lazy"`, `decoding="async"`, and `content-visibility: auto`
- **Confetti script deferred** — Only fetched on first quiz interaction, not on page load
- `requestAnimationFrame`**-throttled** scroll handler with passive listeners
- **Safari support** — `-webkit-backdrop-filter` for glass nav and mobile menu

### Design System

- **Sean Halpin-inspired palette** — Warm cream background (`#EDE7DE`) with 4 accent colors (green, blue, coral, yellow)
- **Section-specific underline colors** for visual rhythm across headers
- **Bouncy cubic-bezier transitions** on cards, buttons, and interactive elements
- **Responsive** — Fully functional from mobile to ultrawide with Tailwind utility classes

## Tech Stack

| Layer | Technology |
| --- | --- |
| Markup | Semantic HTML5 |
| Styling | Tailwind CSS (CDN) + custom CSS variables |
| Interactivity | Vanilla JavaScript (ES5-compatible, no build step) |
| Animations | CSS transitions + `IntersectionObserver` |
| Confetti | [canvas-confetti](https://github.com/catdad/canvas-confetti) (lazy-loaded CDN) |

## Quick Start

```bash
# No build step required — just open the HTML file
open index.html

# Or serve locally
npx serve .
```

## File Structure

```
├── index.html          # Self-contained single-file application
└── README.md           # This file
```

All styles, scripts, and logic are inlined. Images are hosted on `support.optimizely.com`. No external dependencies beyond Tailwind CDN and the optional confetti library.

## Browser Support

| Browser | Status |
| --- | --- |
| Chrome 90+ | Fully supported |
| Firefox 90+ | Fully supported |
| Safari 15+ | Fully supported (webkit prefixes included) |
| Edge 90+ | Fully supported |
| Mobile Safari / Chrome | Responsive layout with hamburger nav |

## Customization

### Adding a new quiz

1. Add a `<section>` with a `.quiz-card` container and `id="quiz6"`
2. Include buttons with `data-correct="true/false"` and `onclick="handleQuiz(this,'quiz6',6)"`
3. Add a `<div class="score-pip" id="pip-6">` to the score tracker
4. Update `totalQuizzes` from `5` to `6` in the `<script>` block

### Changing the color palette

Edit the CSS custom properties in `:root` — all components reference these variables:

```css
:root {
  --accent-green: #00B171;
  --accent-blue: #3E8BFF;
  --accent-coral: #FF5A5A;
  --accent-yellow: #FFC82C;
}
```

## License

Internal use — Optimizely, Inc.
