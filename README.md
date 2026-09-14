# awadhesh246.github.io

My personal site and blog, built with [Jekyll](https://jekyllrb.com/) and served
by [GitHub Pages](https://pages.github.com/). Live at
**https://awadhesh246.github.io**.

## Structure

```
.
├── _config.yml     # site config (title, theme: minima, links)
├── index.md        # homepage / short resume
├── about.md        # about page
├── _posts/         # blog posts (YYYY-MM-DD-title.md)
├── assets/         # images, résumé PDF
├── Gemfile         # for local preview (GitHub Pages builds automatically)
└── .gitignore
```

## Add a new post

Create a file `_posts/YYYY-MM-DD-my-title.md` with front matter:

```markdown
---
layout: post
title: "My Title"
date: 2026-01-01
---

Post content in Markdown…
```

## Preview locally (optional)

GitHub Pages builds the site automatically on push, so this is only needed to
preview before pushing:

```bash
bundle install
bundle exec jekyll serve
# open http://127.0.0.1:4000
```

## Notes

- Theme: `minima` (built into GitHub Pages — no build action required).
- The `files-to-add/` folder is a local staging area and is git-ignored.
- **Full maintenance guide:** see [`docs/MAINTAINING.md`](docs/MAINTAINING.md) — how to
  add posts, edit pages, preview locally, troubleshoot, and add features later.
- A reusable blank post lives at [`docs/post-template.md`](docs/post-template.md).
