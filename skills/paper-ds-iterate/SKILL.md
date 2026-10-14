---
name: paper-ds-iterate
description: Refine selected Paper components or nodes after feedback without restarting the exploration. Read the user's canvas edits, checkpoint revisions, preserve the current baseline, change only selected pieces, and verify survivors in context. Use for iterate on these nodes, keep this option, make it denser, use the actual Badge, or continue the next round.
metadata:
  version: "0.2.0"
---

# Iterate on the selected work

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Read the manifest and the subject's existing revisions. This skill starts from what the user selected, not from the original prompt.

<workflow>

1. Read every named node with `get_node_info`, `get_tree_summary`, `get_jsx`, and a screenshot. Confirm the file, parent, and subject. Ask only if the selected scope is materially ambiguous.
2. Read the actual source, Foundations notes, relevant component instances, and the latest token snapshot. Compare the current canvas with the last checkpoint. Preserve any user's changes, including grouping, padding, optional slots, and notes.
3. Restate the bounded change in one sentence. "Keep these two" means refine only those two; do not regenerate the rejected options or turn a refinement into a whole-system redesign.
4. Checkpoint the starting artwork. Clone the selected draft into a new round when the user wants comparison history or it would replace earlier work. Edits explicitly requested on a working draft can happen in place after capture. Canonical, approved, and locked artwork are never edited in place.
5. Apply targeted style, content, and structural edits. Clone the actual component when the user requests Badge, ProductAvatar, or another named piece. If a proposed change cannot be expressed by the existing component, label it as a system/API proposal in chat; do not invent support.
6. Choose the smallest comparison needed using `../paper-ds-options/references/comparisons.md`. A padding refinement uses Current/Proposed. Long errors need content stress. Only a new direction needs alternatives.
7. Verify the survivors in the actual surrounding screen, supported themes, relevant states, and real container widths. Preserve source content; grow stages instead of shrinking the subject. Keep findings off the canvas.
8. Capture the resulting draft, record its parent revision, source, token snapshot, and remaining divergences. Report the selected nodes, revision, changes, and evidence. Use `paper-ds-land` only when the user approves adoption or requests implementation.

</workflow>

<rules>

- Re-read selection and tokens before another round if the user edited Paper. Never treat an earlier screenshot as the latest design.
- A user edit is a new input, not damage to normalize back to the template.
- Preserve existing work and node identity with `update_styles`, `set_text_content`, and `move_nodes`. Use a new clone when preserving an approved baseline requires it.
- Use DS spacing, typography, and radii. If the requested value is outside the scale, state the proposed exception instead of silently changing the system.
- Do not archive rejected options until the user chooses what to keep or asks to clean up. Saved history makes later reconsideration possible.

</rules>
