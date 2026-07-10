# Root Index — Domain Map

Route by matching your current task to a "route here when" line, then open that
domain's `index.md`. Load nothing else at this level.

`scaffold` domains have **no pages yet** — do not route into them expecting answers;
follow the cross-pointers in their index or take the next matching seeded domain
(routing protocol step 1, `AGENTS.md`).

| Domain | Status | Route here when |
|--------|--------|-----------------|
| [databases](wiki/databases/index.md) | **seeded** | Designing schemas/tables/keys, choosing or evaluating indexes, writing or optimizing queries, choosing transaction/isolation behavior |
| [backend](wiki/backend/index.md) | scaffold | Writing server-side application code: API design, ORM usage, concurrency, caching, background jobs, service integration |
| [frontend](wiki/frontend/index.md) | scaffold | Building web UI: components, state, rendering performance, forms, accessibility, browser behavior |
| [infrastructure](wiki/infrastructure/index.md) | scaffold | CI/CD, containers, cloud resources, networking, observability, deploy/rollback strategy |
| [testing](wiki/testing/index.md) | scaffold | Writing or reviewing tests, choosing test level (unit/integration/e2e), test data, coverage strategy, QA process |
| [debugging](wiki/debugging/index.md) | scaffold | Diagnosing a failure: reproducing, isolating root cause, reading errors/logs/traces, performance investigation |
| [security](wiki/security/index.md) | scaffold | Handling user input, authn/authz, secrets, dependencies, or anything crossing a trust boundary |
| [platforms](wiki/platforms/index.md) | scaffold | OS-specific development concerns: macOS/Windows/Linux toolchains, shells, filesystem/process differences |
| [mobile](wiki/mobile/index.md) | scaffold | Building iOS/Android/cross-platform apps: lifecycle, offline, release/store concerns |

Scaffold domains grow via `skills/ingest/SKILL.md`; flip their status to seeded on
first real page.
