---
name: paper-ds-canvas
description: Shared rules for drawing in Paper through the Paper MCP without breaking things. Load before any paper-ds skill writes to a Paper file, and whenever a Paper screenshot comes back blank, artboards overlap, a node ID lookup returns the wrong ID, or dark mode needs to be drawn.
---

# Paper canvas rules

Every `paper-ds-*` skill loads this first.

## Before the first write

1. Call `get_basic_info` with the target `fileId`. Every file-scoped response carries `file.id`. If it is not the file you meant, stop and correct `fileId`. A write to the wrong file cannot be undone.
2. Read `paper-ds.json` in the project root. It holds the file ID, page map and component node map. If it is missing, load `paper-ds-setup`.
3. Call `get_font_family_info` for every family before writing text. A missing weight falls back silently and breaks every measurement after it.
4. Call `get_tokens` and compare `contentHash` with the manifest. A different hash means tokens changed outside your session. Re-read before trusting names.

## Writing

- One visual group per `write_html` call. The user watches the canvas live, and small writes keep failures local.
- Flex only. No `margin`, `display: grid`, `display: inline` or tables.
- Font sizes in `px`, never below 12. Letter spacing in `em`. Line height in `px`.
- Set `layer-name` on every structural element. Later runs find nodes by name.
- Use tokens as `var(--name)` everywhere Paper accepts them: color, `padding`, `gap`, `border-radius`, `font-size`, `line-height`, `letter-spacing`. Never write a value that exists as a token.
- Read the ID of a new node from `createdNodes[0].id` in the last content item of the response. The first content item is the file header and contains the file ID, so matching the first `"id"` in the response returns the wrong value.
- Reuse with `x-paper-clone` or `duplicate_nodes`. Clones inherit tokens and structure, so they cannot drift.
- Fix a defect with `update_styles` or `set_text_content`. Never delete and redraw for a small fix.
- Call `finish_working_on_nodes` when done, or the working indicator stays on the canvas.

## Dark mode

Paper tokens hold one value, and a frame cannot override a variable for its children. So themes are separate tokens:

- Light roles: `--color-ground`, `--color-ink`
- Dark roles: `--color-dark-ground`, `--color-dark-ink`

Pick a theme per frame and use only that theme's tokens inside it. Never mix. To show both themes, draw two frames.

Read `themes` in `paper-ds.json` before drawing:

- `["light", "dark"]`: every option and review shows a light and a dark stage side by side.
- `["dark"]` or `["light"]`: one stage per option. The single theme's roles use the plain names (`--color-ground`), with no `dark-` set. Never draw a stage for a theme the product does not ship.

Sync from code with `paper-ds-tokens`, which maps the project's dark selector onto the `dark-` names.

## Comment color

Every system defines a `comment` role (neon pink by default) with `comment-subtle`, in every theme the product ships. It marks review only: pins, threads, highlights on feedback. Never use it for status, buttons or decoration, and never use pink anywhere else. That exclusivity is why a comment is findable on any screen.

## Sharing

Do not include private example-file URLs or IDs in public documentation, screenshots' captions, or generated examples. Use repo-local images for documentation. Share a user's working-file link only within their requested handoff, not as a reusable demo source.

## Reading back

- A screenshot right after a write can be blank or stale. Call `get_tree_summary` on the node, then screenshot again. Never judge a write from a blank image.
- Review each checkpoint in one line: spacing, type, contrast, alignment, artboard fit, repetition. Fix, then move on.
- Screenshot at scale 1. Use scale 2 only to read small text.

## Text on the canvas

Paper's canvas is dark. Text on an unfilled artboard uses `var(--color-canvas-text)` and `var(--color-canvas-muted)`. System ink is unreadable there. Text inside a filled artboard uses the system's roles.

Overarching notes (an overview) have no fill, border or card. `create_artboard` ignores `backgroundColor: transparent` and gives the artboard a white fill. After creating it, call `update_styles` with `background: none`, then check `get_computed_styles` for `backgroundColor`.

An overview is its own artboard, 760px wide, no padding, placed above the row of artboards at `left: 0` with at least 80px clear below it. A full-width overview in the row looks like an empty sheet.

Padding set at creation sometimes cannot be changed later (`paddingInline` updates are ignored). If an artboard's padding is wrong, create a new artboard with the right padding, `move_nodes` the children into it, and delete the old one.

## Placing artboards

- Set `left` and `top` explicitly. Lay artboards in a row, 80px apart, so none can overlap. `create_artboard` can place a new artboard over an old one after `move_nodes`.
- A `fit-content` artboard reports height `null` or `?`. Read its height from a screenshot, never from a guess.
- Never set an artboard `top` with `bottom: auto` or `height` to fix a child. `find_nodes` by `position: absolute` also returns the artboard, and updating it pins its height. Select children by ID.
- `move_nodes` with `parentId: "root"` lifts a frame to the page. The frame loses its width and height. Set both again at once.
- `setTimeout` is undefined in codemode. Never wait with a timer. Call `get_tree_summary`, then screenshot again.
- Row width of a sheet is the sum of its option widths plus gaps plus 160px of padding. Compute it, and place the next artboard at `left + width + 80`.

## What Paper cannot do

Record each in the manifest `divergences` when the project's code depends on it.

- `color-mix()` inside an SVG fill is flattened. Resolve it to a plain color first.
- SVG noise filters do not render. Use a generated noise PNG at the same opacity and `paper-asset://`.
- A frame cannot switch themes (see Dark mode).
- Fonts load at launch. After installing one, the user must quit and reopen Paper.
- `paper-gen://` generates images only when the user asked for images.
