---
name: paper-ds-components
description: Bring a project's components into Paper as real, cloneable artboards with every variant and state, and keep a map from each component to its Paper node and source file. Use when the user asks to pull components into Paper, document components in Paper, or when an option sheet needs the real component instead of a hand-drawn imitation.
---

# Paper DS components

Load `paper-ds-canvas` first. Option sheets only look like the product if they clone the real components. A hand-drawn chip fails the first time someone says "use the actual Badge".

## Where components come from

Try these in order. Stop at the first that works and record which one in the manifest.

1. **Code.** Read the component directory in `paper-ds.json`. Each component's variant and size unions, defaults and class recipe are the source of truth.
2. **Stories.** Storybook or similar stories give real props and states per component. Use them to pick which states to draw.
3. **Figma.** If the system lives in Figma, load `paper-ds-options/references/figma.md` and import with `get_guide("figma-import")`.
4. **Screenshots.** Last resort. Ask the user for screenshots and draw from them. Mark every component drawn this way `approximate` in the manifest.

## Procedure

1. List components from the source. Ask which to bring in when there are more than 12. Never import all of a large library without asking, because each component costs dozens of writes.
2. Create the page `Components` if it does not exist (see `paper-ds-pages`).
3. One artboard per component, named exactly as in code (`Badge`). Build from the code's actual recipe: padding, radius, type size and colors by role. Never approximate a value that the code states.
4. Lay out a matrix inside the artboard:
   - Columns are variants. Rows are sizes. Each cell is one component instance.
   - A second block shows states: default, hover, focus, disabled, loading, error. Draw only states the component has.
   - One panel per theme the product ships.
5. Name every instance layer by its props: `Badge warning subtle sm`. An agent finds the right instance by name.
6. Add `Instruction notes for agents` under each artboard: when to use it, the alternative to use instead, the default variant. Take these from the code and call sites. Write nothing you cannot trace to a file.
7. Record in `paper-ds.json`: `components.<Name> = { "node": "<artboard id>", "source": "<path>" }`.
8. Screenshot each artboard in every theme the product ships and fix defects with targeted edits.

## Using components in a sheet

Clone the instance named for the props you need with `x-paper-clone`, and override only content. Never redraw a component that has a node in the manifest. If the manifest has no node for it, import it first.

## When Paper cannot match the code

Gradients built from `color-mix()`, SVG noise and filters do not render. Draw the nearest static equivalent, label the layer `approximate`, and add a line to `divergences` naming the component and the missing effect. The sheet then tells stakeholders the final result will differ.

## Rules

- A component that appears in code but has no call sites is probably dead. Ask before importing it.
- A variant drawn in Paper that is not in the code's union does not exist. Never add one to make a sheet look fuller.
- Keep instance sizes at the real pixel size. Scale a whole sheet stage if it must fit, never the component.
