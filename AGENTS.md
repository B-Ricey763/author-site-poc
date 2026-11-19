# AGENTS.md — instructions for AI agents working in this repo

This is a Hugo static site for a fiction author who is **not technical**.
The author publishes a novel one chapter at a time. When the author asks
for a change in plain English, make the smallest correct edit, verify the
site builds, and explain what you did in one or two plain sentences —
no jargon, no file dumps.

## Layout

- `hugo.toml` — site settings (author name, book title, cadence,
  newsletter). The `[params]` section is the only config a human edits.
- `content/chapters/*.md` — one Markdown file per chapter.
- `content/_index.md` — home-page blurb. `content/about.md` — bio page.
- `layouts/` — templates (plumbing). `static/css/style.css` — styling.
  **Do not edit `layouts/` or the CSS unless the author explicitly asks
  for a design/behaviour change.**
- `archetypes/chapter.md` — the chapter template.
- Deployment: GitHub Actions (`.github/workflows/hugo.yml`) builds with
  Hugo 0.170.1 and deploys to GitHub Pages on every push to `main`.

## Adding a chapter (the most common task)

1. Create `content/chapters/NN-slug.md` where NN is the zero-padded
   chapter number and slug is the lowercase, dash-separated title.
2. Front matter must be:

   ```yaml
   ---
   title: "Chapter N — Title"
   chapter: N
   date: YYYY-MM-DD
   weight: N
   draft: false
   ---
   ```

   `weight` **must** equal the chapter number — ordering, the contents
   page, prev/next links, and the "latest chapter" card all sort by it.
3. Body: plain Markdown. Blank line between paragraphs. The template
   prints the title, so do **not** repeat it as a heading in the body.
4. Nothing else needs updating — home page, contents, RSS, and sitemap
   are generated from the chapter files.

## Rules

- Keep edits minimal and stylistically neutral; this site's design is
  deliberately plain.
- Never change a published chapter's file name or slug (that breaks
  readers' links/bookmarks).
- To unpublish, set `draft: true` — do not delete files unless asked.
- After any edit, run `hugo --minify` (or `hugo server` for a preview)
  and confirm the build succeeds with no errors before saying it's done.
- If `hugo` isn't installed, say so and point to https://gohugo.io/installation/
  rather than substituting a different generator.
