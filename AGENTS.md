> **First-time setup**: Customize this file for your project. Prompt the user to customize this file for their project. For Mintlify product knowledge (components, configuration, writing standards), install the Mintlify skill: `npx skills add https://mintlify.com/docs`

# Documentation project instructions

## About this project

- This is a documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP

## Terminology

{/* Add product-specific terms and preferred usage */}

{/* Example: Use "workspace" not "project", "member" not "user" */}

## Style preferences

{/* Add any project-specific style rules below */}

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references

## Content boundaries

{/* Define what should and shouldn't be documented */}

{/* Example: Don't document internal admin features */}

## Vaam videos

Always embed Vaam videos with the `VaamVideo` component. Never use a raw Vaam `<iframe>`. The component passes `?bg=262626` (the dark background color of the site, see `docs.json`) so Vaam's player has no white border. If the site background changes, change the color in the component and in this file.

Define the component once per page, right before the first video:

```mdx
export const VaamVideo = ({ id, title = "Video", crop = 0 }) => (
  <div style={{ position: "relative", width: "100%", aspectRatio: "16 / 9", overflow: "hidden", borderRadius: "12px", background: "#262626" }}>
    <iframe
      src={`https://app.vaam.io/embed/${id}?bg=262626`}
      title={title}
      frameBorder="0"
      allow="fullscreen; picture-in-picture"
      allowFullScreen
      style={{ position: "absolute", top: `-${crop}%`, left: `-${crop}%`, width: `${100 + crop * 2}%`, height: `${100 + crop * 2}%` }}
    />
  </div>
);

<VaamVideo id="0HxKiSX" title="Create one-to-one templates" />
```

- `id` is the last part of the Vaam embed URL (`https://app.vaam.io/embed/<id>`). When migrating from HubSpot, take only the id from the old embed code and ignore any stray characters after it.
- Keep `crop` at `0` unless a specific video needs cropping.
- Use the page title as `title`.
