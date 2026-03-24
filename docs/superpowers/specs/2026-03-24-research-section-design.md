# Research Section Design Spec

## Overview

Add a "Research" section to msakkal.com — a dedicated space for essay-style articles analyzing how AI is used (and misused) in real products. The first article: "Putting AI Everywhere Does Not Mean Success."

## Motivation

The user has firsthand experience building with AI (Cortex) and strong opinions on when AI adds value vs. when it adds pointless complexity. The Research section gives these essays their own home, separate from personal writing.

## Site Changes

### 1. Navigation

Add a "Research" link to the header nav across all pages.

**Homepage nav (new):**
```html
<nav>
    <a href="/research/">Research</a>
    <a href="https://ms-dev.app" target="_blank">Cortex</a>
    <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
</nav>
```

**Post pages and research article pages nav (new):**

Existing post pages already have a "Blog" link pointing to `/`. Preserve that and add "Research":
```html
<nav>
    <a href="/">Blog</a>
    <a href="/research/">Research</a>
    <a href="https://ms-dev.app" target="_blank">Cortex</a>
    <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
</nav>
```

This nav applies to all post pages and all research article pages.

### 2. Research Listing Page — `/research/index.html`

A new page that lists all research articles. Structure mirrors the homepage but only contains research content.

**Layout:**
- Header: same as homepage (name, tagline, nav with Research/Cortex/LinkedIn)
- Section title: "Research" (using existing `.section-title` style)
- Article list: each entry shows date, title (linked to article), and excerpt (using existing `.post-list`, `.post-item`, `.post-date`, `.post-excerpt` styles)
- No tags on research articles
- Footer: same as homepage

**Styles:** Reuse homepage CSS as the base. Omit `.post-tag` / `--tag-bg` styles (no tags on research articles). Inline CSS per page (consistent with current approach — no shared stylesheet).

### 3. Research Article Template — `/research/{slug}.html`

Individual article pages. Structure mirrors existing post pages (e.g., `/posts/why-cortex-exists.html`).

**Layout:**
- Header: same as other pages
- Post header: title (Lora, 32px) + date (Inter, 13px uppercase)
- Post content: paragraphs, h2 subheadings, blockquotes, links, images
- Back link: "&larr; Back to Research" pointing to `/research/`
- Footer: same as other pages

**Nav in header:** Same as post pages (Blog, Research, Cortex, LinkedIn).

**Meta tags:** Full Open Graph and Twitter card meta tags for each article, same pattern as existing posts.

**Additional CSS for article pages** (not in the base post template but needed):
```css
.post-content blockquote {
    border-left: 3px solid var(--border); padding-left: 20px; margin: 24px 0;
    font-style: italic; color: var(--text-secondary);
}
.post-content img {
    max-width: 100%; height: auto; border-radius: 4px; margin: 24px 0;
}
```

**Images:** If an article includes screenshots, store them in `/research/images/`. Use descriptive alt text on all `<img>` tags.

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
  index.html                    (modified — add Research nav link)
  posts/
    why-cortex-exists.html      (modified — add Research nav link)
    the-contradiction.html      (modified — add Research nav link)
    different.html              (modified — add Research nav link)
    my-story.html               (modified — add Research nav link)
  research/
    index.html                  (new — research listing page)
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
