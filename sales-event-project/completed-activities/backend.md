# Backend — Sales Event

[Archive index](README.md) · [Project overview](../README.md)

## Original sales, payment, and ticket lifecycle

May's direct commits established HTTP acceptance, asynchronous reservation, event-scoped queries, customer contact capture, pending payment, QR-ticket issuance/email, transactional payment outbox, check-in, retention, retry state, and payment intents/webhooks. API acceptance precedes persistence; failed payments restore inventory. Historical changes to broker and retry behavior are recorded at their actual later dates.

**References:** [May journal](../2026-05.md), [domain at the baseline](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/domain.md).

## Dedicated email retries and reliable publication

| Original task | Problem and delivered behavior | Evidence and limits |
| --- | --- | --- |
| P1.1 | Retry processing shared the main worker lifecycle. Added a separately deployable retry command, health/metrics, Compose target, and integration smoke while retaining backoff, locking, and dead-letter policy. | [PR #4](https://github.com/VarnerDamascenoJr/sales-event-project/pull/4), [PR #5](https://github.com/VarnerDamascenoJr/sales-event-project/pull/5); shared backlog reports completion and later 2026-09-16 validation |
| P1.5 | Successful publish calls did not prove routing/acknowledgement. Enabled confirms and mandatory routing; `nack`, returns, and confirmation failures preserve outbox retry/dead-letter state. | [PR #9](https://github.com/VarnerDamascenoJr/sales-event-project/pull/9); broker acknowledgement does not establish consumer processing |

The five-attempt retry policies cap exponential backoff at one hour. `SALE_FAILED` still has no local consumer binding; its deliberate unbound route demonstrates failed publication instead of silent success.

## Correlation and observability across the journey

| Original task | Delivered behavior | Reference |
| --- | --- | --- |
| P1.2 | Persist request/correlation/transaction IDs and preserve context through reservation, payment, outbox, ticket/email, retry, and check-in | [PR #6](https://github.com/VarnerDamascenoJr/sales-event-project/pull/6), preceded by [PR #2](https://github.com/VarnerDamascenoJr/sales-event-project/pull/2)/[PR #3](https://github.com/VarnerDamascenoJr/sales-event-project/pull/3) |
| P1.3 | Carry correlation headers with W3C trace headers through RabbitMQ and derived events | [PR #7](https://github.com/VarnerDamascenoJr/sales-event-project/pull/7) |
| P1.4 | Optional OTLP plus shared business spans for sales, payment, outbox, messaging, delivery, email, and check-in | [PR #1](https://github.com/VarnerDamascenoJr/sales-event-project/pull/1), [PR #8](https://github.com/VarnerDamascenoJr/sales-event-project/pull/8) |
| P1.7 | Grafana business journey panels and explicit duplicate-payment/check-in metrics | [PR #11](https://github.com/VarnerDamascenoJr/sales-event-project/pull/11) |
| P4.1 | Distinct service identities/namespace, tested trace propagation, and documented shared-platform setup | [PR #12](https://github.com/VarnerDamascenoJr/sales-event-project/pull/12) |

The shared portfolio backlog reports these tasks completed. Platform-side collection/dashboards remain owned by the platform; this collection records the Sales contribution and attributed integrated smoke.

## Planning history for OptiFlow

P4.3 added `cmd/optiflow-export` and `sales-event-optiflow-export.v1` with sales/items, payment, email, tickets/check-ins, and correlation fields. The shared backlog separately records OptiFlow's importer, fixture, validation, and reproducible scenario. Export implementation and consumer acceptance are separate responsibilities.

**References:** [PR #13](https://github.com/VarnerDamascenoJr/sales-event-project/pull/13), [planning export documentation](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/optiflow-export.md).

## Statistical export and baseline models

| Original task | Delivered behavior and relevant limits | Reference |
| --- | --- | --- |
| S1.1 | Versioned events, UTC timestamps, status counts, and 1m/5m/1h/1d windows; some events derive from current entity state rather than a complete transition log | [PR #16](https://github.com/VarnerDamascenoJr/sales-event-project/pull/16) |
| S1.2 | Conditional funnel stages with Wilson intervals and Beta(1,1) posterior summaries, grouped by cohort/dimensions | [PR #17](https://github.com/VarnerDamascenoJr/sales-event-project/pull/17) |
| S1.3 | Payment/email/check-in timing, censored observations at export time, hazard buckets, and observed-event percentiles; percentiles exclude censored observations | [PR #18](https://github.com/VarnerDamascenoJr/sales-event-project/pull/18) |
| S1.4 | Moving-average demand with temporal evaluation, MAE/RMSE, and next-window forecasts; densified series capped at 500 windows per ticket | [PR #20](https://github.com/VarnerDamascenoJr/sales-event-project/pull/20) |
| S1.5 | Poisson stockout probability from current inventory and filtered demand; baseline sensitivity to sparse history/narrow filters remains documented | [PR #21](https://github.com/VarnerDamascenoJr/sales-event-project/pull/21) |
| S1.6 | `optiflow-sales-priors.v1` conversion, cancellation, demand, timing, and stockout parameters within the analytics export; consumer integration remains separate | [PR #22](https://github.com/VarnerDamascenoJr/sales-event-project/pull/22) |

PR #19 supplied the protected HTTP export and shared `analyticsdb` reader. S1.1–S1.6 are checked in the shared statistical backlog; this import preserves that source status without independently repeating its original bank/fixture, model, or cross-project acceptance checks. The synthetic fixture is contract evidence, not an empirical operational finding.

**References:** [PR #19](https://github.com/VarnerDamascenoJr/sales-event-project/pull/19), [analytics contract and limitations](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/docs/analytics-export.md), [October corrections/refactors](../2026-10.md).
