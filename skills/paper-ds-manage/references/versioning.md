# Versioning the work

There are three different numbers. Never substitute one for another.

| Number | Meaning | When it changes |
| --- | --- | --- |
| Package version | Which release of these skills is installed | A maintainer prepares a skills release |
| Manifest schema version | The shape of `paper-ds.json` | The manifest format changes |
| Subject revision | Which captured component, block, or page design this is | Baseline import, a material iteration, or a user's edits are checkpointed |

## Project manifest

Use `schemaVersion: 2` and record the installed package version as `skillsVersion`. Subject revision numbers are integers, local to each subject. `Notice r3` has no relationship to `Button r3` or a library's npm version.

See `manifest-example.json` for the record shape. `authority` records the chosen token and component sources (`code`, `figma`, or `paper`); record null and ask if ownership is unresolved. `components` keeps its existing `node` and `source` fields and records its canonical `page`. `pages.componentPages` maps component names to their dedicated pages; `pages.components` is the index. Blocks and pages use the same record shape under `subjects`, with `kind` identifying the subject type.

`currentRevision` points at the canonical Paper baseline or approved design. `implementedRevision` points only at a revision verified in code. Both may differ. An unverified import or a design-only project has `implementedRevision: null`.

## Checkpoint

Before the first agent edit, and before overwriting a working draft:

1. Read the current nodes, source, tokens, and any user's edits. Record source kind, path, and Git commit or Figma version when available. Unknown versions stay null.
2. Allocate the next revision number and a token snapshot number. Never reuse one from an archived revision. Reuse an identical existing token snapshot instead of duplicating it.
3. Save the token list, themes, `get_jsx` output, assets needed to reproduce the subject, and a screenshot for each supported theme under `paper-ds/history/<subject>/r<N>/`. Store tokens once under `paper-ds/history/tokens-r<N>.json`.
4. Record the artifact paths, source, parent revision, node, status, and one sentence saying what changed. Store the matching token snapshot path.
5. Only after the checkpoint succeeds may the agent edit or archive the nodes. If capture fails, stop; do not claim the revision was saved.

Paper clones reference live tokens. A token change can alter an archived frame. The saved token snapshot, artwork export, assets, and screenshots are the historical evidence; the old live frame is not a frozen version. Rebuilding a historical frame requires resolving its saved token values or binding a separate snapshot token set. Never replace the project's current tokens to display history.

Checkpoint at meaningful round boundaries, not after every tool call. Small fixes within an unapproved draft can share a revision. Before a later round replaces that draft or incorporates the user's edits, capture it and allocate the next revision.

A revision entry uses this shape; fill it from actual evidence, not these example paths:

```json
{
  "revision": 2,
  "basedOn": 1,
  "node": "CAPTURED_NODE_ID",
  "status": "draft",
  "summary": "Move the action below long messages",
  "source": { "kind": "code", "path": "src/components/Notice.tsx", "version": null },
  "tokenSnapshot": "paper-ds/history/tokens-r1.json",
  "artifacts": {
    "jsx": "paper-ds/history/notice/r2/artwork.jsx",
    "assets": [],
    "screenshots": { "dark": "paper-ds/history/notice/r2/dark.png" }
  },
  "approval": null,
  "implementation": null
}
```

An implementation entry records source paths, source version if known, checks with actual results, visual evidence, and remaining divergences. Reviews are append-only records with the examined revision, token snapshot, checks, and findings. Do not replace one with a fabricated "passed" field.

## Revision status

| Status | Evidence required |
| --- | --- |
| `baseline` | Source and checkpoint captured. No invented approval |
| `draft` | An exploration or iteration, not a canonical replacement |
| `approved` | The user explicitly identifies the subject and revision to adopt |
| `implemented` | Approved revision matched to code, applicable checks passed, and visual verification recorded |
| `archived` | Preserved older or rejected work; prior approval and implementation evidence remain in the record |

Approval records include the user's identity when known, the exact instruction, and when it was given. A selection such as "keep these two" narrows the next round; it does not approve either for implementation.

When the first canonical baseline is captured, set `currentRevision` to that baseline. Capturing an exploration or user's proposed edit never advances this pointer automatically.

Approval applies to the captured artwork, source assumptions, and token snapshot named in the record. If any of those materially change after approval, create a new draft and get approval for that revision; never carry an old approval onto different artwork.

Reviewing without editing does not create an artwork revision. Append a review entry naming the examined revision, checks, and remaining findings. If review identifies edits not yet checkpointed, capture them before continuing.

## Shared token changes

Capture tokens before a sync and record the resulting token snapshot afterward. Update `tokensHash` and `tokenSnapshot` only after per-token results and a read-back agree with the requested source.

A token sync does not increment every component's revision or declare them implemented. Set affected subjects' `needsReview` to true, scoped by token references when available. Clear it only after checking the current design under the new tokens.

## Restore

A restore is a new draft based on the selected historical revision. Rebuild it from saved artwork, tokens, and assets on an exploration page. Keep the current revision and current global token set intact. Ask for approval before promoting the restore; run implementation verification again if code should change.

## Older manifests

For an unversioned manifest:

1. Preserve all file IDs, page IDs, sources, node mappings, themes, and divergences.
2. Add `schemaVersion`, `skillsVersion`, `tokenSnapshot`, `subjects`, and empty `revisions` and `reviews` on existing component records. Their revision pointers start null. Add source `authority` only from observed ownership or the user's answer, never from a guess.
3. Capture a baseline from the actual current source and Paper state on first use. Do not manufacture dates, approvals, or implemented revisions.
4. Show the proposed migration before writing it, save a local backup, and get permission. Unknown schema versions stop the workflow rather than being reset by setup.

## Package releases

The repository's `VERSION` and every skill's `metadata.version` match. `CHANGELOG.md` describes the release. While pre-1.0, minor versions add workflows or change the manifest contract; patch versions fix instructions without changing that contract. At 1.0, use standard major/minor/patch compatibility rules.

A package version does not upgrade a project's manifest automatically. Read the migration procedure first. Version tags, pushes, GitHub releases, and publication require authorization; writing a version file does not create a release.

## Privacy

History can contain private file IDs, source paths, screenshots, and assets. It stays in the user's project and follows that project's storage policy. Never copy it into these skills' repository or public blog examples. Do not publish project history without permission.
