# Storybook workflow

Storybook is used to build and review the site as a set of authored building blocks.

## Goals

- Develop components in isolation (typography, poem renderer, layouts, CTAs).
- Validate edge cases (long poems, short poems, image-heavy works).
- Review responsive behavior and reduced-motion behavior without running the whole app.

## Story structure (recommended)

Organize stories by “meaning”, not by file structure:

- `Foundations/`
  - typography scale
  - spacing samples
  - color palettes / themes
- `Primitives/`
  - `Text`, `Link`, `Button` (minimal)
  - layout primitives (`Box`, `Stack`) if adopted
- `Poem/`
  - `PoemBlock`, `Stanza`, `Line`
  - annotation patterns (if any)
- `Work/`
  - `WorkHeader`, `WorkFooterCTA`
  - image compositions
- `Reader/`
  - scroll narrative reader
  - paging reader (if added)

## Required stories for each component

For any component that ships:

- **Default**: the normal, intended use
- **Variants**: size/emphasis states (if applicable)
- **Edge cases**:
  - long text
  - empty optional fields
  - narrow viewport and wide viewport
- **Reduced motion**: if the component animates

## Addons (optional but useful)

These are typical Storybook capabilities to consider:

- viewport testing (mobile/desktop)
- accessibility checks (a11y addon)
- interaction tests for click/tap flows (when needed)

The goal is not to add many tools; it’s to catch regressions early.

## vanilla-extract notes

vanilla-extract styles are compile-time, so:

- keep tokens consistent
- ensure stories demonstrate token-driven variants (not hard-coded overrides)

## Review checklist

- Is the poem still readable?
- Does the component feel like part of the same artwork (tokens respected)?
- Does it work with keyboard and reduced motion?
- Does it degrade gracefully without optional effects?
