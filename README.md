# danielcieslak.github.io

Personal portfolio site for **Daniel Cieslak** — Data Analytics Engineer.
Single-page, static site built with Tailwind CSS, hosted on GitHub Pages at
<https://danielcieslak.github.io>.

## How it works

The page layout is in **`index.html`**. The content you change often —
**projects, articles, and "What I'm Learning"** — lives in separate data files
under the **`content/`** folder:

```
content/
├── projects.json    ← Selected Work
├── articles.json    ← Writing
└── learning.json    ← What I'm Learning
```

`index.html` loads these files at page load and renders them automatically. So
to post or edit content you edit a JSON file — you never touch the layout HTML.

## Adding / editing content

### Add a project — `content/projects.json`

Copy an existing block, paste it, and edit the text. Keep the comma between
blocks. Order in the file = order on the page; delete a block to remove it.

```json
{
    "title": "Workforce headcount dashboard",
    "blurb": "Executive Power BI dashboard modelling headcount and turnover for 11,500+ employees.",
    "links": [
        { "label": "Case study", "url": "https://..." },
        { "label": "Code", "url": "https://github.com/danielcieslak/..." }
    ]
}
```

- Add as many `links` as you like (`Code`, `Live demo`, `Case study`, …).
- Use `"url": "#"` as a placeholder if you don't have a link yet.

### Add an article — `content/articles.json`

```json
{
    "title": "How we cut manual reporting by 90%",
    "date": "June 2026",
    "summary": "One or two sentences on what the piece is about.",
    "url": "https://linkedin.com/pulse/..."
}
```

`url` can be **either**:
- an **external** link (LinkedIn, Medium, Substack) — opens in a new tab automatically, or
- a **page you host yourself**, e.g. `"articles/my-post.html"` — create that HTML
  file in the repo and link to it. (Recommended: keep the canonical copy on your
  own site and cross-post the link to LinkedIn.)

### Edit "What I'm Learning" — `content/learning.json`

Change `intro` (one line of text) and the `topics` list of
`{ "topic", "detail" }` items.

> **JSON rules:** every value is in `"double quotes"`, use a comma between items
> but **not** after the last one. If the page shows nothing, the JSON probably
> has a typo — paste it into <https://jsonlint.com> to find it.

### Other sections (About, Experience, Contact, CV)

These change rarely, so they're plain HTML in `index.html` — edit the text
directly. Replace `cv.pdf` in the repo root with your real résumé PDF.

## Preview locally

Because the browser *fetches* the JSON files, opening `index.html` directly
(`file://`) will show the page with **empty** content sections. Run a small
local server instead:

```sh
python3 -m http.server
```

Then visit <http://localhost:8000>. (On GitHub Pages it just works — this only
affects local preview.)

## Publishing

The site is a GitHub Pages **user site** — pushing to the `main` branch of
`danielcieslak/danielcieslak.github.io` publishes automatically:

```sh
git add -A
git commit -m "Update projects and articles"
git push
```

Changes go live at <https://danielcieslak.github.io> within a minute or two.

## Notes / possible upgrades

- Tailwind is loaded from `cdn.tailwindcss.com`, which is meant for prototyping
  and prints a console warning in production. If you want to remove the warning
  and shrink the payload, switch to a compiled Tailwind build (adds a build step).
- If you start writing a lot of long-form articles, consider moving to a
  Markdown-based static generator (Jekyll runs on GitHub Pages with no local
  build). For now, self-hosted HTML pages or external links via the `articles`
  list are enough.
