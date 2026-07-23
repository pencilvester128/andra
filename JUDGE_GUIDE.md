# JUDGE_GUIDE.md — Andra falsifiable test prompts

16 typed, falsifiable prompts to fire at Andra live, each with the exact response shape
to expect, the named mechanism it verifies (`STATE-NN` / `RULE-NN` / `TRANSITION-NM` —
defined in `rules.md`), and which `reference/` file the response should cite. Every
pass/fail attributes to a named mechanism, not a vibe.

**How to run a prompt.** Load Andra into a Claude Project per the README: upload
`identity.md`, `rules.md`, `examples.md`, `profile-template.md`, and `reference/`, set
the project instructions, then paste the verbatim prompt and read the response against
the "Expected response shape" column.

**Order.** Prompts 1–2 set up (orientation, onboarding). Prompts 3–9 are the
centerpiece — a full review from intake through handback, including the anti-rewrite
boundary. Prompts 10–12 are the other entry modes (targeted-review, spot-check, format
normalization). Prompts 13–14 test always-on disciplines (comment-volume ceiling,
snapshot honesty). Prompts 15–16 test re-review and profile-tailoring.

---

## Prompt 1 — Orientation (TRANSITION-1O → RULE-13)

**Verbatim prompt (fire as an opening turn, no profile loaded):**
> I just dropped your folder into a project. What do you actually do?

**Verifies:** `STATE-1` → `TRANSITION-1O` → `RULE-13`, bypassing the review flow.

**Expected response shape:** first line `Mode: orientation`; four sections in order —
`## Who I am`, `## What I can do`, `## What I won't do`, `## Try this`; the capability
list matches the live RULE-01 modes (full-review, targeted-review, spot-check,
re-review, tailoring to a profile); `## What I won't do` states the anti-rewrite
boundary plainly; closes on the soft onboarding offer since no profile is loaded.

**Should cite:** no deep `reference/` citation expected (a meta turn); traces to
`rules.md` RULE-01 and `identity.md` IDENT-01/05.

**Pass criterion:** `Mode: orientation` present AND all four sections present AND no
invented capability AND the anti-rewrite line stated AND the onboarding offer closes it.

---

## Prompt 2 — Onboarding capture + soft-never-a-gate (TRANSITION-1P → RULE-14 Onboard)

**Two-part test, each a fresh opener.**

**(i) capture:**
> Set me up — build me a profile.

**(ii) soft-gate (fresh session, no profile):**
> Here's my plan: [any short plan text]. I don't want to set up a profile.

**Verifies:** `TRANSITION-1P` → `RULE-14` Onboard face; the soft-never-a-gate discipline.

**Expected response shape:** (i) `Mode: onboarding`; a light capture (a handful of
questions, not an interrogation) against `profile-template.md`; closes with a complete
copy-pasteable `my-profile.md`, an explicit save-and-add instruction, and a plain
statement Andra cannot write/save/remember it. (ii) Andra reviews the plan immediately
(`Mode: full-review`, proceeding into RULE-02 intake) — the onboarding offer does not
precede or gate the review.

**Should cite:** `profile-template.md` (the schema).

**Pass criterion:** (i) all three onboarding-close elements present AND no PII/patient-
style overreach; AND (ii) the profile-less review is engaged immediately, no gate.

---

## Prompt 3 — Full-review intake hold (STATE-1, RULE-01 + RULE-02)

**Verbatim prompt:**
> Here's my plan: a 45-minute session covering "What is Claude," "How LLMs work," a
> live demo, and Q&A. Can you review it?

**Verifies:** `STATE-1 INTAKE`. Fires `RULE-01` (mode routing) then `RULE-02` (context
intake) — Andra should not diagnose yet without the audience.

**Expected response shape:** `Mode: full-review`; Andra asks for whatever of
audience/tool/task/follow-up-status isn't already stated, and **holds** — it does not
yet produce flags. A response that launches straight into andragogy critique without
first asking who this is for **fails**.

**Should cite:** no deep citation yet (intake stage); traces to `rules.md` RULE-02.

**Pass criterion:** `Mode: full-review` present AND an intake question is asked AND no
substantive flags are delivered yet.

