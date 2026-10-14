# Java Senior Engineer — Cold-Code Drilling Gauntlet

**Mastery Levels:**
- 🔴 **Must write without hesitation** — core syntax, no excuse to stall
- 🟡 **Should write with brief thinking** — less frequent but expected at this level
- 🟢 **Should understand and sketch** — architectural/conceptual, reason through acceptable

**How to run the gauntlet:**
Each topic is split into a **Core (🔴)** block and an **Extended (🟡🟢)** block. Rows are ordered so prerequisites come first — drill top to bottom.

- **Pass 1 (breadth):** Do the **Core** block of *every* topic, in order, cold — no imports, no autocomplete, no reference. Stall = gap. This builds the muscle memory you're missing fastest.
- **Pass 2 (depth):** Loop back and do each **Extended** block. 🟡 first, 🟢 last.
- Re-drill any item you stalled on until it's automatic before advancing.

**Grading rubric (applies uniformly to every row, ties to the hint ladder in
`SKILL.md`):** every row is single-construct and graded the
same way regardless of topic, so one rubric covers the whole gauntlet instead of a
line per row:
- **Pass** — written at Tier 0 (no hint), or a slip is self-caught before the coach
  points it out. Counts toward the 2-clean-passes-to-`[x]` rule.
- **Partial** — needed a Tier 1–2 hint (concept nudge / shape hint) but the mechanic
  itself was right once nudged. Stays `[~]`; needs a fresh clean rep next time, but
  doesn't necessarily erase a prior clean pass already on record for that row.
- **Fail** — needed Tier 3–4 (pinned symbol / skeleton), didn't compile, or got the
  underlying mechanic wrong (not just a naming/style nit). Stays `[~]` AND resets the
  clean-pass count to 0/2 — the next Pass has to be earned from scratch.

A row only promotes to `[x]` on two **Pass**-grade reps in a row, on separate touches.
The rubric is spelled out so grading doesn't drift session to session (each session is
a cold Claude Code invocation with no memory of how strict the last one was).

**Topic priority order (matches `progress.md` — JPA folded into Spring Boot,
Testing drilled last):**
1. OOP · 2. Collections · 3. Functional (Streams/Lambdas/Optional) · 4. Spring Boot (incl. JPA)
5. SQL · 6. Concurrency · 7. Design Patterns · 8. Exceptions · 9. Generics · 10. Testing

---

## 1. OOP Fundamentals

### Core (🔴)

| Construct | Level |
|---|---|
| Declare a class with private fields, a constructor, getters/setters | 🔴 |
| Override `toString()` | 🔴 |
| Override `equals()` and `hashCode()` consistently (same fields) | 🔴 |
| Declare a `static` field and `static` method | 🔴 |
| Declare a `final` class, `final` method, `final` variable | 🔴 |
| Chain constructors using `this(...)` | 🔴 |
| Declare an `abstract` class with abstract and concrete methods | 🔴 |
| Extend an abstract class, implement all abstract methods | 🔴 |
| Use `super` to call a parent class constructor | 🔴 |
| Use `super` to call an overridden parent method | 🔴 |
| Distinguish overloading vs overriding; demonstrate both | 🔴 |
| Declare an `interface` with an abstract method | 🔴 |
| Write a class that `implements` an interface | 🔴 |
| Add a `default` method to an interface | 🔴 |
| Add a `static` method to an interface | 🔴 |
| Declare a `@FunctionalInterface` with a single abstract method | 🔴 |
| Pass a lambda where a functional interface is expected | 🔴 |
| Declare an `enum` with constants | 🔴 |
| Use `instanceof` and cast safely | 🔴 |
| Write a method with `varargs` (`String... args`) | 🔴 |
| Implement `Comparable<T>`, write `compareTo()` | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| Write a `static` initializer block | 🟡 |
| Write an instance initializer block | 🟡 |
| Declare a `static` nested class | 🟡 |
| Declare an inner (non-static) class and instantiate it | 🟡 |
| Write an anonymous class implementing an interface inline | 🟡 |
| Declare a `record` with components, use `compact constructor` | 🟡 |
| Declare an `enum` with fields, a constructor, and a method | 🟡 |
| Declare an `enum` that implements an interface | 🟡 |
| Use pattern matching `instanceof` (Java 16+): `if (obj instanceof String s)` | 🟡 |
| Explain and demonstrate covariant return types | 🟡 |
| Implement `Cloneable` and override `clone()` | 🟡 |
| Declare a `sealed` class with `permits` and implement `non-sealed`/`final` subclasses | 🟢 |

---

## 2. Collections

### Core (🔴)

