# Maintaining awadhesh246.github.io

A complete, practical guide to running and growing this site. Written for future-you.

- **Live site:** https://awadhesh246.github.io
- **Repo:** https://github.com/awadhesh246/awadhesh246.github.io
- **Engine:** [Jekyll](https://jekyllrb.com/) + theme `minima`, hosted free on
  [GitHub Pages](https://pages.github.com/). GitHub rebuilds the site automatically
  every time you push to the `main` branch — you don't run any build yourself.

---

## 0. Mental model (read this once)

- You write **Markdown** files. GitHub Pages turns them into HTML pages.
- **Pages** (like Home, About) are standalone `.md` files in the repo root.
- **Blog posts** are `.md` files in the `_posts/` folder, named by date.
- **Configuration** (title, theme, links) lives in `_config.yml`.
- **Images / files** (PDF, pictures) live in `assets/`.
- Push to `main` → wait 1–2 minutes → the change is live. That's the whole loop.

```
awadhesh246.github.io/
├── _config.yml     # site-wide settings (title, theme, links)
├── index.md        # homepage
├── about.md        # About page
├── _posts/         # blog posts — one .md file per post
│   └── 2026-09-14-specs-are-the-new-source-code.md
├── assets/         # images, résumé PDF, downloads
├── docs/           # this guide (not published as a page)
├── Gemfile         # only used for optional local preview
└── .gitignore
```

---

## 1. The everyday workflow

Every change — a new post, an edit, a new image — follows the same three commands
from inside the repo folder (`/mnt/c/Users/emuakwa/JIRA/awadhesh246.github.io`):

```bash
git add -A
git commit -m "Describe what you changed"
git push
```

Then wait ~1–2 minutes and refresh https://awadhesh246.github.io.

> **Identity reminder:** this repo is configured to commit as
> `awadhesh246 <awadhesh246@gmail.com>` and to skip signed pushes — both set
> *locally* so your Ericsson git identity is untouched. You don't need to redo this.

---

## 2. How to add a new blog post

This is the most common task. Two steps.

### Step 1 — create the file

In `_posts/`, create a file named with **this exact pattern**:

```
_posts/YYYY-MM-DD-a-short-title.md
```

Examples:
- `_posts/2026-10-01-my-first-note.md`
- `_posts/2026-12-15-lessons-from-a-side-project.md`

The date in the filename sets the post's date and its URL. The words after the date
become the URL slug (use lowercase and hyphens, no spaces).

### Step 2 — write the content

Every post starts with a **front matter** block (the part between the `---` lines),
then your content in Markdown:

```markdown
---
layout: post
title: "My First Note"
date: 2026-10-01
categories: [notes]
excerpt: "A one-line summary shown in the post list and previews."
---

Write your post here in **Markdown**.

You can use headings, lists, links, images, quotes, and code blocks.
```

That's it. Commit and push (Section 1), and the post appears automatically in the
"Latest writing" list on the homepage.

### Front matter fields explained

| Field | Required? | What it does |
|-------|-----------|--------------|
| `layout` | yes | Always `post` for blog entries. |
| `title` | yes | The post title (quote it if it contains a colon). |
| `date` | yes | Publish date `YYYY-MM-DD` (can add time: `2026-10-01 14:30:00 +0530`). |
| `categories` | no | Tags/groupings, e.g. `[ai, notes]`. |
| `excerpt` | no | Short summary for the list/previews. If omitted, the first paragraph is used. |

> **Tip — drafts:** to keep a post unpublished, either give it a **future date**, or
> put it in a `_drafts/` folder without a date in the filename (drafts only show when
> previewing locally with `--drafts`).

---

## 3. Markdown you'll use most

```markdown
# H1 heading
## H2 heading
### H3 heading

Normal paragraph text. **bold**, *italic*, `inline code`, [a link](https://example.com).

- bullet list item
- another item

1. numbered item
2. another

> A blockquote / callout.

​```python
# a fenced code block with syntax highlighting
def hello():
    print("hi")
​```
```

### Adding an image to a post

1. Put the image file in `assets/` (e.g. `assets/my-diagram.png`).
2. Reference it in the post with a leading slash:

```markdown
![Alt text describing the image](/assets/my-diagram.png)
```

### Linking to another post or page

```markdown
[See my SDD post](/2026/09/14/specs-are-the-new-source-code/)
[About me](/about/)
```

---

## 4. Editing the homepage, About, or links

| To change… | Edit this file |
|------------|----------------|
| Homepage intro text | `index.md` |
| About page | `about.md` |
| Site title / tagline | `title:` and `tagline:` in `_config.yml` |
| Social links (GitHub, LinkedIn) | `minima.social_links` in `_config.yml` |
| Résumé PDF | replace `assets/Awadhesh-Kumar.pdf` (keep the same name) |

After editing, commit and push (Section 1).

### Adding a brand-new page (e.g. "Projects")

1. Create `projects.md` in the repo root:

```markdown
---
layout: page
title: Projects
permalink: /projects/
---

## mdview
A tiny Markdown-to-HTML reader. [Repo](https://github.com/awadhesh246/mdview)
```

2. To show it in the top navigation bar, add it to `header_pages` in `_config.yml`:

```yaml
header_pages:
  - about.md
  - projects.md
```

3. Commit and push. It'll be live at `/projects/`.

---

## 5. Previewing changes before publishing (optional)

You can push straight to `main` and check the live site — that's fine for a personal
blog. If you'd rather preview locally first, you need Ruby + Jekyll (not currently
installed on this machine). One-time setup on Ubuntu/WSL:

```bash
sudo apt update
sudo apt install -y ruby-full build-essential zlib1g-dev
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install jekyll bundler
```

Then, from the repo folder:

```bash
bundle install          # first time only
bundle exec jekyll serve # builds and serves at http://127.0.0.1:4000
```

Edit files, refresh the browser, and push when happy.

> If setup is a hassle, skip it — pushing and checking the live site works perfectly
> well for a blog this size.

---

## 6. Adding more features later

The site is intentionally simple now. Here's how to grow it, roughly easiest first.

### 6.1 A nicer theme
`minima` is clean but basic. Popular upgrades that still work on GitHub Pages:
- **minimal-mistakes** — feature-rich (sidebars, author profile, galleries).
- **jekyll-theme-hydejack**, **al-folio** (great for a portfolio/CV).

To switch: change `theme:` in `_config.yml` to a
[GitHub-Pages-supported theme](https://pages.github.com/themes/), or use a
"remote theme" (see 6.6). Each theme has its own config options — read its README.

### 6.2 Comments on posts
Static sites have no database, so use a third-party comment widget:
- **Giscus** (free, uses GitHub Discussions on your repo) — recommended.
- **Utterances** (free, uses GitHub Issues).
Add the widget's snippet to the post layout (or a theme override).

### 6.3 Analytics (visitor stats)
- **GoatCounter** or **Plausible** (privacy-friendly), or Google Analytics.
- Most themes support adding a tracking snippet via `_config.yml` or a small include.

### 6.4 A custom domain (e.g. `awadhesh.dev`)
1. Buy a domain from any registrar.
2. In the repo: **Settings → Pages → Custom domain**, enter it (this creates a
   `CNAME` file).
3. At your registrar, add the DNS records GitHub shows (an `A`/`ALIAS` or `CNAME`).
4. Enable "Enforce HTTPS" once DNS propagates.

### 6.5 Contact form
Static sites can't process forms themselves. Use a free form backend:
- **Formspree** or **Getform** — point an HTML `<form>` at their URL, no server needed.

### 6.6 Plugins / remote themes
GitHub Pages only allows an
[approved plugin list](https://pages.github.com/versions/) (SEO tags, sitemap, feed,
etc.). Useful safe ones:
```yaml
plugins:
  - jekyll-feed        # RSS feed at /feed.xml
  - jekyll-seo-tag     # better meta tags for search/social
  - jekyll-sitemap     # sitemap.xml for search engines
```
For plugins/themes *outside* the approved list, switch the build to **GitHub
Actions** (build Jekyll yourself, then deploy) — more flexible, slightly more setup.

### 6.7 Tags / categories pages, search, dark mode
- **Tag pages:** themes like minimal-mistakes generate them; on minima you add a
  small `_layouts`/`_includes` override.
- **Search:** client-side search with [lunr.js](https://lunrjs.com/) or a theme that
  bundles it — no backend needed.
- **Dark mode:** many modern themes include a toggle; otherwise add CSS with
  `prefers-color-scheme`.

---

## 7. Troubleshooting

| Symptom | Likely cause / fix |
|---------|--------------------|
| Change not showing after push | Wait 1–2 min; hard-refresh (Ctrl+F5). Check repo **Actions**/**Pages** tab for a failed build. |
| Whole site 404 or won't build | A broken `_config.yml` (YAML is indentation-sensitive) or bad front matter. Check the Pages build log in repo Settings → Pages. |
| Post not appearing | Filename must be `YYYY-MM-DD-title.md` in `_posts/`, with valid front matter, and a date **not in the future**. |
| Image broken | Path must start with `/assets/…` and the file must be committed. |
| Résumé link 404 | The PDF must be at `assets/Awadhesh-Kumar.pdf` and committed. |
| Push rejected `--signed push` | Already handled (`push.gpgSign=false` locally). If it recurs in a new clone, re-run that config. |

**Where to see build errors:** repo → **Settings → Pages** shows the last build
status; the **Actions** tab shows detailed logs if a build failed.

---

## 8. Quick reference (cheat sheet)

```bash
# add a new post
#   create _posts/YYYY-MM-DD-title.md with front matter, then:
git add -A && git commit -m "New post: <title>" && git push

# edit a page or config, then:
git add -A && git commit -m "Update <what>" && git push

# add an image: drop it in assets/, reference as /assets/name.png, then commit+push
```

Live in ~1–2 minutes at **https://awadhesh246.github.io** after each push.
