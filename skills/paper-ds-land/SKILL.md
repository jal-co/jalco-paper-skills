---
name: paper-ds-land
description: Fold an approved Paper revision back into the design system and, when requested, the real component code. Preserve the previous version, update canonical artwork and usage guidance, verify code fidelity, and record approval separately from implementation. Use for adopt this option, make this the current component, implement these selected nodes, or land the approved design.
metadata:
  version: "0.2.0"
---

# Land an approved decision

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. This closes the loop between an exploration and the maintained system. It is not a publishing command.

<workflow>

1. Read the exact subject, revision, selected nodes, source, checkpoints, and latest Paper artwork. Confirm whether the user requested design adoption only or implementation too. If there are several survivors or no adoption instruction, ask which revision to land.
2. Record the user's actual approval instruction. Do not turn "looks promising" or "keep these two" into final approval. An explicit implementation request for a specific revision authorizes that implementation, not publication or unrelated API changes.
3. Capture the previous canonical artwork and token snapshot before replacement. If artwork, source, or tokens materially changed since approval, checkpoint a new draft, set the subject's `needsReview` to true, and compare again. Get approval for the new revision before adoption; never transfer approval to different artwork.
4. Promote the approved artwork to its own canonical component page, or the canonical Block/page location for other subjects. Components remains an index. Update the component's `page` and `pages.componentPages` mapping when needed. Preserve the previous revision in history, update the canonical `node` and `currentRevision`, and update usage notes from the approved behavior. A change to protected Foundations or TEMPLATE needs explicit scope and permission.
5. For design-only adoption, stop with status `approved`. Leave `implementedRevision` unchanged or null. Report the remaining code difference.
6. For implementation, read values directly from Paper with `get_jsx`, `get_computed_styles`, and asset tools. Read source, props, styles, stories, and real call sites. Translate the approved design into existing components and APIs, not literal generated div trees. Limit changes to the approved subject.
7. Run the project's applicable existing checks and visually compare the implementation with the approved Paper revision using the same content, states, themes, and widths. Use screenshots to verify fidelity, not to infer source values. If a check or fidelity comparison fails, fix it or leave implementation incomplete. Remaining divergences must be explicitly accepted trade-offs, not unresolved failures.
8. Refresh canonical Paper instances from the verified implementation only within the approved scope. Record the actual source version if available, check results, visual evidence, and remaining divergences. Mark the revision `implemented` and advance `implementedRevision` only after verification succeeds.
9. Archive previous rounds the user agreed to retire. Keep their artifacts and decision history. Report current Paper revision, implemented revision, source, checks, and remaining drift.

</workflow>

<rules>

- A selected option does not grant permission to change every call site, add dependencies, widen a component API, or revise token semantics. Ask when the approved result requires those changes.
- Semantic or global token changes need a separate impact review using `paper-ds-tokens`; they affect more than this component.
- Never claim implementation succeeded because Paper was updated, code compiled, or an option was approved. Record visual and behavioral evidence too.
- Generate documentation from the actual approved component and source: when to use it, default variants, alternatives, optional slots, and supported states. Do not document a prop or variant that does not exist.
- Restore earlier work as a new revision. Never move the revision counter backward or overwrite historical artifacts.
- Commits, pushes, release tags, PRs, deployments, and native comment-thread changes require their own authorization. Do not perform them as an automatic part of adoption.

</rules>