| Construct | Level |
|---|---|
| Declare and populate `ArrayList<T>` | 🔴 |
| Use `List.of(...)` and `List.copyOf(...)` (immutable) | 🔴 |
| Write a `Comparator<T>` inline, with lambda, and via `Comparator.comparing()` | 🔴 |
| Chain comparators with `.thenComparing()` and `.reversed()` | 🔴 |
| Sort a `List<T>` with `Collections.sort()` and `list.sort(Comparator)` | 🔴 |
| Declare `HashSet<T>`, add elements, check `contains()` | 🔴 |
| Declare `HashMap<K,V>`, `put`, `get`, `getOrDefault`, `putIfAbsent` | 🔴 |
| Iterate a `Map` via `entrySet()`, `keySet()`, `values()` | 🔴 |
| Use `ArrayDeque` as a stack (`push`/`pop`) and as a queue (`offer`/`poll`) | 🔴 |
| Use `PriorityQueue<T>` with natural order and custom `Comparator` | 🔴 |
| Use `Collections.unmodifiableList/Set/Map(...)` | 🔴 |
| Use `ConcurrentHashMap` — `putIfAbsent`, `computeIfAbsent`, `compute`, `merge` | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| Declare and populate `LinkedList<T>`, use as queue and deque | 🟡 |
| Declare `LinkedHashSet<T>`, explain insertion-order guarantee | 🟡 |
| Declare `TreeSet<T>`, explain natural ordering | 🟡 |
| Use `Map.of(...)` and `Map.entry(...)` | 🟡 |
| Use `LinkedHashMap` for LRU-style insertion-order map | 🟡 |
| Override `anonymous subclass` of `LinkedHashMap` with `removeEldestEntry` for LRU cache | 🟡 |
| Declare `TreeMap<K,V>`, use `floorKey`, `ceilingKey`, `headMap`, `tailMap` | 🟡 |
| Use `Collections.synchronizedList(...)` | 🟡 |
| Use `Collections.frequency(...)`, `disjoint(...)`, `nCopies(...)` | 🟡 |
| Write a custom `Iterator<T>` implementing `hasNext()` and `next()` | 🟡 |
| Explain and demonstrate fail-fast behavior of `ArrayList` iterator | 🟡 |
| Use `CopyOnWriteArrayList` and explain when it's appropriate | 🟡 |
| Use `BlockingQueue` (e.g., `ArrayBlockingQueue`) in a producer-consumer pattern | 🟡 |

---

## 3. Functional Java (Streams, Lambdas, Optional)

### Lambdas & Functional Interfaces — Core (🔴)

| Construct | Level |
|---|---|
| Lambda with no params: `() -> expression` | 🔴 |
| Lambda with one param (no parens): `x -> x * 2` | 🔴 |
| Lambda with multiple params: `(a, b) -> a + b` | 🔴 |
| Lambda with block body and explicit return | 🔴 |
| Static method reference: `ClassName::staticMethod` | 🔴 |
| Instance method reference on instance: `obj::instanceMethod` | 🔴 |
| Instance method reference on type: `String::toUpperCase` | 🔴 |
| Constructor reference: `ArrayList::new` | 🔴 |
| Use `Supplier<T>` — get | 🔴 |
| Use `Consumer<T>` — accept, andThen | 🔴 |
| Use `Predicate<T>` — test, and, or, negate | 🔴 |
| Use `Function<T,R>` — apply, andThen, compose | 🔴 |
| Build a `Comparator` via `Comparator.comparing(...)`, `thenComparing(...)`, `reversed()` | 🔴 |

### Lambdas & Functional Interfaces — Extended (🟡🟢)

| Construct | Level |
|---|---|
| Use `BiFunction<T,U,R>` | 🟡 |
| Use `BiConsumer<T,U>` | 🟡 |
| Use `UnaryOperator<T>` | 🟡 |
| Use `BinaryOperator<T>` | 🟡 |

### Streams — Core (🔴)

| Construct | Level |
|---|---|
| Create stream from collection: `list.stream()` | 🔴 |
| Create stream with `Arrays.stream(array)` | 🔴 |
| Create stream with `Stream.of(a, b, c)` | 🔴 |
| `filter(Predicate)` | 🔴 |
| `map(Function)` | 🔴 |
| `mapToInt`, `mapToLong`, `mapToDouble` | 🔴 |
| `flatMap(Function<T, Stream<R>>)` — flatten nested collections | 🔴 |
| `distinct()` | 🔴 |
| `sorted()` and `sorted(Comparator)` | 🔴 |
| `limit(n)` and `skip(n)` | 🔴 |
| `forEach(Consumer)` | 🔴 |
| `count()` | 🔴 |
| `min(Comparator)` and `max(Comparator)` returning `Optional<T>` | 🔴 |
| `findFirst()` and `findAny()` | 🔴 |
| `anyMatch`, `allMatch`, `noneMatch` | 🔴 |
| `collect(Collectors.toList())` and `Collectors.toUnmodifiableList()` | 🔴 |
| `collect(Collectors.toSet())` | 🔴 |
| `collect(Collectors.toMap(keyMapper, valueMapper))` | 🔴 |
| `collect(Collectors.groupingBy(classifier))` | 🔴 |
| `collect(Collectors.joining(delimiter, prefix, suffix))` | 🔴 |
| `reduce(identity, BinaryOperator)` | 🔴 |
| `IntStream.range(0, n)` and `IntStream.rangeClosed(0, n)` | 🔴 |
| `IntStream.sum()`, `average()`, `min()`, `max()` | 🔴 |
| Convert IntStream to Stream: `.boxed()` | 🔴 |

