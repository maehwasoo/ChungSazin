# Requirements

This document lists initial requirements for the interactive web poetry book. It is written for an MVP that can grow.

## Functional requirements (MVP)

### Content + navigation

- A **Works index**: list works (poems) with thumbnail/teaser and entry point.
- A **Work reader view**: display a single work (poem + images) in an authored layout.
- Basic **navigation**:
  - enter a work from the index,
  - return to index,
  - move to next/previous work (optional for MVP, but planned).

### Reading modes (support, not necessarily all at MVP)

The architecture must allow multiple presentation modes, even if only one ships first:

- **Scroll narrative** (default candidate): reading progresses with scroll.
- **Paging / book-like**: discrete pages (tap/click to advance).
- **Object interaction**: poem fragments respond to hover/tap/drag in limited areas.

### Purchase CTA

- Each work and/or the site should provide a **purchase link** (external).
- The CTA must be:
  - visible without being disruptive,
  - consistent in placement,
  - accessible (keyboard, screen reader).

### Responsiveness

- Works must render correctly on mobile and desktop (responsive layout).
- Touch and mouse interactions must both be supported (no “hover-only” meaning).

### Content delivery

- Works are loaded from local files initially (repo-managed).
- Later: works can come from an API/CMS without rewriting the UI.

## Non-functional requirements

### Performance

- Maintain smooth scroll and transitions on mobile.
- Avoid layout thrash (repeated forced reflows) during reading.
- Images must be optimized (responsive sizes, lazy loading where appropriate).

### Accessibility

- Respect `prefers-reduced-motion` (offer a low-motion path).
- Preserve text readability: contrast, line-height, and font sizing.
- Keyboard operation for core navigation (index ↔ work, CTA focus).
- Avoid interactions that require precision dragging as the only path.

### Reliability

- Works should load even on slower connections (static-first bias).
- Degrade gracefully if advanced effects fail (progressive enhancement).

### Maintainability

- Component-first development with Storybook.
- Design tokens in one place (typography, spacing, color, motion).
- Clear separation:
  - content model,
  - presentation (layout),
  - interaction (motion/gestures).

## Explicit non-goals (MVP)

- User accounts / sign-in
- Comments / community features
- Complex editor UI for content

## Open decisions

- Build tool + router choice (Vite + React Router vs Next.js, etc.)
- Initial reading mode to ship first (recommended: scroll narrative)
- Content format (JSON vs MD/MDX), based on how poems are authored
