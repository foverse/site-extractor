---
name: site-extractor
description: Extracts the design system (colors, fonts, spacing, components) and the pages (structure, content, metadata) of a website. Use when the user gives a URL and asks to clone, audit, document or reuse a site's design or page content.
---

# Site Extractor

## Inputs
- A URL (required)
- Scope: design only, pages only, or both (default: both)
- Page limit (default: 20)

## Workflow

### 1. Discover pages
- Fetch /sitemap.xml (and robots.txt for sitemap links).
- If none, crawl internal links from the homepage, same domain only.
- Deduplicate URLs, drop query strings and anchors.

### 2. Extract pages
For each page, capture:
- URL, title, meta description, canonical, lang
- H1 to H3 outline
- Main content as clean markdown (no nav, footer, cookies)
- Images with alt text, internal and external links
- Schema.org JSON-LD

### 3. Extract design
From the homepage and 2 to 3 representative templates:
- Colors: most used hex values, grouped (primary, secondary, background, text, accent)
- Typography: font families, sizes, weights, line heights for h1-h6, body, buttons
- Spacing scale, border radius, shadows
- Components: header, hero, cards, buttons, forms, footer (structure + styles)
- Breakpoints from the CSS media queries

### 4. Output
- pages.md: one section per page
- design-tokens.json: colors, fonts, spacing, radius, shadows
- site-map.md: page tree with depth
- summary.md: key findings (template types, design consistency, gaps)

## Rules
- Respect robots.txt and rate limits (1 request per second).
- Never extract logins, forms with personal data, or paywalled content.
- Do not copy copyrighted text or images for republication, only for analysis or reference.
- Report any page that fails (status code) instead of skipping silently.
