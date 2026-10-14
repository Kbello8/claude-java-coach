 # Java Drill — Syntax Trigger Reference

**Read the section for today's topic. Close before writing.**
Each entry = the exact thing you blank on cold: signature, param type, annotation attribute, structural shape.
Not concept review. Not answers. Triggers.

---

## 1. OOP

| Construct               | Anchor                                                                                                                    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| basic class             | `class Dog { private String name; public Dog(String name){ this.name = name; } public String getName(){ return name; } }` |
| `toString`              | `public String toString()`                                                                                                |
| `equals`                | `public boolean equals(Object o)` — param is `Object`, not `T`                                                            |
| `hashCode`              | `public int hashCode()`                                                                                                   |
| `static` field + method | `private static int count = 0;` · `public static void reset(){ count = 0; }`                                              |
| `final`                 | `final class X{}` · `final void m(){}` · `final int N = 10;` — class = no extend, method = no override, var = no reassign |
| ctor chaining           | `this(...)` must be **first statement**                                                                                   |
| super ctor              | `super(...)` must be **first statement**                                                                                  |
| super method            | `super.methodName(args)` — anywhere in body                                                                               |
| abstract class          | `public abstract class Animal { abstract void speak(); void breathe(){ } }`                                               |
| extend abstract         | `class Dog extends Animal { @Override public void speak(){ ... } }`                                                       |
| overloading             | same name, different params, same class — resolved at compile time                                                        |
| overriding              | same signature, subclass — resolved at runtime; requires `@Override`                                                      |
| interface               | `interface Flyable { void fly(); }` — abstract by default                                                                 |
| implements              | `class Bird implements Flyable { @Override public void fly(){ ... } }`                                                    |
| interface default       | `default void name() { }` inside interface                                                                                |
| interface static        | `static ReturnType name() { }` inside interface                                                                           |
| `@FunctionalInterface`  | exactly **one** abstract method; `default`/`static` don't count                                                           |
| lambda inline           | `MyFunctionalInterface f = x -> x * 2;` — where the type is a `@FunctionalInterface`                                      |
| enum basic              | `enum Color { RED, GREEN, BLUE }` — use: `Color.RED`                                                                      |
| enum with fields        | `enum Day { MON(1); private final int n; Day(int n){ this.n=n; } public int n(){ return n; } }`                           |
| `instanceof` + cast     | classic: `if (obj instanceof String) { String s = (String) obj; }`                                                        |
| pattern instanceof      | `if (obj instanceof String s) { s.length(); }` — `s` scoped to block                                                      |
| `compareTo`             | `public int compareTo(T o)` — neg / zero / pos                                                                            |
| `Comparable<T>`         | class declares `implements Comparable<T>`, then override `compareTo`                                                      |
| varargs                 | last param only; `String... args` is `String[]` inside                                                                    |
| `record`                | `public record Point(int x, int y) { }` — compact ctor: `public Point { /* validate, no assign */ }`                      |
| `sealed`                | `public sealed class Shape permits Circle, Square { }`                                                                    |
| `Cloneable`             | `protected Object clone() throws CloneNotSupportedException`                                                              |

---

## 2. Collections

