---
name: paper-ds-options
description: Generate design options in Paper for a component, block or full page, drawn with the user's own design system and laid out for stakeholder review. Use when the user asks for variants, options, directions, explorations or alternatives of a UI piece, or asks to show stakeholders a few ways to do something. Works without Mobbin.
---

# Paper DS options

Load `paper-ds-canvas`, then read `paper-ds.json`. If the manifest or the `Foundations` page is missing, run `paper-ds-setup` first. Options drawn without the system look like every other generated design.

## Choose the comparison

Read `references/comparisons.md` before drawing. Decide what the user is comparing: directions, Current/Proposed, states, content, themes, widths, context, an optional slot, foundation specimens, or an ordered flow. State that decision in one sentence in chat. The request decides the comparison; a template does not require six candidates.

Then choose the primitive. Reviewing one existing thing, not choosing between options? Use `paper-ds-review`.

```
What is being decided?
├── One component (a badge, a tile, a toast)  → paper-ds-options-component
├── A section made of components (pricing table, settings card, empty state) → paper-ds-options-block
└── A whole screen or flow step               → paper-ds-options-page
```

If the request spans two levels, ask which decision comes first. A page option sheet that invents new components hides two decisions in one picture.

## Procedure

1. **Pin the content.** Find the real surface in the project code. Copy its labels, data shape, counts and states. Every option shows exactly this content, so only structure differs. Invented filler hides whether a layout survives real names and real counts. If nothing exists, write one realistic data set and state it in the context line.
2. **Read the system.** Read the Foundations notes and the `Instruction notes for agents` on each artboard you use. Use only roles, scale steps and components in the manifest. Never write a hex that exists as a token.
3. **Gather references** from the first source that works (see `references/references.md`). None is required. A sheet without references is fine.
4. **Plan the chosen comparison.** For structural directions, list distinct ideas in chat. Two ideas that differ only in color or spacing are one idea; replace the duplicate. Include a dense, a spacious, and a non-obvious direction when the request is an open exploration. For states, revisions, or other checks, use the relevant conditions from `references/comparisons.md` instead of inventing directions.
5. **Create the exploration page** named for the subject (see `paper-ds-pages`), then clone the matching sheet from `TEMPLATE`. Read the template frame with `get_jsx` first. The user may have edited it, and a clone must keep their edits.
6. **Draw each option** in one stage per theme listed in `themes`. Clone real components from the manifest. Draw only what the idea changes.
7. **Review.** Screenshot the sheet. Check every option against the real content, in every theme. Fix with targeted edits. Look for clipped text, a tile that matches its stage color, and hard-coded colors.
8. **Reply** with the page URL, then one line per option: number, name, what it gives up. End with a recommendation and why.

## Sheet anatomy

Every sheet has a header row (zone heading and logo), a row of options, and per option a title block with an index, a name and a one-line pitch, then one stage per theme the product ships. Keep the template's gaps.

Three slots come from the template and are on by default:

- `Optional Logo`: the system's logo, top right. Replace it with a clone from Foundations.
- `Optional Trade-off`: one line starting "Gives up:".
- `Optional Notes`: an empty feedback box.

Delete a slot from the clone when it adds nothing. Never fill one with filler. The empty feedback box is for stakeholders.

## Comments

Keep review comments, pins, and findings off the sheet. Put critique in the reply. The reserved comment role stays in Foundations; it is not part of an option's design.

## Rounds

1. After feedback, make a second sheet below the first, named `Round 2`, holding only the survivors.
2. Draw round two in context: place each survivor inside the real screen it ships in, not on a blank stage. An option that wins alone often fails next to its neighbors.
3. When one wins, move the losers to `Archive` and note the decision in the page's last frame.

## Rules

- The decision sets the count. Current/Proposed and With/Without use two stages; state matrices use the actual states. For open exploration, start with three to six distinct directions unless the user asks for more.
- Never recommend an option you would not ship. State the cost of the recommendation.
- A sheet shows differences. If three options look alike at a glance, merge them.
