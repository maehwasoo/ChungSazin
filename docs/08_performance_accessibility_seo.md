# Performance, accessibility, SEO

This document defines practical quality standards for an interactive poetry site.
Here “quality” is part of the artwork: smoothness and comfort matter.

## Performance

### What to optimize for

- **Smooth reading**: stable layout, no jank while scrolling.
- **Fast entry**: a work opens quickly (text visible early).
- **Reasonable GPU usage**: avoid constant heavy effects on mobile.

### Common performance pitfalls (avoid)

- Animating layout properties (`top`, `left`, `width`, `height`) instead of transforms
- Triggering frequent reflow via reading layout in a loop
- Rendering poem text inside `<canvas>`
- Shipping large JS for effects that are only used in one work

### Practical guidelines

- Animate with `transform` + `opacity` when possible.
- Prefer CSS for simple effects; use JS animation libraries for complex authored sequences.
- Lazy-load heavy scene types (e.g. 3D/WebGL, complex timelines) per work/scene.
- Keep the poem text render path independent from optional effects.

### Images

- Use responsive images when possible (multiple sizes).
- Lazy-load non-critical images; avoid delaying first text render.
- Use `alt` text for meaning; decorative images can have empty alt when appropriate.

### Fonts

- Avoid too many font families/weights.
- Consider variable fonts to reduce downloads (if the chosen font supports it).
- Ensure fallback fonts keep line breaks readable (poetry layout sensitivity).

### Measuring (when implementation exists)

- Lighthouse / Web Vitals (local + production)
- Check low-end mobile device behavior
- Track regressions (before/after for heavy scenes)

## Accessibility (a11y)

Accessibility is not a “checkbox”; it protects the reading experience.

### Baseline requirements

- Semantic HTML for poem structure (headings, paragraphs, lists where appropriate).
- Keyboard navigation:
  - reach purchase CTA,
  - return to index,
  - advance pages (if paging mode exists).
- Visible focus states (do not remove focus rings without replacements).

### Reduced motion (required)

Honor `prefers-reduced-motion`:

- disable non-essential motion
- avoid scroll-bound parallax and continuous movement
- keep narrative structure intact (same content, calmer transitions)

### Text accessibility

- Keep contrast comfortable and consistent.
- Avoid tiny font sizes on mobile.
- Preserve text selection and copy.

## SEO (discoverability)

Poetry is content; basic SEO makes it findable and shareable.

### Metadata

- Page titles per work (work title + collection)
- Description / excerpt per work (if available)
- Social previews (OpenGraph/Twitter cards) for sharing

### Rendering strategy (open decision)

SEO is easier with SSR/SSG than with a pure client-side SPA.
If discoverability matters, prefer a build setup that supports:

- static generation of work pages (fast, shareable)
- stable URLs (`/works/:slug`)

If SPA is chosen initially, at least ensure metadata is handled and routing is stable.

## Analytics (minimal, privacy-conscious)

Track only what’s needed:

- purchase CTA clicks
- work opens (which slug)

Do not let analytics libraries dominate the bundle; keep it lightweight.
