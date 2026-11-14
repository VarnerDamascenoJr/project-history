# Backend — OptiFlow

[Archive index](README.md) · [Project overview](../README.md)

## Delivery planning, strategy comparison, and constraints

The deterministic slice introduced scenario validation, `nearest-neighbor-capacity`, route metrics, benchmarks, and bounded `exact-enumeration`. P3.1–P3.5 document the formulation and comparisons, including cost **792 versus 744** for the small fixture. A direct merge later introduced `cost-aware-greedy`.

PR #59 corrected final-distance pruning for non-metric matrices. November's PR #60 integrated real OR-Tools CP-SAT, followed by integer route reconstruction in PR #61. `OPTIMAL` and `FEASIBLE` retain distinct guarantees. Required-order diagnostics do not force every annotated order into a route.

**References:** [PR #1](https://github.com/VarnerDamascenoJr/OptiFlow/pull/1), [PR #16](https://github.com/VarnerDamascenoJr/OptiFlow/pull/16), [PR #17](https://github.com/VarnerDamascenoJr/OptiFlow/pull/17), [PR #18](https://github.com/VarnerDamascenoJr/OptiFlow/pull/18), [PR #19](https://github.com/VarnerDamascenoJr/OptiFlow/pull/19), [PR #20](https://github.com/VarnerDamascenoJr/OptiFlow/pull/20), [PR #59](https://github.com/VarnerDamascenoJr/OptiFlow/pull/59), [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60), [PR #61](https://github.com/VarnerDamascenoJr/OptiFlow/pull/61), [`6cf804a`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/6cf804a9f541581e2f01c477500b0f3618768051), [current mathematical contract](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/mathematical-formulation.md).

## History, execution API, and NestJS migration

P3.6–P3.8 delivered JSON scenario/run/result storage, the HTTP API, queued lifecycle transitions, retry, concurrency, and duration settings. P3.11 added the local scenario console; P4.4 added correlated logs and Prometheus execution/queue metrics.

PR #63 replaced manual routing with NestJS controllers/modules and one shared runtime repository/queue per application. Domain handlers and the JavaScript optimizer remain independent. The queue still resides in process and memory; synchronous solvers can block the API, timeout checks do not guarantee preemptive interruption, and JSON storage assumes one writer.

**References:** [PR #21](https://github.com/VarnerDamascenoJr/OptiFlow/pull/21), [PR #22](https://github.com/VarnerDamascenoJr/OptiFlow/pull/22), [PR #23](https://github.com/VarnerDamascenoJr/OptiFlow/pull/23), [PR #26](https://github.com/VarnerDamascenoJr/OptiFlow/pull/26), [PR #31](https://github.com/VarnerDamascenoJr/OptiFlow/pull/31), [PR #54](https://github.com/VarnerDamascenoJr/OptiFlow/pull/54), [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63), [module and runtime boundaries](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/backend-architecture.md).

## Sales imports and uncertainty-aware decisions

P4.3 imports `sales-event-optiflow-export.v1` into the delivery scenario, with explicit failures for incomplete records. S3.1 accepts both prior fixtures and `simulationPriors` embedded in Sales analytics exports, retaining source period/sample metadata and a synthetic fallback mode.

P3.9/P3.10 and S3.2–S3.6 add seeded fixed-plan simulation, expected-cost intervals, quantile diagnostics, VaR/CVaR, paired comparisons, decision profiles, temporal backtests, regret, and sensitivity. Conclusions depend on the declared data and loss preferences; a numerical recommendation is not a general operational guarantee.

**References:** [PR #24](https://github.com/VarnerDamascenoJr/OptiFlow/pull/24), [PR #25](https://github.com/VarnerDamascenoJr/OptiFlow/pull/25), [PR #30](https://github.com/VarnerDamascenoJr/OptiFlow/pull/30), [PR #41](https://github.com/VarnerDamascenoJr/OptiFlow/pull/41), [PR #42](https://github.com/VarnerDamascenoJr/OptiFlow/pull/42), [PR #43](https://github.com/VarnerDamascenoJr/OptiFlow/pull/43), [PR #45](https://github.com/VarnerDamascenoJr/OptiFlow/pull/45), [PR #46](https://github.com/VarnerDamascenoJr/OptiFlow/pull/46), [PR #47](https://github.com/VarnerDamascenoJr/OptiFlow/pull/47), [PR #48](https://github.com/VarnerDamascenoJr/OptiFlow/pull/48), [temporal decision backtest](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/decision-backtesting.md), [sensitivity scope](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/decision-sensitivity.md).

## Demand forecasting and integrated studies

PR #62 adds naive/moving-average forecasts by location/window, rejects irregular histories, and evaluates one-step predictions using only previously observed windows. Model selection is inspectable before solver use; forecasts do not overwrite confirmed orders. Its first fixture is synthetic, with no predictive intervals or independent evaluation of the selection process.

S4.1–S4.4 demonstrate planning under funnel uncertainty, reliability-informed loss, stockout/capacity tradeoffs, and a simulated intervention. The [validation record](validation-and-publication.md#statistical-studies-and-versioned-evidence) distinguishes stored study artifacts, controlled assumptions, and unavailable raw rehearsals.

**References:** [PR #49](https://github.com/VarnerDamascenoJr/OptiFlow/pull/49), [PR #50](https://github.com/VarnerDamascenoJr/OptiFlow/pull/50), [PR #51](https://github.com/VarnerDamascenoJr/OptiFlow/pull/51), [PR #52](https://github.com/VarnerDamascenoJr/OptiFlow/pull/52), [PR #62](https://github.com/VarnerDamascenoJr/OptiFlow/pull/62), [forecasting contract and limits](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/demand-forecasting.md).
