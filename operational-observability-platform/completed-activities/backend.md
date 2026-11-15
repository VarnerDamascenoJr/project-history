# Backend — Operational Observability Platform

[Archive index](README.md) · [Project overview](../README.md)

## PostgreSQL foundation and runtime health

The foundation introduced pool/transaction helpers, migration execution, and the `control_plane` schema. P2.1 adds core tables through a new migration, preserves prior checksums, runs migrations at startup, and reports degraded PostgreSQL health with HTTP 503. API E2E tests use PostgreSQL rather than replacing the runtime contract with a stub.

**References:** [PR #3](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/3), [PR #6](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/6), [database and health behavior](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/README.md).

## Telemetry demo, dashboards, and portfolio producers

P2.2–P2.4 extend correlation and demo transactions with controlled asynchronous/dependency behavior, RED metrics, OTLP trace/log export, and technical/business dashboards. P4.1/P4.2 ingest Sales telemetry and provision the Sales journey view. P4.4 adds the OptiFlow scrape and execution dashboard; it does not move optimization logic into this repository.

**References:** [PR #4](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/4), [PR #5](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/5), [PR #7](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/7), [PR #8](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/8), [PR #9](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/9), [PR #14](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/14), [PR #15](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/15), [PR #16](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/16), [dashboard-to-trace/log investigation](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/dashboard-investigation.md).

## SLOs, symptom alerts, and statistical views

P2.5/P2.6 persist objectives/evaluated counts and expose state, error budget, and symptom metrics/rules. S2.1/S2.2 preserve rolling-window sources and classify short/long burn rate. S2.3 adds latency histograms and tail summaries. S2.4 uses EWMA to distinguish a spike from a sustained shift, with explicit baseline requirements.

S2.6 forecasts the next evaluated-window breach using a smoothed historical-frequency baseline and walk-forward diagnostics, including Brier/calibration summaries and false-positive/negative counts. Results are conditional on stored counts and declared parameters; they do not establish automatic live Prometheus evaluation or general forecasting accuracy.

**References:** [PR #10](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/10), [PR #11](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/11), [PR #19](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/19), [PR #20](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/20), [PR #21](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/21), [PR #27](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/27), [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31), [evaluation and statistical contracts](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/slo-error-budget.md).

## Incident investigation and hypothesis confidence

P2.7 persists incident state, evidence, hypotheses, timeline, and resolution data. S2.5 records numeric confidence changes and ranks active hypotheses with their history. Resolved incidents retain a stable closed state, and resolution requires root cause and preventive actions.

**References:** [PR #13](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/13), [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28), [investigation lifecycle](https://github.com/VarnerDamascenoJr/operational-observability-platform/blob/53ec569fb2d43253c4e91110db297baf89213e44/docs/incident-investigation.md).

## Cursor precision and transactional consistency

PR #29 introduces keyset incident listing and consistent HTTP 404 handling while documenting a timestamp-precision concern. PR #30 preserves PostgreSQL microseconds in cursors, replaces per-row hydration with batch reads, wraps composite writes in transactions, locks confidence updates, and transactionally removes obsolete SLO objectives during reconfiguration.

**References:** [PR #29](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/29), [PR #30](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/30).
