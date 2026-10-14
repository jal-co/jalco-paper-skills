---
name: paper-ds-tokens
description: Maintain the design system's tokens between its chosen source and Paper without erasing user edits or revision history. Compare drift, sync code or Figma values, explicitly pull approved Paper changes back to source, or generate a new system when requested. Use when tokens change, a theme drifts, or components need checking under a shared token revision.
metadata:
  version: "0.2.0"
---

# Maintain the token source

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Read the manifest's source authority and token snapshot before comparing values.

## Choose the direction

- `sync`: the selected source is authoritative; read code or Figma and update Paper.
- `pull`: the user explicitly wants Paper's proposed values written back into source.
- `generate`: no system exists; propose a set and get approval before writing it.

Do not overwrite Paper edits merely because code differs. If both changed since the last snapshot, show the conflict and ask which value wins.

<workflow>

1. Read source tokens, Paper tokens, supported themes, and the last snapshot. Compare names, values, aliases, and types. Separate missing, changed, conflicting, and Paper-only entries.
2. Show the proposed direction and affected token groups. Preserve Paper-only tokens, including canvas and comment roles. Deletion, renaming, or changing shared semantics needs explicit approval.
3. Capture the existing tokens and relevant artwork before mutation. Shared tokens can alter canonical and archived nodes, so determine their impact by inspecting references and protect historical screenshots and artwork with their original token snapshot.
4. Apply the requested sync with `create_tokens` and `set_tokens`, or make the authorized source edits for a pull. Inspect every entry result; a tool call can partially fail.
5. Read tokens back and verify them against the intended source using normalized CSS units, not string equality. Record reported precision loss, such as rounded OKLCH hue, as a divergence with the original source preserved; do not claim exact round-trip fidelity or keep resyncing indefinitely. For pulls, also run the source's applicable existing checks. If results differ or checks fail, record the failure and stop before declaring a successful snapshot.
6. Save the new snapshot, update `tokenSnapshot` and `tokensHash`, refresh affected Foundation displays without erasing usage notes, and mark affected subjects `needsReview`. A sync never silently increments or approves all components.

</workflow>

## Preserve the source

Keep token values and alias relationships exact. If the source uses raw values or uneven ramps, do not invent nearest-step aliases to make the display look cleaner. Propose a separate system change instead. Record a source-to-Paper name mapping when names must differ; do not rename code as a side effect of import.

Map types to Paper's token categories and retain supported CSS variables. Use the existing namespace when it works. New generated tokens can use Tailwind v4 names: `--color-*`, `--text-*`, `--leading-*`, `--tracking-*`, `--font-*`, `--font-weight-*`, `--spacing-*`, `--radius-*`, `--breakpoint-*`, `--container-*`, and `--opacity-*`.

## Themes

For one theme, roles use plain names such as `--color-ground`, whose value may be dark. For both, light uses plain names and dark uses `--color-dark-*`. Record the mapping and selector or Figma collection for reverse sync. Resolve inherited dark values from the source rather than treating every missing override as a missing role. Do not assume non-color tokens are identical if the source explicitly varies them.

## Reserved comment color

Retain or propose a neon-pink `comment` and a `comment-subtle` role for each shipped theme. Keep them distinct from brand and status colors. They remain documented in Foundations, but no drawn pins, comment cards, or findings appear in option or review sheets. Do not write these Paper presentation roles into product code without permission.

## Compare and generate

Read `../paper-ds-options/references/comparisons.md`. Palette coverage uses ramps; semantic choices use role tables; contrast uses the same text on real surfaces. Font choices use matched copy in headings, body, controls, and numerals.

For generation, ask for brand direction, themes, and font preferences. Propose OKLCH ramps, semantic roles, a small type scale, and spacing/radii. Verify contrast before asking for approval. These choices apply only to a new system, never to an imported one.

Unsupported effects or unresolved values go in `divergences`. Do not invent a replacement and report zero drift.