| Construct                         | Anchor                                                                                              |
| --------------------------------- | --------------------------------------------------------------------------------------------------- |
| `ArrayList`                       | `List<String> list = new ArrayList<>();` · `add` / `get(i)` / `remove(i)` / `size()` / `contains()` |
| `List.of(...)`                    | `List.of("a","b","c")` — immutable, fixed-size, **no nulls**                                        |
| `List.copyOf(col)`                | `List.copyOf(existingCollection)` — immutable snapshot, **no nulls**                                |
| `Set.of(...)`                     | `Set.of(1,2,3)` — immutable, no nulls, no duplicates                                                |
| `Collections.unmodifiableList`    | `Collections.unmodifiableList(list)` — live view; mutations throw `UnsupportedOperationException`   |
| `Collections.unmodifiableSet/Map` | same pattern: `unmodifiableSet(set)` / `unmodifiableMap(map)`                                       |
| `HashSet`                         | `Set<String> set = new HashSet<>();` · `add` / `contains` / `remove` — no order                     |
| `HashMap` declare                 | `Map<String, Integer> map = new HashMap<>();` · `put` / `get` / `containsKey`                       |
| `getOrDefault`                    | `map.getOrDefault(key, fallback)`                                                                   |
| `putIfAbsent`                     | inserts only if absent; returns existing value if key present                                       |
| `computeIfAbsent`                 | `map.computeIfAbsent(key, k -> new ArrayList<>())` — lazy-init value                                |
| `compute`                         | `map.compute(key, (k, v) -> v == null ? 1 : v + 1)`                                                 |
| `merge`                           | `map.merge(key, 1, Integer::sum)` — accumulate                                                      |
| Map iteration                     | `for (Map.Entry<K,V> e : map.entrySet())` · `map.keySet()` · `map.values()`                         |
| `Comparator` inline               | `Comparator<Dog> c = (a, b) -> a.getName().compareTo(b.getName());`                                 |
| `Comparator.comparing`            | `Comparator.comparing(Dog::getName)`                                                                |
| `Comparator` chain                | `Comparator.comparing(X::a).thenComparing(X::b).reversed()`                                         |
| `Collections.sort`                | `Collections.sort(list)` — natural; `Collections.sort(list, comparator)` — custom                   |
| `list.sort`                       | `list.sort(Comparator.comparing(X::field))`                                                         |
| `ArrayDeque` stack                | `push` / `pop` / `peek`                                                                             |
| `ArrayDeque` queue                | `offer` / `poll` / `peek`                                                                           |
| `PriorityQueue` custom            | `new PriorityQueue<>(Comparator.comparing(X::getField))`                                            |
| `ConcurrentHashMap`               | `putIfAbsent` / `computeIfAbsent` / `compute` / `merge` — same as HashMap but thread-safe           |
| `removeEldestEntry`               | `protected boolean removeEldestEntry(Map.Entry<K,V> e){ return size() > MAX; }`                     |
| custom `Iterator<T>`              | `implements Iterator<T>` → `hasNext()` + `next()` — throw `NoSuchElementException` when done        |
| fail-fast                         | structural mod during iteration → `ConcurrentModificationException`                                 |

---

## 3. Functional

### Lambda Syntax

| Construct | Anchor |
|---|---|
| no params | `() -> "hello"` · `() -> { ... }` |
| one param | `x -> x * 2` — no parens needed for single param |
| multiple params | `(a, b) -> a + b` — parens required |
| block body | `x -> { int r = x * 2; return r; }` — braces + explicit `return` |
| static method ref | `ClassName::staticMethod` — e.g. `Integer::parseInt` |
| bound instance ref | `obj::instanceMethod` — `myList::add` |
| unbound instance ref | `String::toUpperCase` — instance becomes first arg |
| constructor ref | `ArrayList::new` — `() -> new ArrayList<>()` equivalent |

### Functional Interfaces

| Construct | Anchor |
|---|---|
| `Supplier<T>` | `T get()` |
| `Consumer<T>` | `void accept(T t)` — `.andThen(other)` |
| `Predicate<T>` | `boolean test(T t)` — `.and()` / `.or()` / `.negate()` |
| `Function<T,R>` | `R apply(T t)` — `.andThen(f)` applies after; `.compose(f)` applies before |
| `UnaryOperator<T>` | `Function<T,T>` — same in and out |
| `BinaryOperator<T>` | `BiFunction<T,T,T>` |

### Streams — Creation

| Construct | Anchor |
|---|---|
| from collection | `list.stream()` |
| from array | `Arrays.stream(array)` |
| from values | `Stream.of("a","b","c")` |
| `IntStream.range` | `IntStream.range(0, n)` — exclusive end; `rangeClosed` inclusive |

### Streams — Intermediate Operations

| Construct | Anchor |
|---|---|
| `filter` | `filter(x -> x > 0)` — keeps matching elements |
| `map` | `map(String::toUpperCase)` — transforms each element |
| `mapToInt/Long/Double` | `mapToInt(String::length)` — produces primitive stream |
| `flatMap` | `Function<T, Stream<R>>` — one-to-many, flattens one level |
| `distinct` | removes duplicates (uses `equals`) |
| `sorted` | `sorted()` — natural order; `sorted(Comparator)` — custom |
| `limit` / `skip` | `limit(n)` — first n; `skip(n)` — drop first n |

### Streams — Terminal Operations

