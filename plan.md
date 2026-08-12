# Drill Plan

## Target
- Role: Backend / full-stack engineer, Java + Spring
- Stack focus: Java 17, Spring Boot, JPA/Hibernate, SQL, basic system design
- Interview date / timeline: (fill in if you have one — helps the coach prioritize)

## Curriculum rows
The coach works top-to-bottom, one row per drill, and re-queues anything you miss.
Edit freely — add, remove, or reorder rows for your own target role.

1. [ ] Collections internals — HashMap resizing, equals/hashCode contract
2. [ ] Concurrency — synchronized vs ReentrantLock, executor services
3. [ ] Concurrency — volatile, happens-before, common race-condition patterns
4. [ ] Spring — bean lifecycle, dependency injection scopes
5. [ ] Spring — request lifecycle in Spring MVC/Boot, filters vs interceptors
6. [ ] JVM — garbage collection basics, memory model (heap/stack, escape analysis)
7. [ ] JPA/Hibernate — N+1 queries, lazy vs eager fetch, first/second-level cache
8. [ ] SQL — indexing basics, transaction isolation levels
9. [ ] Design patterns — where Spring uses them (proxy, factory, singleton scope)
10. [ ] System design — one classic problem sized for your target role/level
11. [ ] Testing — unit vs integration, mocking boundaries, what not to mock

## Grading rubric
Applies to every row above, so grading stays consistent across sessions (each session
is a fresh Claude Code invocation with no memory of how strict the last one was):
- **Pass** — written cold, no hints, or a slip self-caught before the coach points it
  out. Counts toward the 2-clean-passes-to-done rule.
- **Partial** — needed a nudge or concept reminder (hint tier 1-2) but the mechanic was
  right once nudged. Re-queue; needs a fresh clean rep.
- **Fail** — needed a near-full hint (tier 3), didn't compile, or the underlying
  mechanic was wrong. Re-queue AND reset any prior clean-pass credit on that row to 0.

## Worked examples
Optional — add one short worked example per row here (or inline under the row) if a
topic benefits from seeing the shape once before cold-drilling it blind. Not required
for rows you already have muscle memory adjacent to; use judgment on which rows need
one. Example for row 1:

```java
// Collections internals — the idiom that recurs most: count-then-scan via HashMap
Map<String, Integer> counts = new HashMap<>();
for (String w : words) counts.merge(w, 1, Integer::sum);
```

## Active priority override
Leave this section blank normally. If an upcoming interview needs a specific topic
pulled forward out of order, name it here — this section wins over the row order above
until you clear it.
