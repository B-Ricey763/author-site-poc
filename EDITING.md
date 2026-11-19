# Editing this site — the non-technical guide

You do **not** need to know how to code to run this site. The whole site
is just text files written in **Markdown** (the same simple formatting
used on Reddit and Discord: blank line = new paragraph, `*word*` =
*italics*, `**word**` = **bold**, `>` at the start of a line = a quote).

## The only files you'll normally touch

| What you want to change | File |
| --- | --- |
| A new chapter | Add a file in `content/chapters/` (see below) |
| Fix a typo in a chapter | Edit that chapter's file in `content/chapters/` |
| The book blurb on the home page | `content/_index.md` |
| Your bio / about page | `content/about.md` |
| Your name, the book's title, release schedule | The top of `hugo.toml` (it's labeled) |

Everything else — `layouts/`, `static/`, `.github/` — is plumbing.
You never need to open it.

## Publishing a new chapter (on the GitHub website, nothing to install)

1. Open this repository on github.com.
2. Go into the `content/chapters/` folder.
3. Click **Add file → Create new file**.
4. Name it like the others: `04-the-next-title.md` (number, then a
   short lowercase title with dashes, ending in `.md`).
5. Paste this template and fill it in:

   ```
   ---
   title: "Chapter 4 — The Next Title"
   chapter: 4
   date: 2026-11-17
   weight: 4
   draft: false
   ---

   Your chapter text starts here. Leave a blank line between
   paragraphs, exactly like an email.
   ```

   - `chapter` and `weight` are just the chapter number — they keep
     the chapters in order.
   - `date` is the publish date.
   - Set `draft: true` while you're still working on it and the
     chapter stays hidden; flip it to `false` to publish.
6. Scroll down, click **Commit changes**.

That's it. Within a minute or two the site rebuilds itself and the
chapter is live, automatically added to the contents page, the home
page's "latest chapter", and the RSS feed.

## Fixing a typo

Open the chapter file on GitHub, click the pencil icon, fix it,
**Commit changes**. Done.

## The easier way: let an AI agent do it

This repo contains an `AGENTS.md` file written for AI coding agents
(ChatGPT/Codex, Claude, etc.). You can hand the whole repo to an agent
and just talk to it in plain English, for example:

- "Add this as chapter 5, dated Friday" (paste your text)
- "Fix the spelling of the character's name everywhere in chapter 2"
- "Change my release schedule in the site settings to Mondays only"
- "Update my bio to say I live in Austin now"

The agent reads `AGENTS.md`, makes the edit the right way, and can
check the site still builds. You just review and approve.

## Previewing before you publish (optional, needs a helper or an agent)

If the site files are on a computer, one command shows a private
preview at http://localhost:1313 :

```
hugo server
```

Ask an agent to "run the site locally and show me chapter 4" — it
knows what to do.

## Decisions still to make (one-time)

- **Email list:** pick a service (Buttondown is simple and free to
  start). Paste its form address into `newsletterAction` in
  `hugo.toml` and the home-page signup starts working.
- **Web address:** the site can live free at
  `https://<username>.github.io/<repo>/`, or on a custom domain later.
