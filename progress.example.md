# Drill Progress

Copy this file to `progress.md` (the coach does it automatically on first run). The
coach reads and updates `progress.md`, not this file.

**Legend:** `[ ]` not attempted · `[~]` stalled / needed hints (re-drill) · `[x]` passed cold
**Rule:** a row becomes `[x]` only after two Pass-grade cold reps in a row, on separate
touches (see the rubric in `curriculum.md`). Checklist lines stay bare — no inline
notes. Detail goes on the Re-Drill List, the Recall Queue, or `session-log.md`.

> Drill Core blocks first (all topics), then Extended. Testing is drilled last.

---

## Re-Drill List (auto-maintained — clear when re-passed)

Misses only. Each entry: row name + what went wrong + any framing that worked.

- _(empty until first miss)_

---

## Recall Queue (spaced repetition)

The Re-Drill List only resurfaces **misses**. This queue resurfaces **everything
drilled**, including clean first-try passes — those decay too, just slower. Box schedule:

- **Box 1** (new, or dropped back after a miss) → due next session.
- **Box 2** (1 clean cold recall at Box 1) → due ~2 sessions later.
- **Box 3** (2 clean cold recalls in a row) → due ~4 sessions later.
- **Box 4** (3 clean cold recalls in a row) → retired, drop the row.
- A miss at ANY box → back to Box 1, regardless of how high it had climbed.

Every session's warm-up pulls the 1-2 rows with the oldest "Due" session before any new
drilling. Rows enter this queue only from normal row-by-row drilling, not from
full-topic quizzes (quiz results go to the Re-Drill List and `session-log.md`). At
session end, every row actually drilled — pass or miss — gets logged or updated here.

| Row | Box | Last recalled | Due |
|---|---|---|---|
| _(empty until first session)_ | | | |

---

## 1. OOP

### Core 🔴
- [ ] class: private fields, ctor, getters/setters
- [ ] override `toString()`
- [ ] override `equals()` + `hashCode()`
- [ ] `static` field + method
- [ ] `final` class / method / variable
- [ ] ctor chaining `this(...)`
- [ ] `abstract` class
- [ ] extend abstract, implement all abstract methods
- [ ] `super` → parent ctor
- [ ] `super` → overridden method
- [ ] overloading vs overriding
- [ ] `interface` with abstract method
- [ ] class `implements` interface
- [ ] `default` method on interface
- [ ] `static` method on interface
- [ ] `@FunctionalInterface`
- [ ] pass lambda where functional interface expected
- [ ] `enum` with constants
- [ ] `instanceof` + safe cast
- [ ] varargs `String... args`
- [ ] `Comparable<T>` + `compareTo()`

### Extended 🟡🟢
- [ ] static initializer block
- [ ] instance initializer block
- [ ] static nested class
- [ ] inner (non-static) class + instantiate
- [ ] anonymous class inline
- [ ] `record` + compact constructor
- [ ] `enum` with fields/ctor/method
- [ ] `enum` implements interface
- [ ] pattern-matching `instanceof`
- [ ] covariant return types
- [ ] `Cloneable` + `clone()`
- [ ] `sealed` / `permits` / `non-sealed` 🟢

## 2. Collections

### Core 🔴
- [ ] `ArrayList<T>` populate
- [ ] `List.of` / `List.copyOf` (immutable)
- [ ] `Comparator<T>` inline / lambda / `comparing()`
- [ ] chain comparators `thenComparing` / `reversed`
- [ ] sort: `Collections.sort` + `list.sort(Comparator)`
- [ ] `ArrayDeque` as stack
- [ ] `ArrayDeque` as queue
- [ ] `PriorityQueue` natural + custom comparator
- [ ] `HashSet<T>` add / `contains`
- [ ] `HashMap` put/get/getOrDefault/putIfAbsent
- [ ] iterate Map: entrySet/keySet/values
- [ ] `ArrayDeque` as stack + queue
- [ ] `PriorityQueue` natural + custom comparator
- [ ] `Collections.unmodifiableList/Set/Map`
- [ ] `ConcurrentHashMap` putIfAbsent/computeIfAbsent/compute/merge

