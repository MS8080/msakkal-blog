# Research Section Design Spec

## Overview

Add a "Research" section to msakkal.com — a dedicated space for essay-style articles analyzing how AI is used (and misused) in real products. The first article: "Putting AI Everywhere Does Not Mean Success."

## Motivation

The user has firsthand experience building with AI (Cortex) and strong opinions on when AI adds value vs. when it adds pointless complexity. The Research section gives these essays their own home, separate from personal writing.

## Site Changes

### 1. Navigation

Add a "Research" link to the homepage header nav, alongside the existing Cortex and LinkedIn links.

**Homepage header nav (current):**
```html
<nav>
    <a href="https://ms-dev.app" target="_blank">Cortex</a>
    <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
</nav>
```

**Homepage header nav (new):**
```html
<nav>
    <a href="/research/">Research</a>
    <a href="https://ms-dev.app" target="_blank">Cortex</a>
    <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
</nav>
```

The same nav link should appear in the header of all post pages and research article pages.

### 2. Research Listing Page — `/research/index.html`

A new page that lists all research articles. Structure mirrors the homepage but only contains research content.

**Layout:**
- Header: same as homepage (name, tagline, nav with Research/Cortex/LinkedIn)
- Section title: "Research" (using existing `.section-title` style)
- Article list: each entry shows date, title (linked to article), and excerpt (using existing `.post-list`, `.post-item`, `.post-date`, `.post-excerpt` styles)
- No tags on research articles
- Footer: same as homepage

**Styles:** Reuse all existing CSS from homepage. No new styles needed. The inline CSS is duplicated per page (consistent with current approach — no shared stylesheet).

### 3. Research Article Template — `/research/{slug}.html`

Individual article pages. Structure mirrors existing post pages (e.g., `/posts/why-cortex-exists.html`).

**Layout:**
- Header: same as other pages
- Post header: title (Lora, 32px) + date (Inter, 13px uppercase)
- Post content: paragraphs, h2 subheadings, blockquotes, links
- Back link: "&larr; Back to Research" pointing to `/research/`
- Footer: same as other pages

**Nav in header:**
```html
<nav>
    <a href="/research/">Research</a>
    <a href="https://ms-dev.app" target="_blank">Cortex</a>
    <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
</nav>
```

**Meta tags:** Full Open Graph and Twitter card meta tags for each article, same pattern as existing posts.

### 4. First Article — "Putting AI Everywhere Does Not Mean Success"

- File: `/research/ai-everywhere-not-success.html`
- Listed on `/research/index.html` with date, title, and excerpt
- Content: essay/opinion piece written from the user's raw input (experiences, screenshots, examples provided separately)
- Tone: matches existing writing — direct, personal, clear. Not academic, not preachy.
- Core argument: Adding AI to a product doesn't automatically make it better. Many implementations add complexity, cost, and user confusion without solving the actual problem. Examples include unnecessary AI chatbots that still route to humans, email filtering that adds overhead without value.

**Note:** Article content will be written in a separate step after the user provides their raw material (experiences, screenshots, examples).

## File Structure

```
msakkal-blog/
  index.html              (modified — add Research nav link)
  posts/
    why-cortex-exists.html (modified — add Research nav link)
  research/
    index.html             (new — research listing page)
    ai-everywhere-not-success.html (new — first article)
```

## What This Spec Does NOT Cover

- Article content (depends on user-provided material)
- Any JavaScript or build tooling changes (site remains static HTML)
- Any changes to existing post content or styling
- RSS feed or SEO sitemap updates

## Design Principles

- Match existing site aesthetics exactly (typography, colors, spacing)
- Keep the static HTML approach — no frameworks, no build steps
- Inline CSS per page (consistent with current pattern)
- Mobile-responsive (same breakpoints as existing pages)
