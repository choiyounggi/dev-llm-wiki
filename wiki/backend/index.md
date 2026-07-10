# backend — Domain Index

Route here for: server-side application code — API contracts (status codes,
error bodies, retries, pagination), outbound service calls, caching, background
jobs/queue consumers, exception-handling structure, server-side auth token
handling (JWT issuance/refresh/revocation), transaction boundary placement in
application code, and in-process shared state/pool sizing. SQL, index, and
DB-side transaction/locking mechanics stay in the databases domain (pages link
there).

Match your situation to a "load when" line; load only matching pages.

## api-design

| Page | Load when |
|------|-----------|
| [error-responses](api-design/error-responses.md) | Designing or reviewing API error handling — choosing status codes (400/401/403/404/409/422/500), defining the error body shape, deciding what a 500 may reveal; clients report inconsistent/unparseable errors |
| [idempotency](api-design/idempotency.md) | An endpoint with side effects (create, charge, send) can receive the same request twice — client retry after timeout, user double-submit, gateway retry; designing idempotency-key storage; deciding which operations are safe to retry |
| [pagination-contract](api-design/pagination-contract.md) | Designing a list endpoint's request/response contract — cursor vs page-number, limit caps, total counts, expired-cursor behavior (the backing SQL/index → databases/query-optimization/keyset-pagination) |

## reliability

| Page | Load when |
|------|-----------|
| [timeouts-and-retries](reliability/timeouts-and-retries.md) | Your service calls another service/external API/DB over the network — setting timeouts and deadlines, deciding what to retry per failure type, backoff/jitter, capping concurrency against a slow dependency; debugging pool exhaustion or retry storms |

## caching

| Page | Load when |
|------|-----------|
| [invalidation-and-stampede](caching/invalidation-and-stampede.md) | Adding a cache in front of an expensive read — choosing invalidation (delete-on-write vs TTL), building cache keys (tenant/locale/version dimensions), protecting hot keys from stampede; debugging stale reads, cross-tenant leaks, or expiry-time load spikes |

## jobs

| Page | Load when |
|------|-----------|
| [idempotent-handlers](jobs/idempotent-handlers.md) | Writing a queue consumer, background job, or scheduled task — surviving at-least-once redelivery, dedupe by message id, transactional outbox for enqueue-with-DB-write, poison messages/DLQ, checkpointing long jobs; debugging duplicate side effects from jobs |

## errors

| Page | Load when |
|------|-----------|
| [exception-handling](errors/exception-handling.md) | Writing a catch block or deciding where errors are handled/logged/translated in a service — catch placement, log-once, wrapping with cause preserved, typed results for expected outcomes; one fault producing duplicate alerts |

## auth

| Page | Load when |
|------|-----------|
| [jwt-server-side](auth/jwt-server-side.md) | Implementing or reviewing JWT issuance/verification on the server — choosing the signing algorithm (HS256 vs RS256/ES256/EdDSA), the per-request verification checklist (alg allowlist, exp/nbf, iss/aud, typ), access/refresh token lifetimes, refresh-token storage and rotation with reuse detection, revocation on logout/password change, deciding what goes in claims (the session-vs-token choice lives in wiki/security/authn/; client-side token storage in wiki/frontend/) |

## orm

| Page | Load when |
|------|-----------|
| [transaction-boundaries](orm/transaction-boundaries.md) | Deciding where a DB transaction starts/ends in application code — service vs controller vs per-repository-call boundaries, what belongs inside (external calls and slow computation out), @Transactional-style annotation/proxy pitfalls (self-invocation, method visibility, rollback-only propagation), read-only flags, chunking batch writes; debugging partial writes or connection-pool exhaustion around open transactions |

## concurrency

| Page | Load when |
|------|-----------|
| [shared-state-and-pools](concurrency/shared-state-and-pools.md) | Request handlers share in-process mutable state (caches, counters, maps) — choosing concurrency-safe structures/confinement vs pushing correctness-bearing state to the shared store in multi-instance deployments; sizing thread pools and connection pools; deadlocks from holding one pooled resource while acquiring another; bounding in-memory queues; debugging deadlock or starvation under load |
