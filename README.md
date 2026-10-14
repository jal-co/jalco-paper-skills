# Manage a design system and iterate on components with Paper

<a href="LICENSE"><picture><source media="(prefers-color-scheme: dark)" srcset="https://shieldcn.dev/badge/license-MIT.svg?variant=secondary&amp;size=xs&amp;mode=dark" /><img alt="MIT license" src="https://shieldcn.dev/badge/license-MIT.svg?variant=secondary&amp;size=xs&amp;mode=light" /></picture></a>
<a href="docs/usage.md"><picture><source media="(prefers-color-scheme: dark)" srcset="https://shieldcn.dev/badge/skills-13.svg?variant=secondary&amp;size=xs&amp;mode=dark" /><img alt="13 skills" src="https://shieldcn.dev/badge/skills-13.svg?variant=secondary&amp;size=xs&amp;mode=light" /></picture></a>
<a href="CHANGELOG.md"><picture><source media="(prefers-color-scheme: dark)" srcset="https://shieldcn.dev/badge/version-0.2.0%20unreleased.svg?variant=secondary&amp;size=xs&amp;mode=dark" /><img alt="Version 0.2.0 unreleased" src="https://shieldcn.dev/badge/version-0.2.0%20unreleased.svg?variant=secondary&amp;size=xs&amp;mode=light" /></picture></a>

Skills that encode an ongoing way of working in [Paper](https://paper.design): keep the real system available, start from an actual component, compare what matters, refine selected nodes, verify the result in context, and fold approved decisions back into the system and code.

[Read the illustrated workflow](docs/usage.md)

[Versioning the work](docs/versioning.md)

[Open the Paper demo](https://app.paper.design/file/01M4YB3J8ZFB5RE8JA0T21YQV8/p-3-0) / [Demo images and source notes](docs/demo.md)

![Three Alert action-placement comparisons using default shadcn styling in light and dark](docs/images/shadcn-alert-options.jpg)

## The loop

1. **Maintain the system.** Connect source tokens, fonts, logos, component recipes, and usage rules. Keep Paper aligned without erasing intentional canvas edits.
2. **Start from something real.** Read the component, its actual content and states, current revision, and neighboring UI.
3. **Compare the decision.** Structures need directions. A revision needs Current/Proposed. Behavior needs states, widths, and real content.
4. **Iterate together.** The user selects nodes and edits the canvas. The agent reads those edits and changes only the selected work.
5. **Verify in context.** Check survivors in the real screen, supported themes, relevant states, and real widths.
6. **Land the decision.** Adopt an explicitly approved revision, implement when requested, verify fidelity, and update the canonical component and its usage guidance.

Setup happens once. The loop continues. Each canonical component gets its own page; Components is an index, and exploration and review pages stay separate.

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

**Use `paper-ds-manage` by default.** Describe what you want to do; it routes to the right skill. You can also call a focused skill directly.

> Use paper-ds-manage for our Alert component. Read the current implementation and my selected Paper nodes. Preserve my edits, compare only what needs a decision, and show the survivors in context.

For a first connection:

> Use paper-ds-setup for this project and my Paper file. We ship dark mode only. Use our real tokens and logo, and keep the sheets compact.

After feedback:

> Use paper-ds-iterate on these two nodes. Keep my spacing changes, replace the chip with our actual Badge, and test the long message in context.

To finish:

> Adopt Alert r3 with paper-ds-land and implement it in the existing component. Verify its real states and dark theme. Do not push or publish anything.

## What to use when

| You want to | Use |
| --- | --- |
| Manage ongoing work without choosing a skill yourself | [paper-ds-manage](docs/usage.md#paper-ds-manage) |
| Connect your DS to Paper for the first time | [paper-ds-setup](docs/usage.md#paper-ds-setup) |
| Sync colors, fonts, spacing, radii, or check drift | [paper-ds-tokens](docs/usage.md#paper-ds-tokens) |
| Bring in real components and their states | [paper-ds-components](docs/usage.md#paper-ds-components) |
| Explore alternatives or compare Current/Proposed | [paper-ds-options](docs/usage.md#paper-ds-options) |
| Refine specific nodes after feedback | [paper-ds-iterate](docs/usage.md#paper-ds-iterate) |
| Check one design's states, widths, themes, and context | [paper-ds-review](docs/usage.md#paper-ds-review) |
| Adopt an approved revision and optionally implement it | [paper-ds-land](docs/usage.md#paper-ds-land) |
| Organize pages, rename layers, or archive rounds | [paper-ds-pages](docs/usage.md#paper-ds-pages) |

You normally do not call the format helpers directly: [component](docs/usage.md#paper-ds-options-component), [block](docs/usage.md#paper-ds-options-block), and [page](docs/usage.md#paper-ds-options-page) choose the sheet format. [paper-ds-canvas](docs/usage.md#paper-ds-canvas) supplies shared Paper tool rules.

The usual sequence is **Manage → options → iterate → review → land**. Skip stages the task does not need. Setup happens once; tokens and components get refreshed when needed. Selecting an option does not mark it approved or implemented.

## The shadcn example

The illustrated run uses the default neutral theme and `base-nova` registry recipes. Each of these 15 components has its own page:

**Button, Badge, Input, Textarea, Checkbox, RadioGroup, Switch, Slider, Progress, Tabs, Avatar, Card, Alert, Separator, Skeleton.**

![Compact index of the 15 component pages](docs/images/shadcn-components.jpg)

The page order is TEMPLATE, Foundations, Components index, component pages, exploration/review, then Archive. New pages are placed in their group immediately, not left beside whichever page is active.

The Alert example explains the iteration loop:

- **r1:** imported source baseline
- **r2:** three action-placement comparisons
- **r3:** the below-message action, refined for spacing and checked with long content, narrow width, and a billing fixture

These are local design revisions, not official shadcn releases or component variants. r3 is still a draft. The canonical Alert remains r1, and no revision is marked implemented. See [the worked example](docs/usage.md#the-shadcn-worked-example).

## Versions

Package version **0.2.0 is unreleased**. `VERSION`, skill metadata, and [CHANGELOG.md](CHANGELOG.md) track the package; they do not claim a Git tag exists.

**Release versioning is still pending.** Publishing these changes to `main` is not a versioned release. Before releasing, verify that the version metadata and changelog agree, then create an explicitly approved version tag and release notes.

Each project has a schema-versioned `paper-ds.json`. Each subject has its own numbered revisions, source evidence, saved artwork and token snapshots, approval status, and implemented revision. A selected draft is not approved; an approved design is not implemented.

Historical frames still follow live tokens. Saved snapshots and screenshots preserve what a revision actually looked like. See [versioning](docs/versioning.md).

## Customize without losing your work

Edit TEMPLATE frames to change future sheets. Spacing, type, and radii reference your own system. Optional slots can be removed. The agent preserves your edits and checkpoints them before another round replaces them.

Review sheets show the subject only. Critique stays in chat or native comments, never in drawn cards, pins, or finding lists. The linked demo and its screenshots are approved for sharing. Unrelated private files and project histories stay private.

## Verification status

The current screenshots show the source-based shadcn run. Registry lookup, static component specimens, revision capture, and layout review were exercised. Empty template stages are intentional. Paper reports rounded OKLCH hue precision; the original source values stay in local snapshots, with that difference recorded.

Keyboard behavior, loading behavior, touch hit areas, adoption, and code implementation were not verified. Figma import, reverse sync, single-theme setup, and historical restore also still need end-to-end testing. These are agent instructions, not a plugin that enforces the workflow automatically.

## License

[MIT](LICENSE). Copyright 2026 Justin Levine.
