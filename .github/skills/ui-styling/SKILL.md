---
name: ui-styling
description: Create and review polished, accessible, responsive UI for Astro pages and components. Use when the task changes layout, spacing, typography, motion, hierarchy, or visual polish.
---

# UI Styling Skill

Use this skill when the work changes the feel of an Astro page or component, especially layout, spacing, typography, responsiveness, motion, or visual hierarchy.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Read the relevant file-specific instructions.
- Check the current visual language before changing layout or motion.

## Creative Foundation

Pick one visual direction before you write code. Do not mix directions without a reason.

- Editorial: large type, tight rhythm, restrained color, strong contrast.
- Technical: compact labels, clear modules, measured spacing, monospaced accents.
- Tactile: layered surfaces, subtle depth, soft shadow, material-like separation.
- Airy: generous whitespace, soft borders, calm pacing, fewer competing elements.

The page should communicate its primary job in one sentence. If that sentence is unclear, the layout is probably still generic.

## Structural Requirements

- Give the page one clear first-screen decision.
- Use hierarchy to tell the user what matters first, second, and third.
- Group related content into visibly distinct sections.
- Avoid equal-weight cards when the content does not deserve equal weight.
- Let content length influence sizing when that improves readability.

### Good: Single Focal Hero

- One clear headline.
- One supporting paragraph.
- One obvious action or next step.
- Supporting content appears after the hero has established the page's purpose.

### Good: Readable Content Grid

- Grid items have a title, a short body, and consistent spacing.
- Card heights do not need to match if the content is different.
- Typography communicates importance instead of relying on decoration.

### Bad: Generic Centered Stack

- Big title.
- Three floating cards.
- Everything has the same visual weight.
- Nothing tells the user what matters first.

## Motion Design

- Motion is optional.
- Animate opacity and transform before anything else.
- Respect `prefers-reduced-motion`.
- Use motion to clarify state changes, entrances, or emphasis.
- Do not add decorative motion that fights the content.

## Typography and Texture

- Build a clear type scale with visible contrast between levels.
- Keep line length and line height comfortable on small screens.
- Avoid default stacks if the repo already has a deliberate type system.
- Use texture sparingly: gradient washes, fine borders, subtle noise, or depth cues.
- Keep labels, helper text, and captions visually quieter than the primary content.

## Performance Guardrails

- Prefer static HTML and CSS first.
- Keep client JavaScript minimal.
- Avoid layout-thrashing properties when motion is required.
- Use responsive images and sensible sizes.
- Defer heavy effects on touch devices or low-motion environments.

## Astro Implementation Notes

- Keep the layout static-first unless interactivity is needed.
- Isolate interactive islands instead of making the whole page client-side.
- Share tokens through CSS variables when the same values repeat.
- Extract reusable pieces into components instead of duplicating style rules.
- Follow the repo's existing design language if one already exists.

## Reference Files

- [Layout Patterns](references/layout-patterns.md) - Static landing pages, content pages, feature grids, and common failure modes.

## Validation

- The hierarchy is obvious within a few seconds.
- Mobile, tablet, and desktop layouts do not overflow or collapse awkwardly.
- Contrast and focus states remain readable.
- Motion, if present, has a purpose.
- The final result matches the repository's stack and style conventions.

## Output

- Specific UI issues or improvements.
- File and line references when possible.
- A short fix recommendation for each item.
- A note on the visual direction chosen.