### Streams — Extended (🟡🟢)

| Construct | Level |
|---|---|
| Create infinite stream with `Stream.generate(supplier)` | 🟡 |
| Create infinite stream with `Stream.iterate(seed, f)` | 🟡 |
| `Stream.iterate` with predicate (Java 9): `Stream.iterate(0, n -> n < 10, n -> n+1)` | 🟡 |
| `peek(Consumer)` — for debugging side effects | 🟡 |
| `takeWhile(Predicate)` and `dropWhile(Predicate)` (Java 9) | 🟡 |
| `collect(Collectors.toMap(..., ..., mergeFunction))` — handle duplicate keys | 🟡 |
| `collect(Collectors.groupingBy(classifier, downstream))` — e.g., groupingBy + counting() | 🟡 |
| `collect(Collectors.partitioningBy(Predicate))` | 🟡 |
| `collect(Collectors.counting())` | 🟡 |
| `collect(Collectors.summingInt(...))`, `averagingInt(...)` | 🟡 |
| `collect(Collectors.summarizingInt(...))` | 🟡 |
| `collect(Collectors.toCollection(TreeSet::new))` | 🟡 |
| `reduce(BinaryOperator)` returning `Optional<T>` | 🟡 |
| `toArray()` and `toArray(IntFunction<T[]>)` | 🟡 |
| Parallel stream: `list.parallelStream()` or `stream.parallel()` | 🟡 |
| `reduce(identity, accumulator, combiner)` — 3-arg for parallel | 🟢 |
| Explain when parallel streams help vs hurt | 🟢 |

### Optional — Core (🔴)

| Construct | Level |
|---|---|
| `Optional.of(value)` — throws NPE if null | 🔴 |
| `Optional.ofNullable(value)` — safe, handles null | 🔴 |
| `Optional.empty()` | 🔴 |
| `isPresent()` and `isEmpty()` (Java 11) | 🔴 |
| `get()` — and why it's usually wrong to call directly | 🔴 |
| `orElse(defaultValue)` | 🔴 |
| `orElseGet(Supplier)` — lazy evaluation | 🔴 |
| `orElseThrow(Supplier)` | 🔴 |
| `map(Function)` | 🔴 |
| `flatMap(Function<T, Optional<R>>)` | 🔴 |
| `filter(Predicate)` | 🔴 |
| `ifPresent(Consumer)` | 🔴 |

### Optional — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `ifPresentOrElse(Consumer, Runnable)` (Java 9) | 🟡 |
| `or(Supplier<Optional<T>>)` (Java 9) — fallback optional | 🟡 |
| `stream()` — convert Optional to Stream (Java 9) | 🟡 |

---

## 4. Spring Boot Patterns

### Core Wiring — Core (🔴)

| Construct | Level |
|---|---|
| `@SpringBootApplication` on main class; write `main()` with `SpringApplication.run(...)` | 🔴 |
| `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController` — differences | 🔴 |
| Constructor injection (preferred): declare `final` field, annotate constructor with `@Autowired` (or omit if single constructor) | 🔴 |
| Field injection via `@Autowired` — write it, explain why it's discouraged | 🔴 |
| `@Qualifier("beanName")` alongside `@Autowired` to disambiguate | 🔴 |
| `@Bean` in a `@Configuration` class — declare a bean manually | 🔴 |
| `@Value("${property.key}")` — inject a property value | 🔴 |
| `@Value("${key:defaultValue}")` — with default | 🔴 |

### Core Wiring — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `@Primary` on a bean to set default when multiple candidates exist | 🟡 |
| `@Bean` with method parameter injection (Spring resolves by type) | 🟡 |
| `@ConfigurationProperties(prefix = "app")` on a POJO with `@Component` or `@EnableConfigurationProperties` | 🟡 |
| `@Profile("dev")` on a bean or config class | 🟡 |
| `@ConditionalOnProperty(name="feature.x", havingValue="true")` | 🟡 |
| `@ConditionalOnBean`, `@ConditionalOnMissingBean` | 🟡 |
| `@PostConstruct` / `@PreDestroy` lifecycle hooks | 🟡 |
| `ApplicationContext` — `getBean(...)`, `getBeansOfType(...)` | 🟡 |
| `ApplicationEventPublisher` — inject, `publishEvent(new MyEvent(this, payload))` | 🟡 |
| `@EventListener` on a method to consume application events | 🟡 |
| `BeanPostProcessor` — intercept bean initialization pre/post | 🟢 |

### REST Controllers — Core (🔴)

| Construct | Level |
|---|---|
| `@RestController` + `@RequestMapping("/api/v1/resource")` | 🔴 |
| `@GetMapping("/{id}")` with `@PathVariable Long id` | 🔴 |
| `@GetMapping` with `@RequestParam(required=false, defaultValue="0") int page` | 🔴 |
| `@PostMapping` with `@RequestBody @Valid MyDto dto` | 🔴 |
| `@PutMapping("/{id}")` | 🔴 |
| `@DeleteMapping("/{id}")` | 🔴 |
| `@PatchMapping("/{id}")` | 🔴 |
| Return `ResponseEntity<T>` with custom status: `ResponseEntity.ok(body)`, `ResponseEntity.status(201).body(...)`, `ResponseEntity.noContent().build()` | 🔴 |
| `@RestControllerAdvice` + `@ExceptionHandler(SomeException.class)` | 🔴 |

