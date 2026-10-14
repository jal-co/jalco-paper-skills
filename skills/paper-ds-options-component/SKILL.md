---
name: paper-ds-options-component
description: Draw an option sheet for a single component, such as a badge, tile, toast, input or menu, using the user's design system. Called by paper-ds-options when the decision is about one component. Use directly when the user asks for variants of one component.
---

# Options for a component

Run the `paper-ds-options` procedure. This skill sets the sheet format for components.

## Format

- Clone `Sheet Component` from TEMPLATE. Three options across, 320 x 200 stages, one stage per theme per option. Spacing and type come from the system tokens (see `paper-ds-setup/references/template.md`).
- Three is the row capacity, not a required count. Six directions use two rows. Current/Proposed uses two frames; state checks use the actual states.
- Each stage shows the component at its real pixel size, centered. Never scale a component to fill the stage.

## What every stage shows

Pin the content once and show it in every option: the same label, the same value, the same state.

Add a state strip below the stage only when the choice depends on states. Show the states the component actually has: default, long text, empty, error, loading. Pick the two that stress the structure most. A strip of five identical-looking states is noise.

## Ideas to cover

For an open structural exploration, draw ideas from these axes. State checks, revisions, and responsive comparisons keep the design fixed instead:

- Where the primary figure sits and how big it is
- What carries the secondary data: text, glyph, bar, none
- How it is bounded: card, rule, field, nothing
- How color is used: none, an edge, a fill, an icon only
- Dense and spacious versions of the same idea count as one idea

## Checks

- The stage color must differ from the component surface. A component that matches its stage has no visible edge. Use the `raised` role for the component on a `surface` stage.
- Long content: render one option with the longest real value from the data. If it breaks, say so on the sheet.
- Use the real component from the manifest where one exists. Say which parts are redrawn.
- If an option relies on an effect Paper cannot render, label it `approximate` and add it to `divergences`.
