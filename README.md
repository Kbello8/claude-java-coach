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

[`SKILL.md`](SKILL.md), written in Claude Code's Skill format (YAML frontmatter +
Markdown instructions), plus the data files it reads and writes alongside it:

- [`plan.md`](plan.md) — target role, session ritual, pacing tracks (steady ~20
  sessions / sprint ~10), quiz format, milestones, and an optional priority override.
- [`curriculum.md`](curriculum.md) — the gauntlet: ~380 single-construct rows across
  10 topics (OOP, Collections, Functional, Spring Boot + JPA, SQL, Concurrency, Design
  Patterns, Exceptions, Generics, Testing), split into Core 🔴 and Extended 🟡🟢,
  plus the grading rubric and one worked example per topic.
- [`primer.md`](primer.md) — a syntax trigger sheet. Read today's section before
  drilling, then close it.
- `progress.md` — your row checklist (`[ ]`/`[~]`/`[x]`), Re-Drill List, and
  spaced-repetition Recall Queue. Auto-created from
  [`progress.example.md`](progress.example.md) on first run.
- `session-log.md` — the coach's per-session notes, newest first. Created on first wrap.

All are plain Markdown you own and can edit. `progress.md` and `session-log.md` are
git-ignored so your personal state never ends up in a commit.

## How to use it

**Prerequisites:** Claude Code, and JDK 17 on your PATH (`java -version`). For the
Spring/JPA/Testing rows you'll also want a throwaway Spring Boot 3 project
(start.spring.io) to write them in.

1. **Install the skill.** Clone this repo as your skill folder — all the files above
   have to sit next to `SKILL.md`, so copying `SKILL.md` alone won't work:
   `git clone <this repo> ~/.claude/skills/java-coach`
2. **(Optional) Tune it.** Fill in your target role/interview date in `plan.md`, and
   trim or reorder rows in `curriculum.md` to match your stack.
3. **Start a session** from a scratch folder where you'll write your drill code. In
   Claude Code, say `/java-coach`, "drill me", or "interview prep session." The coach
   reads your plan and progress and announces where you left off.
4. **Drill.** Warm-up first (spaced-repetition recall + a design brief built from your
   past misses), then new rows one at a time. You write every line in a `.java` file;
   the coach compiles and runs it, quotes errors back, and grades Pass / Partial /
   Fail. Hints climb one rung at a time (nudge → shape → exact symbol → one-line
   skeleton). It will not write the code for you or edit your files.
   Commands: `status`, `quiz me`, `wrap`.
5. **Submit code for review** when a concept calls for it. The coach reviews for
   correctness, idiom, and interview talking points — one finding per line, no
   padding.
6. **End the session** by saying `wrap`. The coach updates `progress.md` (checklist,
   Re-Drill List, Recall Queue) and adds an entry to `session-log.md`: what was
   covered, what needs re-drilling, recurring gaps, and next session's focus. This is what makes the next session pick up where you left off instead of
   re-covering ground.

## What to expect

- **Strict, not friendly.** It's built to behave like a demanding interviewer/mentor,
  not a patient tutor. If that's not the coaching style you want, this isn't the
  right tool as-is (though the instructions are plain Markdown — edit `SKILL.md` to
  taste).
- **No answers on demand.** Tiered hints exist specifically to stop you from asking
  "just tell me" and getting it. You have to work for each hint tier.
- **Ships with a full curriculum, fully yours to edit.** `curriculum.md` covers
  general Java 17 / Spring Boot 3 backend topics so it works immediately — but it's
  your file, not a locked-in course. Reorder, trim, or replace rows to match your
  actual target role (keep `progress.example.md`'s checklist in step if you do).
- **State lives in plain Markdown files you own,** not a database or hidden config —
  you can read, edit, or delete your own progress log at any time.
- **Spaced repetition, not just miss-tracking.** `progress.md`'s Recall Queue
  resurfaces every drilled row on a box schedule, including clean first-try passes —
  correct answers decay too, just slower than misses.
- **Requires ending sessions with `wrap`.** That's when the coach saves your state.
  Skip it and the next session has nothing to work from. This is a tool for someone who wants
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
- Want a passive reference/tutorial, or are learning Java from zero — the gauntlet
  assumes you've met the concepts and need cold recall, not first exposure.
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
