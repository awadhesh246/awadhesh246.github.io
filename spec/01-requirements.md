# 01 — Requirements: awadhesh246.github.io

- **Project:** Personal website & blog
- **Status:** implemented (v1) — reconstructed
- **Author:** Awadhesh Kumar
- **Date:** 2026-09-14

> **Step 1 of SDD.** The site was first built ad-hoc, then iterated on live (added
> certifications, tried a contact form, switched to LinkedIn, removed WordPress).
> These specs are reconstructed afterwards so the site becomes a **living example** of
> spec-driven development going forward. Reversed decisions are kept on purpose — they
> are the most useful part of the record.

---

## 1. Problem statement

I want a personal home on the web that I fully own — for my résumé, my writing, and
notes from my AI-native learning journey — without paying for hosting or maintaining a
CMS. A fresh start, separate from any previous blog.

## 2. Goals

- A simple, fast, free site I control (no subscription, no server to run).
- A homepage that introduces me and links to my profiles.
- An about page with a fuller bio.
- A blog I can grow by adding Markdown files.
- Easy for future-me to maintain and extend.

## 3. Non-goals

- Not migrating old content — this is a clean start.
- No CMS, database, or paid hosting.
- No high-maintenance channels I won't keep up with (e.g. an inbox I rarely check).

## 4. Persona / users

- **Primary:** me — publishing and maintaining it with minimal friction.
- **Secondary:** recruiters, peers, and readers — reading my writing and finding my
  profiles/résumé.

## 5. Functional requirements

- **R1 — Own the site, free.** The system SHALL be hosted at zero cost on
  infrastructure I control (my GitHub account).
- **R2 — Homepage.** The site SHALL have a homepage introducing me with links to my
  key profiles.
- **R3 — About page.** The site SHALL have an about page with a fuller bio.
- **R4 — Blog.** The site SHALL support blog posts authored as Markdown files, listed
  automatically, newest first.
- **R5 — Résumé download.** The site SHALL offer my résumé as a downloadable PDF.
- **R6 — Certifications.** The site SHALL link to my Credly certifications.
- **R7 — Contact.** The site SHALL provide a way for readers to reach me.
- **R8 — Low-friction publishing.** Adding a post SHALL require only creating a
  Markdown file and pushing to Git — no build step run by me.

## 6. Non-functional requirements

- **N1 — Zero cost.**
- **N2 — Fast / static** (no server-side processing at request time).
- **N3 — Low maintenance** — future-me can add content with a documented, simple flow.
- **N4 — Privacy** — don't publish contact details I'd rather keep semi-private
  (e.g. phone number on web pages).

## 7. Acceptance criteria

- Visiting `https://awadhesh246.github.io` shows the homepage with working profile
  links. (R1, R2)
- The about page loads at `/about/` with the bio. (R3)
- A new file in `_posts/` appears in the blog list after a push, within ~2 minutes. (R4, R8)
- The résumé downloads from a link. (R5)
- Certifications link opens my Credly profile. (R6)
- A contact route exists and works without me maintaining an inbox. (R7, N3)
- Total cost is zero. (N1)

## 8. Open questions — and how they were resolved

| # | Question | Resolution |
|---|----------|------------|
| Q1 | Static-site engine? | **Jekyll** — native to GitHub Pages, no build action (design D1). |
| Q2 | How should contact work? | Evolved: form → **LinkedIn** (see design D5 / the reversal). |
| Q3 | Keep the old WordPress blog linked? | **No** — clean start; all WordPress references removed (D6). |
| Q4 | Put phone number on the site? | **No** — kept off web pages; only in the downloadable PDF (N4). |

## 9. Out-of-scope ideas (future)

- Projects page linking my open-source repos (e.g. `mdview`).
- RSS feed + SEO tags (approved Jekyll plugins).
- Nicer theme, tags/category pages, search, dark mode.
- Custom domain.
