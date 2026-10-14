# TEMPLATE page

Agents clone these frames for every sheet. The user changes how sheets look by editing a frame here. Read those edits before each round; never restore defaults just because the session changed.

## Built from the system's tokens

Every gap, padding, type size and radius on a sheet is a token from the user's system, written as `var(--...)`. Paper keeps the reference, so a sheet follows the system when its tokens change, and a sheet for a dense product reads dense.

Map each part to a step. The steps below are the Tailwind v4 names. Use the nearest step the system has.

| Part | Token |
| --- | --- |
| Sheet padding | `--spacing-8` |
| Between header, options and rows | `--spacing-6` |
| Between options | `--spacing-6` |
| Inside an option (title, stages, notes) | `--spacing-3` |
| Between stages | `--spacing-2` |
| Sheet title | `--text-xl`, `--leading-xl` |
| Context line | `--text-base`, muted |
| Option name | `--text-base`, 600 |
| Pitch and trade-off | `--text-sm`, muted |
| Index | mono `--text-xs`, muted |
| Stage radius | `--radius-md` |
| Notes radius | `--radius-sm` |

Never write a pixel value for any of these when the system has a token. If the system has no spacing scale, run `paper-ds-tokens` first.

The sheet type sets the subject size, not the comparison. Use `../../paper-ds-options/references/comparisons.md` to choose structural options, Current/Proposed, states, widths, theme pairs, or context. Remove unused option frames rather than inventing candidates to fill them.

Stage sizes are content sizes, not spacing, so they stay in pixels:

| Sheet | Options across | Stage |
| --- | --- | --- |
| `Sheet Component` | 3 | 320 x 200 |
| `Sheet Block` | 2 | 480 x 320 |
| `Sheet Page` | 3 | 480 x 600, height set by content |
| `Sheet Review` | 1 subject | 400 x 260 focus, 196 x 128 states, 808 x 360 in context |

Grow a stage only when the subject does not fit. Never shrink the subject.

## Anatomy

1. `Header row`: `Zone heading` (title, context line) on the left, `Optional Logo` on the right.
2. `Options`: a row of `Option NN` frames.
3. Each option: `Option title` (index and name on one line, then the pitch, then the trade-off slot), `Stages` (one stage per theme the product ships), `Optional Notes`.

`Sheet Review` swaps the options for one column: `Focus`, `Optional States`, `Optional In context`. It holds no findings or comments.

## Optional slots

| Slot | Where | Default |
| --- | --- | --- |
| `Optional Logo` | Right of the header | The system's mark and name at `--text-sm` |
| `Optional Trade-off` | Under the pitch, one line starting "Gives up:" | On |
| `Optional Notes` | Bottom of each option, one line labeled Feedback | On |

Delete a slot from a clone when the task does not need it. Never fill one with filler. To drop a slot for good, the user deletes it here.

## Rules

- Read the frame with `get_jsx` before cloning. If the user changed a frame, the clone keeps the change.
- Stage fill is a role (`var(--color-surface)`), never a hex.
- Single-theme products get one stage per option. Compute its width from the remaining stages and resolved gaps; do not blindly halve a width that includes a pair gap.
- Revisions and statuses live in the manifest. Use a compact revision suffix on cloned sheets, not a metadata panel.
- Add a new sheet type only when the user asks. Copy the closest one and rename it.
