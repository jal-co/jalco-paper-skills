---
name: paper-ds-pages
description: Organize a Paper file into a predictable page structure for a design system, and audit an existing file for a better one. Use when the user asks to organize or clean up a Paper file, asks whether their pages are laid out well, or after setup creates new pages.
metadata:
  version: "0.2.0"
---

# Paper DS pages

Load `paper-ds-canvas` first. Pages are how a person finds anything in a file, and how an agent finds the right place to draw.

## Page order

| Page | Holds | Icon |
| --- | --- | --- |
| `TEMPLATE` | Sheet frames that options clone from | blueprint |
| divider | | |
| `Foundations` | Color, type, spacing, logo, fonts | swatches |
| `Components` | Compact index of component pages | table |
| One page per component | Canonical baseline, variants, states, and usage for that component | table |
| `Blocks` | Sections and composites | presentation |
| divider | | |
| One page per exploration | Option sheets, named for what they explore | design |
| divider | | |
| `Archive` | Options that lost and old rounds | paper |

Canonical pages use the exact component name (`Button`, `Alert`). Explorations use a separate name such as `Alert exploration`, and reviews use `Alert review`, so the baseline never gets buried among drafts. Do not use `Page 1` or `Options v2`. The `arrow` icon marks the single page the team is working on now, on one page at a time.

Read `references/naming.md` and `../paper-ds-manage/references/versioning.md` before renaming or archiving.

## Naming

- Canonical artboard: the component name. Exploration: `Notice r2 Round 1` or `Review Notice r2`. Keep the subject name stable, append a compact revision suffix, and record ancestry in the manifest instead of a large canvas panel. Foundations use `NN Title`.
- Option frame: `Option 01 <name>`. Stage frame: `Stage light (Render)` and `Stage dark (Render)`.
- Slots: `Optional <name>`. Notes: `Instruction notes for agents`.
- Never leave `Frame` or `Rectangle` on a layer an agent must find.

## Apply

1. Call `get_basic_info` and list pages and dividers.
2. Create missing pages with `create_page` and immediately place each into its correct group using a freshly read complete order. Creation inserts beside the active page, not the intended group. Preserve unrelated pages and the user's grouping. Set names and icons with `update_pages`.
3. Place dividers and order with `arrange_pages`.
4. Archive only the rounds the user agreed to retire. Capture their artifact and token snapshots first, move with `move_nodes`, and update their revision status without removing approval or implementation evidence. Never delete history or infer approval from page position.
5. Update page IDs, exploration mappings, and any canonical node references in `paper-ds.json`. Moving artwork preserves its subject revision number.

## Audit

Run this when the user asks "is there a better way to organize this".

1. Read every page: artboard count, names, last-modified order if known.
2. Sort findings into: pages with no clear subject, artboards named `Frame` or `Untitled`, a page holding both foundations and explorations, rounds of the same exploration spread over several pages, orphan artboards far from the rest.
3. Propose a restructure as a list of moves: from, to, and why. Ask before moving anything.
4. Apply only what the user approves, then screenshot the page list.

A user who rearranged a page by hand did it on purpose. Copy their pattern where it works, and never undo it.
