# Research Section Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add a Research section to msakkal.com with its own listing page, article template, and nav links across all pages.

**Architecture:** Static HTML pages matching the existing site's hand-written approach. New `/research/` directory with `index.html` (listing) and individual article HTML files. Nav updated across all existing pages.

**Tech Stack:** HTML, inline CSS, Google Fonts (Inter + Lora). No JavaScript, no build tools.

**Spec:** `docs/superpowers/specs/2026-03-24-research-section-design.md`

---

### Task 1: Create Research Listing Page

**Files:**
- Create: `research/index.html`

- [ ] **Step 1: Create the research directory**

```bash
mkdir -p research
```

- [ ] **Step 2: Create `research/index.html`**

This page mirrors the homepage layout but only shows research articles. Uses homepage CSS minus `.post-tag`/`--tag-bg`/`.intro` styles. Includes the homepage nav (Research, Cortex, LinkedIn — no "Blog" link since this is a top-level section like homepage).

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="icon" type="image/png" href="/favicon.png">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Research | Mohamad Sakkal</title>
    <meta name="description" content="Essays on AI, technology, and when adding complexity doesn't solve the problem.">
    <meta property="og:title" content="Research | Mohamad Sakkal">
    <meta property="og:description" content="Essays on AI, technology, and when adding complexity doesn't solve the problem.">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://msakkal.com/research/">
    <meta name="twitter:card" content="summary">
    <meta name="twitter:title" content="Research | Mohamad Sakkal">
    <meta name="twitter:description" content="Essays on AI, technology, and when adding complexity doesn't solve the problem.">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Lora:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

        :root {
            --bg: #fafaf9;
            --text: #1c1917;
            --text-secondary: #57534e;
            --border: #e7e5e4;
        }

        body {
            font-family: 'Lora', Georgia, serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.7;
            font-size: 17px;
            -webkit-font-smoothing: antialiased;
        }

        .container {
            max-width: 820px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* Header */
        header {
            padding: 60px 0 40px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 48px;
        }

        header h1 {
            font-family: 'Inter', sans-serif;
            font-size: 24px;
            font-weight: 600;
            letter-spacing: -0.02em;
            margin-bottom: 8px;
        }

        header p {
            color: var(--text-secondary);
            font-size: 15px;
            font-family: 'Inter', sans-serif;
            font-weight: 400;
        }

        header nav {
            margin-top: 20px;
            display: flex;
            gap: 24px;
        }

        header nav a {
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.2s;
        }

        header nav a:hover { color: var(--text); }

        .section-title {
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            color: var(--text-secondary);
            margin-bottom: 8px;
        }

        /* Post list */
        .post-list { list-style: none; }

        .post-item {
            padding: 32px 0;
            border-bottom: 1px solid var(--border);
        }

        .post-item:first-child { padding-top: 0; }

        .post-date {
            font-family: 'Inter', sans-serif;
            font-size: 13px;
            color: var(--text-secondary);
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: 8px;
        }

        .post-item h2 {
            font-family: 'Lora', Georgia, serif;
            font-size: 22px;
            font-weight: 600;
            line-height: 1.3;
            margin-bottom: 10px;
        }

        .post-item h2 a {
            color: var(--text);
            text-decoration: none;
        }

        .post-item h2 a:hover { text-decoration: underline; }

        .post-excerpt {
            color: var(--text-secondary);
            font-size: 16px;
            line-height: 1.6;
        }

        /* Footer */
        footer {
            padding: 48px 0;
            margin-top: 48px;
            border-top: 1px solid var(--border);
            font-family: 'Inter', sans-serif;
            font-size: 13px;
            color: var(--text-secondary);
        }

        footer a {
            color: var(--text-secondary);
            text-decoration: none;
        }

        footer a:hover { color: var(--text); }

        .footer-links {
            display: flex;
            gap: 20px;
            margin-bottom: 16px;
            flex-wrap: wrap;
        }

        /* Responsive */
        @media (max-width: 480px) {
            header { padding: 40px 0 32px; }
            .post-item h2 { font-size: 19px; }
            body { font-size: 16px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Mohamad Sakkal</h1>
            <p>Developer. Builder of Cortex.</p>
            <nav>
                <a href="/">Blog</a>
                <a href="/research/">Research</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
        </header>

        <main>
            <h2 class="section-title">Research</h2>

            <ul class="post-list">
                <!-- First article placeholder — will be added when content is ready -->
            </ul>
        </main>

        <footer>
            <div class="footer-links">
                <a href="mailto:contact@msakkal.com">Email</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
            </div>
            <p>&copy; 2026 Mohamad Sakkal. Vienna, Austria.</p>
        </footer>
    </div>
</body>
</html>
```

- [ ] **Step 3: Verify in browser**

Open `research/index.html` in a browser. Confirm:
- Header matches homepage (name, tagline, nav)
- Nav shows Blog, Research, Cortex, LinkedIn
- "Research" section title appears
- Footer matches homepage
- Responsive at 480px breakpoint

- [ ] **Step 4: Commit**

```bash
git add research/index.html
git commit -m "Add research listing page"
```

---

### Task 2: Add Research Nav Link to Homepage

**Files:**
- Modify: `index.html:201-204` (nav section)

- [ ] **Step 1: Add Research link to homepage nav**

In `index.html`, change the nav from:
```html
            <nav>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
```

To:
```html
            <nav>
                <a href="/research/">Research</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
```

- [ ] **Step 2: Verify in browser**

Open `index.html`. Confirm "Research" link appears in nav and points to `/research/`.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "Add Research nav link to homepage"
```

---

### Task 3: Add Research Nav Link to All Post Pages

**Files:**
- Modify: `posts/why-cortex-exists.html:85-89` (nav section)
- Modify: `posts/the-contradiction.html:100-104` (nav section)
- Modify: `posts/different.html:83-87` (nav section)
- Modify: `posts/my-story.html:90-94` (nav section)

All four post pages have identical nav markup. Add the Research link after the Blog link in each.

- [ ] **Step 1: Update nav in `posts/why-cortex-exists.html`**

Change:
```html
            <nav>
                <a href="/">Blog</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
```

To:
```html
            <nav>
                <a href="/">Blog</a>
                <a href="/research/">Research</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
```

- [ ] **Step 2: Update nav in `posts/the-contradiction.html`**

Same change as Step 1.

- [ ] **Step 3: Update nav in `posts/different.html`**

Same change as Step 1.

- [ ] **Step 4: Update nav in `posts/my-story.html`**

Same change as Step 1.

- [ ] **Step 5: Verify one post page in browser**

Open `posts/why-cortex-exists.html`. Confirm nav shows Blog, Research, Cortex, LinkedIn.

- [ ] **Step 6: Commit**

```bash
git add posts/why-cortex-exists.html posts/the-contradiction.html posts/different.html posts/my-story.html
git commit -m "Add Research nav link to all post pages"
```

---

### Task 4: Create Research Article Placeholder Template

**Files:**
- Create: `research/ai-everywhere-not-success.html`

This is a placeholder article page. The content sections will be filled in later when the user provides their material. The structure and styling are complete.

- [ ] **Step 1: Create `research/ai-everywhere-not-success.html`**

Based on the post page template (`posts/why-cortex-exists.html`) with these changes:
- Back link points to `/research/` with text "Back to Research"
- Nav includes Blog, Research, Cortex, LinkedIn
- Adds blockquote and img CSS rules
- Placeholder content sections

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="icon" type="image/png" href="/favicon.png">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Putting AI Everywhere Does Not Mean Success | Mohamad Sakkal</title>
    <meta name="description" content="Adding AI to a product doesn't automatically make it better. Many implementations add complexity and confusion without solving the actual problem.">
    <meta property="og:title" content="Putting AI Everywhere Does Not Mean Success">
    <meta property="og:description" content="Adding AI to a product doesn't automatically make it better. Many implementations add complexity and confusion without solving the actual problem.">
    <meta property="og:type" content="article">
    <meta property="og:url" content="https://msakkal.com/research/ai-everywhere-not-success.html">
    <meta name="twitter:card" content="summary">
    <meta name="twitter:title" content="Putting AI Everywhere Does Not Mean Success">
    <meta name="twitter:description" content="Adding AI to a product doesn't automatically make it better. Many implementations add complexity and confusion without solving the actual problem.">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Lora:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
        :root {
            --bg: #fafaf9; --text: #1c1917; --text-secondary: #57534e;
            --border: #e7e5e4; --max-width: 820px;
        }
        body {
            font-family: 'Lora', Georgia, serif; background: var(--bg); color: var(--text);
            line-height: 1.7; font-size: 17px; -webkit-font-smoothing: antialiased;
        }
        .container { max-width: var(--max-width); margin: 0 auto; padding: 0 24px; }
        header {
            padding: 60px 0 40px; border-bottom: 1px solid var(--border); margin-bottom: 48px;
        }
        header h1 {
            font-family: 'Inter', sans-serif; font-size: 24px; font-weight: 600;
            letter-spacing: -0.02em; margin-bottom: 8px;
        }
        header p { color: var(--text-secondary); font-size: 15px; font-family: 'Inter', sans-serif; }
        header nav { margin-top: 20px; display: flex; gap: 24px; }
        header nav a {
            font-family: 'Inter', sans-serif; font-size: 14px; color: var(--text-secondary);
            text-decoration: none; transition: color 0.2s;
        }
        header nav a:hover { color: var(--text); }
        .post-header { margin-bottom: 40px; }
        .post-header h1 {
            font-family: 'Lora', Georgia, serif; font-size: 32px; font-weight: 600;
            line-height: 1.25; margin-bottom: 12px;
        }
        .post-meta {
            font-family: 'Inter', sans-serif; font-size: 13px; color: var(--text-secondary);
            text-transform: uppercase; letter-spacing: 0.05em;
        }
        .post-content p { margin-bottom: 20px; }
        .post-content h2 {
            font-family: 'Inter', sans-serif; font-size: 18px; font-weight: 600;
            margin-top: 44px; margin-bottom: 16px;
        }
        .post-content ul { margin-bottom: 20px; padding-left: 24px; }
        .post-content li { margin-bottom: 8px; }
        .post-content a { color: var(--text); }
        .post-content blockquote {
            border-left: 3px solid var(--border); padding-left: 20px; margin: 24px 0;
            font-style: italic; color: var(--text-secondary);
        }
        .post-content img {
            max-width: 100%; height: auto; border-radius: 4px; margin: 24px 0;
        }
        .back-link {
            display: inline-block; margin-top: 48px; font-family: 'Inter', sans-serif;
            font-size: 14px; color: var(--text-secondary); text-decoration: none;
        }
        .back-link:hover { color: var(--text); }
        footer {
            padding: 48px 0; margin-top: 48px; border-top: 1px solid var(--border);
            font-family: 'Inter', sans-serif; font-size: 13px; color: var(--text-secondary);
        }
        footer a { color: var(--text-secondary); text-decoration: none; }
        footer a:hover { color: var(--text); }
        .footer-links { display: flex; gap: 20px; margin-bottom: 16px; flex-wrap: wrap; }
        @media (max-width: 480px) {
            header { padding: 40px 0 32px; }
            .post-header h1 { font-size: 26px; }
            body { font-size: 16px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Mohamad Sakkal</h1>
            <p>Developer. Builder of Cortex.</p>
            <nav>
                <a href="/">Blog</a>
                <a href="/research/">Research</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
            </nav>
        </header>

        <main>
            <div class="post-header">
                <h1>Putting AI Everywhere Does Not Mean Success</h1>
                <div class="post-meta">March 24, 2026</div>
            </div>

            <div class="post-content">
                <!-- CONTENT PLACEHOLDER — will be written from user's raw material -->
                <p>Article content will go here.</p>

                <a href="/research/" class="back-link">&larr; Back to Research</a>
            </div>
        </main>

        <footer>
            <div class="footer-links">
                <a href="mailto:contact@msakkal.com">Email</a>
                <a href="https://linkedin.com/in/MS443" target="_blank">LinkedIn</a>
                <a href="https://ms-dev.app" target="_blank">Cortex</a>
            </div>
            <p>&copy; 2026 Mohamad Sakkal. Vienna, Austria.</p>
        </footer>
    </div>
</body>
</html>
```

- [ ] **Step 2: Add article listing to `research/index.html`**

Replace the empty `<ul class="post-list">` comment with:
```html
            <ul class="post-list">
                <li class="post-item">
                    <div class="post-date">March 24, 2026</div>
                    <h2><a href="/research/ai-everywhere-not-success.html">Putting AI Everywhere Does Not Mean Success</a></h2>
                    <p class="post-excerpt">Adding AI to a product doesn't automatically make it better. Many implementations add complexity and confusion without solving the actual problem.</p>
                </li>
            </ul>
```

- [ ] **Step 3: Verify in browser**

Open `research/index.html`. Confirm the article appears in the list with date, title, and excerpt. Click the title to confirm it links to the article page. On the article page, confirm "Back to Research" links back to the listing.

- [ ] **Step 4: Commit**

```bash
git add research/ai-everywhere-not-success.html research/index.html
git commit -m "Add first research article placeholder and listing entry"
```
