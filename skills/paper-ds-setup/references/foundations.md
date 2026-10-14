# Foundations page

One artboard per foundation. Each can be linked, screenshotted and cloned alone, and an agent reads a small tree instead of 800 nodes.

## Artboard frame

- Name: `NN Title`, for example `01 Color roles`
- Width 2480, height `fit-content`, fill `var(--ground)`, padding 64px 80px, flex column, gap 32px
- Stacked down the page at `left: 0`, 80px apart, positions measured from screenshots

## Header

Two lines at the top of every artboard. No index number, no rule, no box.

- Title: 28px, weight 500, ink
- One sentence below: 16px, muted, what the section governs

## The overview has no background

`00 Overview` has no fill on the artboard and none on anything inside it. Reason: a filled box reads as another component, and an overview frames the content.

Paper's canvas is dark, so text on it uses the canvas roles, not ink or muted:

- Title and body: `var(--canvas-text)`
- Secondary lines: `var(--canvas-muted)`

Create both tokens during setup, aliased to the lightest and a mid step of the neutral ramp. Ink on the dark canvas is unreadable.

## Artboards, in order

| Artboard | Content |
| --- | --- |
| `00 Overview` | System name at 56px, one line on its purpose, one paragraph saying this page is the source of truth |
| `01 Color roles` | One swatch per role, 120px tall, then role name, token, value, one usage line |
| `02 Color ramps` | One row per hue, one cell per step. A dot and the role name mark which step each role uses. Cell text flips between white and ink by luminance |
| `03 Typography` | A specimen card per family (large Aa, alphabet, digits, each weight), then a scale table: token, size, line height, tracking, live sample |
| `04 Spacing and radius` | Spacing bars at 6x with token and value, radius swatches with token and value |
| `05 Logo` | Variants per surface, clear space, minimum sizes, placements. Skip when there is no asset |
| `06 Font stacks` | Role token, family, CSS stack, source and license, weights, usage |

Add `Shadows`, `Motion` or `Opacity` only when the token source defines them.

## Notes for agents

Last child of each artboard except the overview. Layer name `Instruction notes for agents`.

- A 1px top rule in `var(--hairline)`, 24px padding above, 720px wide
- Heading "Notes for agents", 13px, weight 600, ink
- Two or three lines, 14px, muted, one rule per line, no bullets or arrows
- No fill, no border box, no chip

Each rule is something that changes what an agent draws. Seed rules:

- Colors: components use roles, never ramp steps or hex values. A missing role is added here first.
- Ramps: a role with no dot has drifted from its ramp.
- Type: call `get_font_family_info` first. Sizes come from the scale.
- Spacing: gaps inside a group use steps 1 to 3, between groups 6 to 8.
- Logo: never recolor or redraw. Clone it. Under the minimum height, use the mark alone.
- Fonts: mockups use the first family. Code uses the whole stack.

## Sizes

Never below 12px, anywhere on the page. Tiny mono captions at 11px read as noise, not detail.

## Roles alias ramps

A role's value is `var(--ramp-step)`, not a copy of the hex. Without aliasing, a ramp edit leaves roles stale and the dots on `02 Color ramps` lie.

## Hairlines

In light mode the border token is translucent black at 8%. A solid grey looks pasted on. In dark mode it is a solid grey, because a translucent white border glows.
