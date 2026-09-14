---
layout: post
title: "Specs Are the New Source Code"
date: 2026-09-14
categories: [spec-driven-development, ai-native]
excerpt: "On my AI-native learning journey I keep coming back to one idea from spec-driven development — living artifacts. Here's what it means and why it changes how I build."
---

I'm working my way through an AI-native way of building software. The step that
reframed things for me was learning **spec-driven development** — and specifically
one idea I can't unsee: **living artifacts.** Here's what clicked.

![From dead documents to living artifacts](/assets/sdd-living-artifacts.png)

For most of software's history, the code was the truth. Everything else — the design doc, the requirements, the diagram on the whiteboard — drifted the moment the first line was written. Documentation was a photograph of a plan; the code was the living thing.

**Spec-driven development (SDD) inverts that.** It says: the human-authored specification is the source of truth, and the code is what we *derive* from it.

That sounds like a small reordering. It isn't. It changes what "done" means, where ambiguity gets resolved, and — increasingly — how humans and AI agents share the same understanding of what we're building.

## The principle in one sentence

> Define intent in versioned documents first. Let those documents drive the design, the code, the tests, and the docs — in that order.

Intent flows **downward**: requirements → design → code & test specs → implementation → verification. Nothing appears downstream that can't be traced back to a decision made upstream. The spec isn't paperwork you write to satisfy a process. It's the **contract** everyone — and everything — builds against.

## The deeper idea: living artifacts

The spec on its own isn't the real shift. The real shift is treating *all* our artifacts as **living** — not just the spec, but the design, the decision records, the tests, and the docs.

A living artifact is one that stays true because it *can't quietly fall out of sync*. Three properties make it "living":

- **It's versioned like code.** It lives in the repository, in a diffable format, with history — not in a wiki on a different clock, not in a slide someone emailed once.
- **It's connected.** Every artifact has an identity and explicit links to what it depends on. The requirement knows which design realizes it; the design knows which code and tests implement it; the test knows which requirement it verifies. Together they form a connected web, not a pile of disconnected files.
- **It participates in change.** Because the links exist, editing one artifact can *surface* the others it affects. Change the design, and the code, tests, and docs it touches are flagged for review — rather than left to rot until someone notices months later.

Contrast that with how most teams work today: the requirement lives in a ticket, the design in a wiki, the decision in a chat thread, the code in Git, the tests somewhere else. Each is a frozen snapshot the moment it's written, and none of them know the others exist. Drift isn't a discipline failure — it's the inevitable result of artifacts living apart, changing on different clocks, with no connection between them.

Living artifacts fix that structurally. Put the artifacts on the *same clock, in the same change*, with the links to prove what affects what — and staying in sync becomes the default state instead of a chore. The spec sits at the center of that web as the source of truth, but the whole web is what stays alive.

## Why it matters now more than ever

Two forces make this more than a nice discipline:

**1. Drift is expensive.** When the document and the code disagree, people trust neither. New joiners read stale wikis. Reviewers approve changes they don't fully understand. Bugs hide in the gap between "what we said it does" and "what it actually does." SDD closes that gap by making the spec and the code *travel together* — a change to one is a change to both, reviewed as a single unit.

**2. AI agents need a contract.** An agent generating code is only as good as the intent you give it. A vague prompt yields vague software. A clear, versioned spec is exactly the context an agent needs to produce the right code and the right tests. In an AI-native workflow, the spec becomes the shared language between human judgment and machine execution. Guess-driven prompting doesn't scale. Spec-driven does.

## What SDD is *not*

The principle is easy to caricature, so let me be precise:

- **It is not more bureaucracy.** A good spec is *"good enough"* — detailed enough that no one (human or agent) builds the wrong thing, but not so detailed that writing it costs more than the code. Under-specify and you get garbage. Over-specify and you've written the software twice.
- **It is not for every change.** A typo fix or a config bump doesn't warrant a ceremony. SDD is a discipline applied where change and complexity justify it — not a religion applied everywhere.
- **It is not write-once.** The spec is a *living* artifact. When reality forces a change, you update the intent first and let it flow down — not the other way around.

## The quiet superpower: honesty

Here's the effect that surprised me most when I tried it.

Writing the spec and the tests *before* — or even alongside — the code forces your implementation and your documentation to tell the truth. A feature you *assumed* worked gets a test, and the test either passes or exposes the lie. A claim in your README gets checked against reality. Ambiguity surfaces while it's still cheap to fix, instead of in production.

SDD's real value was never the documents. It's that the documents make it *hard to fool yourself.*

## How to start (small)

You don't need a framework or a mandate. You need one habit:

1. Before your next non-trivial change, write down **what** and **why** — as testable statements.
2. Sketch the **how** and record the decisions you rejected.
3. Turn the "what" into **test cases** before you write the code.
4. Commit the spec **with** the code, so they never diverge.

Do that once and you'll feel it: fewer surprises, honest docs, and a clean thread from intent to implementation to test.

The code used to be the truth. In an AI-native world, **the spec is** — and the code is just its most detailed expression.

---

*This is part of my AI-native learning journey. How are you approaching spec-driven or AI-assisted development — what's working, and what isn't? I'd genuinely like to hear.*
