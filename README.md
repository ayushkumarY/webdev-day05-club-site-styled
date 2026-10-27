# Day 5 Assignment — CSS Fundamentals

**Week 5 (5.1–5.5)**

## Goal

Style your completed Day 4 club website with one external stylesheet shared by every page. Practice CSS selectors and the cascade, typography and colour, CSS custom properties, and debugging with browser DevTools.

## Repository

Use this repository name:

```text
<rollno>-<firstname>-webdev-day05-club-site-styled
```

## Project setup

1. Find your completed Day 4 website folder.
2. Copy the entire Day 4 folder and use the copy for Day 5.
3. In the copied folder, delete the existing `.git` folder so the new project has its own repository history.
4. Open a terminal in the copied project folder and initialize Git:

   ```bash
   git init
   ```
5. Keep your existing pages, images, and content. Create a `css` folder for the stylesheet.

Suggested structure:

```text
project-folder/
├── index.html
├── other-pages.html
├── images/
├── css/
│   └── style.css
└── design-notes.md
```

## Assignment steps

Complete each step in order. Save and commit your work at each checkpoint.

### 1. Create and link the stylesheet

Create `css/style.css`. Add the stylesheet link inside the `<head>` of **every** HTML page. For pages in the project root, use:

```html
<link rel="stylesheet" href="css/style.css">
```

If a page is inside a subfolder, adjust the relative path, for example `../css/style.css`.

Add initial styles for the page background, text, and headings. Confirm in the browser that the stylesheet loads.

**Commit:** `style: link stylesheet`

### 2. Practice selectors and the cascade

Use at least four selector types in your stylesheet. Include examples of:

- Element selector, such as `body` or `h1`
- Class selector, such as `.card`
- ID selector, such as `#join-us`
- Descendant selector, such as `.site-nav a`

Create a class-versus-ID style conflict on an element in your own page. Inspect it in DevTools and note which declaration wins and why. Remove or resolve the experiment before final submission if it makes the site look incorrect.

**Commit:** `style: add selectors`

### 3. Add typography and colour

Use the Google Fonts pair in the starter stylesheet or choose a suitable pair of your own. Pick a small colour palette and apply it consistently to headings, body text, links, buttons, backgrounds, and cards.

**Commit:** `style: add typography and colours`

### 4. Use CSS design tokens

Move your colours, font choices, common sizes, and spacing values into custom properties under `:root`. Use `rem` for scalable font sizes and spacing. Use percentages or fluid layout rules where they suit the design.

The starter stylesheet below demonstrates these techniques. Adapt its selectors and component styles to fit the HTML you already have.

**Commit:** `refactor: use css variables`

### 5. Debug, document, and push

Use DevTools to inspect the pages and fix styling issues. Remove duplicate or conflicting rules from the final stylesheet. Create `design-notes.md` using the prompts below. Commit and push your repository.

**Commit:** `docs: add design notes`

## Starter stylesheet

Create `css/style.css` and copy this code into it. The class names are examples; either add matching classes to your HTML or rename the selectors to match your existing Day 4 markup.

