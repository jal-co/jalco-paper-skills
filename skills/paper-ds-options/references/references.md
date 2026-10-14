# Gathering references

References show how strong products solve the same problem. They feed the list of structural ideas. They never feed the styling. The user's system supplies the styling.

## Sources, in order

```
Is the Mobbin MCP connected? (tools named mcp__mobbin__*)
├── Yes → Mobbin
└── No
    ├── Does the user have a Figma file or link for this surface? → references/figma.md
    ├── Does the Paper file already hold similar pages? → read them with get_tree_summary and get_screenshot
    ├── Did the user attach screenshots? → use them
    └── None → skip references and write ideas from the content itself
```

Use the first source that works. Never ask the user to install Mobbin. Say which source was used.

## Mobbin

Run three to five searches aimed at how strong products lay out this kind of content, not at products that look like the user's:

- `search_screens` for a single screen
- `search_sections` for a block
- `search_flows` for multi-step surfaces

Pass `output_destination: "design_tool"` and `output_tool: "Paper"`. If a search reports a sign-in requirement, stop and tell the user to sign in to the server.

Look at the returned images. Never describe a result from its metadata alone. Cite each result you use with its `mobbin_url`.

## Without references

Name the structural axes of the content and make one idea per axis:

- How the main figure or object is presented: large, inline, in a row, in a field
- How supporting data attaches: beside, below, behind, in a drawer
- How density changes: one item per card, a row per item, a table
- How emphasis works: size, color fill, an edge, position
- What the user does next: where the action sits, and how many there are

Write one line per idea in chat before drawing.

## What to take from a reference

Take the structure: the grouping, the order, the proportions. Never take its colors, type or radii. A reference never appears on a sheet unless the user asks for a "reference" column, in which case it is a labeled image beside the options.
