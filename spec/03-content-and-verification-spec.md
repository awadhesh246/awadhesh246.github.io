# 03 — Content & Verification Spec: awadhesh246.github.io

- **Project:** Personal website & blog
- **Inputs:** [`02-design.md`](02-design.md)
- **Date:** 2026-09-14

> **Step 3 of SDD.** For a static content site, "code standards" become **content &
> file conventions**, and "test cases" become **build/content checks** you verify
> after a push. No test framework — the checks are observable on the live site or in
> the Pages build log.

---

## 1. Conventions (the project's "coding standards")

- **Pages:** root-level `.md` with front matter (`layout: home|page`, `title`,
  and `permalink` for non-home pages).
- **Posts:** `_posts/YYYY-MM-DD-title.md`, lowercase hyphenated slug, front matter
  with `layout: post`, `title`, `date`; optional `categories`, `excerpt`.
- **Assets:** live in `assets/`, referenced with a leading slash (`/assets/name.ext`).
- **Excluded from build:** `docs/`, `spec/`, `files-to-add/`, `README.md`, `Gemfile`.
- **Links:** internal links use root-relative paths (`/about/`, `/assets/...`).
- **Privacy:** no phone number or private contact details on published pages (N4).
- **Commits:** per-repo identity `awadhesh246 <awadhesh246@gmail.com>`; small,
  descriptive messages; push to `main`.

## 2. "Interface" — the public surface

| URL | Source | Purpose |
|-----|--------|---------|
| `/` | `index.md` | Homepage + latest posts |
| `/about/` | `about.md` | Bio |
| `/:year/:month/:day/:title/` | `_posts/*.md` | Blog posts |
| `/assets/Awadhesh-Kumar.pdf` | asset | Résumé download |

## 3. Verification checks (the "test cases")

Verify after each push (live site or Pages build log). Each maps to a requirement.

- **C1 (R1/N1):** site loads at `https://awadhesh246.github.io` over HTTPS, free hosting.
- **C2 (R2):** homepage shows intro + working links (GitHub, LinkedIn, Credly, résumé, contact).
- **C3 (R3):** `/about/` loads with the bio.
- **C4 (R4/R8):** a new `_posts/YYYY-MM-DD-*.md` appears in the list, newest first, after push.
- **C5 (R5):** résumé link downloads the PDF (HTTP 200).
- **C6 (R6):** certifications link opens the Credly profile.
- **C7 (R7/N3):** contact link opens LinkedIn (no inbox to maintain).
- **C8 (N4):** no phone number appears on any published page (only in the PDF).
- **C9 (build):** Pages build succeeds — no errors in Settings → Pages / Actions.
- **C10 (D6):** no "wordpress" string anywhere in the repo (`grep -ri wordpress`).

## 4. Definition of done

- All checks C1–C10 pass.
- `docs/MAINTAINING.md` documents how to add posts/pages and extend the site.
- Specs (this folder) committed alongside the site.
