# Demo and image index

[Back to the README](../README.md) / [Illustrated workflow](usage.md)

[Open the approved Paper demo](https://app.paper.design/file/01M4YB3J8ZFB5RE8JA0T21YQV8/p-3-0)

This copy and its screenshots are approved for sharing. The original file is not. Viewing the demo may require Paper sign-in or file access; anonymous access has not been verified.

## What the file contains

The copy has 21 pages, 28 artboards, and 146 tokens. Its 15 canonical component pages are Button, Badge, Input, Textarea, Checkbox, RadioGroup, Switch, Slider, Progress, Tabs, Avatar, Card, Alert, Separator, and Skeleton.

The source is shadcn/ui's documented default neutral theme plus `base-nova` Base UI registry recipes. Geist and Geist Mono are the sample app's fonts, not a font requirement imposed by the component recipes. Upstream component commit versions were not pinned.

These are source-based Paper drawings, not screenshots of rendered React components. The billing screen is a fixture, not a shipped product.

## Alert walkthrough

- [Exploration](https://app.paper.design/file/01M4YB3J8ZFB5RE8JA0T21YQV8/p-4-0): r2 compares native top-right action, below-description action, and separated footer with the same message and Retry action. r3 refines the below-description layout with a 12px action gap.
- [Review](https://app.paper.design/file/01M4YB3J8ZFB5RE8JA0T21YQV8/p-5-0): r3 with normal and long content, a 240px container, both themes, and the billing fixture.

r1 remains canonical. r2 and r3 are local drafts, not official shadcn variants or releases. Neither approval nor verified implementation is recorded for r3.

## Images

All 13 files below come from the approved copy. Paths are relative to this document.

| Image | Shows |
| --- | --- |
| [Alert comparisons](images/shadcn-alert-options.jpg) | Three placements with fixed content in both themes |
| [Alert r3](images/shadcn-alert-r3.jpg) | The below-description refinement and 12px gap |
| [Alert review](images/shadcn-alert-review.jpg) | Normal/long content, narrow width, and billing fixture |
| [Component index](images/shadcn-components.jpg) | The 15 canonical components |
| [Checkbox](images/shadcn-checkbox.jpg) | Static checked, unchecked, focus, invalid, and disabled specimens |
| [Tabs](images/shadcn-tabs.jpg) | Default/line and horizontal/vertical specimens |
| [Avatar](images/shadcn-avatar.jpg) | Fallback sizes, badge, and overlapping group |
| [Color roles](images/shadcn-color-roles.jpg) | Light/dark source roles |
| [Neutral ramp](images/shadcn-neutral-ramp.jpg) | Neutral ramp beside the source roles |
| [Typography](images/shadcn-type.jpg) | Sample app fonts and type scale |
| [Component template](images/shadcn-template-component.jpg) | Empty component comparison stages |
| [Block template](images/shadcn-template-block.jpg) | Empty block comparison stages |
| [Page template](images/shadcn-template-page.jpg) | Empty page comparison stages |

Empty template stages are intentional.

## What was checked

Source lookup, static specimens, local revision checkpoints, screenshots, and page organization were exercised. The copy's page and revision references were checked, and all 146 token records matched the saved source snapshot.

Paper reports some OKLCH hues rounded to one decimal. The source values are preserved locally and the precision difference is recorded. Skeleton's pulse is a static frame; Avatar group blending is approximated with a border.

Keyboard behavior, slider dragging, loading behavior, touch hit areas, adoption, and implementation fidelity were not verified. Figma import, reverse sync, single-theme setup, and historical restore still need end-to-end testing.