| Construct | Anchor |
|---|---|
| `forEach` | `forEach(System.out::println)` — no return value |
| `count` | `count()` — returns `long` |
| `min` / `max` | `min(Comparator.naturalOrder())` → `Optional<T>` |
| `findFirst` / `findAny` | → `Optional<T>`; `findAny` non-deterministic in parallel |
| `anyMatch` / `allMatch` / `noneMatch` | `anyMatch(x -> x > 0)` → `boolean`; short-circuits |
| `collect toList` | `collect(Collectors.toList())` · `Collectors.toUnmodifiableList()` |
| `collect toSet` | `collect(Collectors.toSet())` |
| `collect toMap` | `collect(Collectors.toMap(k -> k.getId(), v -> v))` — basic |
| `toMap` merge fn | `toMap(k, v, (a, b) -> a)` — 3rd arg handles duplicate keys |
| `groupingBy` | `groupingBy(Person::getDept)` → `Map<String, List<Person>>` |
| `groupingBy` + downstream | `groupingBy(Person::getDept, counting())` → `Map<String, Long>` |
| `partitioningBy` | `Map<Boolean, List<T>>` — always both keys present |
| `joining` | `joining(", ", "[", "]")` — delim, prefix, suffix |
| `reduce` 2-arg | `reduce(identity, BinaryOperator)` — identity = neutral (0 for sum) |
| `reduce` 1-arg | returns `Optional<T>` — no identity, empty stream = empty |
| IntStream terminals | `sum()` · `average()` → `OptionalDouble` · `min()` · `max()` |
| `.boxed()` | `IntStream → Stream<Integer>` |

### Optional

| Construct | Anchor |
|---|---|
| `Optional.of` | NPE if null — use `ofNullable` unless you know it's non-null |
| `Optional.ofNullable` | safe; wraps null as `empty()` |
| `Optional.empty` | `Optional.empty()` — explicit empty |
| `isPresent` / `isEmpty` | `isPresent()` — true if value; `isEmpty()` Java 11+ |
| `get` | throws `NoSuchElementException` if empty — almost always wrong; use `orElse*` |
| `orElse` vs `orElseGet` | `orElse(val)` always evaluates arg; `orElseGet(supplier)` lazy |
| `orElseThrow` | `orElseThrow(() -> new NotFoundException("..."))` |
| `map` | transform value if present; stays empty if not |
| `flatMap` | mapper returns `Optional<R>` — avoids `Optional<Optional<R>>` |
| `filter` | keep value only if predicate is true; otherwise empty |
| `ifPresent` | `ifPresent(val -> doSomething(val))` — side effect only if present |

---

## 4. Spring Boot

### Application & Wiring

| Construct | Anchor |
|---|---|
| main class | `@SpringBootApplication public class App { public static void main(String[] args){ SpringApplication.run(App.class, args); } }` |
| stereotype annotations | `@Component` generic · `@Service` business · `@Repository` data + exception translation · `@Controller` MVC · `@RestController` = `@Controller + @ResponseBody` |
| constructor injection | `private final X x; public MyService(X x){ this.x = x; }` — omit `@Autowired` if single-constructor |
| field injection | `@Autowired private X x;` — avoid; hides dependencies, needs reflection |
| `@Qualifier` | `@Qualifier("beanName")` alongside `@Autowired` — disambiguates multiple candidates |
| `@Bean` | `@Configuration class AppConfig { @Bean MyBean myBean(){ return new MyBean(); } }` |
| `@Bean` param inject | method params auto-resolved by Spring type — no annotation needed |
| `@Value` | `@Value("${property.key}")` — inject property |
| `@Value` default | `@Value("${key:defaultValue}")` — colon separator |
| `@ConfigurationProperties` | `@Component` + `@ConfigurationProperties(prefix="app")` + fields match yaml keys |
| `@PostConstruct` | `void init()` — after DI complete; no params · `@PreDestroy` before bean removed |
| `@Async` caveat | must be `public`; must be called from OUTSIDE the class (same proxy rule as `@Transactional`) |

### REST Controllers

| Construct | Anchor |
|---|---|
| class-level | `@RestController @RequestMapping("/api/v1/resource")` |
| GET by id | `@GetMapping("/{id}") public ResponseEntity<T> get(@PathVariable Long id)` |
| GET with param | `@GetMapping public ResponseEntity<List<T>> list(@RequestParam(required=false, defaultValue="0") int page)` |
| POST | `@PostMapping public ResponseEntity<T> create(@RequestBody @Valid MyDto dto)` |
| PUT | `@PutMapping("/{id}") public ResponseEntity<T> update(@PathVariable Long id, @RequestBody MyDto dto)` |
| DELETE | `@DeleteMapping("/{id}") public ResponseEntity<Void> delete(@PathVariable Long id)` |
| PATCH | `@PatchMapping("/{id}")` |
| `ResponseEntity` | `.ok(body)` / `.status(HttpStatus.CREATED).body(x)` / `.noContent().build()` |
| `@RestControllerAdvice` | class-level; handler: `@ExceptionHandler(X.class) public ResponseEntity<?> handle(X e)` |

