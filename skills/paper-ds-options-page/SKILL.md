---
name: paper-ds-options-page
description: Draw an option sheet of whole-page directions, such as a billing page, dashboard, settings page or onboarding step, laid out side by side for stakeholders. Called by paper-ds-options when the decision is about a full screen. Use directly when the user asks for page-level directions.
metadata:
  version: "0.2.0"
---

# Options for a page

Run the `paper-ds-options` procedure. This skill sets the sheet format for pages.

## Format

- Clone `Sheet Page` from TEMPLATE. Three options across, each with one full-page stage per theme, 480px wide, 600px tall to start, height set by content.
- For a wide product UI, make the stages 1120px wide and put light and dark in separate rows. Say so in the context line.
- Make the zone heading's context line a scenario, not a description: who is using it and what state they are in ("Free plan, two projects, no card on file").

## What a page option decides

For an open page exploration, each option is a direction and answers a different question about the page. Current/Proposed, state, and responsive checks keep the page direction fixed instead:

- What the page leads with: the usage, the plan, the money owed, the next action
- How the page is divided: one column, two, sections, tabs
- What it asks the user to do first
- What it hides

For structural directions, do not make two options that lead with the same thing. Name them for their lead: "Usage first", "Projects first". Revisions use Current and Proposed instead.

## Scenario

Pin one scenario and draw every option in it. The scenario decides which states appear: free plan, over a limit, new user, empty. If the page differs sharply by state, draw a second sheet for the second scenario. Never mix scenarios on one sheet.

## Build

1. Clone shell components (sidebar, header) from the manifest. Draw them once and clone them into every option so the shell cannot differ.
2. Draw the page content per option. Use real data from the product, not placeholder.
3. Keep a fixed width. Let the height grow with content, and set `fit-content`.

## Checks

- Compare the options at thumbnail size. If you cannot tell them apart, the directions are not different enough.
- Every option answers the scenario's first question within the top third of the page.
- Check the shortest and longest real content in each option.
- A rounded page does not mean a polished page. Look for a spacing step that is not on the scale.

## After feedback

Make a `Round 2` sheet with the chosen direction in context: the real shell, real adjacent pages, real data. Then archive the rest.
