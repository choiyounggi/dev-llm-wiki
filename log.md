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
