# Information architecture (IA)

This IA aims to balance two needs:

1) **Deep reading** of a single work (poem-first), and  
2) **Light browsing** across works (discovery + a path to purchase).

## Primary site map (MVP)

- **Works index**: `/` (or `/works`)
  - entry point to each work
  - optional short intro to the collection
- **Work reader**: `/works/:slug`
  - the authored interactive experience for a single work
- **About / Credits**: `/about` (optional for MVP)
  - author/artist credits, contact, publication info
- **Purchase redirect/info**: `/buy` (optional)
  - can be a stable URL that redirects to the current purchase link

> Note: keeping routes minimal supports an “artwork” feel.

## Global navigation principles

- Prefer **one primary navigation action** at a time:
  - from index → open a work,
  - from a work → return to index.
- Avoid full nav bars and dense menus unless the collection size requires it.
- Keep UI chrome subtle so typography remains the main visual object.

## Works index layout options

Choose one; keep the other as a future option.

### Option A: Vertical list (recommended for poetry)

- Large typography and generous spacing
- Each work has:
  - title,
  - 1-line teaser (optional),
  - a cover image or abstract glyph (optional)
- Better on mobile, feels “book-like”

### Option B: Grid gallery (recommended for image-forward collections)

- Visually scannable
- Risk: the poem becomes secondary if thumbnails dominate

## Work reader layout (core)

The Work reader is the core “canvas”. It should be designed around:

- **Poem area** (text)
- **Image layer(s)** (background / inline / sidecar)
- **Interaction layer** (motion/scroll/gesture, optional and progressive)

### Reader chrome

Keep controls minimal but reliable:

- Back to index (always available)
- Progress indicator (optional; can be subtle)
- Purchase CTA:
  - visible but not disruptive
  - accessible focus order

## Purchase CTA placement (recommended)

Use two placements to avoid being intrusive while remaining discoverable:

1) **End-of-work CTA**: after finishing the poem/experience  
2) **Subtle persistent CTA**: a small “Buy the book” link in a corner/header

Avoid modal popups as the primary purchase path.

## Multi-mode reading support (architecture requirement)

Even if the MVP ships one mode, the IA should allow mode variants:

- Scroll narrative (default candidate)
- Paging (tap/click to advance)
- Object interaction (localized “scenes”)

Implementation note: treat “mode” as a property of a Work (or a user toggle) rather than as a separate site section.
