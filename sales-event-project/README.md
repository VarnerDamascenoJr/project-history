# Sales Event

An event-driven ticket sales backend covering asynchronous reservations, payments, ticket issuance, email delivery, check-in, distributed observability, and operational analytics for React Dash and OptiFlow.

**Source:** [VarnerDamascenoJr/sales-event-project](https://github.com/VarnerDamascenoJr/sales-event-project)

**Local checkout:** `/home/varner/github/sales-event-project`

**History collected:** 2026-11-10

**Source baseline:** [`d542ee3`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d542ee346bcd3ededc746b6cb31cec33ee7d0eac), the integration of [PR #37](https://github.com/VarnerDamascenoJr/sales-event-project/pull/37) into `main` on **2026-10-14** in `America/Fortaleza`.

## Reading guide

| Record | Coverage |
| --- | --- |
| [May 2026](2026-05.md) | Original sales backend, payments, tickets, outbox, check-in, retention, migrations, and access controls |
| [June 2026](2026-06.md) | Architecture, domain, operational documentation, and agent guide |
| [August 2026](2026-08.md) | Initial OpenTelemetry implementation before its September integration |
| [September 2026](2026-09.md) | Correlation, dedicated retry worker, reliable publication, failure demos, portfolio integration, statistical exports, and HTTP refactors |
| [October 2026](2026-10.md) | Analytics corrections, demo generator, responsibility splits, and observability/database-reader coverage |
| [Activity archive](completed-activities/README.md) | Four broad areas with original task identifiers and delivery boundaries |
| [Integration register](completed-activities/validation-and-publication.md#delivery-register) | All 36 merged PRs, local merge dates, target branches, integration commits, and available checks |

Only months containing source work have journals. The November collection date does not imply a November application delivery.

## Technical context and decisions

Go 1.22, Gin, PostgreSQL through `pgx/v5`, and RabbitMQ form the backend. Separate API, sales/ticket worker, email retry worker, and migration commands run through Docker Compose. Prometheus, Loki, Promtail, Grafana, and optional OpenTelemetry/OTLP provide observability. There is no frontend in this source repository.

- Accept `POST /sales` asynchronously; a successful acceptance does not mean the worker has persisted the sale or reserved inventory yet.
- Reserve inventory before payment, restore it on failed payment, and record completion/failure events transactionally in the outbox.
- Issue QR tickets after `SALE_COMPLETED`; use persisted state and uniqueness constraints for replay and duplicate check-in handling.
- Publish with RabbitMQ confirms and `mandatory=true`; unbound routes, negative acknowledgements, and confirmation errors keep outbox events in retry/dead-letter processing.
- Run email retries in a dedicated process while retaining the existing five-attempt policy, capped exponential backoff, and locking behavior.
- Preserve request, correlation, transaction, and W3C trace context across HTTP, RabbitMQ, outbox, workers, and logs.
- Keep `sales-event-optiflow-export.v1` planning history separate from the statistical `sales-analytics-export.v1` contract. Share analytics database reading between CLI and HTTP.
- Expose uncertainty through funnel intervals/posteriors, censored timing observations, temporal demand evaluation, stockout estimates, and simulation priors. These are documented baselines, not new research conclusions.
- Serialize analytics JSON before sending HTTP 200; sanitize non-finite numbers and return a contextual, safe HTTP 500 on remaining serialization failures.

## Latest recorded validation

[PR #37](https://github.com/VarnerDamascenoJr/sales-event-project/pull/37) reports a shuffled full Go test run through Docker and **100% statement coverage for `internal/analyticsdb`**. Database-reader tests use `Queryer`/`pgx.Rows` doubles without external PostgreSQL. The PR also reports that both extracted SQL statements remained byte-identical and that the new behavior tests passed against the original implementation before refactoring.

[PR #36](https://github.com/VarnerDamascenoJr/sales-event-project/pull/36) separately reports **98.2% statement coverage for `internal/observability`**, including an `httptest` OTLP collector for traces, metrics, and logs. Remaining uncovered paths concern exporter construction failures. These percentages apply to their named packages and candidates, not the whole application.

The latest [PR check](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38667791073) and [merged-main CI](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38668042281) concluded successfully. The main run at `d542ee3` passed unit tests, lint, integration tests, and runtime image builds, with Compose cleanup succeeding. Its timestamp is October 15 in UTC and **2026-10-14** in Fortaleza.

The [validation archive](completed-activities/validation-and-publication.md) preserves earlier limits, including PR #3's missing local Compose plugin and PR #22's failed Docker image pull. No application tests, build, dependency audit, data generation, or integrated demo were rerun for this collection.

## Task sources and import boundary

There is no project-local backlog file in the inspected checkout. Task context comes from the tracked [portfolio backlog](https://github.com/VarnerDamascenoJr/OptiFlow/blob/08e775d7890c0b6ac873588c281caa574145b852/docs/portfolio-project-backlog.md), [statistical backlog](https://github.com/VarnerDamascenoJr/OptiFlow/blob/08e775d7890c0b6ac873588c281caa574145b852/docs/portfolio-statistics-masters-backlog.md), and [React Dash correction backlog](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/analytics-dashboard-backlog.md). The archive preserves P1.1–P1.7, P4.1, P4.3, P5.4, S1.1–S1.6, and CFX1–CFX4 with their ownership and validation boundaries.

The shared backlogs report the P/S work as completed or checked; cross-project completion remains attributed to those sources. This import establishes the Sales deliveries and does not independently revalidate OptiFlow importers, platform dashboards, research studies, or every original acceptance criterion. CFX1–CFX4 have corresponding Sales fixes; their backlog text remains planning/evidence context rather than a newly edited status. CFX9 remains a broader demo-isolation request: the generator's optional inventory reset is a partial implementation, not evidence of complete cross-project cleanup. CFX5–CFX8 concern React Dash and are not Sales deliveries.

After fetching the source remote, `origin/main` matched GitHub at `d542ee3`. The source working tree remained clean on `refactor/analyticsdb-export` at `9c85b4b`, one merge commit behind the baseline. Its files match the recorded baseline; no source checkout switch or application edit was needed. All **36 merged PR integration commits** are ancestors of the baseline. PR #15 is closed without merge and excluded from that count; the CI implementation was delivered through direct commits.

Earlier architecture/agent notes retain pre-confirm RabbitMQ descriptions, and some testing documentation refers to old router filenames. The later implementation, README, PRs, and dated journals establish the subsequent behavior without rewriting those historical documents.

Original evidence paths under `/Users/varnerdamasceno/github-varner/evidence/` and `/home/varner/.codex/reports` were unavailable here. Their contents and screenshots were not inspected or copied; descriptions and shared backlog notes supply the attributed historical evidence.

This history was prepared as an **uncommitted local draft** on **2026-11-10**. On **2026-11-11**, the owner authorized publication on `docs/sales-event-project-history` with one file per commit and a PR for review. Source application files and shared backlogs were not changed.

## Source documentation at the baseline

- [Project README](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/README.md)
- [Architecture](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/architecture.md)
- [Domain and invariants](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/domain.md)
- [Database](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/database.md)
- [Analytics export](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/analytics-export.md)
- [OptiFlow planning export](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/optiflow-export.md)
- [Controlled failure scenarios](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/failure-scenarios.md)
- [Business journey dashboard](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/business-journey-dashboard.md)
- [Platform integration](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/observability-platform-integration.md)
- [Testing](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/testing.md)
- [CI scope](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/.github/workflows/ci.yml)
