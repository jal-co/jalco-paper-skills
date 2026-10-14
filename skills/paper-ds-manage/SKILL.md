---
name: paper-ds-manage
description: Manage a design system and iterate on its components in Paper alongside the user. Start from the real system, route imports, comparisons, focused iterations, review, and approved implementation, and keep revision history. Use for ongoing Paper design-system work, continuing an exploration, managing drift, or deciding what to do next with a component.
metadata:
  version: "0.2.0"
---

# Manage a design system in Paper

<workflow>

1. Read `paper-ds.json` and `references/versioning.md`. Check the target Paper file with `paper-ds-canvas`. If there is no manifest, use `paper-ds-setup`; do not restart setup for an existing system.
2. Identify the subject and the decision. Read its source, actual content and states, existing Paper nodes, Foundations guidance, and revision record. Prefer the user's named nodes over a generic component lookup.
3. Route the request using the table below. Continue through the requested work, not every stage of the lifecycle.
4. Before changing artwork, read it back. The user may have edited it since the last round. Checkpoint those edits and preserve them as the starting point.
5. At the end, report what changed, its revision, verification evidence, and what remains unapproved or unimplemented. Keep critique in chat, not on the sheet.

</workflow>

| Request | Skill |
| --- | --- |
| Connect a system for the first time | `paper-ds-setup` |
| Keep tokens aligned with the chosen source | `paper-ds-tokens` |
| Bring in or refresh actual components | `paper-ds-components` |
| Explore or compare structures | `paper-ds-options` |
| Work on selected nodes after feedback | `paper-ds-iterate` |
| Check one subject, its states, widths, or context | `paper-ds-review` |
| Fold an approved decision back into Paper and code | `paper-ds-land` |
| Organize, rename, or archive | `paper-ds-pages` |

<rules>

- The system is the ongoing work, not the setup output. Re-read source and Paper before a new round; neither is assumed current.
- Keep the baseline, proposed design, and implemented result distinguishable. A recommendation is not approval, and approval is not implementation.
- A source conflict needs a choice: code, Figma, or the user's current Paper edits. Do not silently overwrite one with another.
- Do not make a new library, palette, or component API to fill a sheet. Work with the real system and flag additions as proposals.
- Preserve the user's page organization, selected nodes, optional slots, supported themes, and edited template styles.
- A version checkpoint belongs in the project's local history, not in a large metadata panel on the canvas. Use short revision suffixes only.

</rules>