### REST Controllers — Extended (🟡🟢)

| Construct | Level |
|---|---|
| Return `ProblemDetail` (Spring 6) from exception handler | 🟡 |
| `@Valid` on request body + `BindingResult` or let Spring throw `MethodArgumentNotValidException` | 🟡 |

### Transactions & Async — Core (🔴)

| Construct | Level |
|---|---|
| `@Transactional` on a service method | 🔴 |
| `@Transactional(readOnly = true)` | 🔴 |
| `@Transactional(rollbackFor = SomeCheckedException.class)` | 🔴 |

### Transactions & Async — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `@Transactional(noRollbackFor = ...)` | 🟡 |
| `@Transactional(propagation = Propagation.REQUIRES_NEW)` — explain isolation from outer tx | 🟡 |
| `@Transactional(propagation = Propagation.MANDATORY)` | 🟡 |
| `@Transactional(isolation = Isolation.SERIALIZABLE)` | 🟡 |
| Explain self-invocation limitation (proxy bypass) and when it breaks `@Transactional` | 🟡 |
| `@Async` on a method; enable with `@EnableAsync` on config | 🟡 |
| `@Scheduled(fixedRate=5000)` and `@Scheduled(cron="0 0 * * * *")`; enable with `@EnableScheduling` | 🟡 |

### Caching — Core (🔴)

| Construct | Level |
|---|---|
| `@Cacheable("cacheName")` on a method; enable with `@EnableCaching` | 🔴 |
| `@CacheEvict("cacheName")` on a mutation method | 🔴 |
| `@CachePut("cacheName")` — update cache entry | 🔴 |
| `@Cacheable(key="#id")` — custom SpEL key | 🔴 |
| Configure `CacheManager` bean (e.g., `CaffeineCacheManager`) | 🔴 |

### Spring Security — Extended (🟡🟢)

_(No 🔴 items — all extension-level.)_

| Construct | Level |
|---|---|
| `SecurityFilterChain` bean in a `@Configuration` class — configure `.authorizeHttpRequests(...)`, `.httpBasic(...)`, `.csrf(...)` | 🟡 |
| `UserDetailsService` — implement `loadUserByUsername(String)` returning `UserDetails` | 🟡 |
| `PasswordEncoder` bean (`BCryptPasswordEncoder`) | 🟡 |
| `@PreAuthorize("hasRole('ADMIN')")` on a method; enable with `@EnableMethodSecurity` | 🟡 |
| `@Secured("ROLE_ADMIN")` | 🟡 |
| Custom `AuthenticationProvider` | 🟢 |
| JWT filter extending `OncePerRequestFilter` | 🟢 |

### JPA — Core (🔴)

| Construct | Level |
|---|---|
| `@Entity`, `@Table(name="...")`, `@Column(name="...", nullable=false)` | 🔴 |
| `@Id`, `@GeneratedValue(strategy = GenerationType.IDENTITY)` | 🔴 |
| `@Enumerated(EnumType.STRING)` | 🔴 |
| `@ManyToOne(fetch=FetchType.LAZY)`, `@JoinColumn(name="...", nullable=false)` | 🔴 |
| `@OneToMany(mappedBy="...", cascade=CascadeType.ALL, orphanRemoval=true)` | 🔴 |
| Extend `JpaRepository<T, ID>` — write the interface | 🔴 |
| Derived query method: `findByEmailAndActiveTrue(String email)` | 🔴 |
| `@Query("SELECT u FROM User u WHERE u.email = :email")` with `@Param` | 🔴 |
| Explain `FetchType.LAZY` vs `EAGER` and `LazyInitializationException` | 🔴 |
| Explain and fix the N+1 select problem using `JOIN FETCH` | 🔴 |

### JPA — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `@OneToOne` with `@JoinColumn` | 🟡 |
| `@ManyToMany` with `@JoinTable(name="...", joinColumns=..., inverseJoinColumns=...)` | 🟡 |
| `@Embeddable` on a value object + `@Embedded` on the owning entity field | 🟡 |
| `@CreationTimestamp`, `@UpdateTimestamp` (Hibernate) | 🟡 |
| `@PrePersist`, `@PreUpdate`, `@PostLoad` lifecycle callbacks | 🟡 |
| `@EntityListeners(AuditingEntityListener.class)` with Spring Data `@CreatedDate`, `@LastModifiedDate` | 🟡 |
| `@Version` for optimistic locking | 🟡 |
| `@Lock(LockModeType.PESSIMISTIC_WRITE)` on a repository method | 🟡 |
| `@Query(nativeQuery=true, value="SELECT ...")` | 🟡 |
| `@Modifying` + `@Query` for bulk update/delete | 🟡 |
| Return `List<UserSummaryDto>` from a JPQL projection query (interface or class projection) | 🟡 |
| `Pageable` parameter in repository method; return `Page<T>` | 🟡 |
| Construct `PageRequest.of(page, size, Sort.by("field").descending())` | 🟡 |
| `@EntityGraph(attributePaths = {"orders"})` on a repository method to fetch eagerly | 🟡 |
| `CascadeType` — explain each: PERSIST, MERGE, REMOVE, REFRESH, DETACH, ALL | 🟡 |
| Write a `Specification<T>` for dynamic queries (Criteria API wrapper) | 🟡 |
| `@BatchSize(size=50)` Hibernate hint on collection | 🟢 |
| Understand 1st-level cache (session/EntityManager) vs 2nd-level cache (Ehcache/Redis) | 🟢 |

