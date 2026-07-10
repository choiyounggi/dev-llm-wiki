# backend/java — Stack Subtree Index

Route here for: JVM (Java/Kotlin, Spring, JPA/Hibernate) stack-specific backend
concerns. Language-agnostic principles → wiki/backend/common/ (backend domain index
routes both).

Match your situation to a "load when" line; load only matching pages. When a common
page owns the principle (transaction boundaries, async failure routing, pool sizing),
load it alongside the stack page here — these pages link the exact ids.

## jpa

| Page | Load when |
|------|-----------|
| [entity-mapping](jpa/entity-mapping.md) | Writing or reviewing JPA entity classes/associations — fetch types (to-one EAGER default), bidirectional sync helpers, entity equals/hashCode; debugging `LazyInitializationException`, `MultipleBagFetchException`, entities vanishing from Sets, or unexpected joins/queries traced to mappings; deciding DTO projection vs entity for read-only endpoints; evaluating Open Session in View |
| [persistence-context](jpa/persistence-context.md) | Debugging changes saved without calling save (dirty checking), stale reads within one transaction (first-level cache), flush timing surprises around queries, detached-entity errors (merge vs persist, lost updates after merge); designing or fixing slow/memory-hungry JPA batch inserts; choosing IDENTITY vs SEQUENCE id generation for batch-heavy tables |

## spring

| Page | Load when |
|------|-----------|
| [proxy-pitfalls](spring/proxy-pitfalls.md) | A Spring annotation (`@Transactional`/`@Async`/`@Cacheable`/`@Retryable`) silently has no effect at runtime; reviewing where such annotations are placed — self-invocation, non-public methods, final classes/methods (Kotlin), calls from constructors/`@PostConstruct`; writing tests that assert the annotation's effect |

## runtime

| Page | Load when |
|------|-----------|
| [threads-and-memory](runtime/threads-and-memory.md) | Choosing platform vs virtual threads for blocking-I/O JVM services; thread-pool exhaustion under blocking I/O; virtual-thread pinning (`synchronized`, pre-Java-24); diagnosing rising heap/old-gen (heap dumps, dominator tree), container OOMKilled without Java `OutOfMemoryError` (heap vs cgroup limit, `-Xmx` sizing), or RSS growth with stable heap (native/direct memory) |