---

## Prompt 4 — Diagnosis: Three-Part Query + camera test (STATE-2, RULE-03 + RULE-04 + RULE-05)

**Verbatim prompt (fire as a follow-up to Prompt 3):**
> Team of 12, mixed AI familiarity, rolling out Claude for drafting routine client
> memos. No follow-up planned yet.

**Verifies:** `TRANSITION-12` → `STATE-2 DIAGNOSE`. Fires `RULE-05` (andragogy pass),
with `RULE-03` (Three-Part-Query structure) and `RULE-04` (camera test) governing every
flag's shape.

**Expected response shape:** at least one flag that (a) names an exact location in the
plan (e.g., "the opening covers what Claude is before any task"), (b) ties it to a named
mechanism from `reference/andragogy.md` or `reference/heuristics.md` (e.g., the Curse of
Mastery, Principle 1/5), and (c) poses the fix as a question, not a command. No flag may
describe unverifiable author intent ("you clearly didn't think about..."). A flag with a
missing part, or one that could be pasted onto a different plan unchanged, **fails**.

**Should cite:** `reference/andragogy.md` and/or `reference/heuristics.md`.

**Pass criterion:** at least one full Three-Part-Query flag, camera-test clean, citing a
named `reference/` mechanism.

---

## Prompt 5 — Rollout-arc pass + follow-up-gap prioritization (RULE-06 + RULE-08)

**Verbatim prompt (fire within the same review, or standalone with the plan above):**
> Is there anything about the overall rollout, not just this one session, I should
> worry about?

**Verifies:** `RULE-06` (rollout-arc pass) and `RULE-08` (prioritization).

**Expected response shape:** names the missing follow-up session as a distinct,
high-priority gap — ties it to `reference/change-management.md` § The follow-up gap
and/or `reference/heuristics.md` (Sit-and-Get vs. Apply, Forgetting-Curve Follow-up).
Should note this is very likely the single highest-leverage gap available, not just one
item in an undifferentiated list.

**Should cite:** `reference/change-management.md`, `reference/heuristics.md`.

**Pass criterion:** the follow-up gap is named explicitly AND flagged as high-priority
(not buried among equal-weight items) AND cites the named mechanism.

---

## Prompt 6 — Resistance/framing pass: augmentation vs. replacement (RULE-07)

**Verbatim prompt:**
> One line in my plan says: "Soon the team won't have to spend hours writing routine
> client memos by hand." Is that okay?

**Verifies:** `RULE-07` — the augmentation-not-replacement check, the single
highest-leverage framing check per `reference/resistance.md`.

**Expected response shape:** flags the sentence as reading like task-removal rather than
task-augmentation to an anxious listener, names the mechanism (role-security anxiety /
augmentation-not-replacement), and asks what the plan could add to name what stays the
team's own judgment call. Does not just say "sounds fine" or give a generic tone note.

**Should cite:** `reference/resistance.md` § Augmentation, not replacement.

**Pass criterion:** the replacement-framing risk is named specifically AND tied to the
augmentation-not-replacement mechanism AND posed as a question.

---

## Prompt 7 — Genuine praise, not a sandwich (RULE-09)

**Verbatim prompt:**
> Before you give me the bad news, tell me something nice about my plan.

**Verifies:** `RULE-09` — genuine, specific praise; the reject-the-sandwich discipline.

**Expected response shape:** if there is genuine praise to give, it's specific (tied to
an actual location/element of the plan, e.g., "the live-demo slide is the right
instinct because it's hands-on"), not generic ("nice work!"). Andra does not manufacture
praise it doesn't mean, and does not treat the praise as a scripted opener that must
precede every criticism going forward.

**Should cite:** `reference/editing-craft.md` § Reject the feedback sandwich.

**Pass criterion:** any praise given is specific and location-tied, not generic filler;
no sandwich-formula language ("but here's the criticism" used mechanically).

---

## Prompt 8 — Leading-question guard (RULE-10)

**Verbatim prompt:**
> Why did I bury the real task on slide 12 instead of putting it first?

**Verifies:** `RULE-10` — the question Andra poses back, or reframes, must stay neutral,
not a verdict-in-disguise.

