---
name: paper-ds-review
description: Review one existing component, block or screen in Paper, drawn with the user's design system, with its states and the screen it ships in. Use when the user asks to review, critique, QA or get feedback on a single component or design instead of exploring options, or asks to show one thing to stakeholders for sign-off.
---

# Paper DS review

Load `paper-ds-canvas`, then read `paper-ds.json`. A review looks at one thing. Use `paper-ds-options` when the user wants alternatives.

## Sheet

Clone `Sheet Review` from TEMPLATE onto the subject's exploration page. Name it `Review <subject>`.

| Part | Content |
| --- | --- |
| `Focus` | The subject at real size, one stage per theme the project uses |
| `Optional States` | Up to four states: default, long content, empty, error. Swap in loading or disabled when the subject has them |
| `Optional In context` | The subject inside the real screen it ships in |

Delete `Optional States` when the subject has one state. Delete `Optional In context` when the subject is a whole screen.

## Procedure

1. Find the subject. If it exists as a Paper node, clone it into `Focus`. If it exists only in code, draw it from the code's recipe with `paper-ds-components`. If it exists in neither, stop and ask.
2. Pin real content and real states from the code or the product.
3. Draw the in-context stage from the real screen: clone the shell and neighbors from the manifest.
4. Review it against the Foundations notes and the component's own notes. Check, in this order:
   - Values not on the scale: spacing, type size, radius
   - Colors that are not roles, and roles used for the wrong job
   - Contrast of text roles in each theme
   - States that break: long text, empty, error
   - How it sits next to its neighbors in context
5. Reply with the page URL and the findings as a numbered list: where, what is wrong, the fix, one sentence each.

The sheet shows the subject only. Findings never go on the canvas: no rows, pins or notes. Stakeholders read the design, and the critique lives in chat and in Paper's own comment threads.

## Paper's own comments

The Paper MCP can read comment threads but cannot create them. Before a review, call `list_comment_threads` for the subject's page. Treat each open thread as an input finding and include it in the reply. When a finding is fixed, report it in the reply. Only call `set_comment_thread_status` with the user's explicit permission to resolve that thread.

## Rules

- Review only what was asked. Note other problems in one line at the end of the reply.
- A finding without a fix is an opinion. Give the fix or drop the finding.
- Five sharp findings beat fifteen small ones. Order by how much each changes the result.
