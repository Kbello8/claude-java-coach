# Drill Plan

The schedule and session rules. The rows to drill live in `curriculum.md`; your
status on each row lives in `progress.md`.

## Target
- Role: Backend / full-stack engineer, Java + Spring
- Stack focus: Java 17, Spring Boot 3, JPA/Hibernate, SQL
- Interview date / timeline: (fill in if you have one — helps the coach pick a track)

## Active priority override
Leave blank normally. If an upcoming interview needs a topic pulled forward out of
order, name it here — this section wins over normal topic order until you clear it.

## Core principles (why this order)
- **Retrieval > review.** Reading the primer is study; the *win* is writing cold. Spend
  most of each session typing, not reading.
- **Spaced repetition.** A `[~]` stall resurfaces next session, and again later, until
  it's `[x]`. Clean passes decay too, just slower — the Recall Queue in `progress.md`
  box-schedules EVERY drilled row, not just misses.
- **Interleaving.** Don't grind one topic to 100% then never revisit. Mix prior-topic
  re-drills into every session — interleaving beats blocking for retention.
- **Breadth before depth.** All Core (🔴) blocks first across all topics (Pass 1), then
  Extended (Pass 2). Confidence and coverage early; advanced last.

## Per-session shape (~30–45 min, same ritual every time)
1. **Warm-up (5 min):** Recall Queue pull, then re-drill rows from the stall list. Cold.
2. **Read primer (3 min):** only the `primer.md` section for today's block. Then CLOSE it.
3. **Drill new block (20–30 min):** write each row cold. Stall >30s → hint ladder, mark `[~]`.
4. **Cool-down (2 min):** coach logs the session (attempted / passed / still stalled).

## Track A — Steady (recommended, ~20 sessions)
Pass 1 (Core 🔴) — one block per session:
- S1 OOP · S2 Collections · S3 Generics + Exceptions
- S4 Concurrency · S5 Lambdas + Streams · S6 Streams cont. + Optional
- S7 Design Patterns (all 3 sub-blocks) · S8 Spring Wiring + REST
- S9 Spring Tx + SQL · S10 JPA
- **S11 — Pass 1 checkpoint:** coach quizzes 15 random Core rows across all topics
  (excluding Testing). Any stall → re-drill list. Don't start Pass 2 until Core is ~90% `[x]`.

Pass 2 (Extended 🟡🟢) — same cadence, S12→S20, topic by topic. 🟢 = sketch/explain
aloud, not full cold-write.

## Track B — Sprint (~10 sessions, higher intensity)
- Two Core blocks per session, S1–S6 = all of Pass 1. S6 checkpoint quiz.
- S7–S10 = Extended, skim 🟢 (recognition only).
- Use only if the interview is near and sessions are long.

> **Testing deferred:** drill Testing Core + Extended only after all other topics, or
> when explicitly requested. Skip Testing in session planning until then.

## Full-topic quiz format
When a whole topic's Core block gets quizzed in one go (checkpoints, or a "quiz me on
all of Collections" request):
- **One evolving domain.** Run the quiz as a single build-up arc on one domain/class set
  (e.g. `Animal` abstract → `Dog` extends + implements `Trainable`), each row adding to
  the same files — not disconnected unrelated rows. Pick a fresh domain each quiz.
- **80% specific / 20% vague.** ~80% of rows name the exact method/class/signature (fast
  syntax reps). ~20% (2–4 rows) name only the capability ("always hand back the highest
  scorer next") so the learner has to pick the tool — flag these as ambiguity reps when
  posed, so the extra scoping time is expected.
- Post the full row list up front.

## Milestones
- **M1 (end Pass 1):** write any 🔴 row cold, no hesitation. This is the muscle-memory goal.
- **M2 (end Pass 2 🟡):** brief-think any 🟡 row.
- **M3:** the "Highest ROI" list at the bottom of `curriculum.md` — Builder, Strategy,
  Observer, Singleton (enum), CompletableFuture chain, Stream + Collectors,
  `@Transactional` semantics, N+1 + JOIN FETCH, `@WebMvcTest`, `@Mock`/`@InjectMocks`/
  `verify` — all `[x]`. Interview-ready.

## Anti-patterns (don't)
- Don't read the primer mid-write. Recognition ≠ retrieval.
- Don't leave IDE autocomplete / AI completion on — it writes the muscle memory for you.
- Don't grind one topic to perfection while others sit at zero — breadth first.
- Don't mark `[x]` on a hinted pass. Hint = `[~]`. Earn the `[x]` clean.
