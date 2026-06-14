# Hours to Burn — project guide

This file tells Claude Code how to work on this site. Read it before making changes.

## What this is

Hours to Burn is a personal cigar blog written by Salvatore Genovese. The angle: cigars enjoyed occasionally and intentionally, not daily, and without snobbery. It is a plain static website. No framework, no build step, no bundler. Just hand-written HTML files that the browser opens directly.

## How the site is built

- `index.html` is the homepage (the magazine-style landing page).
- Each article is its own HTML file, named with a kebab-case slug that matches its title:
  - `an-afternoon-in-the-yard.html` (category: The philosophy)
  - `your-first-cigar.html` (category: The how-to)
- All CSS lives inline in a `<style>` block inside each file. Every article shares the same template and styles.
- Images (the byline portrait, the footer SG monogram, the homepage cover photo) are embedded directly as base64 `data:` URIs. There are no separate image files to manage. When you duplicate an article file, these embedded images carry over automatically, which is what keeps the byline and footer consistent.
- The favicon is the SG monogram, set in `<head>`.

## Voice and writing rules (most important section)

The writing must sound like Salvatore, not like generic content. Match these:

- Plain, concrete, declarative. Short sentences are good. Say the real thing.
- Dry and a little wry. Quiet self-undercutting closes are on-brand (e.g. "not for any noble reason," "least of all yourself," "this one included").
- First person for his own pieces. He writes from his own experience.
- Show, don't announce. Never explain that a moment "mattered." Let detail carry it.

Hard rules, do not break:

- **No em dashes, ever.** Use commas, colons, periods, or parentheses instead. This is the single most important rule.
- **Never use the word "snobbery" or "connoisseur,"** or frame things as anti-snob. The unpretentious tone should come through without naming it.
- No corny aphorisms or slogan-style headlines ("X is better when Y"). Use plain, editorial, or descriptive phrasing.
- No invented structure: no fake issue numbers, no "No. 01" tags, no pretend magazine furniture.
- Concrete beats connective. Cut any sentence that exists only to sound like a brand.

When in doubt, write less, and keep the parts that are specific and true.

## How to add a new post

1. Duplicate an existing article file as the template. `your-first-cigar.html` is a clean one. Name the copy with a kebab-case slug matching the new title (e.g. `cut-light-savor.html`). Do not rename or delete already-published files; their URLs are permanent.
2. In the new file, change only these fields:
   - `<title>` in `<head>`: `New Title · Hours to Burn`
   - the category line: `<span class="cat">The how-to</span>` (use the right category)
   - the headline: `<h1>New Title</h1>`
   - the dek: `<p class="dek">one plain sentence</p>`
   - the byline date: `<span>Month Year</span>` (e.g. `June 2026`)
   - the body inside `<div class="prose"> ... </div>` (keep the final `<p class="end">◆</p>`)
   - the footer tag: `<span class="tag">Hours to Burn · The how-to</span>`
   - Leave the byline `<img>` and the footer seal `<img>` untouched. They are the embedded portrait and monogram.
3. In the prose, the first paragraph automatically gets a drop cap. Just write normal `<p>` paragraphs.
4. Add a card for the post in `index.html`, inside `<div class="cards">`. Copy an existing `<a class="card" ...>` block, point its `href` at the new file, and set the category, `<h3>` title, and one-sentence blurb.
5. Add a natural cross-link if a related post exists. Link a meaningful phrase in the prose using `<a href="other-post.html">phrase</a>`, not a whole sentence. Prose links are already styled.
6. Commit and push. The push is what publishes the site (see Deploy).

## Editing the landing page

- The three cornerstone cards live in `<div class="cards">`. The first two are wired; the third (`#`) is a placeholder for a future post.
- The dark card tiles (`<div class="shot"></div>`) are intentional ember-in-the-dark graphics, not missing images. A real cigar photo can be dropped in later, but they are fine empty.
- The footer email signup is a "coming soon" placeholder on purpose. Do not wire it to collect emails without being asked; it is not functional by design right now.

## Deploy

The repo is connected to Cloudflare Pages. Pushing to the default branch automatically rebuilds and publishes the live site at hourstoburn.com. There is no manual upload step once that connection exists. To publish a change: commit, push, done.

## Do not

- Do not add em dashes, ever.
- Do not add analytics, tracking, or third-party scripts without being asked.
- Do not rename or delete published article files (breaks URLs).
- Do not reintroduce a functional email form unless asked.
- Do not invent details about cigars or the author. If a fact is needed, leave a clearly marked `[TODO: ask Salvatore]` for him to fill.