### Extended 🟡🟢
- [ ] `LinkedList` as queue + deque
- [ ] `LinkedHashSet` (insertion order)
- [ ] `TreeSet` (natural ordering)
- [ ] `Map.of` / `Map.entry`
- [ ] `LinkedHashMap` insertion-order
- [ ] LinkedHashMap `removeEldestEntry` LRU
- [ ] `TreeMap` floorKey/ceilingKey/headMap/tailMap
- [ ] `Collections.synchronizedList`
- [ ] `Collections.frequency/disjoint/nCopies`
- [ ] custom `Iterator<T>` hasNext/next
- [ ] fail-fast ArrayList iterator (explain)
- [ ] `CopyOnWriteArrayList`
- [ ] `BlockingQueue` producer-consumer

## 3. Functional

### Lambdas Core 🔴
- [ ] `() -> expr`
- [ ] `x -> x*2`
- [ ] `(a,b) -> a+b`
- [ ] block body + return
- [ ] static method ref `Class::m`
- [ ] instance method ref `obj::m`
- [ ] type method ref `String::toUpperCase`
- [ ] ctor ref `ArrayList::new`
- [ ] `Supplier` get
- [ ] `Consumer` accept/andThen
- [ ] `Predicate` test/and/or/negate
- [ ] `Function` apply/andThen/compose
- [ ] `Comparator.comparing/thenComparing/reversed`

### Lambdas Extended 🟡
- [ ] `BiFunction`
- [ ] `BiConsumer`
- [ ] `UnaryOperator`
- [ ] `BinaryOperator`

### Streams Core 🔴
- [ ] `list.stream()`
- [ ] `Arrays.stream(arr)`
- [ ] `Stream.of(...)`
- [ ] `filter`
- [ ] `map`
- [ ] `mapToInt/Long/Double`
- [ ] `flatMap`
- [ ] `distinct`
- [ ] `sorted` / `sorted(Comparator)`
- [ ] `limit` / `skip`
- [ ] `forEach`
- [ ] `count`
- [ ] `min` / `max` → Optional
- [ ] `findFirst` / `findAny`
- [ ] `anyMatch` / `allMatch` / `noneMatch`
- [ ] `toList` / `toUnmodifiableList`
- [ ] `toSet`
- [ ] `toMap(k,v)`
- [ ] `groupingBy(classifier)`
- [ ] `joining(delim,prefix,suffix)`
- [ ] `reduce(identity, op)`
- [ ] `IntStream.range / rangeClosed`
- [ ] `IntStream.sum/average/min/max`
- [ ] `.boxed()`

### Streams Extended 🟡🟢
- [ ] `Stream.generate`
- [ ] `Stream.iterate(seed, f)`
- [ ] `Stream.iterate(seed, pred, f)`
- [ ] `peek`
- [ ] `takeWhile` / `dropWhile`
- [ ] `toMap(...mergeFn)`
- [ ] `groupingBy(classifier, downstream)`
- [ ] `partitioningBy`
- [ ] `counting`
- [ ] `summingInt` / `averagingInt`
- [ ] `summarizingInt`
- [ ] `toCollection(TreeSet::new)`
- [ ] `reduce(op)` → Optional
- [ ] `toArray` / `toArray(IntFunction)`
- [ ] parallel stream
- [ ] `reduce(identity, acc, combiner)` 🟢
- [ ] parallel: help vs hurt 🟢

### Optional Core 🔴
- [ ] `of`
- [ ] `ofNullable`
- [ ] `empty`
- [ ] `isPresent` / `isEmpty`
- [ ] `get` (+ why wrong)
- [ ] `orElse`
- [ ] `orElseGet`
- [ ] `orElseThrow`
- [ ] `map`
- [ ] `flatMap`
- [ ] `filter`
- [ ] `ifPresent`

### Optional Extended 🟡
- [ ] `ifPresentOrElse`
- [ ] `or(Supplier)`
- [ ] `stream()`

## 4. Spring Boot

### Core Wiring Core 🔴
- [ ] `@SpringBootApplication` + main
- [ ] stereotypes diff (@Component/@Service/@Repository/@Controller/@RestController)
- [ ] constructor injection (final field)
- [ ] field injection @Autowired (+ why discouraged)
- [ ] `@Qualifier`
- [ ] `@Bean` in `@Configuration`
- [ ] `@Value("${key}")`
- [ ] `@Value("${key:default}")`
- [ ] `application.yml` setup

