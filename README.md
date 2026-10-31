# Site Extractor

A skill for coding assistants and agents to extract a website's design system (tokens, colors, typography, components) and content hierarchy from a URL.

Works with Antigravity, Cursor, Claude Code, and other agent environments that support skill instructions.

## What it extracts

- Page structure: Sitemap discovery, internal link crawl, metadata, headings outline, and clean markdown content.
- Design tokens: Palette hex codes (primary, background, text, accent), typography scale, spacing, border radiuses, shadows, and media queries.
- UI patterns: Header, navigation, card, button, and footer structure.

Generated output files:
- pages.md: Markdown exports per page.
- design-tokens.json: Extracted tokens for Tailwind, CSS variables, or design tools.
- site-map.md: Site hierarchy tree.
- summary.md: Breakdown of templates and component consistency.

## Installation

### Project level

Place SKILL.md in your project's .agents/skills/site-extractor/ directory:

```bash
mkdir -p .agents/skills/site-extractor
cp SKILL.md .agents/skills/site-extractor/
```

### Global level

To make the skill available across all projects on your machine:

macOS / Linux:
```bash
mkdir -p ~/.gemini/config/skills/site-extractor
cp SKILL.md ~/.gemini/config/skills/site-extractor/
```

Windows (PowerShell):
```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.gemini\config\skills\site-extractor"
Copy-Item SKILL.md "$HOME\.gemini\config\skills\site-extractor\"
```

## Usage

Provide a URL to the agent and specify the scope if needed:

```text
Extract the design system and pages from https://example.com
```

Options:
- Scope: design only, pages only, or both (default)
- Page limit: e.g. limit to 20 pages

## Rules

- Honors robots.txt and limits crawl rate to 1 request per second.
- Skips authentication pages, private dashboards, and personal data forms.
- For reference and architecture analysis only.

## License

MIT
