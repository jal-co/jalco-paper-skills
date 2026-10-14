---
name: paper-ds-tokens
description: Sync design tokens between a project's code and a Paper file, in both directions, including dark mode and the comment color. Use when the user asks to pull their tokens into Paper, update the Paper theme, check whether Paper has drifted from code, or generate a token set for a project that has none.
---

# Paper DS tokens

Load `paper-ds-canvas` first. Paper tokens hold one value each, so dark mode and the comment role follow the naming rules below.

## Modes

Pick one from the request. Ask only if it is unclear.

- **sync**: code is the source. Push code values into Paper. Default.
- **pull**: Paper is the source. Write Paper values back to code.
- **generate**: the project has no tokens. Build a set, ask the user to approve it, write it to Paper and code.

## Sync

1. Find the token source from `paper-ds.json`. Parse every color, size, font, radius and spacing token.
2. Call `get_tokens` for the file.
3. Diff the two by name. Report three lists: missing in Paper, drifted (same name, different value), and only in Paper.
4. Show the lists before writing. A diff of more than 20 entries gets summarized by group first.
5. Apply with `create_tokens` for missing and `set_tokens` for drifted. Never delete a Paper-only token without asking.
6. Store the new `contentHash` in the manifest.

## Naming

Paper reads the Tailwind v4 namespaces: `--color-*`, `--text-*`, `--leading-*`, `--tracking-*`, `--font-*`, `--font-weight-*`, `--spacing-*`, `--radius-*`, `--breakpoint-*`, `--container-*`, `--opacity-*`. Map project names onto these. A name outside the namespaces is not found by the type filters.

Order matters when creating: neutrals first, then semantic roles, then the rest. Within a type, smallest value first.

## Dark mode

If the product ships one theme, write its roles under the plain names (`--color-ground`) and skip the `dark-` set. A dark-only product's `--color-ground` is dark. Record `themes` in the manifest.

When it ships both, code usually switches theme with a selector (`.dark`, `[data-theme]`, `prefers-color-scheme`). Paper cannot. Map it like this:

1. Read the light values from the base selector and the dark values from the dark selector.
2. Write light as `--color-<role>` and dark as `--color-dark-<role>`.
3. Write non-color tokens once. Size, type and radius do not change by theme.
4. Record the dark selector in the manifest so a reverse sync can rebuild it.

A role present in light and absent in dark is a bug in the code. Report it. Never copy the light value across to hide it.

## Roles alias ramps

Role tokens are aliases: `--color-primary` is `var(--color-blue-700)`. A role holding a copy of a hex goes stale the moment the ramp changes. If the code defines roles as raw values, alias them to the nearest ramp step and say which step you chose.

Build ramps in OKLCH, eleven steps (50 to 950), so equal steps look equal. Lightness should fall steadily from about 97 to 13. HSL ramps look uneven because 50% lightness differs by hue.

## The comment role

Every system carries two extra roles, in each theme it ships:

| Role | Light | Dark | Use |
| --- | --- | --- | --- |
| `comment` | pink 500 | pink 400 | Pins, threads, highlights on review feedback |
| `comment-subtle` | pink 50 | pink 950 | Thread background |

The default hue is neon pink (OKLCH hue 355). Ask once whether the user wants another hue, but keep one rule: nothing but review uses it. If the system already uses pink for brand or status, pick a different hue for comments, because one color cannot mean both.

## Comparing token choices

Read `../paper-ds-options/references/comparisons.md` when choosing between token values. Use ramps for palette coverage, role tables for semantic mappings, and the same text-on-surface examples for contrast. Font choices need matched headings, paragraphs, controls, and numerals, not only large letter specimens.

## Generate

1. Ask for the brand color, a mood in one word, and whether there is a font preference.
2. Build the ramps, then roles for each theme the product ships, then the type scale (12, 14, 16, 22, 36, 56), spacing on a 4px base, and three radii.
3. Check text roles against their backgrounds. Body text needs 4.5 to 1. Muted text must still clear it.
4. Show the set as swatches in chat. Write it only after approval.
5. Write the same set to the project in its own format, then run sync to confirm zero drift.

## What Paper cannot hold

Record these in `divergences`: `color-mix()` values (resolve them), gradients and shadows as tokens (write them inline from a role), and fonts the machine lacks.
