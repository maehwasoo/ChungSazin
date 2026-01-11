# Interaction patterns

This project treats interaction as part of the authored voice.
Interactions are *meaningful*, *limited*, and *reliable*.

## Interaction design rules

1) **Reading is always possible**  
   The poem must remain readable even if effects fail or are disabled.

2) **Use few, intentional effects**  
   Prefer 2–3 strong moments over constant motion.

3) **Progressive enhancement**  
   Advanced scenes should be optional and degrade gracefully.

4) **Accessibility first**  
   Respect reduced motion and ensure keyboard navigation works.

## Pattern A: Scroll narrative (recommended default)

### What it is

The work unfolds as the user scrolls. Scroll position maps to “scene progress”.

### Why it fits poetry

- close to natural reading flow
- works on mobile with one hand
- supports subtle reveals and pacing

### Implementation guidelines

- Use transforms and opacity (cheap to animate) rather than layout changes.
- Avoid “scroll-jacking” (forcing custom scroll behaviors) unless absolutely necessary.
- Use semantic HTML for poem text; avoid rendering the poem inside `<canvas>`.

### Scene mapping options

- **Section-based activation**: activate a stanza when it enters the viewport (IntersectionObserver).
- **Progress-based mapping**: map scroll range to a continuous 0–1 value for a scene.

Keep the mapping logic separate from the poem rendering component.

## Pattern B: Paging / book-like

### What it is

Reading advances in discrete steps (tap/click/keyboard).

### Strengths

- strong sense of “pages” and composition
- good for carefully framed poem+image pairings

### Risks

- can feel game-like if over-animated
- requires more explicit UI controls (next/prev), which can add “chrome”

### Guidelines

- support keyboard (Arrow keys / Space) and tap
- allow scrolling as a fallback when content exceeds the viewport

## Pattern C: Object interaction (localized)

### What it is

Specific words/lines/images respond to tap/hover/drag.

### Use it when

- an interaction reveals structure (e.g., annotations, alternate readings)
- a visual metaphor needs direct manipulation

### Guidelines

- Prefer **tap** as the primary interaction (works on mobile + desktop).
- Hover can be a bonus, never the only path.
- Avoid precision drag as the only way to proceed.

## Motion system (consistency)

Motion should come from tokens:

- durations: short/medium/long
- easing: 1–2 curated curves
- distances: small/medium

Do not let every scene define bespoke timing; that breaks the “single artwork” feeling.

## Reduced motion support (required)

When `prefers-reduced-motion` is enabled:

- disable non-essential animations
- replace motion with instant state changes or simple fades
- keep the narrative structure intact

## Library choices (not decided)

Two common approaches:

- **Framer Motion**: React-friendly, declarative animations; good for UI + transitions.
- **GSAP**: powerful timeline control; good for authored sequences.

Either can work. The key is the *architecture*: scenes and effects should be swappable.

## Optional: 3D / WebGL scenes

If a work needs 3D:

- treat it as a scene type, loaded only when needed
- ensure the poem text remains in DOM, not in canvas
- provide a readable fallback for low-end devices
