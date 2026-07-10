# Root Index — Domain Map

Route by matching your current task to a "route here when" line, then open that
domain's `index.md`. Load nothing else at this level.

`scaffold` domains have **no pages yet** — do not route into them expecting answers;
follow the cross-pointers in their index or take the next matching seeded domain
(routing protocol step 1, `AGENTS.md`).

| Domain | Status | Route here when |
|--------|--------|-----------------|
| [databases](wiki/databases/index.md) | **seeded** | Designing schemas/tables/keys, choosing or evaluating indexes, writing or optimizing queries, choosing transaction/isolation behavior |
| [backend](wiki/backend/index.md) | **seeded** | Server-side application code: API contracts (status codes, errors, pagination), idempotency, outbound calls (timeouts/retries), caching, background jobs, exception handling |
| [frontend](wiki/frontend/index.md) | **seeded** | Web UI code: state placement, rendering performance, in-UI data fetching, forms, XSS-safe output, accessibility |
| [infrastructure](wiki/infrastructure/index.md) | **seeded** | CI/CD pipelines, secrets in build/deploy, container image builds, rollout/rollback strategy, observability (logs/metrics/alerting) |
| [testing](wiki/testing/index.md) | **seeded** | Writing or structuring automated tests: level choice, cases/assertions, test data, mock decisions, flaky tests (release-process quality → qa) |
| [qa](wiki/qa/index.md) | **seeded** | Release-quality process: release gates, regression scoping, bug reports, severity/priority triage, exploratory testing (writing automated test code → testing) |
| [debugging](wiki/debugging/index.md) | **seeded** | Diagnosing a failure — finding what is wrong and why: reproducing, bisection, hypothesis testing, traces/logs, intermittent failures (fixing the diagnosed fault → its owning domain) |
| [security](wiki/security/index.md) | scaffold | Handling user input, authn/authz, secrets, dependencies, or anything crossing a trust boundary (XSS rendering → frontend/security; CI secrets → infrastructure/ci-cd) |
| [platforms](wiki/platforms/index.md) | scaffold | OS-specific development concerns: macOS/Windows/Linux toolchains, shells, filesystem/process differences |
| [mobile](wiki/mobile/index.md) | scaffold | Building iOS/Android/cross-platform apps: lifecycle, offline, release/store concerns |

Scaffold domains grow via `skills/ingest/SKILL.md`; flip their status to seeded on
first real page.
