# mobile — Domain Index

Route here for: app-side iOS/Android/cross-platform concerns — process lifecycle
and state survival, offline storage and sync, network calls from the device,
store releases/rollout/hotfix strategy, and startup performance. Server-side API
patterns (idempotency storage, retry contracts, error bodies) stay in the backend
domain (pages link there).

Match your situation to a "load when" line; load only matching pages.

## lifecycle

| Page | Load when |
|------|-----------|
| [process-death-and-state](lifecycle/process-death-and-state.md) | Building any screen with in-progress user state (forms, wizards, selections, media position) — choosing where each kind of state lives (saved-state vs local storage vs keychain/keystore); a bug report says "app lost my data when I switched apps"; designing deep-link/notification entry that must rebuild state on a cold process; writing a process-death test plan |

## offline

| Page | Load when |
|------|-----------|
| [offline-first-sync](offline/offline-first-sync.md) | The app must work with intermittent connectivity — reads and/or user actions offline that sync later; designing the local-store/outbox/sync architecture; choosing a conflict-resolution policy (last-write-wins vs field merge vs user resolution); debugging lost offline edits, duplicated actions after reconnect, or screens that blank out when the network drops |

## networking

| Page | Load when |
|------|-----------|
| [calls-on-mobile-networks](networking/calls-on-mobile-networks.md) | Implementing API calls in a mobile app — timeouts, failure UI states, retry-on-connectivity-restored, batching background requests for battery, payload budgets; field reports of hangs, battery drain, or timeouts that don't reproduce on office wifi; planning degraded-network testing (airplane-mode mid-request, throttled 3G) |

## release

| Page | Load when |
|------|-----------|
| [staged-rollout-and-hotfix](release/staged-rollout-and-hotfix.md) | Planning a mobile release or rollout strategy (Play staged %, App Store phased release, crash-gated widening); a critical bug shipped and you need remediation options (halt, expedited review, kill switch); designing server-side feature flags/kill switches, forced-update (minimum version), or API backward-compatibility policy for shipped app versions |

## performance

| Page | Load when |
|------|-----------|
| [startup-time](performance/startup-time.md) | Cold start feels slow or the startup metric regressed between versions; reviewing what runs at launch (Application/AppDelegate init, SDK setup, DI graph); deciding what to defer past the first frame; setting up startup measurement (Perfetto/Macrobenchmark, Instruments App Launch) or a release-gated startup metric |
