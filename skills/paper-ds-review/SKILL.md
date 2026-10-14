---
name: paper-ds-review
description: Verify one real Paper design or revision against its system, states, widths, themes, and actual product context without inventing alternatives. Record the reviewed revision and evidence separately from approval or implementation. Use for review, critique, QA, in-context checks, or stakeholder sign-off of one subject.
metadata:
  version: "0.2.0"
---

# Check the subject in context

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Read the exact selected nodes, source, and revision, not just a component name. Existing user edits are part of the subject.

Read `../paper-ds-options/references/comparisons.md`. Choose only checks that could change the verdict. A revision uses actual Current and Proposed. A single component may need long content, relevant states, themes, widths, or its surrounding screen. Do not generate alternatives unless asked.

<workflow>

1. Read source and current artwork. If the selected node is unavailable, ask rather than drawing a substitute. If source and Paper disagree, identify which design is being reviewed.
2. Capture previously unrecorded artwork or user edits as a baseline or draft checkpoint. Reviewing an unchanged revision does not allocate a new artwork revision.
3. Clone `Sheet Review` only if a separate review display is needed. Reuse an existing adequate display. Include Focus, relevant States, and In context; remove empty sections and unsupported themes.
4. Use real content and actual surrounding components. Do not show a 320px screenshot as a responsive 200px rendering. Reflow at the real width.
5. Check scale values, semantic roles, contrast, content stress, actual states, optional slots, and how the subject fits its neighbors. For behavioral or implementation claims, run applicable checks in the real product. Static Paper screenshots cannot prove keyboard behavior or loading logic.
6. Record the examined revision and token snapshot, verification evidence, and unresolved findings in the subject's `reviews`. Clear `needsReview` only for the checks completed under current tokens and source; an incomplete verification leaves it true.
7. Reply with concise findings, each naming the location, problem, and fix. State what was not tested. A clean review is evidence, not user approval or a shipped revision.

</workflow>

## Comments

The sheet holds the design only. No drawn comment cards, finding rows, pins, or critique notes. Findings belong in chat.

Read existing native Paper comments as input when available. Never create, alter, or resolve a thread without explicit permission for that action. Keep private file URLs and review artifacts out of public examples.

## Next step

Use `paper-ds-iterate` for requested fixes and `paper-ds-land` for a specifically approved revision. Do not automatically change code or canonical artwork as a side effect of review.
