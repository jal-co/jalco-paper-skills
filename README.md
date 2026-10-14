# Manage a design system and iterate on components with Paper

Skills that encode an ongoing way of working in [Paper](https://paper.design): keep the real system available, start from an actual component, compare what matters, refine selected nodes, verify the result in context, and fold approved decisions back into the system and code.

[Read the illustrated workflow](docs/usage.md)

[Versioning the work](docs/versioning.md)

![Six stat tile directions shown in light and dark](docs/images/stat-tile-options.jpg)

## The loop

1. **Maintain the system.** Connect source tokens, fonts, logos, component recipes, and usage rules. Keep Paper aligned without erasing intentional canvas edits.
2. **Start from something real.** Read the component, its actual content and states, current revision, and neighboring UI.
3. **Compare the decision.** Structures need directions. A revision needs Current/Proposed. Behavior needs states, widths, and real content.
4. **Iterate together.** The user selects nodes and edits the canvas. The agent reads those edits and changes only the selected work.
5. **Verify in context.** Check survivors in the real screen, supported themes, relevant states, and real widths.
6. **Land the decision.** Adopt an explicitly approved revision, implement when requested, verify fidelity, and update the canonical component and its usage guidance.

Setup happens once. The loop continues.

## Install

From this checkout:

```bash
npx skills add . --skill '*'
```

From GitHub:

```bash
npx skills add jal-co/jalco-paper-skills --skill '*'
```

Install the whole set because skills load shared references. A private repository requires Git access. `--list` checks discovery without installing. See the [skills CLI](https://github.com/vercel-labs/skills) for agent selection and global installation.

Connect the agent to the Paper MCP separately. Give it access to the project's source and assets. Figma import requires a Figma MCP. Mobbin is optional.

## Start working

> Use paper-ds-manage for our Notice component. Read the current implementation and my selected Paper nodes. Preserve my edits, compare only what needs a decision, and show the survivors in context.

For a first connection:

> Use paper-ds-setup for this project and my Paper file. We ship dark mode only. Use our real tokens and logo, and keep the sheets compact.

After feedback:

> Use paper-ds-iterate on these two nodes. Keep my spacing changes, replace the chip with our actual Badge, and test the long message in context.

To finish:

> Adopt Notice r3 with paper-ds-land and implement it in the existing component. Verify its real states and dark theme. Do not push or publish anything.

## Skills

| Skill | Its part of the loop |
| --- | --- |
| [paper-ds-manage](docs/usage.md#paper-ds-manage) | Entry point for ongoing work and routing |
| [paper-ds-setup](docs/usage.md#paper-ds-setup) | Connect sources and create the maintained workspace |
| [paper-ds-tokens](docs/usage.md#paper-ds-tokens) | Compare drift and snapshot shared token changes |
| [paper-ds-components](docs/usage.md#paper-ds-components) | Import or refresh actual component baselines |
| [paper-ds-options](docs/usage.md#paper-ds-options) | Choose and draw the right comparison |
| [paper-ds-options-component](docs/usage.md#paper-ds-options-component) | Component-sized comparisons |
| [paper-ds-options-block](docs/usage.md#paper-ds-options-block) | Section-sized comparisons |
| [paper-ds-options-page](docs/usage.md#paper-ds-options-page) | Page and journey comparisons |
| [paper-ds-iterate](docs/usage.md#paper-ds-iterate) | Bounded iterations after feedback |
| [paper-ds-review](docs/usage.md#paper-ds-review) | Verify the selected revision in context |
| [paper-ds-land](docs/usage.md#paper-ds-land) | Adopt approved artwork and verify requested code changes |
| [paper-ds-pages](docs/usage.md#paper-ds-pages) | Keep pages, names, canonical nodes, and archives useful |
| [paper-ds-canvas](docs/usage.md#paper-ds-canvas) | Shared Paper tool and rendering rules |

## Versions

Package version **0.2.0 is unreleased**. `VERSION`, skill metadata, and [CHANGELOG.md](CHANGELOG.md) track the package; they do not claim a Git tag exists.

Each project has a schema-versioned `paper-ds.json`. Each subject has its own numbered revisions, source evidence, saved artwork and token snapshots, approval status, and implemented revision. A selected draft is not approved; an approved design is not implemented.

Historical frames still follow live tokens. Saved snapshots and screenshots preserve what a revision actually looked like. See [versioning](docs/versioning.md).

## Customize without losing your work

Edit TEMPLATE frames to change future sheets. Spacing, type, and radii reference your own system. Optional slots can be removed. The agent preserves your edits and checkpoints them before another round replaces them.

Review sheets show the subject only. Critique stays in chat or native comments, never in drawn cards, pins, or finding lists. Private demo links are not included.

## Verification status

The screenshots show an invented sample system called Ledger and the layouts developed in Paper. Empty template stages are intentional. They are not proof of a completed external import or implementation.

The lifecycle and versioning instructions still need end-to-end testing on a real project, including Figma import, reverse sync, single-theme setup, historical restore, and the Paper-to-code verification loop. These are agent instructions, not a plugin that enforces the workflow automatically.

## License

[MIT](LICENSE). Copyright 2026 Justin Levine.
