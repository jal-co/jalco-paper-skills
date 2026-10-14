---
name: paper-ds-setup
description: Connect a project's design system to a Paper file. Creates the Foundations page (colors, type, spacing, logo, fonts), the TEMPLATE page that option sheets are cloned from, and paper-ds.json. Use first in any project, when the user asks to set up Paper for their design system, or when paper-ds.json is missing.
---

# Paper DS setup

Load `paper-ds-canvas` first. Setup runs once per file. Every other `paper-ds-*` skill reads what it produces.

## Procedure

1. **Check the MCP.** Call `get_basic_info`. If the Paper tools are missing, stop and tell the user to open Paper and turn on its MCP server.
2. **Pick the file.** Ask whether to use the open file, a URL, or a new file. Call `create_file` only when asked.
3. **Find the tokens.** Look in this order: `components.json` (shadcn), a Tailwind v4 `@theme` block, Style Dictionary or `tokens.json`, a `theme.ts` export, plain CSS variables. If two candidates exist, ask which is canonical. If none exist, stop and offer `paper-ds-tokens` generate mode.
4. **Ask five questions in one message:**
   - Which themes does the product ship: light and dark, dark only, or light only?
   - Where are the logo files? Never draw a logo unless the user asks for a placeholder.
   - Do options get numbers (01) or letters (A)?
   - What fill should the stage behind each option have: surface, ground or ink?
   - Does the user want a trade-off line or a feedback box under each option? Both default to included as `Optional` slots they can delete.
5. **Sync tokens** with `paper-ds-tokens`.
6. **Build Foundations** from `references/foundations.md`.
6b. **Place the logo.** If the user gave a logo file, write it as an `img` with `paper-asset://` into the `Ledger logo` frame on `05 Logo`, replacing the placeholder, then replace the `Optional Logo` layer on every TEMPLATE sheet with a clone of it. If there is no file, keep the placeholder and say so. Never draw a logo from a description.
7. **Build TEMPLATE** from `references/template.md`, applying the answers from step 4 to the frames themselves. For a single-theme product, delete the second stage from every sheet and the second focus stage from `Sheet Review`, and halve the width of each option.
8. **Organize pages** with `paper-ds-pages`.
9. **Write `paper-ds.json`** (shape below) and store the token `contentHash`.
10. **Verify.** Screenshot every artboard. Report the Paper URLs and anything skipped.

## paper-ds.json

```json
{
  "fileId": "",
  "tokenSource": { "path": "", "kind": "tailwind-v4 | css-vars | style-dictionary | ts" },
  "tokensHash": "",
  "themes": ["light", "dark"],
  "componentDir": "",
  "pages": { "template": "", "foundations": "", "components": "", "blocks": "", "pages": "", "explorations": "", "archive": "" },
  "components": {},
  "divergences": []
}
```

`components` maps a component name to `{ "node": "", "source": "" }`. `divergences` is a list of strings. `paper-ds-components` and `paper-ds-canvas` fill both.

## Rules

- Draw Foundations from the token source. Never invent a value. A made-up swatch teaches agents a color the code does not have.
- An existing Foundations or TEMPLATE page is never overwritten. Run the `paper-ds-pages` audit and ask.
- The look of an option sheet lives in the frames on TEMPLATE, not in a settings list. Users edit a frame directly, and agents read it with `get_jsx`.
