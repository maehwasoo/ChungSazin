# Delivery plan (phased)

This plan is designed to produce a high-quality “vertical slice” early, then scale to multiple works.

## Phase 0 — Project setup (foundation)

Outcome: a working skeleton with styling + Storybook so we can iterate on the artwork.

- Choose build tool and routing strategy (open decision)
- Set up:
  - React + TypeScript
  - vanilla-extract (tokens + global styles)
  - Storybook
- Create minimal routes:
  - Works index
  - Work reader view

Acceptance criteria:

- “Hello work” renders with real typography tokens
- Storybook renders with the same tokens/styles as the app

## Phase 1 — One-work vertical slice (MVP core)

Outcome: one complete work from entry → reading → purchase CTA.

- Implement Works index (simple list)
- Implement Work reader (single mode recommended: scroll narrative)
- Add purchase CTA placement (subtle persistent + end-of-work)
- Implement content-as-code for one work

Acceptance criteria:

- Works index → open work → finish reading → purchase link is reachable
- Mobile and desktop layouts are both comfortable
- Reduced-motion path is available

## Phase 2 — Scale to multiple works

Outcome: add more works without rewrites.

- Add content organization for multiple works
- Add navigation next/previous (optional)
- Expand Storybook coverage for poem/rendering components

Acceptance criteria:

- Adding a work is “mostly data + assets” (not new UI code)
- No regressions in typography and spacing

## Phase 3 — Quality pass (performance + a11y + polish)

Outcome: the site feels smooth and intentional across devices.

- Optimize images and loading
- Validate accessibility (keyboard, focus, contrast)
- Confirm reduced-motion experience

Acceptance criteria:

- Scroll and transitions feel smooth on mobile
- Core flows are usable with keyboard

## Phase 4 — Optional expansions

Only after the core reading experience is strong:

- Add additional reading mode(s) (paging, object scenes)
- Add localized 3D/WebGL scenes (if meaningful)
- Add CMS/admin workflow (if content updates become frequent)
