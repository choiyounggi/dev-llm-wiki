# testing — Domain Index

Route here for: writing or structuring automated tests — choosing the test
level, selecting cases and assertions, test data and isolation, mock/fake
decisions, fixing flaky tests. Release-process quality (gates, manual testing,
bug triage) → wiki/qa/.

Match your situation to a "load when" line; load only matching pages.

## strategy

| Page | Load when |
|------|-----------|
| [test-level-choice](strategy/test-level-choice.md) | Deciding at which level (unit/integration/e2e) to test new or changed behavior; reviewing a test plan's level distribution; logic buried in a controller or framework wiring needs coverage |

## quality

| Page | Load when |
|------|-----------|
| [minimum-case-set](quality/minimum-case-set.md) | Writing tests for a function/endpoint/change and choosing which cases to cover; reviewing whether coverage suffices; picking boundary values by input type; adding a regression test for a bug fix |
| [behavior-not-implementation](quality/behavior-not-implementation.md) | Deciding what a test should assert; a behavior-preserving refactor broke tests; tempted to expose privates for testing; deciding whether a snapshot test is appropriate |

## data

| Page | Load when |
|------|-----------|
| [test-data-and-isolation](data/test-data-and-isolation.md) | Tests need fixture data and you are choosing how to create it; tests pass alone but fail together (or vice versa); DB cleanup, shared fixtures, time-dependent logic, or unique-value collisions |

## mocking

| Page | Load when |
|------|-----------|
| [what-to-mock](mocking/what-to-mock.md) | Deciding whether to mock/stub/fake a dependency or use the real one; mocks breaking on refactors; testing handling of a third-party's failure modes; the same mock setup is copy-pasted across tests |

## flaky

| Page | Load when |
|------|-----------|
| [diagnosing-flaky-tests](flaky/diagnosing-flaky-tests.md) | A test fails intermittently with no code change: on retry, in CI only, or only when run with other tests; deciding policy for a newly identified flaky test (quarantine vs retry) |
