---
name: "figma-design-md"
description: "Applies the Figma-inspired design system from FIGMA-DESIGN.md. Invoke when rebuilding UI in Figma style, especially for dark mode, monochrome layouts, and playful pastel accents."
---

# Figma Design MD

Use this skill when the user wants the interface to feel closer to Figma's visual language: editorial, monochrome, rounded, direct, and lightly playful through selective pastel surfaces.

## What This Skill Does

- Applies the Figma-inspired design system from `FIGMA-DESIGN.md`
- Reworks pages into a cleaner black/white structure with selective accent blocks
- Improves typography, CTA hierarchy, spacing rhythm, and panel composition
- Supports both standard and dark-mode reinterpretations of the design language

## When To Invoke

Invoke this skill when:

- The user asks for a Figma-like UI
- The user wants dark mode redesigned with a cleaner editorial feel
- The current page feels too generic, too decorative, or visually inconsistent
- You are refining panels, controls, preview cards, tool surfaces, or layout hierarchy

## Required First Step

Before making UI changes, read:

- `FIGMA-DESIGN.md`

That file is the source of truth for:

- monochrome base colors
- pastel block accents
- typography scale
- radius and pill system
- button and input patterns
- section composition

## Working Rules

1. Start from black/white contrast first.
2. Use pastel accents sparingly as section interrupts, not everywhere.
3. Prefer oversized rounded pills for strong actions.
4. Keep the UI direct, crisp, and editorial.
5. Let hierarchy come from scale, spacing, and contrast.
6. Avoid muddy shadows, heavy gradients, or multiple competing accents.
7. In dark mode, keep the canvas black and let controls/surfaces carry separation.

## Implementation Checklist

- Normalize tokens before changing components
- Use one monochrome foundation across the whole page
- Choose 2-3 accent block colors maximum
- Keep previews readable and visually dominant
- Ensure controls still feel practical for tool usage
- Recheck empty states, toggles, cards, and form controls

## Output Expectations

When using this skill:

- Update the page directly
- Preserve usability while increasing visual distinctiveness
- Keep the result coherent across panel, preview stage, controls, and supporting states
- Mention alignment to `FIGMA-DESIGN.md`