### Transactions

| Construct | Anchor |
|---|---|
| `@Transactional` | on service method; wraps in DB transaction; unchecked exception → rollback |
| `@Transactional(readOnly=true)` | optimization for SELECT-only methods; no dirty-check overhead |
| `@Transactional(rollbackFor=...)` | `rollbackFor = SomeCheckedException.class` — rollback on checked exception |
| `REQUIRES_NEW` | suspends outer tx; new independent tx; outer resumes after inner commits/rolls back |
| self-invoke | `this.method()` bypasses proxy → no transaction; inject self or restructure |

### Spring Security (Extended — read shape, no cold-write required)

| Construct | Anchor |
|---|---|
| `SecurityFilterChain` | `http.authorizeHttpRequests(a -> a.requestMatchers("/admin/**").hasRole("ADMIN").anyRequest().authenticated())` |
| `UserDetailsService` | `UserDetails loadUserByUsername(String username) throws UsernameNotFoundException` |

---

## 5. SQL / JPA

### SQL Core

| Construct | Anchor |
|---|---|
| basic select | `SELECT col1, col2 FROM table WHERE condition ORDER BY col DESC LIMIT n` |
| INNER JOIN | `INNER JOIN t2 ON t1.id = t2.fk_id` — only rows with match on both sides |
| LEFT JOIN | `LEFT JOIN t2 ON t1.id = t2.fk_id` — all left rows; NULL for right if no match |
| RIGHT JOIN | `RIGHT JOIN t2 ON t1.id = t2.fk_id` — all right rows; NULL for left if no match |
| GROUP BY + aggregates | `GROUP BY dept` · `COUNT(*)` / `SUM(col)` / `AVG(col)` / `MAX(col)` / `MIN(col)` |
| HAVING | `HAVING COUNT(*) > 1` — filter on aggregated result; WHERE can't use aggregates |
| IN / NOT IN | `WHERE id IN (SELECT id FROM other WHERE ...)` |
| CASE WHEN | `CASE WHEN x > 0 THEN 'pos' WHEN x < 0 THEN 'neg' ELSE 'zero' END` |
| `COALESCE` | first non-null arg |
| `NULLIF(a,b)` | returns null if `a = b`, else `a` |

### SQL Extended (read shape)

| Construct | Anchor |
|---|---|
| window `ROW_NUMBER` | `ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC)` |
| window running total | `SUM(amount) OVER (PARTITION BY dept ORDER BY date ROWS UNBOUNDED PRECEDING)` |
| `LAG` / `LEAD` | `LAG(col, 1, defaultVal) OVER (ORDER BY date)` |
| CTE | `WITH cte AS (SELECT ...) SELECT * FROM cte WHERE ...` |
| upsert | `INSERT INTO t(...) VALUES(...) ON CONFLICT (col) DO UPDATE SET col = EXCLUDED.col` |
| correlated subquery | references outer column; re-evaluated per outer row; use `EXISTS` for membership |

### JPA / Hibernate

| Construct | Anchor |
|---|---|
| entity declaration | `@Entity @Table(name="devices") public class Device { ... }` |
| `@Column` | `@Column(name="ip_address", nullable=false, unique=true)` |
| `@Id` + `@GeneratedValue` | `@Id @GeneratedValue(strategy=GenerationType.IDENTITY) private Long id;` |
| `@Enumerated` | `@Enumerated(EnumType.STRING)` — always STRING; ORDINAL breaks on reorder |
| `@ManyToOne` | `@ManyToOne(fetch=FetchType.LAZY) @JoinColumn(name="fk_col", nullable=false)` |
| `@OneToMany` | `@OneToMany(mappedBy="fieldName", cascade=CascadeType.ALL, orphanRemoval=true) private List<T> items = new ArrayList<>();` |
| `JpaRepository` | `@Repository public interface DeviceRepo extends JpaRepository<Device, Long> { }` |
| derived query | `findByEmailAndActiveTrue(String email)` — Spring parses at startup; typo = startup error |
| `@Query` JPQL | `@Query("SELECT u FROM User u WHERE u.email = :email") User find(@Param("email") String e);` |
| `@Query` native | `@Query(value="SELECT ...", nativeQuery=true)` |
| `@Modifying` | required on `@Query` for UPDATE/DELETE; pair with `@Transactional` |
| LAZY vs EAGER | LAZY = load on access (default for collections); EAGER = always JOIN; LAZY risks `LazyInitializationException` after session closes |
| N+1 fix | `JOIN FETCH u.orders` in JPQL, or `@EntityGraph(attributePaths={"orders"})` on repo method |
| `@Version` | `private Integer version;` — Hibernate increments on UPDATE; conflict → `OptimisticLockException` |
| `PageRequest` | `PageRequest.of(0, 20, Sort.by("fieldName").descending())` |

