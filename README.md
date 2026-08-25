# joaovmcorreia.github.io

Personal site + blog, built with [Jekyll](https://jekyllrb.com) and hosted for free on
GitHub Pages. Pushing to `main` rebuilds and deploys the site automatically — no build
step to run yourself.

Live at: https://joaovmcorreia.github.io

## Updating content

**Write a new blog post**
Add a Markdown file to `_posts/` named `YYYY-MM-DD-a-short-title.md`:

```markdown
---
title: "My post title"
---

Whatever you want to say, in Markdown.
```

That's it — it shows up on `/notes/` and the homepage automatically, newest first.

Got half an idea? Drop it in `_drafts/` instead (same file, no date in the filename).
Drafts never appear on the live site until you move them into `_posts/` with a date.

**Edit your research projects**
Everything on `/research/` comes from `_data/research.yml` — edit that one file (it has
a `current` list and a `past` list). The homepage's "Selected work" preview pulls from
the same file, so you only ever update a project in one place.

**Edit your publications**
Same idea: `_data/publications.yml`, with `journal_articles`, `conference_papers`,
`book_chapters`, and `talks` lists. Add a new entry by copying an existing one. Add a
`url:` field to link the title to the paper (DOI, ACL Anthology, etc.) — omit it and
the title just renders as plain text.

**Edit the homepage intro, focus tags, or contact links**
Those live directly in `index.html` and `contact.html` — they're plain HTML with a
little Liquid templating, safe to edit by hand.

## Running it locally

Requires Ruby **3.x** (this repo pins 3.3 in `.ruby-version`). GitHub Pages' `github-pages`
gem is frozen to old dependency versions for stability, and Homebrew's default `ruby`
formula is usually too new for it — resolving against it can land Bundler on a very old,
broken `github-pages` release (native extensions that fail to compile, ancient Jekyll).
If you don't already have a compatible Ruby:

```bash
brew install ruby@3.3
echo 'export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"' >> ~/.zshrc
# open a new terminal, then confirm:
ruby -v   # should print 3.3.x, not 4.x
```

First time only, from this directory:

```bash
bundle install
```

Then, any time you want to preview changes before pushing:

```bash
bundle exec jekyll serve --drafts
```

Open http://localhost:4000. Drop `--drafts` if you don't want draft posts included in
the preview.

If `bundle install` ever fails with a native-extension error (e.g. `yajl-ruby`,
`nokogiri`), it almost always means the wrong Ruby is active — check `ruby -v` first.

## Design

One accent color, three fonts (Newsreader, IBM Plex Sans, IBM Plex Mono), all defined
as CSS variables at the top of `assets/css/main.css`. Layouts live in `_layouts/`,
shared header/footer in `_includes/`.
