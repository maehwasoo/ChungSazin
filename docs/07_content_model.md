# Content model (static-first, CMS-ready)

This document defines a content model that works well when content is stored in the repo,
and can later map to a CMS/API with minimal UI changes.

## Core concepts

- **Work**: a single poem + images + optional interactions, presented as one unit.
- **Poem**: structured text (stanzas → lines), plus optional annotations.
- **Asset**: images (and later audio/video) referenced by a Work.
- **Scene**: an authored interaction segment (scroll range, paging step, or gesture moment).

## Minimal Work schema (proposed)

The model should be explicit and boring at the data level. Complexity belongs in presentation/interaction layers.

### Work (fields)

- `id`: stable identifier (string)
- `slug`: URL slug (string)
- `title`: display title (string)
- `subtitle`: optional (string)
- `date`: optional publication/creation date (string)
- `tags`: optional list (string[])
- `purchase`:
  - `label` (string, e.g. “Buy the book”)
  - `url` (string, external)
- `poem`:
  - `stanzas`: array of stanza objects
- `assets`:
  - `images`: array of image objects
- `reader`:
  - default reading mode and per-work configuration
- `scenes` (optional):
  - interaction scene definitions

### Stanza

- `id`: optional stable id (string)
- `lines`: string[]
- `tone`: optional styling hint (e.g. “whisper”, “shout”) — avoid overusing

### Image asset

- `id`: stable id
- `src`: path or URL
- `alt`: alt text (required for accessibility)
- `caption`: optional
- `role`: `cover | background | inline | sidecar`
- `focalPoint`: optional (x/y) for responsive cropping decisions

## Interaction model (keep it small)

Interactions should be described at a high level and implemented as reusable scene types.

### Scene (proposed)

- `id`
- `type`: `scroll | page | object`
- `targets`: what it affects (e.g. stanza id, image id, a named layer)
- `trigger`:
  - for scroll: a range (start/end)
  - for paging: step index
  - for object: gesture event (tap/drag/hover)
- `effects`: a small list of effect descriptors (fade, translate, blur, reveal)

Rule: never encode raw animation curves for every line in content; encode intent and map to tokens.

## File organization (proposed)

Choose one of these patterns:

### Pattern A: One folder per Work (recommended)

- `src/content/works/<slug>/work.json`
- `src/content/works/<slug>/poem.json` (or `poem.md`)
- `src/content/works/<slug>/images/*`

Pros: work is portable, reviewable, self-contained.

### Pattern B: Central manifest

- `src/content/works.json` (list + references)
- `src/content/poems/*`
- `src/content/images/*`

Pros: easy to list works; cons: harder to move a work as a unit.

## CMS mapping (future)

To keep CMS integration painless:

- avoid coupling UI to file paths
- define a `Work` TypeScript type that matches the schema
- create one “adapter” layer that converts API responses → `Work`