### Core Wiring Extended 🟡🟢
- [ ] `@Primary`
- [ ] `@Bean` method param injection
- [ ] `@ConfigurationProperties`
- [ ] `@Profile`
- [ ] `@ConditionalOnProperty`
- [ ] `@ConditionalOnBean` / `@ConditionalOnMissingBean`
- [ ] `@PostConstruct` / `@PreDestroy`
- [ ] `ApplicationContext` getBean/getBeansOfType
- [ ] `ApplicationEventPublisher` publishEvent
- [ ] `@EventListener`
- [ ] `BeanPostProcessor` 🟢

### REST Core 🔴
- [ ] `@RestController` + `@RequestMapping`
- [ ] `@GetMapping("/{id}")` + `@PathVariable`
- [ ] `@RequestParam(required,defaultValue)`
- [ ] `@PostMapping` + `@RequestBody @Valid`
- [ ] `@PutMapping`
- [ ] `@DeleteMapping`
- [ ] `@PatchMapping`
- [ ] `ResponseEntity` ok/status/noContent
- [ ] `@RestControllerAdvice` + `@ExceptionHandler`

### REST Extended 🟡
- [ ] `ProblemDetail`
- [ ] `@Valid` + BindingResult / MethodArgumentNotValidException

### Tx & Async Core 🔴
- [ ] `@Transactional`
- [ ] `@Transactional(readOnly=true)`
- [ ] `@Transactional(rollbackFor=...)`

### Tx & Async Extended 🟡
- [ ] `noRollbackFor`
- [ ] `REQUIRES_NEW`
- [ ] `MANDATORY`
- [ ] `isolation=SERIALIZABLE`
- [ ] self-invocation limitation
- [ ] `@Async` + `@EnableAsync`
- [ ] `@Scheduled` + `@EnableScheduling`

### Caching Core 🔴
- [ ] `@Cacheable` + `@EnableCaching`
- [ ] `@CacheEvict`
- [ ] `@CachePut`
- [ ] `@Cacheable(key=SpEL)`
- [ ] `CacheManager` (Caffeine)

### Security Extended 🟡🟢 (no Core)
- [ ] `SecurityFilterChain`
- [ ] `UserDetailsService`
- [ ] `PasswordEncoder` (BCrypt)
- [ ] `@PreAuthorize` + `@EnableMethodSecurity`
- [ ] `@Secured`
- [ ] custom `AuthenticationProvider` 🟢
- [ ] JWT filter `OncePerRequestFilter` 🟢

### JPA Core 🔴
- [ ] `@Entity` / `@Table` / `@Column`
- [ ] `@Id` / `@GeneratedValue(IDENTITY)`
- [ ] `@Enumerated(STRING)`
- [ ] `@ManyToOne(LAZY)` + `@JoinColumn`
- [ ] `@OneToMany(mappedBy,cascade,orphanRemoval)`
- [ ] extend `JpaRepository<T,ID>`
- [ ] derived query `findByEmailAndActiveTrue`
- [ ] `@Query` JPQL + `@Param`
- [ ] LAZY vs EAGER + LazyInitializationException
- [ ] N+1 + JOIN FETCH fix

### JPA Extended 🟡🟢
- [ ] `@OneToOne`
- [ ] `@ManyToMany` + `@JoinTable`
- [ ] `@Embeddable` / `@Embedded`
- [ ] `@CreationTimestamp` / `@UpdateTimestamp`
- [ ] `@PrePersist` / `@PreUpdate` / `@PostLoad`
- [ ] `@EntityListeners` auditing
- [ ] `@Version` optimistic lock
- [ ] `@Lock(PESSIMISTIC_WRITE)`
- [ ] native query
- [ ] `@Modifying` bulk update/delete
- [ ] JPQL projection DTO
- [ ] `Pageable` / `Page<T>`
- [ ] `PageRequest.of(...Sort)`
- [ ] `@EntityGraph`
- [ ] CascadeType (explain each)
- [ ] `Specification<T>`
- [ ] `@BatchSize` 🟢
- [ ] 1st vs 2nd level cache 🟢

