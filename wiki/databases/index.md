# databases — Domain Index

Route here for: schema/table/key design, index decisions, query writing and
optimization, transaction/concurrency behavior.

Match your situation to a "load when" line; load only matching pages.

## indexing

| Page | Load when |
|------|-----------|
| [index-selection](indexing/index-selection.md) | Deciding whether a column/query deserves an index; a query is slow and you suspect a missing index |
| [composite-index-column-order](indexing/composite-index-column-order.md) | Creating a multi-column index; choosing column order for equality + range/sort queries |
| [covering-indexes](indexing/covering-indexes.md) | An indexed query still reads the table heavily; considering INCLUDE/index-only scans |
| [partial-and-expression-indexes](indexing/partial-and-expression-indexes.md) | Queries always filter a fixed rare condition (status, deleted_at) or a function of a column (lower(email)) |
| [index-write-cost](indexing/index-write-cost.md) | Adding indexes to write-heavy tables; bulk loads; auditing for unused/redundant indexes |

## query-optimization

| Page | Load when |
|------|-----------|
| [reading-execution-plans](query-optimization/reading-execution-plans.md) | Any slow query; verifying an index/query change with EXPLAIN before shipping |
| [keyset-pagination](query-optimization/keyset-pagination.md) | Implementing pagination, infinite scroll, or batch table walks |
| [large-in-lists](query-optimization/large-in-lists.md) | Building `IN (...)` queries whose list size can grow (batch lookups, fetch-by-ids) |
| [n-plus-one-queries](query-optimization/n-plus-one-queries.md) | Loading a list plus per-row associations via an ORM; query count scales with result size |
| [existence-and-count-checks](query-optimization/existence-and-count-checks.md) | Writing "is there any…", counts, badges, or gating logic on row presence |

## schema-design

| Page | Load when |
|------|-----------|
| [requirements-to-tables](schema-design/requirements-to-tables.md) | Turning feature requirements into tables, columns, and relationships |
| [primary-key-choice](schema-design/primary-key-choice.md) | Choosing PK type (sequence vs UUID); ids exposed publicly; MySQL clustered-index concerns |
| [nullability-and-defaults](schema-design/nullability-and-defaults.md) | Declaring column nullability/defaults; queries dropping rows around NULLs |
| [soft-delete](schema-design/soft-delete.md) | Records must be restorable/auditable; designing or debugging deleted_at schemas |

## transactions

| Page | Load when |
|------|-----------|
| [isolation-level-selection](transactions/isolation-level-selection.md) | Check-then-act writes, lost updates, duplicate bookings, choosing isolation/locking |
