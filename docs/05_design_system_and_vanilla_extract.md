# Design system + vanilla-extract

This project’s “design system” is not a UI kit. It is a set of tokens and rules that keep the site feeling like one authored artwork.

`vanilla-extract` is used to:

- centralize tokens (typography, spacing, color, motion),
- keep component styles co-located and type-safe,
- avoid runtime styling overhead.

## Design tokens (what to standardize)

### Typography tokens (highest priority)

Poetry lives and dies by typography. Standardize:

- font families (serif/sans/mono, variable fonts if used)
- font sizes (scale, min/max on mobile vs desktop)
- line-height per text style
- letter spacing (tracking)
- paragraph/stanza spacing rules

Recommended: define a small set of text roles, not dozens:

- `display` (index titles)
- `title` (work title)
- `poem` (main poem body)
- `caption` (image captions)
- `ui` (buttons/links)

### Spacing tokens

- global grid / base spacing unit
- stanza gap vs line gap
- page margins and safe areas (mobile notch)

### Color tokens

Keep it simple unless the artwork requires complex palettes:

- background / foreground
- subtle muted text
- focus ring color
- accent (for links/CTA)

### Motion tokens (for authored feel)

Motion is part of the “voice”:

- durations (short/medium/long)
- easing curves (one or two, consistent)
- distance scales (small/medium)
- opacity levels

## vanilla-extract conventions (recommended)

### File placement

- `src/styles/`
  - `tokens.css.ts` (theme tokens)
  - `theme.css.ts` (theme contract + themes)
  - `global.css.ts` (global style resets, minimal)

Component styles:

- colocate `Component.css.ts` next to the component.

### Avoid “random” values

Rule: if you repeat a value, make it a token.
If you use a value only once, ask if it’s truly unique or a missing token.

### Variants and recipes

If a component has variants (e.g. size, emphasis), use a recipe-like pattern:

- variant keys are typed (prevents invalid combinations)
- variants are documented in Storybook

### Utility-style layout (optional)

If you want Tailwind-like ergonomics while staying type-safe, consider:

- “sprinkles” style utilities (typed atomic properties)
- a small set of layout primitives (`Box`, `Stack`, `Inline`, `Text`)

This keeps markup clean and avoids long class lists.

## Poem typography rules (practical)

### Preserve authored line breaks

Poems should render line breaks exactly as authored.
Implementation options:

- render each line and insert `<br />`, or
- render as a block with `white-space: pre-wrap` (only if the authoring format supports it cleanly).

### Stanza spacing

Stanza spacing should be stable across devices:

- use tokens for stanza gap
- avoid collapsing margins that change unexpectedly across layouts

### Responsive readability

For mobile:

- avoid too-large text that forces constant scrolling
- avoid too-small text that breaks emotional impact

For desktop:

- avoid extremely long line lengths (measure width)
- prefer max-width constraints for poem blocks

## Dark mode (open decision)

If dark mode is desired:

- treat it as a theme (token swap), not per-component hacks
- ensure poem contrast remains comfortable (not pure white on pure black)

If dark mode is not desired:

- still keep tokens flexible so later theming is not painful
