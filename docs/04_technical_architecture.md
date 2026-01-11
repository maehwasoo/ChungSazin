# Technical architecture

This document proposes a frontend-first architecture for:

- React + TypeScript
- Storybook-driven component development
- `vanilla-extract` for styling (type-safe CSS + tokens)
- Optional TanStack Query for future CMS/API integration

## Architecture goals

- **Poem-first rendering**: typography is stable, readable, and responsive.
- **Progressive enhancement**: a work must be readable without advanced effects.
- **Composable interactions**: build “scenes” without tangling them with layout.
- **Maintainable content pipeline**: start static, evolve to CMS later.

## High-level layering (mental model)

1) **Content layer**: poem text + metadata + assets references  
2) **Presentation layer**: layout, typography, responsive structure  
3) **Interaction layer**: motion, scroll mapping, gesture handling  
4) **Platform layer**: routing, analytics, error handling, performance tooling

Keep these boundaries explicit to avoid “everything everywhere” complexity.

## Suggested project structure (when code is added)

This is a suggested structure; adjust to the chosen build tool.

- `src/app/`
  - app shell, routing, providers
- `src/pages/`
  - route-level components (Index, Work)
- `src/features/works/`
  - work reader, work index, work data access
- `src/content/`
  - static content files (initially)
- `src/shared/`
  - UI primitives, utilities, hooks
- `src/styles/`
  - tokens, global styles, themes (vanilla-extract)

## Styling approach: vanilla-extract

Why it fits this project:

- Tokens (font scale, spacing, color, motion) are centralized and reusable.
- Styles are co-located with components without runtime CSS-in-JS cost.
- Type safety reduces “silent” styling bugs and improves refactors.

See: `05_design_system_and_vanilla_extract.md`.

## State management

Prefer local, explicit state:

- Most state is UI-local (reading progress, active scene, image focus).
- Avoid a global state store until a real need appears.

### URL as state (recommended)

Use the URL for:

- which work is open (`/works/:slug`)
- optional mode selection (`?mode=scroll|page|object`)

Avoid encoding high-frequency values (scroll position) in the URL.

## Data fetching and TanStack Query

### MVP (static-first)

MVP can load content from local files:

- build-time imports (fast, type-friendly), or
- runtime fetch from a static JSON manifest (simple, decoupled).

### Later (CMS/API)

TanStack Query becomes valuable when:

- works list is fetched from an API,
- images are delivered via a media pipeline,
- previews/drafts exist.

Design rule: keep “data access” behind a small boundary (e.g. `worksApi`),
so switching from local files → API does not rewrite UI components.

## Storybook integration

Use Storybook for:

- UI primitives (typography, buttons/links, layout containers)
- Poem rendering components (stanza/line components)
- Interaction components (scroll mapping, scene transitions) in isolation

Storybook should reflect real constraints:

- responsive viewports
- reduced-motion scenarios
- long poem edge cases

See: `09_storybook_workflow.md`.

## Optional 3D / WebGL (Three.js / R3F)

Guideline: treat 3D as an **opt-in scene type**, not as the baseline renderer.

If used:

- lazy-load the 3D bundle only for the work/scene that needs it
- provide a readable fallback for low-end devices and reduced-motion users
- avoid blocking the poem text rendering on 3D initialization

## Observability (lightweight)

Even without a backend, capture basic signals:

- click-through on purchase CTA
- work opens (which work is viewed)
- performance hints (optional, later)

Keep analytics privacy-conscious and minimal.
