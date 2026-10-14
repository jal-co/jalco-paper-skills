# Versioning your work

[Back to the workflow](usage.md)

A version should tell you what changed, what the user approved, and whether code actually matches it. It should not just add "v2" to an artboard name.

## Separate the numbers

- **Package version** identifies the installed skills. The current release is `0.2.0`, recorded in `VERSION` and each skill's metadata and tagged as `v0.2.0`.
- **Manifest schema** identifies the shape of the project's `paper-ds.json`. The new workflow uses schema 2. Older projects need an approved migration, not a reset.
- **Subject revision** identifies a component, block, or page checkpoint. `Alert r3` and `Button r3` have separate histories. Neither is an npm package release.

## What a revision saves

The agent captures the real source, Paper artwork, token values, necessary assets, and rendered evidence. The project keeps that under `paper-ds/history/`, with revision records in `paper-ds.json`.

A record names its parent revision, source path/version when known, Paper node, token snapshot, what changed, status, and any approval or implementation evidence. Unknown source versions remain unknown.

These files can contain private IDs and assets. Keep them under the project's storage policy. Do not publish them as blog examples or copy them into the skills repo.

## The current Alert example

- **r1** is the imported baseline with the source action slot.
- **r2** captures three action-placement comparisons.
- **r3** carries the below-description action forward with more separation and records long-content, narrow-width, and context checks.

r3 is not an official shadcn release or a new source variant. It is still a local draft. Canonical Paper remains at r1, and the implemented revision remains unknown. Approval and browser/code verification have not happened.

The other 14 components each have their own r1 baseline. Their counters do not advance just because Alert reached r3.

## Possible lifecycle after feedback

This table describes the transitions, not completed work in the example:

| Event | Alert record | Canonical Paper revision | Verified code revision |
| --- | --- | --- | --- |
| Import a baseline | r1, baseline captured | r1 | Unknown until verified |
| Explore a new layout | r2, draft based on r1 | r1 | Unchanged |
| "Keep this option" | r2 remains a draft for refinement | r1 | Unchanged |
| User edits it and asks for another round | Capture edits and start r3 based on r2 | r1 | Unchanged |
| "Adopt r3 in Paper only" | r3 approved with the actual instruction | r3 | Unchanged |
| "Implement r3" with successful checks and visual comparison | r3 implemented with evidence | r3 | r3 |

Failed implementation checks leave the approved revision approved, not implemented. A clean design review alone does not advance the code revision.

## Shared tokens are live

An old Paper frame can change when global tokens change. Cloning it does not freeze its appearance.

Snapshots preserve the tokens and rendered evidence used by that revision. A historical restore rebuilds from those saved values in a new draft. It never replaces the current global tokens just to make an old frame look right.

A token sync flags affected subjects for review. It does not manufacture a new approved component version for every token change.

## Restore without erasing history

> Restore Alert r1 as a new draft for comparison. Keep the current component and tokens intact.

The next available revision is based on r1; counters do not move backward. Approval and code verification must happen again before that restore becomes current or implemented.

## Package releases

`VERSION`, all skill metadata, and `CHANGELOG.md` agree. A version file is not a release tag. Publishing a tag or release is a separate authorized action.

[v0.2.0](https://github.com/jal-co/jalco-paper-skills/releases/tag/v0.2.0) is the first tagged release. Changes on `main` after that tag belong to a future release; do not move a published tag to include them.

While the package is pre-1.0, minor versions can add workflows or change the manifest contract. Patch versions fix instructions without changing the contract. Once stable at 1.0, incompatible contracts require a major version.

The [agent versioning reference](../skills/paper-ds-manage/references/versioning.md) defines checkpoints and status rules. The [manifest example](../skills/paper-ds-manage/references/manifest-example.json) shows the initial schema 2 record without fabricated revision history.
