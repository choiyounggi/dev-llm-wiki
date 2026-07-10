# backend — Domain Index

Route here for: server-side application code — API design, ORM usage, concurrency,
caching, background jobs, service integration.

No pages yet. Grow this domain via `skills/ingest/SKILL.md`.

Until seeded, the databases domain covers the DB-facing half of several of these
topics — cross-pointers below.

Planned categories (create on first ingest that fits):

| Category | Will cover |
|----------|-----------|
| api-design | Endpoint shape, versioning, pagination contracts, error responses, idempotency (until seeded: pagination mechanics → `databases/query-optimization/keyset-pagination`) |
| orm-usage | Mapping patterns, transaction boundaries in app code, batching (until seeded: N+1 and batching → `databases/query-optimization/n-plus-one-queries`) |
| concurrency | Shared state, async patterns, thread pools, backpressure (until seeded: DB-side concurrency → `databases/transactions/isolation-level-selection`) |
| caching | Cache keys, invalidation triggers, stampede protection, TTL choice |
| background-jobs | Queues, retries, idempotent handlers, scheduling |
| performance | Hot-path memory/CPU patterns (allocation, loop structure, cache locality) |
