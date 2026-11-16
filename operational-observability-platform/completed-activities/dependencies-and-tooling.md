# Dependencies and Tooling — Operational Observability Platform

[Archive index](README.md) · [Project overview](../README.md)

## TypeScript/Fastify quality tooling

The application starts with Node.js 22, TypeScript, Fastify, PostgreSQL, ESLint, Prettier, and Vitest. PR #1 adds coverage tooling, compiled-API Playwright tests, and CI. `npm run check` combines lint, formatting, unit tests, API E2E, and build. Playwright here verifies HTTP API behavior, not a standalone product frontend.

**References:** [PR #1](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/1), [actual scripts and dependencies](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/package.json), [API E2E configuration](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/playwright.config.ts).

## Telemetry stack and validation scripts

Docker Compose provisions PostgreSQL, Collector, Prometheus, Tempo, Loki, and Grafana. Versioned rules/dashboards and configuration checks support a reproducible local stack; the smoke exercises ingestion, queries, provisioning, metrics, SLOs, and symptom alerts.

The control plane owns configuration/state, while the telemetry services collect/store/explore the heavy signal data. Sales and OptiFlow integrations add producer targets and dashboards with explicit source ownership.

**References:** [PR #2](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/2), [PR #9](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/9), [PR #11](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/11), [PR #14](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/14), [PR #15](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/15), [PR #16](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/16), [configuration validation](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/scripts/validate-observability.sh), [smoke scope](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/scripts/smoke-observability.sh).

## Startup readiness and module refactors

PR #12 corrects the earlier CI PostgreSQL-startup race with readiness waiting before migrations. Later refactors separate app types, SLO/incident modules, route registration, observability hooks, service identity, and shared validation/pagination helpers. This October history does not attribute a later smoke failure to the fixed startup race without evidence.

**References:** [PR #12](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/12), [PR #22](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/22), [PR #23](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/23), [PR #24](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/24), [PR #25](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/25), [PR #26](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/26), [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28), [PR #29](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/29), [PR #30](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/30).

## Actual CI and publication state

The workflow installs dependencies, runs the complete quality command, validates observability configuration, starts Compose, migrates, and executes the telemetry smoke. Failure logs and stack teardown are configured. The latest PR check passed, but the baseline's main run failed at smoke with exit code 4 after earlier steps passed.

The main badge came through direct commit `bd712ce`. PR #17's final-guide proposal closed without merge; PR #18's CI-link change merged only into that proposal's branch. These separate events should not be collapsed into one successful main-branch guide delivery.

**References:** [`bd712ce`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/bd712ce2118c7d805c61b25b759468d5616dc468), [PR #17](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/17), [PR #18](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/18), [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31), [committed workflow](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/.github/workflows/ci.yml), [CI evidence](validation-and-publication.md#latest-ci-evidence).
