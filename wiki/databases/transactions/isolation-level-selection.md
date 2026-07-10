---
id: databases-transactions-isolation-level-selection
domain: databases
category: transactions
applies_to: [postgresql, mysql]
confidence: verified
sources:
  - https://www.postgresql.org/docs/current/transaction-iso.html
  - https://dev.mysql.com/doc/refman/8.0/en/innodb-transaction-isolation-levels.html
last_verified: 2026-07-10
related: [databases-query-optimization-existence-and-count-checks, databases-schema-design-requirements-to-tables]
---

# Choosing Transaction Behavior for Concurrent Writes

## When this applies

A transaction reads data and then writes based on what it read (balance check →
debit, availability check → book, read-modify-write), or you are diagnosing lost
updates / duplicate bookings under concurrency.

## Do this

1. Know your baseline: PostgreSQL defaults to Read Committed, MySQL/InnoDB to
   Repeatable Read. At both defaults, **check-then-act on the same rows can still
   race** — two transactions both pass the check, both write.
2. Pick the narrowest tool that closes your race:

| Case | Do |
|------|----|
| Single-row read-modify-write, no precondition (counter, running total) | Atomic statement: `UPDATE t SET n = n + ? WHERE id = ?` — no explicit locking needed |
| Single-row read-modify-write **with a precondition** (reserve the last unit, debit only if balance suffices) | Fold the precondition into the statement: `UPDATE t SET stock = stock - 1 WHERE id = ? AND stock >= 1`, then check affected rows — 0 means the condition no longer holds (reject that request). Exactly one of N concurrent requests wins, at default isolation, no locks |
| Check a row, then act with logic that cannot fold into one `UPDATE`'s `WHERE` (multi-step validation, external decision between read and write) | Lock the row at read: `SELECT ... FOR UPDATE`, then act inside the same transaction |
| Insert-if-absent (unique registration) | Unique constraint + `INSERT ... ON CONFLICT` / handle duplicate-key error — an exists-check alone races |
| Invariant spans multiple rows (sum of bookings ≤ capacity) | `SERIALIZABLE` isolation with retry-on-serialization-failure, or serialize writers on one advisory/parent-row lock |
| Read a consistent snapshot across several queries (reports) | `REPEATABLE READ` (PostgreSQL) — all reads see one snapshot; no write locks needed |
| Genuinely no conflicting writers (append-only logs) | Default isolation, no locks |

3. If you raise isolation to `REPEATABLE READ`+ (PostgreSQL) or use `SERIALIZABLE`,
   **write the retry loop**: these levels abort conflicting transactions
   (serialization failure) instead of blocking; code without retry turns safety into
   user-facing errors.
4. Keep lock-holding transactions short: no external API calls, no user waits inside
   a transaction holding row locks.

## Edge cases

| Case | Then |
|------|------|
| `FOR UPDATE` on rows joined from multiple tables | Lock only the table you'll update: `FOR UPDATE OF t` — otherwise you serialize on rows you never write |
| Two transactions lock the same rows in different orders | Deadlock. Impose one global lock ordering (e.g. by table then ascending id) and batch-lock with one ordered `SELECT ... FOR UPDATE` |
| MySQL Repeatable Read + `UPDATE` based on stale snapshot reads | Updates see current rows (semi-consistent behavior differs from the read snapshot); apply the conditional-`UPDATE` row above — precondition in the `WHERE`, 0 affected rows = rejected |
| Undecided whether stock is a counter column or reservation rows summed against capacity | The data model decides the locking row: counter column → conditional `UPDATE`; reservation rows → the multi-row invariant row. Model per [databases-schema-design-requirements-to-tables] before choosing machinery |
| Queue-style "grab next unprocessed row" | `SELECT ... FOR UPDATE SKIP LOCKED LIMIT 1` — workers skip contended rows instead of queueing on them |

## Sources

- https://www.postgresql.org/docs/current/transaction-iso.html — isolation levels, serialization failures
- https://dev.mysql.com/doc/refman/8.0/en/innodb-transaction-isolation-levels.html — InnoDB level semantics
