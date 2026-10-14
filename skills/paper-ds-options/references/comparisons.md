# Choosing a comparison

Choose the comparison before choosing the sheet. Start with the decision the user needs to make, not a default grid of six cards.

## Decision table

| Question | Comparison | Keep fixed | Layout |
| --- | --- | --- | --- |
| Which structure should we choose? | Distinct directions | Content, scenario, DS, viewport | Equal-width option stages. Component grid, block columns, or page columns |
| Did this revision improve the existing design? | Current and proposed | Content, theme, viewport, surrounding screen | Two aligned stages labeled Current and Proposed. Include the current version first |
| Does this component handle its states? | State matrix | Component structure and theme | Columns for actual states; rows for actual variants or sizes when those also matter |
| Does it survive real content? | Content stress comparison | Design, theme, viewport | Normal beside long, empty, or error content. Show only cases that change the outcome |
| Does it work in both shipped themes? | Theme pair | Structure, content, state, viewport | Light beside dark. One stage when only one theme ships |
| Does it work at different widths? | Responsive comparison | Design, content, state, theme | Same design at the product's actual container widths. Do not scale a desktop screenshot down |
| Does it belong on this screen? | In-context comparison | Subject and content | Subject alone plus the real screen around it. For alternatives, use the same surrounding screen |
| Is this optional part necessary? | With and without | Everything except that part | Two stages, one slot toggled. Useful for icons, actions, footers, or badges |
| Are these token choices suitable? | Foundation specimens | Usage example and surrounding colors | Ramp for palette coverage, semantic-role table for meaning, text-on-surface samples for contrast |
| Which font or type treatment should we use? | Matched type specimens | Copy, container, hierarchy roles | Same heading, paragraph, control label, and numerals in each candidate. Compare wrapping and readability, not just a large Aa |
| Can someone complete this journey? | Ordered flow | Scenario and user goal | Steps left to right within each direction. Compare complete journeys, not unrelated screens |
| Is this one design ready? | Single-subject review | Existing subject | Use `paper-ds-review`: focus, relevant states, and context. No invented alternatives |

## Selection procedure

1. State the decision in one sentence in chat, such as "We are comparing how the notice handles long errors, not choosing a new style."
2. Pick one primary comparison from the table. If two decisions are materially different, use separate sections or sheets.
3. Add only the supporting comparison that could change the decision. A notice may need long-message states; a menu may need open and selected states; a billing page may need a second account scenario.
4. Choose the template by subject size: Component, Block, Page, or Review. Clone it and remove irrelevant slots. For Current/Proposed or With/Without, keep two options rather than filling the template with extra candidates.
5. Use the system's spacing and type tokens. Grow stages to fit the real subject; never shrink a component just to fit a preset.
6. Verify every shipped theme. When a full matrix becomes unreadable, split it into compact sections instead of squeezing every combination into one grid.

## Keep comparisons fair

- For structural options, change structure only. A different font, data set, or viewport makes it impossible to tell why an option wins.
- Change one variable in With/Without and Current/Proposed comparisons. Label the versions plainly.
- State and responsive checks are not extra design directions. Keep them under their direction or on a separate verification sheet.
- A responsive frame uses the real available width and reflows content. Enlarging or shrinking a screenshot tests nothing.
- Current comes from the actual canonical/source baseline, with its revision and token snapshot. Proposed is an unapproved draft until the user adopts it. If current behavior is unavailable, say so; never invent shipped UI.
- The user can select a node edited outside the last round. Read and checkpoint that edit before comparing it. A surviving option is not automatically approved or implemented.
- Three strong directions beat six padded-out ones. Six is a template capacity, not a required count.
- Keep critique in chat. Comparison labels describe the condition; they are not drawn comments, pins, or finding lists.

## Examples

- "Show six ways to lay out this Notice" uses structural directions. The same warning and action appear in each, with a long-error check on the survivors.
- "Does this button work?" uses a single-subject review with its real states. It does not generate six buttons.
- "Is the new padding better?" uses Current/Proposed with identical content and width, not a gallery of padding values.
- "Which background should this text use?" uses text-on-surface specimens with contrast checks, not isolated swatches.
- "Explore onboarding" uses complete ordered journeys. Each direction gets the same starting state and end goal.
