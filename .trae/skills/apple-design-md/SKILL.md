---
name: "apple-design-md"
description: "Applies the Apple-style design system from the project's DESIGN.md. Invoke when optimizing UI visuals, interaction polish, layout hierarchy, or premium product-style presentation."
---

# Apple Design MD

Use this skill when the user wants the interface to feel more Apple-like, premium, restrained, product-first, or visually polished.

## What This Skill Does

- Applies the Apple design language stored in the project root `DESIGN.md`
- Optimizes visual hierarchy, spacing rhythm, typography, and interaction restraint
- Converts noisy or overly decorative UI into a cleaner, product-first presentation
- Keeps interactive color usage focused and consistent

## When To Invoke

Invoke this skill when:

- The user asks to optimize UI or视觉风格
- The user wants a cleaner, higher-end, Apple-like, or product-focused interface
- The page feels too noisy, too dark, too heavy, or visually inconsistent
- You are refining layout hierarchy, typography, spacing, surfaces, or CTA styling

## Required First Step

Before making UI changes, read:

- `DESIGN.md`

That file is the source of truth for:

- color palette
- typography scale
- spacing rhythm
- radius system
- component patterns
- design principles

## Working Rules

1. Prefer restraint over decoration.
2. Let the content or product be the visual focus.
3. Use one primary interactive color consistently.
4. Avoid unnecessary gradients, borders, shadows, or glow effects.
5. Build hierarchy through spacing, typography, and surface contrast first.
6. Keep controls precise, quiet, and readable.
7. Use soft surface separation instead of hard black/white contrast.

## Implementation Checklist

- Re-read `DESIGN.md` before changing design tokens
- Normalize color tokens before touching individual components
- Improve page hierarchy before polishing micro-interactions
- Simplify controls if they feel visually heavy
- Check empty states, preview states, and toolbar states
- Keep changes coherent across panel, canvas, cards, and form controls

## Output Expectations

When using this skill:

- Update the UI directly instead of only describing the style
- Keep the result visually coherent across the whole page
- Preserve usability while improving aesthetics
- Mention which parts were aligned to `DESIGN.md`
