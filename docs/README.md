# ChungSazin Docs

This folder is the project’s “single source of truth” for product/UX/engineering decisions.
It is written to support an interactive web poetry book: *poems + images*, presented as a cohesive artwork, with an optional purchase CTA.

## Reading order (recommended)

1. `01_product_vision.md`
2. `02_requirements.md`
3. `03_information_architecture.md`
4. `04_technical_architecture.md`
5. `05_design_system_and_vanilla_extract.md`
6. `06_interaction_patterns.md`
7. `07_content_model.md`
8. `08_performance_accessibility_seo.md`
9. `09_storybook_workflow.md`
10. `10_delivery_plan.md`
11. `11_risk_register.md`

## Key decisions (current)

- Styling: `vanilla-extract` (type-safe CSS + design tokens)
- UI philosophy: “poem-first” (typography, rhythm, whitespace before effects)
- 3D/WebGL: optional and localized; do not make it a baseline requirement
- Content management: start as “content-as-code”, add CMS later

## Glossary (short)

- **Work**: a single poem + related visuals + interactions, presented as one unit.
- **Scene**: a timed/scroll/gesture-driven segment within a Work.
- **Reader**: the runtime that displays a Work (scroll mode / paging mode / object mode).
- **Token**: a shared design value (font scale, spacing, color, motion curve).