```css/* Day 5 club site stylesheet
   Add this stylesheet link inside the <head> of every HTML page:
   <link rel="stylesheet" href="css/style.css">
*/

@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Manrope:wght@500;600;700;800&display=swap');

:root {
  /* Colour tokens */
  --color-ink: #17243a;
  --color-muted: #5d6b82;
  --color-primary: #2458a6;
  --color-primary-dark: #173f7d;
  --color-accent: #e5a93d;
  --color-surface: #ffffff;
  --color-page: #f3f6fb;
  --color-border: #dce4ef;

  /* Typography and layout tokens */
  --font-body: 'DM Sans', sans-serif;
  --font-heading: 'Manrope', sans-serif;
  --space-1: 0.5rem;
  --space-2: 1rem;
  --space-3: 1.5rem;
  --space-4: 2rem;
  --content-width: 68rem;
  --radius-card: 0.75rem;
  --shadow-card: 0 0.5rem 1.5rem rgb(23 36 58 / 8%);
}

* {
  box-sizing: border-box;
}

html {
  font-size: 100%;
  scroll-behavior: smooth;
}

body {
  margin: 0;
  color: var(--color-ink);
  background: var(--color-page);
  font-family: var(--font-body);
  font-size: 1rem;
  line-height: 1.6;
}

img {
  display: block;
  max-width: 100%;
  height: auto;
}

a {
  color: var(--color-primary);
  text-underline-offset: 0.2em;
}

a:hover {
  color: var(--color-primary-dark);
}

.site-header {
  color: var(--color-surface);
  background: var(--color-primary);
}

.header-inner,
main,
.site-footer-inner {
  width: min(92%, var(--content-width));
  margin-inline: auto;
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: var(--space-3);
  padding-block: var(--space-2);
}

.site-title {
  margin: 0;
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 800;
}

.site-nav ul {
  display: flex;
  flex-wrap: wrap;
  gap: var(--space-2);
  margin: 0;
  padding: 0;
  list-style: none;
}

.site-nav a {
  display: inline-block;
  padding: 0.4rem 0.65rem;
  border-radius: 0.35rem;
  color: var(--color-surface);
  font-weight: 600;
  text-decoration: none;
}

.site-nav a:hover,
.site-nav a[aria-current="page"] {
  color: var(--color-ink);
  background: var(--color-surface);
}

main {
  padding-block: var(--space-4);
}

.hero {
  padding: clamp(2rem, 7vw, 4.5rem);
  border-radius: var(--radius-card);
  color: var(--color-surface);
  background: linear-gradient(135deg, var(--color-primary), var(--color-primary-dark));
  box-shadow: var(--shadow-card);
}

.hero h1,
h1,
h2,
h3 {
  font-family: var(--font-heading);
  line-height: 1.2;
}

.hero h1 {
  max-width: 15ch;
  margin: 0 0 var(--space-2);
  font-size: clamp(2rem, 5vw, 3.5rem);
}

.hero p {
  max-width: 62ch;
  margin: 0;
  font-size: 1.125rem;
}

.section-heading {
  margin: var(--space-4) 0 var(--space-2);
  color: var(--color-primary-dark);
  font-size: clamp(1.5rem, 3vw, 2rem);
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 15rem), 1fr));
  gap: var(--space-3);
}

.card {
  padding: var(--space-3);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-card);
  background: var(--color-surface);
  box-shadow: var(--shadow-card);
}

.card h2,
.card h3 {
  margin-top: 0;
  color: var(--color-primary-dark);
}

.button {
  display: inline-block;
  padding: 0.7rem 1rem;
  border: 0;
  border-radius: 0.4rem;
  color: var(--color-surface);
  background: var(--color-primary);
  font: 700 1rem var(--font-body);
  text-decoration: none;
  cursor: pointer;
}

.button:hover {
  color: var(--color-surface);
  background: var(--color-primary-dark);
}

#join-us {
  border-left: 0.3rem solid var(--color-accent);
}

.site-footer {
  margin-top: var(--space-4);
  padding-block: var(--space-3);
  color: var(--color-surface);
  background: var(--color-ink);
}

.site-footer p {
  margin: 0;
}

/* Small screens */
@media (max-width: 40rem) {
  .header-inner {
    align-items: flex-start;
    flex-direction: column;
  }

  .site-nav ul {
    gap: var(--space-1);
  }

  main {
    padding-block: var(--space-3);
  }
}
```

## Design notes file

Create `design-notes.md` in the project root and fill in this outline:

```markdown
# Design notes — Day 5

## Design direction
- Site purpose and audience:
- Visual style / mood:

## Colour palette
| Role | Colour value | Where it is used |
|---|---|---|
| Primary | | |
| Secondary | | |
| Accent | | |
| Page background | | |
| Main text | | |

## Typography
- Google Font for headings:
- Google Font for body text:
- Why these fonts work for the site:

## CSS design tokens
| Custom property | Value | Purpose |
|---|---|---|
| `--color-...` | | |
| `--space-...` | | |
| `--font-...` | | |

## Selectors and cascade
List at least four selector types you used. Describe the class-versus-ID test in DevTools, which declaration won, and why.

## DevTools debugging
- Issue found:
- How I found it:
- Fix:

## Final review
- Pages checked:
- Screenshot filename:
- Repository URL:
```

## Turn-in checklist

- [ ] Day 4 website is copied into a fresh Git repository.
- [ ] Every page links to the external stylesheet.
- [ ] The site is styled consistently with fonts and a colour palette.
- [ ] At least four selector types are used.
- [ ] A class-versus-ID conflict was inspected in DevTools and documented.
- [ ] CSS custom properties are used for design tokens.
- [ ] Scalable sizing uses `rem`; suitable fluid widths use `%` or responsive layout rules.
- [ ] Duplicate or conflicting rules have been cleaned up.
- [ ] `design-notes.md` is complete.
- [ ] Repository is pushed; submit its URL and a screenshot of the finished site.

## Final review

Open every page in the browser at desktop and narrow widths. Check that navigation and links work, text is readable, images fit their containers, and no page is missing its stylesheet. Replace the example class and ID names in the starter CSS as needed so they correspond to your own HTML.
