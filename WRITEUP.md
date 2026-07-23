# WRITEUP.md — Andra

Andra is a developmental editor for AI-adoption training plans: the lunch-and-learn, the
month-long rollout, the slide deck a business owner or team leader drafts when they've
been handed the job of turnkeying AI literacy to their own team. The author is almost
always a genuine expert in their domain and almost never a trained educator, and their
plan reliably carries the same predictable failures — organized around what the tool
does instead of what the team needs, no room for the team to try it on their own work,
no scheduled return visit once the first session ends. Those aren't small gaps: MIT's
research on enterprise AI adoption found roughly 95% of pilots show no measurable
return, and traced the cause to a learning gap, not the tool. Andra reviews the plan
against three distinct lenses — andragogy (does the *content* respect how adults
actually learn), the change-management arc (does the *rollout* survive past the first
session), and adoption psychology (does the *framing* trigger the resistance it's trying
to avoid) — and hands back the highest-leverage flags, each tied to a named mechanism,
each posed as a question the author answers themselves. It never rewrites the plan.

The differentiator is the discipline, not the domain knowledge alone. Any model can
recite Knowles' six principles of andragogy if asked. What a shallow build reliably
fails at is holding the line when the author pushes back — "just fix it for me,"
"give me everything, no matter how small," "tell me something nice first" — because the
default gravity of a helpful assistant is to comply. Andra's `rules.md` encodes each of
those pressure points as a named, testable behavior: the anti-rewrite boundary
(`identity.md` IDENT-05) that declines and reframes instead of producing a usable
rewrite; the comment-volume ceiling (`rules.md` RULE-08) that prioritizes even when
asked for exhaustive coverage; the genuine-praise discipline (RULE-09) that refuses the
feedback sandwich. Each is falsifiable — `JUDGE_GUIDE.md` fires the exact pressure and
names the exact failure mode if Andra folds.

The moat underneath all of it is `reference/`, and specifically `reference/
heuristics.md` — seven named patterns (the Curse of Mastery, the Sage-on-the-Stage
Default, the Time-Scarcity Tax, the Sit-and-Get-vs-Apply gap, and others) distilled from
11+ years of the builder's own experience running L&D and change management for real
teams of professional learners, not lifted from a textbook. A generic model asked "why
do training rollouts fail" will produce something generically true; it will not produce
the specific, field-calibrated claim that a missing follow-up session is *usually* the
single highest-leverage gap in a first-draft plan, or that roughly a week is the
interval that lets application happen before the content decays. That's encoded
judgment, cited and never restated, and it's what turns Andra from a plausible-sounding
critique generator into an editor a real trainer would actually trust with their draft.

Andra executes as a folder — `identity.md` sets the developmental-editor frame and the
anti-rewrite boundary; `rules.md` runs 14 named behaviors wrapped by a 5-state review
machine (intake → diagnose → prioritize → hand back, with an optional re-review diff
pass); `reference/` holds the andragogy, change-management, resistance, and editing-
craft substance plus the named field heuristics, cited and never restated; and every
design decision traces to a real ID a judge can check against `rules.md` line by line. A
worked example carries it in `examples.md`: handed a subject-centered lunch-and-learn
with no follow-up, Andra names the Curse-of-Mastery opening, the missing hands-on
moment, and the missing follow-up session — ranks the follow-up gap highest, per the
research on facilitated-versus-self-paced training effectiveness — and when the author
asks Andra to just write the fixed slide, it declines and hands the question back
instead.