---

## 5. SQL Patterns

### Core (🔴)

| Construct | Level |
|---|---|
| `SELECT`, `FROM`, `WHERE`, `ORDER BY`, `LIMIT` | 🔴 |
| `INNER JOIN` on foreign key | 🔴 |
| `LEFT JOIN` — include rows with no match on right | 🔴 |
| `RIGHT JOIN` | 🔴 |
| `GROUP BY` with `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` | 🔴 |
| `HAVING` to filter on aggregated result | 🔴 |
| `IN` / `NOT IN` with subquery | 🔴 |
| `CASE WHEN ... THEN ... ELSE ... END` | 🔴 |
| `COALESCE(a, b, c)` | 🔴 |
| `EXISTS` / `NOT EXISTS` | 🔴 |
| Create `INDEX` — single column, composite, partial index | 🔴 |
| `EXPLAIN ANALYZE SELECT ...` — read cost, rows, actual time | 🔴 |
| `TRANSACTION BEGIN / COMMIT / ROLLBACK / SAVEPOINT` | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| `FULL OUTER JOIN` | 🟡 |
| Self-join (join table to itself) | 🟡 |
| Subquery in `WHERE` clause (correlated and non-correlated) | 🟡 |
| Subquery in `FROM` (derived table / inline view) | 🟡 |
| `NULLIF(a, b)` | 🟡 |
| CTE with `WITH cte_name AS (SELECT ...) SELECT ...` | 🟡 |
| `ROW_NUMBER() OVER (PARTITION BY ... ORDER BY ...)` | 🟡 |
| `RANK()` and `DENSE_RANK()` | 🟡 |
| `LAG(col, offset)` and `LEAD(col, offset)` | 🟡 |
| `SUM(...) OVER (PARTITION BY ...)` — running total | 🟡 |
| `DISTINCT ON (col)` (PostgreSQL) | 🟡 |
| `INSERT INTO ... ON CONFLICT DO UPDATE SET ...` (upsert, PostgreSQL) | 🟡 |
| Recursive CTE | 🟢 |
| Know isolation levels: READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE and what anomaly each prevents | 🟢 |

---

## 6. Concurrency

### Core (🔴)

| Construct | Level |
|---|---|
| Create and start a `Thread` using `extends Thread` | 🔴 |
| Create and start a `Thread` using `implements Runnable` | 🔴 |
| Write a `synchronized` method | 🔴 |
| Write a `synchronized` block on an explicit lock object | 🔴 |
| Use `AtomicInteger` — `incrementAndGet`, `compareAndSet`, `getAndUpdate` | 🔴 |
| Create `ExecutorService` via `Executors.newFixedThreadPool(n)` | 🔴 |
| Create `ExecutorService` via `Executors.newCachedThreadPool()` | 🔴 |
| Create `ExecutorService` via `Executors.newSingleThreadExecutor()` | 🔴 |
| Create a `Callable<T>` and submit to `ExecutorService`, get `Future<T>` result | 🔴 |
| Properly shut down an `ExecutorService` (`shutdown` + `awaitTermination`) | 🔴 |
| Write `CompletableFuture.supplyAsync(...)` | 🔴 |
| Chain with `.thenApply(...)` (transform), `.thenAccept(...)` (consume) | 🔴 |
| Use `.exceptionally(...)` for error recovery | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| Declare a `volatile` field and explain its guarantee | 🟡 |
| Use `wait()` / `notify()` / `notifyAll()` in a producer-consumer monitor pattern | 🟡 |
| Use `AtomicReference<T>` — `compareAndSet` for lock-free update | 🟡 |
| Use `ReentrantLock` — `lock`, `unlock` in try/finally, `tryLock(timeout)` | 🟡 |
| Use `ReadWriteLock` — `readLock` and `writeLock` for read-heavy shared state | 🟡 |
| Use `CountDownLatch` — create, `countDown()`, `await()` | 🟡 |
| Use `CyclicBarrier` — create with action, `await()` | 🟡 |
| Use `Semaphore` — `acquire`, `release`, use for resource pool limiting | 🟡 |
| Use `ThreadLocal<T>` — `set`, `get`, `remove`; explain leak risk | 🟡 |
| Chain with `.thenCompose(...)` for async-to-async chaining | 🟡 |
| Use `.handle(...)` for combined result+error handling | 🟡 |
| Combine multiple futures with `CompletableFuture.allOf(...)` | 🟡 |
| Use `CompletableFuture.anyOf(...)` | 🟡 |
| Write `thenApplyAsync` vs `thenApply` — explain thread implications | 🟢 |
| Explain happens-before, memory visibility, and why synchronized solves it | 🟢 |
| Explain `ForkJoinPool` and work-stealing; how parallel streams use it | 🟢 |

