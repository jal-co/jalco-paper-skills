# Foundations as a maintained reference

Build from the actual source, not a sample palette. Each topic gets its own artboard so it can be found, reused, and checked without reading the whole file.

## Layout

Use the DS's spacing, type, radii, backgrounds, and text roles. Resolve the nearest existing layout steps; do not invent a fixed size scale during import. A compact title and one useful subtitle are enough. No decorative index rows, filled instruction banners, or large metadata panels.

Put artboards in a row with clear gaps and widths computed from their contents. The separate overview is 760px wide above the row, with no fill or padding. Clear its background with `background: none` and verify it. On the dark Paper canvas, use canvas text roles rather than light-system ink.

## Topics

| Artboard | Content |
| --- | --- |
| `00 Overview` | System name, purpose, and source authority. No review commentary |
| `01 Color roles` | Roles grouped by usage, with exact token references and values in each shipped theme |
| `02 Color ramps` | Existing ramp steps and labels showing the aliases actually used by roles |
| `03 Typography` | Real families/weights, scale, and matched heading/body/control/numeral examples |
| `04 Spacing and radius` | Source steps and usage examples, including nested surfaces |
| `05 Logo` | Real assets, variants, clear space, minimum sizes, and placements |
| `06 Font stacks` | Role, family, fallback stack, source, license when known, weights, and usage |

Only add shadows, motion, or other topics when the system defines them. Do not infer a license, clear-space rule, or minimum size without source guidance; ask or mark it unknown in chat. No asset means no invented logo unless a placeholder was requested.

## Usage notes

Each topic can end with `Instruction notes for agents`: plain text under a quiet divider, one rule per line, short enough to scan. No fill, badge, chip, or arrows. Notes describe real decisions, not a generic design manifesto.

Examples depend on the actual system: which surface belongs to a panel, which badge variant is the default, where mono text is used, or which logo variant fits a dark header. Source these from code, documentation, or explicit user decisions. Preserve user edits to these notes during sync.

These notes are part of the maintained system, not findings on a review sheet.

## Updating

Follow `../../paper-ds-manage/references/versioning.md`. Snapshot current tokens and artifacts before a shared change. Update only affected displays and record new source evidence. Mark dependent active subjects for review; do not claim all components were adopted or implemented because Foundations changed.

Keep imported token values and aliases exact. Raw-valued roles are not automatically drift; only claim drift when they differ from the selected source. Proposed palette or alias improvements need their own comparison and approval.
