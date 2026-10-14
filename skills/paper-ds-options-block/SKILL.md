---
name: paper-ds-options-block
description: Draw an option sheet for a block, meaning a section built from several components such as a pricing table, settings card, empty state, onboarding step or data list. Called by paper-ds-options when the decision is about a section. Use directly when the user asks for options for a section of a page.
---

# Options for a block

Run the `paper-ds-options` procedure. This skill sets the sheet format for blocks.

## Format

- Clone `Sheet Block` from TEMPLATE. Two options across, 480 x 320 stages, one stage per theme per option.
- Stage width is the block's real container width. Never stretch a block wider than it ships.
- Stub the page around the block with a flat strip of the `surface` role and two hairline bars at the edges, so the block reads as part of a page. Never draw the real page chrome. It competes with the block.

## What a block option decides

For structural alternatives, each option changes at most two of these. For revisions, states, or responsive checks, use the fixed variables in the comparison guide instead:

- Order of the parts
- Grouping: one list, sections, tabs, columns
- Where the main action sits
- What is shown up front and what sits behind a click
- Density: one line per item, a card per item, a table

Pin the content: the same items, the same counts, the same labels. Include one long label and one empty or loading state so the structure shows its limits.

## Slots

A block often has optional parts (an icon, a badge, a footer). Show them as `Optional <name>` layers on the stage so the user can see the block with and without. Never make an optional part required to look finished.

## Checks

- Compose the block from manifest components. A block of hand-drawn pieces says nothing about the real product.
- Check every theme the product ships. Muted text on a surface fails most often in dark.
- Check the block at its narrowest container width if the product resizes it. Draw that as a second stage only when an option breaks there.