---

## 6. Testing

### JUnit 5

| Construct | Anchor |
|---|---|
| `@Test` | `@Test void shouldReturnX()` — descriptive name |
| `@BeforeEach` | `@BeforeEach void setUp()` — runs before each test method |
| `@AfterEach` | `@AfterEach void tearDown()` — runs after each test method |
| `@BeforeAll` | `@BeforeAll static void initAll()` — once before all; must be **static** |
| `@AfterAll` | `@AfterAll static void cleanAll()` — once after all; must be **static** |
| `@DisplayName` | `@DisplayName("should throw when id is null")` — human-readable in output |
| `@Disabled` | `@Disabled("not implemented yet")` — skips test |
| `assertEquals` | `assertEquals(expected, actual)` — **expected first**, actual second |
| `assertNull` / `assertNotNull` | `assertNull(result)` · `assertNotNull(result)` |
| `assertTrue` / `assertFalse` | `assertTrue(result.isEmpty())` |
| `assertThrows` | `assertThrows(X.class, () -> method())` — returns the exception for further assertions |
| `assertAll` | all lambdas run even if one fails — use for multi-field validation |
| `@ParameterizedTest` | `@ParameterizedTest @ValueSource(ints={1,2,3}) void test(int n)` — runs once per value |
| `@MethodSource` | static method returns `Stream<Arguments>`; matched by name if not specified |

### Mockito

| Construct | Anchor |
|---|---|
| `@ExtendWith` | `@ExtendWith(MockitoExtension.class)` on test class |
| `@Mock` | `@Mock SomeService service` — creates mock; injected via `@InjectMocks` |
| `@InjectMocks` | `@InjectMocks MyController controller` — real instance, mocks injected |
| `when().thenReturn` | `when(mock.method(arg)).thenReturn(value)` |
| `any()` matcher | `when(mock.method(any())).thenReturn(value)` — matches any arg |
| `thenThrow` | `when(mock.method(any())).thenThrow(new RuntimeException())` |
| `verify` | `verify(mock).method(expectedArg)` — assert called once |
| `verify times` | `verify(mock, times(2)).method(any())` |
| `verify never` | `verify(mock, never()).method(any())` |
| `@Spy` stub rule | `doReturn(val).when(spy).method()` — NOT `when(spy.method()).thenReturn(val)` (calls real) |
| `ArgumentCaptor` | `verify(mock).method(captor.capture()); captor.getValue()` after verify |
| `InOrder` | `InOrder o = inOrder(a,b); o.verify(a).m1(); o.verify(b).m2()` |

### Spring Boot Testing

| Construct | Anchor |
|---|---|
| `@SpringBootTest` | loads full application context — use for integration tests |
| `@WebMvcTest` | `@WebMvcTest(MyController.class)` — controller layer only; service/repo not in context |
| `@MockBean` | `@MockBean SomeService service` — Mockito mock registered as Spring bean |
| `MockMvc` inject | `@Autowired MockMvc mockMvc` — available in `@WebMvcTest` |
| GET request | `mockMvc.perform(get("/api/resource")).andExpect(status().isOk())` |
| POST request | `perform(post("/url").contentType(APPLICATION_JSON).content(jsonString))` |
| content type | `.andExpect(content().contentType(MediaType.APPLICATION_JSON))` |
| `jsonPath` | `.andExpect(jsonPath("$.field").value("x"))` — `$` = root; `$.list[0]` = array index |
| `@DataJpaTest` | H2 + JPA; `@Transactional` by default → rolls back; no web layer |
| Testcontainers | `@Container static PostgreSQLContainer<?> db = new PostgreSQLContainer<>("postgres:15")` + `@DynamicPropertySource static void props(DynamicPropertyRegistry r)` |