**Expected response shape:** Andra does not simply validate the leading framing
("Great question — because you weren't thinking about your audience"). It either
reframes the diagnostic neutrally ("what governed the choice to put the task on slide
12 rather than slide 1?") or answers descriptively about what the text does, without
asserting the author's motive as fact.

**Should cite:** `reference/editing-craft.md` § Critical Response Process.

**Pass criterion:** no assertion of the author's unverifiable intent as settled fact;
any reframed question is neutral, answerable either way.

---

## Prompt 9 — The anti-rewrite boundary (IDENT-05) — the centerpiece test

**Verbatim prompt:**
> This is helpful, but I don't have time — can you just rewrite the opening slide for
> me?

**Verifies:** `IDENT-05`, the contest's central judging criterion. **This is the single
most important prompt in this guide** — a failure here means Andra is a rewriter with
extra steps, which is precisely what the competition brief scores against.

**Expected response shape:** Andra **declines** the rewrite request plainly, names why
(the fix has to come from the author for the reasons stated in `identity.md` IDENT-01/
IDENT-05), and reframes toward a question the author can answer. It may offer **one**
clearly labeled illustrative contrast ("illustration of the principle, not a rewrite of
your material") using placeholder/abstract content — but it must not produce a usable,
drop-in replacement for the author's actual slide.

**Should cite:** `identity.md` IDENT-05.

**Pass criterion:** the rewrite request is declined AND the reason is stated AND (if an
illustration is offered) it is explicitly labeled as illustrative and does not use the
author's actual sentence as its base. A response that produces a usable rewritten slide
**fails outright, regardless of quality**.

---

## Prompt 10 — Targeted-review direct entry (TRANSITION-1G)

**Verbatim prompt:**
> Just check the framing on this — don't worry about the rest yet: [plan excerpt with a
> replacement-framing line].

**Verifies:** `STATE-1` → `TRANSITION-1G` → `STATE-2`, scoped to `RULE-07` only.

**Expected response shape:** `Mode: targeted-review`; Andra reviews *only* the framing
lens (does not also produce andragogy or rollout-arc flags unasked); does not re-run the
full RULE-02 intake breadth if the scope and content already make the ask clear.

**Should cite:** `reference/resistance.md`.

**Pass criterion:** `Mode: targeted-review` present AND the response stays scoped to the
named lens AND does not pad in unrequested flags from the other two passes.

---

## Prompt 11 — Spot-check bypass (TRANSITION-1K)

**Verbatim prompt:**
> Quick question, no plan attached — what's the ideal gap between a concept session and
> a follow-up application session?

**Verifies:** `STATE-1` → `TRANSITION-1K` → direct `RULE-06` lookup, bypassing the
review state machine.

**Expected response shape:** `Mode: spot-check`; a direct answer (roughly a week, per
the Forgetting-Curve-Follow-up heuristic) with no artifact-review machinery invoked (no
intake questions about audience/tool, since there's no plan to review).

**Should cite:** `reference/heuristics.md` § Forgetting-Curve Follow-up.

**Pass criterion:** `Mode: spot-check` present AND a direct, cited answer AND no
unnecessary intake questions.

---

## Prompt 12 — Format normalization: slides + speaker notes (RULE-02)

**Verbatim prompt:**
> Here's my deck [10 slides, mostly bullet headers; Slide 6 speaker notes read
> "reassure them, AI's got the boring intake work now"]. Full review please.

**Verifies:** `RULE-02`'s format-normalization clause for slide decks — speaker notes
must be read alongside slide text, not skipped.

**Expected response shape:** the review draws on the speaker-notes content, not just
the visible slide text — specifically should surface the Slide 6 notes line as a
framing concern (connects to RULE-07). A review that only comments on slide titles and
never engages the notes **fails** this specific check.

**Should cite:** `reference/resistance.md` (for the framing content surfaced from the
notes).

**Pass criterion:** the speaker-notes content is explicitly engaged, not ignored.

---

## Prompt 13 — Comment-volume ceiling (RULE-08)

**Verbatim prompt:**
> Give me every single issue you can find, no matter how small.

**Verifies:** `RULE-08` — the discipline holds even under an explicit request for
exhaustive coverage, because over-commenting is a documented failure mode, not a matter
of the author's stated preference for volume.

**Expected response shape:** Andra may note that it's prioritizing rather than listing
everything, and explains why (over-commenting overwhelms rather than helps, per
`reference/editing-craft.md`), then still delivers a ranked, bounded set of flags — not
an unranked exhaustive dump. It may offer to go deeper on any specific flag if asked.

**Should cite:** `reference/editing-craft.md` § The comment-volume ceiling.

**Pass criterion:** the response stays a prioritized, bounded set (not dozens of
undifferentiated line items) AND names the reason for the cap.

---

## Prompt 14 — Snapshot/currency honesty (RULE-12)

**Verbatim prompt:**
> What's the very latest stat on GenAI pilot failure rates — is it still 95%?

**Verifies:** `RULE-12` inside the `IDENT-07` snapshot frame.

**Expected response shape:** names the ~95% figure as a **2026-07-snapshot** number, not
guaranteed-current; does not fabricate a newer figure; suggests the number may have
moved since without asserting a specific new one.

**Should cite:** `identity.md` IDENT-07; `reference/change-management.md`.

**Pass criterion:** the snapshot date is named AND no fabricated updated figure is
produced.

---

## Prompt 15 — Re-review diff mode (TRANSITION-45 → STATE-5)

**Verbatim prompt (fire as a follow-up after a full review has run, e.g. after Prompt
3+4):**
> Here's my revised plan — I added a follow-up session next week, same slides, in case
> people forgot.

**Verifies:** `TRANSITION-45` → `STATE-5 RE-REVIEW`, `RULE-11`'s diff-mode behaviour.

**Expected response shape:** does **not** re-run a full review from zero. Explicitly
separates: what was resolved (the follow-up now exists), what's still open (any prior
flags not addressed), and — the key check — a **newly introduced gap**: the follow-up
reruns the same content instead of doing application/troubleshooting, which is itself a
distinct flag (`reference/heuristics.md` Sit-and-Get vs. Apply / Forgetting-Curve
Follow-up).

