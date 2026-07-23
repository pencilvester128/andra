# Andra

Andra is a developmental editor for AI-adoption and AI-upskilling training plans — the
kind written by a business owner or team leader who's genuinely good at what they do,
but isn't a professional trainer, and has been handed the job of turnkeying AI literacy
to their team. It reviews the plan across Word docs, text, Markdown, slides, or HTML. It
does not write your slides, build your curriculum, or make the call for you — that
stays with you.

It isn't an app. There's no site to log into. The product is a folder of files you drop
into a Claude Project — a workspace on claude.ai where you hand the AI a set of
documents plus standing instructions, and it behaves the way those files describe.

**The one-line operating principle:** point at what's broken in the plan, explain why
it's broken for *this specific audience*, and hand it back for the leader to fix.
Andra never rewrites the plan. If the plan were fixed for the leader, they'd hit the
gaps they didn't anticipate the moment they stood in front of their actual team — and
by then it's too late to learn the mistake cheaply.

## Installation (Claude Project, ~5 minutes)

1. On claude.ai: **Projects → New Project**. Name it, e.g., `Andra — Training Plan Editor`.

2. In **Instructions** (custom instructions), paste exactly:

   > You are Andra, a developmental editor for AI-adoption training plans. Read
   > `identity.md` — it is who you are. Follow `rules.md` verbatim in every review.
   > Your source of truth for every diagnostic pass is the `reference/` files
   > (andragogy, change-management, resistance, editing-craft, heuristics,
   > plan-checklist, failure-modes) — cite them, never restate them wholesale. Never
   > rewrite the user's plan; diagnose it and hand it back.

3. In **Knowledge**, upload the files in two quick passes (claude.ai uploads files,
   not folders — there's no way to drag the whole `andra/` folder in one go):
   - from the repo's root: `identity.md`, `rules.md`, `examples.md`,
     `profile-template.md`;
   - then open `reference/` and upload all **7 files** inside it. That's **11 files
     total** — nothing else (skip `README.md`, `JUDGE_GUIDE.md`, `WRITEUP.md`, and
     `reviews/`; those are for a human reading the repo, not for Andra).

4. Open a chat in the Project and paste your draft plan (or describe it) and tell
   Andra who it's for.

That's the whole setup — the upload *is* the install. You should see Andra open with a
`Mode:` line and, if the audience isn't already stated, a question about who the plan
is for before it critiques anything. If it just starts rewriting your plan, the project
instructions in step 2 didn't take — recheck it.

## Seeing it work

Hand Andra a training plan and ask it to review the plan for rolling out an AI tool to
your team. The first line back is a `Mode:` declaration, so you can see how it read your
request before it runs with it. Every flag that follows takes the same shape: it names
the exact slide or sentence, ties it to a named principle or heuristic, and asks a
question instead of handing you a fix. Try asking it to "just rewrite this part for me"
— it will decline and tell you why, because that's the one boundary it won't cross.

## How it works

Every load-bearing piece carries an ID, so the design can be checked line by line rather
than taken on trust. `IDENT-NN` is a frame primitive — what Andra is and won't do.
`RULE-NN` is a named runtime behaviour. `STATE-NN` is a stage in the review's state
machine, and `TRANSITION-NM` is a move between two stages.

- **The frame** (`identity.md`, `IDENT-01..07`) — what Andra is (a developmental
  editor, not a rewriter), who it's reviewing for, the critique contract, the anti-
  rewrite boundary, and a frozen evidence snapshot.
- **The behaviour** (`rules.md`, `RULE-01..14`) — mode routing, context intake, the
  Three-Part-Query comment structure, the andragogy/rollout-arc/resistance diagnostic
  passes, prioritization, and the review close.
- **The knowledge** (`reference/`) — the andragogy principles, change-management
  frameworks, resistance/adoption psychology, the editing craft that shapes every
  comment, and a set of named field heuristics (the Curse of Mastery, the Sage-on-the-
  Stage Default, and others) drawn from 11+ years running L&D and change management for
  real teams. Rules cite this layer; they don't restate it.
- **The state** (`profile-template.md`) — the trainer's own profile file. You fill it
  and keep it; Andra reads it to tailor itself and proposes edits, but never writes it.

A review follows a fixed trajectory: it intakes the audience and format, diagnoses
against three lenses, prioritizes down to the highest-leverage flags, and hands the plan
back. Five stages (`STATE-1..5`), eight named transitions between them.

## What's in the folder

| Item | What it is |
|---|---|
| `identity.md` | The frame — what Andra is, who it reviews for, the critique contract, the anti-rewrite boundary, the evidence snapshot. |
| `rules.md` | The behaviour — fourteen named behaviours, the five-stage review state machine, and the transitions joining them. |
| `examples.md` | Five worked reviews showing the frame in action, plus a generic-fail vs. specific-pass reference table. |
| `profile-template.md` | The blank trainer-profile schema. You own it; Andra reads it and never writes it. |
| `reference/` | The domain knowledge: andragogy, change-management, resistance/adoption psychology, editing craft, named field heuristics, a citable plan checklist, and a two-sided failure-mode catalogue. |

The rest of the repository (`JUDGE_GUIDE.md`, `WRITEUP.md`, `reviews/`) is there so a
stranger can evaluate the build — not required to run it.

## The stance

An editor is not a rewriter. Andra's whole job is diagnosis: name what's not working,
tie it to a real framework or a named field pattern, and trust the person who owns the
plan to fix it. That's not a stylistic choice — it's the point. A leader who never sees
where their own plan would have failed learns nothing for the next one; a leader who
gets a clean rewrite handed to them ships something they don't fully understand, and
finds out what's missing live, in front of their team.

## What it won't do

- Rewrite your plan, build your curriculum, or design your slides.
- Copyedit or proofread — this is a developmental-layer editor, not a line editor.
- Hand you a "fixed" version of anything. The one narrow exception is a clearly labeled
  illustrative contrast that never touches your actual material.
- Pretend its adoption statistics are live — they're a dated 2026-07 snapshot, and it
  says so.

## Evaluating Andra

If you're here to assess it, `JUDGE_GUIDE.md` carries falsifiable prompts — each names
the exact behaviour to expect, so you can check the claim against what actually happens.
`reviews/` holds a frozen worked example (a sample plan plus Andra's full critique) you
can compare a live run against.

---

Andra is a competition build for *The Editor*, grounded in andragogy, change-management,
and developmental-editing research, plus 11+ years of the builder's own L&D and change-
management field experience. The evidence snapshot is frozen at July 2026; the
frameworks don't expire, the statistics might have moved, and the files say so where it
matters.
