# Dependencies and Tooling — Sales Event

[Archive index](README.md) · [Project overview](../README.md)

## Go, containers, migrations, and local checks

The source declares Go 1.22.0 with a Go 1.22.12 toolchain. Make targets use `golang:1.22-alpine`, `golangci-lint:v1.62.2`, and Compose to run tests, lint, formatting, migrations, integration, and runtime builds. Lint and pre-commit checks were introduced in May. Versioned SQL migrations cover the initial schema/seeds, API keys, retry state, email events, payment intents, trace context, and correlation metadata.

The hook runs formatting/lint fixes and unit tests, stopping if automatic changes need review. The migration runner's semicolon-based splitting remains a documented limitation for more complex future SQL; introducing migrations did not resolve that parser limitation.

**References:** [May journal](../2026-05.md), [Makefile](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/Makefile), [migration runner](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/cmd/migrate/main.go).

## CI and portfolio documentation

P5.4's Sales implementation was delivered by direct commits `4c99c0c` and `22e0d44` on 2026-09-21, including creation of the external network before integration. PR #15 was closed without merging; PR #14 added final portfolio-guide links. The shared backlog reports P5.4 complete across repositories, while this archive records the Sales portion and separately verified latest CI.

At the baseline the `Test, lint and build` job runs `make test`, `make lint`, `make test-integration`, and `make build`, followed by Compose cleanup. The latest main run passed all four commands. A linter containing security rules is not a dependency audit.

**References:** [`4c99c0c`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/4c99c0c336d1e02a200ba4dd5246ec95dedbb423), [`22e0d44`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/22e0d4421e42dedd34751a1de0a7af669a2d291c), [PR #14](https://github.com/VarnerDamascenoJr/sales-event-project/pull/14), [closed PR #15](https://github.com/VarnerDamascenoJr/sales-event-project/pull/15), [baseline workflow](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/.github/workflows/ci.yml).

## Separate responsibilities within existing packages

| Area | Delivered organization | References |
| --- | --- | --- |
| HTTP and schemas | Dedicated contracts/DTOs/errors, store records, pure validation/query parsing, store-backed rules, route groups, and domain test files | [PR #23](https://github.com/VarnerDamascenoJr/sales-event-project/pull/23), [PR #24](https://github.com/VarnerDamascenoJr/sales-event-project/pull/24), [PR #25](https://github.com/VarnerDamascenoJr/sales-event-project/pull/25), [PR #26](https://github.com/VarnerDamascenoJr/sales-event-project/pull/26) |
| Messaging | Connection/topology, publishing, confirms, headers, consumption, and errors | [PR #27](https://github.com/VarnerDamascenoJr/sales-event-project/pull/27) |
| Observability | Logging/redaction/correlation/fan-out, telemetry bootstrap, HTTP/AMQP/context helpers, metrics middleware/server, and corresponding tests | [PR #28](https://github.com/VarnerDamascenoJr/sales-event-project/pull/28), [PR #35](https://github.com/VarnerDamascenoJr/sales-event-project/pull/35), [PR #36](https://github.com/VarnerDamascenoJr/sales-event-project/pull/36) |
| Analytics | Demand-series/model, funnel records/steps, shared values, simulation-prior builders, stockout inventory/estimator/probability, and DTOs | [PR #33](https://github.com/VarnerDamascenoJr/sales-event-project/pull/33), [PR #34](https://github.com/VarnerDamascenoJr/sales-event-project/pull/34) |
| Analytics database reader | Orchestration, SQL, filters, event scans, inventory reads, and interface-based tests | [PR #37](https://github.com/VarnerDamascenoJr/sales-event-project/pull/37) |

The refactors keep existing package/public contracts. PR #35 preserves HTTP metric names/labels/buckets; PR #37 reports byte-identical SQL. PR #36 also delivers the explicit empty-group handler correction, so it is not described as tests only.

## Reproducible demo command

CFX4 introduced the Go analytics generator and retained a stable shell wrapper. Configuration covers sale volume, failure mix, check-ins, email events, async polling, rate-limit retries, seed/run ID, and explicit seeded inventory preparation. Documentation includes targeted lint exceptions rather than a global disable. These source artifacts make a later rehearsal repeatable; this import did not execute them.

**References:** [PR #32](https://github.com/VarnerDamascenoJr/sales-event-project/pull/32), [October journal](../2026-10.md#2026-10-09--version-the-analytics-demo-data-generator).
