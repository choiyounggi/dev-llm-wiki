# Change Log

Append-only. Format: `## [YYYY-MM-DD] <ingest|revise|lint|gap|contradiction|drift> | <summary>`

## [2026-07-10] ingest | Initial scaffold: schema, templates, skills, root index, domain stubs
## [2026-07-10] ingest | Seed databases domain: indexing (5), query-optimization (5), schema-design (4), transactions (1)
## [2026-07-10] ingest | schema-design +3: naming-conventions, foreign-keys-and-referential-actions, column-data-types
## [2026-07-10] lint | Blind routing audit (3 independent agents, 6 scenarios): 6/6 routable with friction — protocol circularity, scaffold-domain traps, unresolved decision forks
## [2026-07-10] revise | Protocol: load-when is the routing gate (trigger = post-load confirmation + drift log), multi-domain tiebreak by owned artifact, scaffold backtrack rule, sanctioned cross-link hops, Do-table specificity precedence
## [2026-07-10] revise | INDEX.md status column (seeded/scaffold); scaffold indexes gained until-seeded cross-pointers; 6 load-when lines realigned to page triggers
## [2026-07-10] revise | Pages: conditional-UPDATE promoted to first-class row (isolation), partial-vs-composite fork given deciding conditions (index-selection), CONCURRENTLY edge, uniqueness triggers on partial-index page, currency/NUMERIC guidance, immutability enforcement, soft-delete status/history disambiguation, keyset cap behavior, N+1 composition
## [2026-07-10] lint | Haiku validation: 6/6 scenarios solved correctly by claude-haiku agents via routing alone (0 STUCK). One deviation (BIGINT PK via unstated internal-table assumption) fixed and re-validated
## [2026-07-10] revise | primary-key-choice: exposure-undecided rule promoted into the main decision table (default UUIDv7, forbid unstated internal classification); v7 generation note added
## [2026-07-10] ingest | Seed 6 domains in parallel (39 pages): debugging (7), testing (6), frontend (8), backend (7), infrastructure (6), qa (5, new domain split from testing). All cited URLs live-verified; practice-based claims tagged field-tested
## [2026-07-10] revise | INDEX.md: 6 domains flipped to seeded, qa registered, testing/qa boundary stated both ways, security scaffold line gained cross-pointers
## [2026-07-10] ingest | Seed final 3 domains + deepen 2 (21 pages): security (6), platforms (5), mobile (5), backend auth/orm/concurrency (3, Planned section retired), frontend auth + infinite-scroll (2). JWT split: choice=security, server=backend, client=frontend. All cited URLs live-verified
## [2026-07-10] revise | INDEX.md: security/platforms/mobile flipped to seeded (all 10 domains seeded); backend/frontend route lines extended
## [2026-07-10] lint | Haiku validation wave 3: 6/6 scenarios (security authn choice, JWT server, token client, infinite scroll, platforms, mobile) solved via routing alone, 0 STUCK — incl. 3-domain hop security→backend→frontend on the authn scenario
## [2026-07-10] ingest | Add plan + implement skills: capable-model planning (decisions in plan, wiki-mapped small-model-sized tasks) and small-model execution contract (no improvisation, BLOCKED over guessing). E2E validated: planner produced a 17-task login plan (8 self-check fixes); haiku executed tasks 01 (DONE, verified) and 03 (correct BLOCKED on unrunnable psql verify — schema itself applied all 4 mapped wiki pages exactly)