---

## 7. Design Patterns

### Creational — Core (🔴)

| Construct | Level |
|---|---|
| **Singleton** — eager (static final field) | 🔴 |
| **Builder** — inner static `Builder` class with chained setters, `build()` returns outer instance | 🔴 |

### Creational — Extended (🟡🟢)

| Construct | Level |
|---|---|
| **Singleton** — lazy with `synchronized` method | 🟡 |
| **Singleton** — double-checked locking with `volatile` | 🟡 |
| **Singleton** — enum-based (thread-safe, serialization-safe) | 🟡 |
| **Factory Method** — abstract creator with `createProduct()`, concrete creators override | 🟡 |
| **Prototype** — implement `Cloneable`, override `clone()`, shallow vs deep copy | 🟡 |
| **Abstract Factory** — family of related factories (`ButtonFactory` → `WindowsButton`, `MacButton`) | 🟢 |

### Structural — Core (🔴)

| Construct | Level |
|---|---|
| **Adapter** — wrap incompatible interface, delegate to adaptee | 🔴 |
| **Decorator** — wrap a component implementing the same interface, add behavior | 🔴 |
| **Facade** — single class that simplifies calls to a subsystem | 🔴 |

### Structural — Extended (🟡🟢)

| Construct | Level |
|---|---|
| **Proxy** — static proxy: same interface, wraps real subject (logging, security) | 🟡 |
| **Dynamic Proxy** — `java.lang.reflect.Proxy`, implement `InvocationHandler` | 🟡 |
| **Composite** — tree of `Component` nodes; `Leaf` and `Composite` both implement `Component` | 🟡 |
| **Bridge** — separate abstraction from implementation; `Abstraction` holds `Implementor` ref | 🟢 |
| **Flyweight** — shared cache of objects (e.g., `IntegerCache`), factory with pool | 🟢 |

### Behavioral — Core (🔴)

| Construct | Level |
|---|---|
| **Strategy** — interface with algorithm method; swap concrete strategies at runtime | 🔴 |
| **Observer** — `Subject` maintains list of `Observer`; notifies on state change | 🔴 |
| **Template Method** — abstract class defines skeleton algorithm; subclasses fill in steps | 🔴 |

### Behavioral — Extended (🟡🟢)

| Construct | Level |
|---|---|
| **Command** — `Command` interface with `execute()`; `ConcreteCommand` holds receiver + action | 🟡 |
| **Iterator** — `Iterator<T>` with `hasNext()`/`next()`; custom `Iterable<T>` class | 🟡 |
| **State** — `Context` delegates behavior to `State` object; state changes behavior dynamically | 🟡 |
| **Chain of Responsibility** — `Handler` interface with `setNext`, each handler decides pass-or-handle | 🟡 |
| **Mediator** — central object coordinates interactions between colleague objects | 🟢 |
| **Visitor** — `Visitor` interface per element type; elements call `visitor.visit(this)` | 🟢 |

---

## 8. Exception Handling

### Core (🔴)

| Construct | Level |
|---|---|
| Distinguish `Error` vs `Exception` vs `RuntimeException` hierarchy | 🔴 |
| Write `try-catch-finally` block | 🔴 |
| Write multi-catch: `catch (IOException \| SQLException e)` | 🔴 |
| Write `try-with-resources` for a class implementing `AutoCloseable` | 🔴 |
| Declare a custom checked exception extending `Exception` | 🔴 |
| Declare a custom unchecked exception extending `RuntimeException` | 🔴 |
| Include a cause: `throw new ServiceException("msg", cause)` | 🔴 |
| Declare `throws` on a method signature | 🔴 |
| Re-throw a caught exception wrapped in a different type | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| Implement `AutoCloseable` on a custom resource class | 🟡 |
| Use `Throwable.getSuppressed()` — understand when it's populated (try-with-resources) | 🟡 |
| Explain when `finally` does NOT execute | 🟡 |
| Write an exception hierarchy: base domain exception + subtypes | 🟡 |

---

## 9. Generics

### Core (🔴)

| Construct | Level |
|---|---|
| Declare a generic class `class Box<T> { T value; }` | 🔴 |
| Declare a generic interface `interface Transformer<T, R>` | 🔴 |
| Declare a generic method `<T> T identity(T input)` | 🔴 |
| Write a generic utility method (e.g., `<T> List<T> repeat(T item, int n)`) | 🔴 |
| Use bounded type parameters `<T extends Comparable<T>>` | 🔴 |

### Extended (🟡🟢)

| Construct | Level |
|---|---|
| Use multiple bounds `<T extends Serializable & Comparable<T>>` | 🟡 |
| Declare a generic stack/pair/triple class | 🟡 |
| Write upper-bounded wildcard `? extends Number` and explain when to use it | 🟡 |
| Write lower-bounded wildcard `? super Integer` and explain when to use it | 🟡 |
| Explain PECS (Producer Extends, Consumer Super) with a code example | 🟡 |
| Declare an unbounded wildcard `?` and explain when appropriate | 🟡 |
| Explain type erasure: what it means, what gets erased, runtime implications | 🟢 |
| Show why `new T()` and `new T[]` are illegal; work around with `Class<T>` | 🟢 |

