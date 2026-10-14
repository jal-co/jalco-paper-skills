---
name: paper-ds-setup
description: Connect an existing design system to Paper so it can be maintained and iterated alongside the user. Identify source authority, supported themes, real assets, and compact sheet defaults; create Foundations, TEMPLATE, and a versioned project manifest. Use for first-time setup or reconnecting an existing file, not to restart ongoing work.
metadata:
  version: "0.2.0"
---

# Connect the real system

Read `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Setup establishes the baseline for ongoing work; it does not invent a new design system.

<workflow>

1. Confirm the Paper MCP works and which file to use. Use an explicit URL or ID already supplied rather than asking again. Create a file only when requested.
2. Read any existing `paper-ds.json` and the file's pages. Reuse them. For an older manifest, follow the migration procedure; do not reset nodes, revisions, or page IDs.
3. Find the actual sources: token files, component directory, stories, design-system docs, assets, and Figma if supplied. Ask which source is authoritative only when they disagree or it is unclear. No token source means propose generation with `paper-ds-tokens` and get approval first.
4. Ask unresolved setup choices in one grouped message: shipped themes; logo files; numbers or letters; stage background; optional trade-off and feedback slots. Use the answers already given. The default is compact DS-token spacing, not a large configuration table.
5. Create the manifest using `../paper-ds-manage/references/manifest-example.json`. Fill only observed values and leave unknown IDs or versions null. Write `schemaVersion: 2` and the installed skills version. This connection record lets the remaining steps reuse the file without recursively running setup.
6. Sync tokens with `paper-ds-tokens` and build or reconcile Foundations from `references/foundations.md`. Existing user artwork is preserved; show proposed reconciliation before applying it.
7. Build or reuse TEMPLATE using `references/template.md`. Place the supplied logo on the Logo foundation and clone it into header slots. No asset means omit the slot unless the user requested a placeholder. Never hardcode the sample system name.
8. For a single-theme system, build one stage per option, with that theme's plain role names. Compute option width from remaining stages and resolved DS gaps; do not halve a width that includes a pair gap.
9. Organize with `paper-ds-pages`. Import only components needed for the next task with `paper-ds-components`; do not require a whole-library import to start.
10. Capture the initial token snapshot and imported subject baselines. Verify artboards with screenshots and check the manifest against actual node IDs. Report the connection, supported themes, source, and any unverified imports. Ask the user to lock finished canonical artboards manually when wanted; the MCP cannot lock them.

</workflow>

<rules>

- Existing design rules, fonts, scale steps, logos, and component APIs come from source or the user's choices. Never replace them with sample values.
- Foundation notes explain actual usage and are editable by the user. They are not review comments.
- No existing Foundations or TEMPLATE artboard is overwritten without approved scope. Future sheets clone the user's current templates.
- Setup alone never marks a component approved or implemented. Imported baselines receive only the evidence actually captured.

</rules>
