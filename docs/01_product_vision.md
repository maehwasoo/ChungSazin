# Product vision

## What we’re building

ChungSazin is an interactive web poetry book: it presents poems and images as a cohesive piece of digital art.
The experience should feel *authored* (like a single artwork), not like a generic content site.

The site also includes a clear path to purchase the physical book (via an external link), without turning the experience into a storefront.

## Core experience pillars

### 1) Poem-first

- Typography is the primary “UI”.
- Whitespace and rhythm (line breaks, stanza spacing, scroll pacing) are part of the artwork.
- Interactions should never make reading harder.

### 2) Intentional interactivity

Interactivity exists only when it:

- clarifies meaning,
- adds emotional texture (timing, reveal, emphasis),
- or connects poem ↔ image in a way print cannot.

If an effect is “cool” but does not support the poem, it is excluded.

### 3) Cross-device, responsive by design

- Mobile: one-handed reading, consistent scroll, minimal precision gestures.
- Desktop: larger typographic presence, optional richer interaction, but same core narrative.

### 4) Performance and accessibility are part of the artwork

Smoothness and comfort are non-negotiable:

- avoid stuttery scroll and heavy GPU usage,
- support reduced motion,
- support dynamic type sizing where possible,
- preserve text selection and copy (poetry is text).

### 5) “Content-as-code” first, CMS later

Early on, works are stored in the repo (JSON/MD/MDX + assets). This enables:

- fast iteration,
- full reviewability,
- easy branching and experimentation.

A CMS can be added once the content model stabilizes.

## Audience and contexts

- People who want to *read* and feel something (quiet, deliberate pacing).
- People who want to *browse* and discover visually.
- People who have the book or are considering buying it.

## Success criteria (qualitative)

- The poem is readable and memorable.
- The interaction feels authored, not gimmicky.
- The purchase link feels natural, not intrusive.
- The site runs smoothly on an average mobile device.

## Non-goals (initially)

- Full e-commerce checkout inside the site
- Heavy 3D as a baseline requirement
- A complex CMS/admin system before the content model is proven