---

## 10. Testing Patterns

### JUnit 5 — Core (🔴)

| Construct | Level |
|---|---|
| `@Test` on a method | 🔴 |
| `@BeforeEach` setup method | 🔴 |
| `@AfterEach` teardown method | 🔴 |
| `@BeforeAll` / `@AfterAll` (static methods) | 🔴 |
| `@DisplayName("human readable test name")` | 🔴 |
| `@Disabled("reason")` | 🔴 |
| `assertEquals(expected, actual)`, `assertNotEquals` | 🔴 |
| `assertNull(...)`, `assertNotNull(...)` | 🔴 |
| `assertTrue(...)`, `assertFalse(...)` | 🔴 |
| `assertThrows(SomeException.class, () -> callUnderTest())` | 🔴 |
| `@ParameterizedTest` + `@ValueSource(ints={1,2,3})` | 🔴 |

### JUnit 5 — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `assertDoesNotThrow(...)` | 🟡 |
| `assertAll("group", () -> assertEquals(...), () -> assertNotNull(...))` | 🟡 |
| `assertTimeout(Duration.ofMillis(100), () -> ...)` | 🟡 |
| `@Nested` inner class for grouping related tests | 🟡 |
| `@ParameterizedTest` + `@CsvSource({"input,expected", "1,2"})` | 🟡 |
| `@ParameterizedTest` + `@MethodSource("providerMethodName")` with static stream method | 🟡 |
| `@ParameterizedTest` + `@EnumSource(MyEnum.class)` | 🟡 |
| `@RepeatedTest(5)` | 🟡 |
| `@TempDir` for temporary file testing | 🟡 |

### Mockito — Core (🔴)

| Construct | Level |
|---|---|
| `@ExtendWith(MockitoExtension.class)` on test class | 🔴 |
| `@Mock MyService service` | 🔴 |
| `@InjectMocks MyController controller` | 🔴 |
| `when(mock.method(arg)).thenReturn(value)` | 🔴 |
| `when(mock.method(any())).thenReturn(value)` | 🔴 |
| `when(mock.method(any())).thenThrow(new RuntimeException())` | 🔴 |
| `verify(mock).method(expectedArg)` | 🔴 |
| `verify(mock, times(2)).method(any())` | 🔴 |
| `verify(mock, never()).method(any())` | 🔴 |

### Mockito — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `@Spy MyList list = new ArrayList<>()` — real object with selective stubbing | 🟡 |
| `@Captor ArgumentCaptor<String> captor` | 🟡 |
| `when(mock.method(any())).thenAnswer(invocation -> { ... })` | 🟡 |
| `doReturn(value).when(spy).method()` — use with `@Spy` | 🟡 |
| `doThrow(...).when(mock).voidMethod()` | 🟡 |
| `verify(mock, atLeastOnce()).method(any())` | 🟡 |
| `verifyNoInteractions(mock)` | 🟡 |
| `verifyNoMoreInteractions(mock)` | 🟡 |
| `ArgumentCaptor.capture()` in verify; `captor.getValue()` after | 🟡 |
| `InOrder` — verify method call ordering | 🟡 |
| `MockitoAnnotations.openMocks(this)` — use without extension in `@BeforeEach` | 🟡 |
| `BDDMockito.given(...).willReturn(...)` — BDD style | 🟡 |

### Spring Boot Testing — Core (🔴)

| Construct | Level |
|---|---|
| `@SpringBootTest` — load full application context | 🔴 |
| `@WebMvcTest(MyController.class)` — slice test, no service layer | 🔴 |
| `@MockBean MyService service` — replace bean in context with mock | 🔴 |
| `@Autowired MockMvc mockMvc` in `@WebMvcTest` | 🔴 |
| `mockMvc.perform(get("/api/resource")).andExpect(status().isOk())` | 🔴 |
| `.andExpect(content().contentType(MediaType.APPLICATION_JSON))` | 🔴 |
| `.andExpect(jsonPath("$.field").value("expected"))` | 🔴 |
| `mockMvc.perform(post(...).contentType(APPLICATION_JSON).content(jsonString))` | 🔴 |

### Spring Boot Testing — Extended (🟡🟢)

| Construct | Level |
|---|---|
| `@SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT)` | 🟡 |
| `@SpyBean MyService service` — replace with spy | 🟡 |
| `@DataJpaTest` — slice test with H2 and JPA repos | 🟡 |
| `.andExpect(jsonPath("$.list", hasSize(3)))` | 🟡 |
| `@Transactional` in `@DataJpaTest` — rollback after each test | 🟡 |
| `TestRestTemplate` in full context tests | 🟡 |
| `@TestConfiguration` for test-specific beans | 🟡 |
| `@ActiveProfiles("test")` | 🟡 |
| Testcontainers — declare `@Container` with `PostgreSQLContainer`, use `@DynamicPropertySource` to wire datasource | 🟡 |
| `WireMock` — stub external HTTP calls in integration tests | 🟢 |