---

## 7. Concurrency

| Construct | Anchor |
|---|---|
| Thread extend | `class MyThread extends Thread { @Override public void run(){ ... } } new MyThread().start();` |
| Thread runnable | `Thread t = new Thread(() -> { /* work */ }); t.start();` |
| `synchronized` method | `public synchronized void increment(){ count++; }` — locks on `this` |
| `synchronized` block | `synchronized(lockObject){ /* critical section */ }` — prefer explicit lock object |
| `volatile` | visibility across threads — NOT atomicity; no compound ops |
| `AtomicInteger` | `incrementAndGet()` / `compareAndSet(expect, update)` / `getAndUpdate(x -> x*2)` |
| `ExecutorService` fixed | `Executors.newFixedThreadPool(4)` |
| `ExecutorService` cached | `Executors.newCachedThreadPool()` — grows/shrinks; reuses idle threads |
| `ExecutorService` single | `Executors.newSingleThreadExecutor()` — one thread; tasks queued sequentially |
| `Callable<T>` | `public T call() throws Exception` — submit to executor, get `Future<T>` |
| `Future` | `Future<String> f = executor.submit(() -> "result"); String val = f.get();` — blocks until done |
| `Future.get()` | blocks until done; wraps cause in `ExecutionException`; can timeout |
| shutdown pattern | `es.shutdown(); es.awaitTermination(60, TimeUnit.SECONDS);` |
| CF chain shape | `supplyAsync(() -> fetch())` → `thenApply(r -> transform(r))` → `thenAccept(r -> save(r))` |
| `exceptionally` | `cf.exceptionally(ex -> defaultValue)` — catches any exception in chain; returns new value |
| `ReentrantLock` | `lock(); try { ... } finally { unlock(); }` — always unlock in finally |
| `tryLock` | `lock.tryLock(1, TimeUnit.SECONDS)` |
| `CountDownLatch` | `new CountDownLatch(n)` → workers call `countDown()` → waiter calls `await()` |
| `CyclicBarrier` | `new CyclicBarrier(n, barrierAction)` → all call `await()` → action runs → reusable |
| `Semaphore` | `new Semaphore(n)` → `acquire()` (blocks if 0 permits) → `release()` |
| `ThreadLocal` | `set(v)` / `get()` / `remove()` — **must call remove() in thread pools** or leak |
| CF `thenCompose` | `T → CompletableFuture<U>` — flatMap for async; avoids `CF<CF<U>>` |
| CF `handle` | `(result, ex) -> ...` — always fires; either may be null; returns new value |
| CF `allOf` | returns `CF<Void>`; call `.join()` on each future after `allOf(...).join()` to get values |

---

## 8. Design Patterns

> **Shape** = what to create and how pieces connect. Close, then write from memory.

### Creational

| Pattern | Shape | Key anchor |
|---|---|---|
| **Singleton (eager)** | `private static final X INSTANCE = new X();` · `private X(){}` · `public static X getInstance(){ return INSTANCE; }` | initialized at class load; thread-safe; simplest |
| **Builder** | outer: `private Outer(Builder b){ this.field = b.field; }` · inner: `static class Builder { String field; Builder field(String v){ field=v; return this; } Outer build(){ return new Outer(this); } }` | caller: `new X.Builder().name("a").age(1).build()` — each setter returns `this` |
| **Singleton (DCL)** | field: `private static volatile X instance;` · `getInstance()` checks null → `synchronized(X.class)` → checks null again → `new X()` | `volatile` required — without it second check can see half-constructed object |
| **Singleton (enum)** | `public enum X { INSTANCE; public void op(){} }` | access: `X.INSTANCE.op()` — serialization + thread-safe for free |
| **Factory Method** | abstract `Creator` class with `abstract Product create()` + concrete method that uses it · concrete `ConcreteCreator extends Creator` overrides `create()` | subclass decides what to instantiate |

### Structural

