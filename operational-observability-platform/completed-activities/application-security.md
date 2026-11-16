# Application Security — Operational Observability Platform

[Archive index](README.md) · [Project overview](../README.md)

## Correlation and trace-context boundaries

Request/correlation/transaction IDs are validated before propagation and logging. Unsafe, duplicate, or oversized values are replaced by generated IDs. Trace identity comes from validated W3C `traceparent`, with malformed/all-zero contexts rejected; the custom `x-trace-id` header is not an accepted trace source.

The logging convention forbids secrets, full payloads, and unrestricted headers. This documents the contract and validation behavior, rather than claiming every possible payload has been audited or that IDs authorize access.

**References:** [PR #3](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/3), [PR #4](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/4), [PR #7](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/7), [correlation and logging contract](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/correlation.md), [header/context validation](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/src/observability/correlation.ts).

## HTTP validation and local deployment

Fastify registers Helmet, shared domain validation, and HTTP error handling. Pagination and risk/control queries have explicit validation, and missing incident lookup maps to HTTP 404. The telemetry stack is documented with loopback-bound ports and local-development access assumptions; production authentication or a clean dependency audit is not imported from these records.

**References:** [PR #2](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/2), [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28), [PR #29](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/29), [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31), [application composition](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/src/app.ts), [local port configuration](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docker-compose.yml).

## Data integrity and investigation history

Migration checksums preserve the applied schema history. Later repository changes use transactions for composite incident/SLO operations and lock confidence updates. Exact cursor timestamps preserve ordering information used by keyset paging. These are delivered data-integrity controls, not new changes made by the history import.

**References:** [PR #6](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/6), [PR #30](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/30), [incident history and resolution rules](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/incident-investigation.md).

## Statistical and evidence boundaries

Hypothesis confidence is a documented ranking score with evidence/history. SLO forecasts depend on the historical window input and report backtest diagnostics; neither result is imported as a proven incident cause or production prediction guarantee. Raw shared-rehearsal artifacts remain at their original evidence locations.

**References:** [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28), [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31), [validation record](validation-and-publication.md).
