# Risk register

This project is intentionally “artwork-like”, so the biggest risks are not only technical.

## Product/UX risks

### Risk: Interactions overwhelm reading

- Symptom: users can’t comfortably read the poem.
- Mitigation:
  - poem-first rules (typography wins)
  - limit interaction moments
  - reduced-motion support

### Risk: Too much UI chrome breaks the “artwork” feel

- Mitigation:
  - minimal global nav
  - consistent, subtle CTA placements

## Technical risks

### Risk: Mobile performance issues (jank, heat, battery)

- Mitigation:
  - progressive enhancement
  - avoid heavy continuous effects
  - lazy-load heavy scenes (3D, complex timelines)

### Risk: Styling drift over time

- Mitigation:
  - tokens in vanilla-extract
  - Storybook as a living spec
  - avoid one-off values

### Risk: Content model becomes too complex

- Mitigation:
  - keep schema simple and explicit
  - encode interaction intent, not raw animation timelines, in content
  - build reusable scene types

### Risk: SEO/shareability suffers with SPA-only rendering

- Mitigation:
  - consider SSG/SSR if discoverability matters
  - ensure stable URLs and metadata per work

## Process risks

### Risk: Overbuilding before proving the feel

- Mitigation:
  - build one-work vertical slice early
  - review on real devices
  - only then scale patterns
