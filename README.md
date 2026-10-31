# Site Extractor Skill 🌐🎨

An AI agent skill to automatically extract a website's **design system** (colors, typography, spacing, components) and **content structure** (pages, outlines, metadata) from any URL.

Compatible with **Google Antigravity**, Cursor, Claude Code, and any AI agent tool that supports markdown-based skills.

---

## ✨ Features

- **Page Discovery:** Automatically inspects `sitemap.xml`, `robots.txt`, and crawls internal links.
- **Content Extraction:** Parses clean Markdown, headings outline (H1-H3), images with alt text, and Schema.org JSON-LD.
- **Design System Reverse-Engineering:**
  - Extracts color palettes (primary, secondary, background, text, accent).
  - Captures typography scales, font families, and line heights.
  - Generates spacing scales, border radiuses, and shadow definitions.
  - Identifies responsive CSS breakpoints and core UI components.
- **Structured Outputs:**
  - `pages.md`: Individual page outlines and cleaned content.
  - `design-tokens.json`: Ready-to-import design tokens (Tailwind, CSS variables, Figma).
  - `site-map.md`: Visual page hierarchy and depth map.
  - `summary.md`: Key structural insights, templates, and consistency audit.

---

## 🚀 Installation

### Option 1: Project-Specific (Recommended for Antigravity)

Clone or copy `SKILL.md` into your project's `.agents/skills/` directory:

```bash
mkdir -p .agents/skills/site-extractor
# Copy SKILL.md into that folder
```

### Option 2: Global (Available Across All Projects)

Copy `SKILL.md` into your global Antigravity config directory:

```bash
# macOS / Linux
mkdir -p ~/.gemini/config/skills/site-extractor
cp SKILL.md ~/.gemini/config/skills/site-extractor/

# Windows (PowerShell)
New-Item -ItemType Directory -Force -Path "$HOME\.gemini\config\skills\site-extractor"
Copy-Item SKILL.md "$HOME\.gemini\config\skills\site-extractor\"
```

---

## 💡 How to Use

Simply ask your AI agent:

> *"Use the site-extractor skill to audit and extract design tokens from https://example.com"*

Or specify parameters:
- **Scope:** `design only`, `pages only`, or `both` (default: both)
- **Page limit:** e.g., `limit to 10 pages` (default: 20)

---

## 🛡️ Ethical Rules & Guardrails

- Honors `robots.txt` and rate limits (1 req/sec).
- Never extracts authenticated screens, login forms, or personal data.
- Intended for audit, design system reconstruction, and reference purposes.

---

## 📄 License

MIT License. See [LICENSE](./LICENSE) for details.