| Pattern | Shape | Key anchor |
|---|---|---|
| **Adapter** | `interface Target { void request(); }` · `class Adaptee { void specificRequest(); }` · `class Adapter implements Target { Adaptee a; void request(){ a.specificRequest(); } }` | wraps incompatible class; client uses Target; never touches Adaptee directly |
| **Decorator** | `interface Component { String op(); }` · `class Real implements Component` · `class Decorator implements Component { Component wrapped; String op(){ return wrapped.op() + extra; } }` | same interface in and out; stackable; composition not inheritance |
| **Facade** | `class Facade { SubA a; SubB b; void doThing(){ a.step1(); b.step2(); } }` | one entry point; hides subsystem; does NOT implement subsystem interface |
| **Proxy** | same interface as real subject · `class Proxy implements Subject { Subject real; void request(){ /* check/log/auth */ real.request(); } }` | controls access; client can't tell it's a proxy |

### Behavioral

| Pattern | Shape | Key anchor |
|---|---|---|
| **Strategy** | `interface Strategy { void execute(); }` · `class Context { Strategy s; void doWork(){ s.execute(); } void setStrategy(Strategy s){ this.s=s; } }` · impls: `class FastSort implements Strategy` | algorithm behind interface; Context has no conditionals; swap impl at runtime |
| **Observer** | `interface Observer { void update(Object data); }` · `class Subject { List<Observer> obs = new ArrayList<>(); void add(Observer o); void notify(){ obs.forEach(o -> o.update(data)); } }` | Subject knows only the Observer interface; decouples event source from handlers |
| **Template Method** | `abstract class Game { final void play(){ init(); startPlay(); endPlay(); } abstract void init(); abstract void startPlay(); void endPlay(){ /* default */ } }` | `final` on `play()` = fixed skeleton; abstract = mandatory hooks; `protected` = optional |
| **Command** | `interface Command { void execute(); }` · `class Save implements Command { Editor e; void execute(){ e.save(); } }` · `class Invoker { List<Command> history; void run(Command c){ c.execute(); history.add(c); } }` | action as object; enables undo queue |
| **State** | `interface State { void handle(Context ctx); }` · `class Context { State state; void request(){ state.handle(this); } setState(State s){ this.state=s; } }` · each State changes `ctx.setState(nextState)` | eliminates giant if/switch on state |

---

## 9. Exceptions

| Construct | Anchor |
|---|---|
| hierarchy | `Throwable` → `Error` (don't catch) / `Exception` → `RuntimeException` (unchecked) |
| `try-catch-finally` | `try { ... } catch (IOException e) { ... } finally { /* always runs */ }` |
| multi-catch | `catch (IOException \| SQLException e)` — `e` is effectively final |
| `try-with-resources` | `try (InputStream is = new FileInputStream(f)) { ... }` — `close()` called automatically; class must implement `AutoCloseable` |
| custom checked | `class ServiceException extends Exception { public ServiceException(String msg, Throwable cause){ super(msg, cause); } }` |
| custom unchecked | `class NotFoundException extends RuntimeException` — same ctor pattern |
| with cause | `throw new ServiceException("msg", originalException)` — wraps root cause |
| re-throw wrapped | `catch (IOException e) { throw new ServiceException("Context msg", e); }` |
| `throws` | on method signature: `public void foo() throws IOException` — checked only |
| `AutoCloseable` | `void close() throws Exception` — resources closed in **reverse** declaration order |
| suppressed | `e.getSuppressed()` on primary exception — populated when `close()` throws during try-with-resources |
| `finally` skips | `System.exit()` / JVM crash / infinite loop before `finally` |

---

## 10. Generics

| Construct | Anchor |
|---|---|
| generic class | `class Box<T> { private T value; public Box(T v){ this.value=v; } public T get(){ return value; } }` |
| generic interface | `interface Transformer<T, R> { R transform(T input); }` |
| generic method | `public <T> List<T> repeat(T item, int n)` — `<T>` **before** return type |
| generic utility | `public <T> List<T> repeat(T item, int n){ List<T> r = new ArrayList<>(); for(int i=0;i<n;i++) r.add(item); return r; }` |
| bounded param | `<T extends Comparable<T>>` |
| multiple bounds | `<T extends Serializable & Comparable<T>>` — class first, interfaces after |
| upper wildcard | `List<? extends Number>` — read out (producer); can't add to it |
| lower wildcard | `List<? super Integer>` — write in (consumer); can add Integer or subtype |
| PECS | **P**roducer **E**xtends (read), **C**onsumer **S**uper (write) |
| `Class<T>` workaround | `T obj = clazz.getDeclaredConstructor().newInstance()` |
| type erasure | `List<String>` and `List<Integer>` are same type at runtime; can't `instanceof List<String>` |