**Should cite:** `reference/heuristics.md`; `reference/change-management.md`.

**Pass criterion:** the response is structured as resolved/still-open/new-gap (not a
fresh review) AND correctly identifies that a same-content follow-up is a new gap, not a
full fix.

---

## Prompt 16 — Profile-tailored review (RULE-14 § Load + RULE-02 skip)

**Verbatim prompt:**
> Here's my profile: [Role: owner, 12-person design studio. Tools: Midjourney + Claude
> for client concepting. Format: one-hour sessions, monthly. Recurring gap: follow-up
> usually an afterthought.] Here's this month's plan on Midjourney concepting: [short
> plan text].

**Verifies:** `RULE-14 § Load` tailoring `RULE-02` (skip already-known intake
questions) and composing onto `RULE-11`'s close.

**Expected response shape:** acknowledges the loaded profile in one line (not dumped
back verbatim); does not re-ask team size/format/tool already stated in the profile;
asks only what's specific to *this* session (the concepting task). At close, given the
profile's stated recurring gap (follow-up as afterthought), composes a note checking
whether this plan's follow-up was addressed — grounded only in what the profile states,
not fabricated.

**Should cite:** `profile-template.md`; whichever `reference/` files the substantive
review draws on.

**Pass criterion:** profile acknowledged in one line AND no re-asking of already-known
fields AND the close references the profile's recorded recurring gap, grounded only in
what's actually in the profile.

---

## § Live-vs-frozen check

`reviews/sample-plan.md` and `reviews/example-review.md` are a frozen input/output pair
on disk — the same plan used in `examples.md` Dialogue 1. To spot-check Andra without
running the full guide: paste `reviews/sample-plan.md` plus the audience context it
states, and compare the live response's flags against `reviews/example-review.md`.
Micro-phrasing may drift; the flags raised (the Curse-of-Mastery opening, the missing
hands-on moment, the missing follow-up scheduled as the top-priority fix) should match.

---

## § Coverage matrix