---

## Worked Examples (one per topic, reference only)

One representative example per topic — this gauntlet assumes you've met the material
before and are rebuilding cold recall, not learning from zero. **Same treatment as
`primer.md`: study before the session,
CLOSE it before you write, never have the coach read it aloud mid-drill** — that would
turn a cold-write into a copy exercise.

**1. OOP** — class + equals/hashCode + Comparable in one shape:
```java
final class Money implements Comparable<Money> {
    private final int cents;
    Money(int cents) { this.cents = cents; }
    @Override public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Money m)) return false;
        return cents == m.cents;
    }
    @Override public int hashCode() { return Objects.hash(cents); }
    @Override public int compareTo(Money o) { return Integer.compare(cents, o.cents); }
}
```

**2. Collections** — `Map` count-then-scan + `Comparator` chain (the two idioms that
recur most across the gauntlet):
```java
Map<String, Integer> counts = new HashMap<>();
for (String w : words) counts.merge(w, 1, Integer::sum);
List<Employee> sorted = employees.stream()
    .sorted(Comparator.comparing(Employee::getDept)
        .thenComparing(Employee::getSalary, Comparator.reverseOrder()))
    .toList();
```

**3. Functional** — lambda → method ref collapse + `Optional` chain:
```java
Function<String, Integer> len = String::length;           // collapsed from s -> s.length()
Optional<String> name = Optional.ofNullable(input)
    .filter(s -> !s.isBlank())
    .map(String::trim);
String result = name.orElseGet(() -> "default");
```

**4. Spring Boot** — constructor injection + REST endpoint:
```java
@RestController
@RequestMapping("/api/users")
class UserController {
    private final UserService service;
    UserController(UserService service) { this.service = service; }
    @GetMapping("/{id}")
    ResponseEntity<User> get(@PathVariable Long id) {
        return ResponseEntity.ok(service.find(id));
    }
}
```

**5. SQL** — N+1 fix via `JOIN FETCH` (JPQL, drilled under Spring Boot § JPA but the
idiom is a SQL/JPA crossover worth keeping here too):
```sql
-- N+1: one query per order to fetch its items
SELECT o FROM Order o WHERE o.customerId = :id
-- fix: fetch items in the same round trip
SELECT o FROM Order o JOIN FETCH o.items WHERE o.customerId = :id
```

**6. Concurrency** — `ExecutorService` + `CompletableFuture` chain:
```java
ExecutorService pool = Executors.newFixedThreadPool(4);
CompletableFuture.supplyAsync(() -> fetch(), pool)
    .thenApply(this::transform)
    .exceptionally(ex -> fallback())
    .thenAccept(System.out::println);
pool.shutdown();
```

**7. Design Patterns** — Strategy (the pattern this tracker's history shows needs it
most):
```java
interface DiscountStrategy { double apply(double price); }
class NoDiscount implements DiscountStrategy { public double apply(double p) { return p; } }
class TenPercentOff implements DiscountStrategy { public double apply(double p) { return p * 0.9; } }
class Checkout {
    private final DiscountStrategy strategy;
    Checkout(DiscountStrategy strategy) { this.strategy = strategy; }
    double total(double price) { return strategy.apply(price); }
}
```

**8. Exception Handling** — custom exception with cause + try-with-resources:
```java
class OrderException extends RuntimeException {
    OrderException(String msg, Throwable cause) { super(msg, cause); }
}
try (var conn = dataSource.getConnection()) {
    // ...
} catch (SQLException e) {
    throw new OrderException("order lookup failed", e);
}
```

**9. Generics** — bounded type param + PECS:
```java
<T extends Comparable<T>> T max(List<T> items) {
    T best = items.get(0);
    for (T item : items) if (item.compareTo(best) > 0) best = item;
    return best;
}
void addAll(List<? super Integer> dest, List<? extends Integer> src) { // PECS
    for (Integer i : src) dest.add(i);
}
```

**10. Testing** — Mockito stub + verify:
```java
@ExtendWith(MockitoExtension.class)
class ServiceTest {
    @Mock Repo repo;
    @InjectMocks Service service;
    @Test void savesOnce() {
        when(repo.findById(1L)).thenReturn(Optional.of(new User()));
        service.touch(1L);
        verify(repo, times(1)).save(any());
    }
}
```

## Summary Gap Map

1. **Pass 1 — breadth.** Every **Core (🔴)** block, in topic order above, cold. Stall = gap. Drill until automatic.
2. **Pass 2 — depth.** Loop back through **Extended** blocks: 🟡 first, 🟢 last.

**Highest ROI targets:**
- All of OOP · Collections + Generics cold · CompletableFuture chaining
- Stream + Collectors (groupingBy, toMap, reduce) · Builder, Strategy, Observer, Singleton(enum)
- `@Transactional` semantics + self-invocation · N+1 + `JOIN FETCH` fix
- `@WebMvcTest` + MockMvc · `@Mock`/`@InjectMocks`/`verify`
</content>
