---
name: paper-ds-options
description: Compare design directions or revisions of a real component, block, or page in Paper using its existing system and content. Choose the right comparison, preserve the baseline, capture draft lineage, and prepare survivors for focused iteration. Use for alternatives, variants, Current/Proposed comparisons, or stakeholder option sheets. Mobbin is optional.
metadata:
  version: "0.2.0"
---

# Compare before deciding

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Read the subject's source, revisions, named nodes, and actual canvas before making a sheet. Missing connections go through `paper-ds-setup`; an existing project does not.

## Choose the comparison

Read `references/comparisons.md`. State the decision in one sentence: structures, Current/Proposed, states, long content, themes, widths, context, an optional slot, foundation specimens, or a flow. A review of one existing design uses `paper-ds-review`; feedback on selected nodes uses `paper-ds-iterate`.

| Subject | Format |
| --- | --- |
| One component | `paper-ds-options-component` |
| A section made of components | `paper-ds-options-block` |
| A full page or flow step | `paper-ds-options-page` |

The subject chooses stage size. The decision chooses the comparison and candidate count.

<workflow>

1. Read the current source and Paper baseline. Capture it with its token snapshot. If either source changed since the latest record, checkpoint the observed state and flag the difference rather than relabeling old artwork as current.
2. Pin the real labels, data shape, counts, states, and surrounding product UI. Use the same content across structural alternatives. Only vary content for an explicit state or stress comparison.
3. Read Foundations guidance and actual component instances. Use only supported roles, scale steps, variants, assets, and themes. Record a proposed exception or API addition instead of silently inventing it.
4. Gather structural references using `references/references.md` if useful. Mobbin, Figma, existing Paper screens, and supplied images are optional inputs, not styling authority.
5. For open exploration, list three to six distinct ideas unless asked otherwise. Two ideas differing only in color or spacing count as one. For Current/Proposed, With/Without, or state checks, draw the actual conditions instead of padding the sheet with alternatives.
6. Clone the user's current TEMPLATE frame, preserving their spacing, type, logo slot, and optional parts. Add only the comparison labels needed. Create or reuse the subject's exploration page; never overwrite a previous round.
7. Draw with the real instances. Include the actual baseline first for revisions. Use one stage per shipped theme and relevant real widths; split a dense matrix instead of shrinking the subject.
8. Verify screenshots against the pinned content and context. Fix clipping, contrast, mismatched component surfaces, and unsupported effects. Keep findings, comments, and pins off the sheet.
9. Capture the drafts and their parent baseline, source, tokens, and evidence. Report the revision, options, trade-offs, recommendation, and remaining divergences in chat. Nothing becomes canonical merely because it was recommended.

</workflow>

## After feedback

Use `paper-ds-iterate` on the exact selected nodes. Read the user's edits first and narrow the next round to survivors. A user selection is not implementation approval. Once the user explicitly approves a revision, `paper-ds-land` adopts it and implements only when requested.

## Sheet slots

`Optional Logo` uses the real asset. `Optional Trade-off` holds a concrete cost when useful. `Optional Notes` is an empty removable stakeholder slot, not a place for agent critique. Remove unused slots. A review sheet has no comments or findings at all.