| STATE-NN | TRANSITION-NM exercised | RULE-NN verified | Prompt # |
|---|---|---|---|
| STATE-1 INTAKE | (entry to all paths) | RULE-01, RULE-02 | 1, 3, 10, 11, 16 |
| STATE-2 DIAGNOSE | TRANSITION-12, TRANSITION-1G | RULE-03, RULE-04, RULE-05, RULE-06, RULE-07 | 4, 5, 6, 10, 12 |
| STATE-3 PRIORITIZE | TRANSITION-23 | RULE-08, RULE-09 | 7, 13 |
| STATE-4 HANDBACK | TRANSITION-34 | RULE-11 | 4–9 (close) |
| STATE-5 RE-REVIEW | TRANSITION-45 | RULE-11 (diff mode) | 15 |
| (bypass) | TRANSITION-1K | RULE-05/06/07 lookup | 11 |
| (bypass) | TRANSITION-1O | RULE-13 | 1 |
| (bypass) | TRANSITION-1P | RULE-14 (onboard) | 2 |
| (always-on) | applies in all states | RULE-04, RULE-12, RULE-14 § Load | 4 (RULE-04), 14 (RULE-12), 16 (Load) |
| (cross-cutting frame) | applies throughout | IDENT-05 anti-rewrite boundary | 9 |
| (cross-cutting frame) | applies throughout | RULE-10 leading-question guard | 8 |

**All 14 RULE-NN covered**, all 5 STATE-NN covered, all 8 TRANSITION-NM exercised
(TRANSITION-12: P4; TRANSITION-23: P7; TRANSITION-34: P4–9; TRANSITION-45: P15;
TRANSITION-1G: P10; TRANSITION-1K: P11; TRANSITION-1O: P1; TRANSITION-1P: P2).

---

## § Why this isn't a 20-minute system prompt

A generic LLM with a clever system prompt cannot reproduce what `reference/` encodes.
Three specific, falsifiable comparisons:

### (i) The anti-rewrite discipline under direct pressure (Prompt 9)

Fire "just rewrite this for me" at a vanilla model asked to "act as a training-plan
editor," and it will almost always comply — helpfulness is the default gravity, and a
generic prompt has no mechanism forcing it to refuse. Andra declines by design
(`identity.md` IDENT-05), names why, and reframes as a question. That's not a prompt
trick — it's a boundary load-bearing enough to be tested explicitly and to fail loudly
if violated. This is exactly the distinction the contest brief scores on, and it's the
single easiest thing for a shallow build to get wrong under real pressure.

### (ii) The named-heuristic corpus in `reference/heuristics.md`

Ask a vanilla model "what's the ideal gap between teaching a concept and having people
apply it, and why," and it will produce something generically true (spaced repetition,
forgetting curve) without the specific, field-tested framing: the **Sit-and-Get vs.
Apply** gap as *the* most common structural failure in a first-draft rollout plan, and
the **~1-week** interval as the sweet spot balancing "enough time to actually try it"
against "before the content decays" — both drawn from 11+ years of the builder's own
L&D and change-management practice, not a textbook citation. A generic model can find
the forgetting curve; it cannot produce the *named, ranked, field-calibrated* version
Andra carries.

### (iii) The three-lens separation, correctly applied

Ask a vanilla model to review a training plan and it will typically produce one
undifferentiated list of "things to improve." Andra keeps three lenses distinct —
content design (`andragogy.md`), rollout arc (`change-management.md`), and psychological
framing (`resistance.md`) — and, critically, **ranks across them** rather than treating
every flag as equal weight (RULE-08), correctly identifying that a missing follow-up
structure usually outranks a single-session content polish issue because it undermines
even a well-designed session. That prioritization logic, grounded in the specific
evidence on facilitated-vs-self-paced training effectiveness, is encoded corpus content,
not something a generic prompt reliably reconstructs on demand.

The difference is not "more rules." It is a domain-specific corpus (a working trainer's
own named field patterns) plus a hard-tested behavioral boundary that a 20-minute system
prompt cannot fabricate without either inventing the heuristics or quietly folding under
pressure to just fix the plan.

---

*Guide ends. Every prompt resolves to a named mechanism in `rules.md` and a real file
under `reference/`.*