## 5. SQL

### SQL Core 🔴
- [ ] SELECT/FROM/WHERE/ORDER BY/LIMIT
- [ ] INNER JOIN
- [ ] LEFT JOIN
- [ ] RIGHT JOIN
- [ ] GROUP BY + COUNT/SUM/AVG/MAX/MIN
- [ ] HAVING
- [ ] IN / NOT IN subquery
- [ ] CASE WHEN
- [ ] COALESCE
- [ ] EXISTS / NOT EXISTS
- [ ] CREATE INDEX (single/composite/partial)
- [ ] EXPLAIN ANALYZE
- [ ] TRANSACTION BEGIN/COMMIT/ROLLBACK/SAVEPOINT

### SQL Extended 🟡🟢
- [ ] FULL OUTER JOIN
- [ ] self-join
- [ ] subquery in WHERE (correlated/non)
- [ ] subquery in FROM
- [ ] NULLIF
- [ ] CTE WITH
- [ ] ROW_NUMBER OVER
- [ ] RANK / DENSE_RANK
- [ ] LAG / LEAD
- [ ] SUM OVER (running total)
- [ ] DISTINCT ON
- [ ] INSERT ON CONFLICT (upsert)
- [ ] recursive CTE 🟢
- [ ] isolation levels + anomalies 🟢

## 6. Concurrency

### Core 🔴
- [ ] `Thread` via `extends Thread`
- [ ] `Thread` via `implements Runnable`
- [ ] `synchronized` method
- [ ] `synchronized` block on lock object
- [ ] `AtomicInteger` inc/CAS/getAndUpdate
- [ ] `Executors.newFixedThreadPool`
- [ ] `Executors.newCachedThreadPool`
- [ ] `Executors.newSingleThreadExecutor`
- [ ] `Callable` → submit → `Future`
- [ ] shutdown + awaitTermination
- [ ] `CompletableFuture.supplyAsync`
- [ ] `.thenApply` / `.thenAccept`
- [ ] `.exceptionally`

### Extended 🟡🟢
- [ ] `volatile` (explain guarantee)
- [ ] wait/notify/notifyAll monitor
- [ ] `AtomicReference` CAS
- [ ] `ReentrantLock` lock/unlock/tryLock
- [ ] `ReadWriteLock`
- [ ] `CountDownLatch`
- [ ] `CyclicBarrier`
- [ ] `Semaphore`
- [ ] `ThreadLocal` set/get/remove + leak
- [ ] `.thenCompose`
- [ ] `.handle`
- [ ] `allOf`
- [ ] `anyOf`
- [ ] thenApplyAsync vs thenApply 🟢
- [ ] happens-before / visibility 🟢
- [ ] ForkJoinPool work-stealing 🟢

## 7. Design Patterns

### Creational Core 🔴
- [ ] Singleton eager
- [ ] Builder

### Creational Extended 🟡🟢
- [ ] Singleton lazy synchronized
- [ ] Singleton DCL + volatile
- [ ] Singleton enum
- [ ] Factory Method
- [ ] Prototype (clone, shallow/deep)
- [ ] Abstract Factory 🟢

### Structural Core 🔴
- [ ] Adapter (needed guidance on wrapping + constructor injection; structure correct once directed)
- [ ] Decorator
- [ ] Facade

### Structural Extended 🟡🟢
- [ ] Proxy (static)
- [ ] Dynamic Proxy (`InvocationHandler`)
- [ ] Composite
- [ ] Bridge 🟢
- [ ] Flyweight 🟢

### Behavioral Core 🔴
- [ ] Strategy (needed full architecture explanation + for-each hint; RuleEngine structure correct once directed)
- [ ] Observer
- [ ] Template Method (needed method signature fixes + syntax correction; pipeline correct once directed)

### Behavioral Extended 🟡🟢
- [ ] Command
- [ ] Iterator (custom Iterable)
- [ ] State
- [ ] Chain of Responsibility
- [ ] Mediator 🟢
- [ ] Visitor 🟢

## 8. Exception Handling

