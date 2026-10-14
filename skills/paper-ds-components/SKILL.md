---
name: paper-ds-components
description: Bring actual design-system components into Paper and keep their baselines aligned with code or Figma. Import the variants, states, and usage rules needed for a task, checkpoint source versions, and preserve existing user revisions when refreshing instances. Use for component imports, stale canonical components, or replacing hand-drawn approximations with the real component.
metadata:
  version: "0.2.0"
---

# Keep real components available

Load `paper-ds-canvas` and `../paper-ds-manage/references/versioning.md`. Read the component source, its call sites, existing instances, and revisions before drawing or refreshing.

## Sources

Use the authority selected in the manifest. Code defines recipes and APIs; stories provide real content and states. For a Figma system, follow `../paper-ds-options/references/figma.md`. Screenshots are a last-resort approximation and never evidence of an exact implementation.

<workflow>

1. Inventory the requested components. Import only what the task needs; a large library can be split into explicit batches. Preserve component names and source locations.
2. Find existing canonical nodes and drafts. If source and Paper both changed, report the conflict rather than overwriting either. Checkpoint any existing artwork before a refresh.
3. Build the baseline on Components with actual variants, sizes, and states. Use one panel per shipped theme. Read values from source rather than substituting a generic-looking component.
4. Name instances by their real props, such as `Badge warning subtle sm`. Include compact usage notes: when to use it, the default variant, an alternative, and supported optional slots. Each rule must trace to source or an explicit user decision.
5. Verify every imported variant that was requested with real content. Capture source version when available, artwork, token snapshot, and rendered evidence. Mark unsupported effects as `approximate` and record them in `divergences`.
6. Add a baseline revision and source mapping to the manifest. An import is not user approval and is not an implementation check. Leave `implementedRevision` null unless matching code checks and visual verification have actually been recorded.
7. When a refresh succeeds, mark dependent active explorations for review rather than silently replacing their chosen instances. The user may have intentionally changed them.

</workflow>

## Reuse

Clone the instance matching the requested props. Override content only unless the task is explicitly to change that component. If the real component cannot express a desired badge, avatar, action, or slot, report the API gap instead of drawing it as if support exists.

Current canonical instances are for new work. A historical comparison uses the captured revision and its saved tokens, not today's instance with an old label.

## Rules

- No new variants to fill a matrix. Draw only the real union or Figma variants.
- Keep real sizes; grow stages instead of scaling the component down.
- A component without call sites is not automatically dead. Report uncertainty and ask before discarding it.
- Canonical replacement requires an approved refresh scope. Design proposals go through `paper-ds-iterate` and `paper-ds-land`.
