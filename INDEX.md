# Root Index — Domain Map

Route by matching your current task to a "route here when" line, then open that
domain's `index.md`. Load nothing else at this level.

| Domain | Route here when |
|--------|-----------------|
| [databases](wiki/databases/index.md) | Designing schemas/tables/keys, choosing or evaluating indexes, writing or optimizing queries, choosing transaction/isolation behavior |
| [backend](wiki/backend/index.md) | Writing server-side application code: API design, ORM usage, concurrency, caching, background jobs, service integration |
| [frontend](wiki/frontend/index.md) | Building web UI: components, state, rendering performance, forms, accessibility, browser behavior |
| [infrastructure](wiki/infrastructure/index.md) | CI/CD, containers, cloud resources, networking, observability, deploy/rollback strategy |
| [testing](wiki/testing/index.md) | Writing or reviewing tests, choosing test level (unit/integration/e2e), test data, coverage strategy, QA process |
| [debugging](wiki/debugging/index.md) | Diagnosing a failure: reproducing, isolating root cause, reading errors/logs/traces, performance investigation |
| [security](wiki/security/index.md) | Handling user input, authn/authz, secrets, dependencies, or anything crossing a trust boundary |
| [platforms](wiki/platforms/index.md) | OS-specific development concerns: macOS/Windows/Linux toolchains, shells, filesystem/process differences |
| [mobile](wiki/mobile/index.md) | Building iOS/Android/cross-platform apps: lifecycle, offline, release/store concerns |

Seeded: **databases**. Other domains are scaffolded and grow via `skills/ingest/SKILL.md`.
