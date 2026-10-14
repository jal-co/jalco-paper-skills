# Naming and locking

## Layer names

Every layer has a name an agent can search for. A layer left as `Frame`, `Rectangle`, `SVG` or `Path` is invisible to the next run.

| Layer | Name |
| --- | --- |
| Foundations artboard | `NN Title` (`01 Color roles`) |
| Sheet artboard | `<subject> r<N> Round <N>` (`Notice r3 Round 2`); `Sheet Component` stays the template name |
| Option | `Option NN <idea>` (`Option 02 Trend as field`) |
| Stage | `Stage light (Render)`, `Stage dark (Render)` |
| Drawn component inside a stage | `<idea> tile`, or the component name and props (`Badge warning subtle sm`) |
| Slot | `Optional <name>` (`Optional Logo`) |
| Agent notes | `Instruction notes for agents`, on Foundations and canonical component guidance only |
| Color swatch | `Swatch`, inside a frame named for the role or step |
| Logo shapes | `Mark` |
| Chart shapes | `Chart` |

Separate words with spaces. Do not use decorative separators, slashes, or pipes in names; they read as hierarchy in the layer panel.

A revision suffix identifies artwork, not approval or implementation. Keep the canonical name stable, and record statuses and ancestry in the manifest. No large version or comment panel belongs on the sheet.

After every sheet, walk the tree with `get_children` and rename any layer still called `Frame`, `Rectangle`, `Text`, `SVG` or `Path`. Name it by its parent: a rectangle in a role row is `Swatch`, a frame in a stage is the tile.

## Locking

The Paper MCP cannot lock layers. Locking is a step for the user:

1. After setup, ask the user to lock `TEMPLATE` sheets and every `Foundations` artboard in Paper.
2. Before editing any node, call `get_node_info`. If the node or an ancestor is locked, stop and ask. A lock means the user decided it is finished.
3. Never unlock, delete and redraw, or duplicate-and-replace a locked node to get around a lock.

If `get_node_info` does not report lock state, treat `TEMPLATE` and `Foundations` as locked anyway. Clone from them, never edit them, unless the user asks for a change there.
