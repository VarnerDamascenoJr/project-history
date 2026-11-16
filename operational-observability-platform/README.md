# Operational Observability Platform

A local operational control plane for service telemetry, SLO evaluation, symptom alerts, and guided incident investigation, with PostgreSQL state and a provisioned OpenTelemetry/Prometheus/Tempo/Loki/Grafana stack.

**Source:** [VarnerDamascenoJr/operational-observability-platform](https://github.com/VarnerDamascenoJr/operational-observability-platform)  
**Local checkout:** `/home/varner/aprendizagem/projetos/operational-observability-platform`  
**History collected:** 2026-11-15  
**Source baseline:** [`53ec569`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/53ec569fb2d43253c4e91110db297baf89213e44), the merge of [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31) into `main` on **2026-10-05** in `America/Fortaleza`.

## Reading guide

| Record | Coverage |
| --- | --- |
| [August 2026](2026-08.md) | Application foundation, quality workflow, and local telemetry stack |
| [September 2026](2026-09.md) | PostgreSQL/correlation, SLOs/alerts, incidents, portfolio telemetry, latency, and module refactors |
| [October 2026](2026-10.md) | Process control, hypothesis confidence, cursor/transaction fixes, and operational risk forecast |
| [Activity archive](completed-activities/README.md) | Four broad areas, original planning boundaries, CI evidence, and all PR records |

## Architecture and decisions

The snapshot uses Node.js 22, TypeScript, Fastify, PostgreSQL, Docker Compose, Vitest, and Playwright. The application owns configuration, evaluation history, and investigation state. The Collector, Prometheus, Tempo, Loki, and Grafana provide telemetry ingestion/storage/exploration.

- Validate correlation IDs and derive trace identity from standard W3C context; retain structured context through the demo flow.
- Apply migrations before accepting traffic, preserve applied migration checksums, and expose database readiness in health.
- Keep SLO input counts/source metadata reproducible. The evaluation API does not automatically query Prometheus just because a source is labelled `prometheus`.
- Treat rolling windows, burn rate, EWMA, and breach-probability forecasting as distinct views with explicit data/parameter limits.
- Persist incident evidence, hypotheses, confidence changes, timeline, and resolution context; apply transactional integrity and precise keyset cursors.
- Use local, loopback-bound telemetry services for the recorded demo. Portfolio producers and dashboards retain their original repository ownership.

## Latest recorded validation

PR #31 reports unit, API E2E, build, lint, formatting, and whitespace checks. Its [PR check](https://github.com/VarnerDamascenoJr/operational-observability-platform/actions/runs/37361881113) succeeded. The subsequent [main run](https://github.com/VarnerDamascenoJr/operational-observability-platform/actions/runs/37366144235), at `53ec569`, **failed in the observability smoke step with exit code 4**. Earlier quality, configuration-validation, stack-startup, and migration steps passed in that run. The inspected log does not establish a root cause or a successful later rerun.

The actual workflow runs `npm run check` (lint, formatting, unit/API E2E tests, and build), observability configuration validation, Compose startup, migrations, and the telemetry smoke. It prints logs on failure and tears down the stack. This history preserves both the successful PR check and failed main execution rather than describing the baseline as wholly green.

No application tests, infrastructure smoke, migration, or dependency audit was executed for this documentation import. Historical commands and raw-evidence references retain their dates and scope. See [validation and publication](completed-activities/validation-and-publication.md).

## Source, planning, and ownership boundaries

GitHub main and the source checkout both point to `53ec569`. The source files and branch were preserved. The API contains **31 PR records: 30 merged and one closed without merge**. Of the merged PRs, **29** are represented in the baseline by two-parent integration commits; **PR #18** exists only in an intermediate branch. **PR #17** closed without merge. The main CI badge came from a separate direct commit.

The local [implementation checklist](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/CHECKLIST.txt) contains **76 items: 42 checked and 34 unchecked**. Several unchecked incident and Sales-integration items lag delivered code/PRs. Alertmanager routing, dynamic sampling, further resilience work, and production-delivery planning remain recorded requests whose completion is not inferred here. The README's earlier next-milestone paragraph also predates delivered Sales integration.

Shared task IDs P2.1–P2.7, P4.1/P4.2/P4.4, P5.4, and S2.1–S2.6 are mapped in the [archive](completed-activities/README.md#task-sources-and-ownership). A September 16 audit note about P2.7 having no PR is preserved as dated context; the later incident PR #13 merged on September 18. P5.4's September 21 green-CI note does not supersede the observed October main failure.

The SLO/forecast inputs and controlled demo scenarios are not a population validation of incident causes or future risk. Confidence scoring is an evidence-linked ranking aid. The source's input/history contracts and operational assumptions remain authoritative.

Historical portfolio evidence refers to `/Users/varnerdamasceno/github-varner/evidence/`, unavailable here. No local report directory for this platform was found under `/home/varner/.codex/reports`. GitHub metadata and the failed-main log were inspected; raw logs/screenshots were not copied into this repository.

## Source documentation at the baseline

- [Project README](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/README.md)
- [Shared local checklist](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/CHECKLIST.txt)
- [Correlation contracts](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/correlation.md)
- [SLO, EWMA, and risk calculation contracts](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/slo-error-budget.md)
- [Incident lifecycle and confidence](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/incident-investigation.md)
- [Symptom alerts and runbooks](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/symptom-alerts.md)
- [Sales telemetry integration](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/sales-event-integration.md)
- [OptiFlow metrics integration](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/optiflow-execution-metrics.md)
- [Actual CI workflow](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/.github/workflows/ci.yml)
