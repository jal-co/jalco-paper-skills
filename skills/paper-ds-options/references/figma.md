# Bringing a system in from Figma

Use this when the user's design system lives in Figma, for tokens, components or reference screens.

## Requirements

- A Figma MCP server is connected. If not, stop and tell the user to connect one. Never guess values from a screenshot.
- The Paper MCP is connected.

## Procedure

1. Call `get_guide({ topic: "figma-import" })` and follow it. Paper only accepts literal CSS values, so every value must be resolved before it is written.
2. **Tokens.** Read Figma variables and styles. Resolve aliases to literal values. Write them with `paper-ds-tokens` generate mode, in the Tailwind v4 namespaces. Keep light and dark as separate `--color-` and `--color-dark-` names.
3. **Components.** For each component the user names, read its variants and auto-layout from Figma and draw it with `paper-ds-components`. Record `figma` as the source in the manifest.
4. **Screens.** Import into the page the user names, one artboard per screen.
5. Resolve before writing: no `var(--...)` from Figma, no Tailwind classes, no token names, no missing dimensions. Use only the last segment of an instance node ID (after the final semicolon).

## Rules

- Import only what the user named. Importing a whole library floods the file.
- Keep Figma's names on layers. People searching Paper will search for the name they know.
- After import, run `paper-ds-tokens` sync to find values Paper changed or dropped, and list them as divergences.
- Never mention Figma or other design tools in placeholder copy that goes on a sheet.
