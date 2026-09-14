# Spec-Driven Development — awadhesh246.github.io

This folder holds the **specification artifacts** for my personal site, following a
spec-driven development (SDD) workflow: intent in versioned documents drives the
content, structure, and changes.

> **Honest note:** the site was first built ad-hoc, then iterated on live (added
> certifications, tried a contact form, switched to LinkedIn, dropped WordPress).
> These specs were written *afterwards* to turn the site into a **living example** of
> SDD — and, crucially, to record the decisions we made **including the ones we
> reversed**. From here, new features are done **spec-first**.

## Artifacts

| # | Step | File |
|---|------|------|
| 1 | Requirements | [`01-requirements.md`](01-requirements.md) |
| 2 | Design + decision log (with reversals) | [`02-design.md`](02-design.md) |
| 3 | Content & verification spec | [`03-content-and-verification-spec.md`](03-content-and-verification-spec.md) |
| 4 | Task list (done + backlog) | [`04-tasks.md`](04-tasks.md) |

## Why this is a good SDD example

Unlike a throwaway tool, this site **actually evolved** — requirements changed and the
artifacts followed. The clearest case is contact: **Formspree form → WordPress page →
LinkedIn**, reversed because I won't reliably check an inbox. That *why* is captured in
the design decision log (D5) so it isn't re-litigated later. That is living artifacts
in practice: the spec and the site change together, and the reasoning survives.

## Working spec-first from here

For the backlog (Projects page, RSS/SEO plugins, second post, theme):
1. Update `01-requirements.md` (what & why) and `02-design.md` (a new decision D#).
2. Add or check off the task in `04-tasks.md`.
3. Make the change and verify against the checks in `03-...`.
4. Commit the spec change **with** the site change, so they travel together.

See also the reusable global skill and templates:
`~/.kiro/skills/spec-driven-development/`.

## Status

v1 shipped (Phases 1–4 done). Backlog is Phase 5 in `04-tasks.md`.
The `spec/` and `docs/` folders are excluded from the built site (`_config.yml`).
