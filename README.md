# claude-java-coach

A [Claude Code](https://docs.claude.com/en/docs/claude-code) **skill** that turns Claude
into a strict, Socratic Java/Spring interview drill coach. It runs structured
warm-ups, drills one curriculum concept at a time, reviews your code, and keeps a
persistent progress log across sessions — so Claude actually remembers what you're
weak on instead of starting from zero every conversation.

This isn't a general "ask Claude Java questions" prompt. It's an opinionated coaching
loop: it won't lecture, it won't hand you the answer on the first miss, and it forces
you to articulate *why*, not just recite syntax.

## What this is

A single file, [`SKILL.md`](SKILL.md), written in Claude Code's Skill format
(YAML frontmatter + Markdown instructions). Claude Code loads it automatically when
you invoke it, and it directs Claude to read/write two files that live alongside it:

- `plan.md` — your curriculum: target role, stack, and an ordered list of concepts
  to drill.
- `progress.md` — a running log the coach appends to after every session: what you
  covered, what you missed, recurring gaps, and what to focus on next time.

Both are user-owned data files, not part of the skill logic. `plan.md` ships pre-filled
with a usable default curriculum; [`plan.example.md`](plan.example.md) is a blank
reset template. `progress.md` starts empty (or is auto-created from
[`progress.example.md`](progress.example.md) on first run).

## How to use it

1. **Install the skill.** Copy `SKILL.md` into a folder named `java-coach` under your
   Claude Code skills directory (typically `~/.claude/skills/java-coach/SKILL.md`).
2. **(Optional) Customize your curriculum.** `plan.md` ships with a ready-to-drill
   default (general Java/Spring backend topics) — you can start immediately. Edit it
   anytime to match your actual target role, stack, and priority order. Want a blank
   slate instead? Copy `plan.example.md` over `plan.md`.
3. **Start a session.** In Claude Code, say something like `/java-coach`, "drill me",
   or "interview prep session." Claude reads your plan and progress files and
   announces where you left off.
4. **Drill.** Expect 2-3 warm-up recall questions on rows you've already covered,
   then a single new concept, asked Socratically — Claude asks, you answer, and hints
   only escalate (nudge → concept reminder → partial code) if you're genuinely stuck.
   It will not give you the full answer on a first miss.
5. **Submit code for review** when a concept calls for it. The coach reviews for
   correctness, idiom, and interview talking points — one finding per line, no
   padding.
6. **End the session.** The coach appends a structured entry to `progress.md`:
   what was covered, what needs re-drilling, recurring gaps, and next session's
   focus. This is what makes the next session pick up where you left off instead of
   re-covering ground.

## What to expect

- **Strict, not friendly.** It's built to behave like a demanding interviewer/mentor,
  not a patient tutor. If that's not the coaching style you want, this isn't the
  right tool as-is (though the instructions are plain Markdown — edit `SKILL.md` to
  taste).
- **No answers on demand.** Tiered hints exist specifically to stop you from asking
  "just tell me" and getting it. You have to work for each hint tier.
- **Ships with a default curriculum, fully yours to edit.** `plan.md` comes
  pre-filled with general Java/Spring backend topics so it works immediately —
  but it's your file, not a locked-in course. Reorder, trim, or replace rows to
  match your actual target role.
- **State lives in plain Markdown files you own,** not a database or hidden config —
  you can read, edit, or delete your own progress log at any time.
- **Requires actually maintaining `plan.md`/`progress.md`.** If you let those files
  go stale, the coach has nothing to work from. This is a tool for someone who wants
  structured, resumable practice — not a one-off Q&A.

## Is this the right fit for you?

Good fit if you:
- Already use Claude Code and want a repeatable interview-prep loop instead of
  re-explaining your situation every session.
- Want drilling, not explaining — you learn by being pushed to answer, not by
  reading another article.
- Are disciplined enough to keep a plan/progress file updated (or fine with the
  coach nudging you to).

Probably not a fit if you:
- Want a passive reference/tutorial (this skill assumes you bring the content list).
- Want a lenient, encouraging tone — this is deliberately terse and demanding.
- Don't use Claude Code (this is a Claude Code Skill, not a standalone app or web
  tool).

## Adapting it

Everything is plain Markdown — fork it and edit `SKILL.md` directly to:
- Change the tone (less strict, more explanatory).
- Change the domain (swap "Java/Spring" for any other stack — the drill *mechanics*
  in this skill aren't Java-specific).
- Change the hint tiers, session-end format, or code-review criteria.

## License

MIT — use, fork, and modify freely.