### Core 🔴
- [ ] Error vs Exception vs RuntimeException hierarchy
- [ ] try-catch-finally
- [ ] multi-catch `IOException | SQLException`
- [ ] try-with-resources (AutoCloseable)
- [ ] custom checked extends `Exception`
- [ ] custom unchecked extends `RuntimeException`
- [ ] include cause `new X("msg", cause)`
- [ ] `throws` on signature
- [ ] re-throw wrapped in different type

### Extended 🟡🟢
- [ ] implement `AutoCloseable` on custom resource
- [ ] `getSuppressed()` (when populated)
- [ ] when `finally` does NOT execute
- [ ] exception hierarchy: base + subtypes

## 9. Generics

### Core 🔴
- [ ] generic class `Box<T>`
- [ ] generic interface `Transformer<T,R>`
- [ ] generic method `<T> T identity(T)`
- [ ] generic util `<T> List<T> repeat(T,int)`
- [ ] bounded `<T extends Comparable<T>>`

### Extended 🟡🟢
- [ ] multiple bounds `<T extends A & B>`
- [ ] generic stack/pair/triple
- [ ] upper-bound wildcard `? extends Number`
- [ ] lower-bound wildcard `? super Integer`
- [ ] PECS w/ code
- [ ] unbounded wildcard `?`
- [ ] type erasure (explain) 🟢
- [ ] `new T()` / `new T[]` illegal + `Class<T>` workaround 🟢

## 10. Testing

### JUnit5 Core 🔴
- [ ] `@Test`
- [ ] `@BeforeEach`
- [ ] `@AfterEach`
- [ ] `@BeforeAll` / `@AfterAll`
- [ ] `@DisplayName`
- [ ] `@Disabled`
- [ ] `assertEquals` / `assertNotEquals`
- [ ] `assertNull` / `assertNotNull`
- [ ] `assertTrue` / `assertFalse`
- [ ] `assertThrows`
- [ ] `@ParameterizedTest` + `@ValueSource`

### JUnit5 Extended 🟡
- [ ] `assertDoesNotThrow`
- [ ] `assertAll`
- [ ] `assertTimeout`
- [ ] `@Nested`
- [ ] `@CsvSource`
- [ ] `@MethodSource`
- [ ] `@EnumSource`
- [ ] `@RepeatedTest`
- [ ] `@TempDir`

### Mockito Core 🔴
- [ ] `@ExtendWith(MockitoExtension)`
- [ ] `@Mock`
- [ ] `@InjectMocks`
- [ ] `when(...).thenReturn`
- [ ] `when(any()).thenReturn`
- [ ] `when(any()).thenThrow`
- [ ] `verify(mock).method(arg)`
- [ ] `verify(times(2))`
- [ ] `verify(never())`

### Mockito Extended 🟡
- [ ] `@Spy`
- [ ] `@Captor`
- [ ] `thenAnswer`
- [ ] `doReturn().when(spy)`
- [ ] `doThrow().when(mock).voidMethod`
- [ ] `verify(atLeastOnce())`
- [ ] `verifyNoInteractions`
- [ ] `verifyNoMoreInteractions`
- [ ] `ArgumentCaptor.capture` + getValue
- [ ] `InOrder`
- [ ] `openMocks(this)`
- [ ] `BDDMockito.given().willReturn`

### Spring Test Core 🔴
- [ ] `@SpringBootTest`
- [ ] `@WebMvcTest`
- [ ] `@MockBean`
- [ ] `@Autowired MockMvc`
- [ ] `mockMvc.perform(get).andExpect(isOk())`
- [ ] `content().contentType(JSON)`
- [ ] `jsonPath("$.field").value(...)`
- [ ] `perform(post().contentType().content())`

### Spring Test Extended 🟡🟢
- [ ] `RANDOM_PORT`
- [ ] `@SpyBean`
- [ ] `@DataJpaTest`
- [ ] `jsonPath("$.list", hasSize(3))`
- [ ] `@Transactional` rollback in DataJpaTest
- [ ] `TestRestTemplate`
- [ ] `@TestConfiguration`
- [ ] `@ActiveProfiles("test")`
- [ ] Testcontainers `@Container` + `@DynamicPropertySource`
- [ ] WireMock 🟢
