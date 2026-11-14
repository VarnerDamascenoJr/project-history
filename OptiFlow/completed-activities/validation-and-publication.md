# Validation and Publication — OptiFlow

[Archive index](README.md) · [Project overview](../README.md)

## Evidence method

Collected on **2026-11-14** from source Git/documentation, committed study summaries, all 63 repository PR records, and latest available CI results. Baseline: `b96520fec39e2b865104e45b5c8e6dfeb511c096`. No application suite, solver, Docker build, study, or audit was executed for this documentation import.

There are **57 PR integrations represented in the baseline** and **six merged only into intermediate branches**. PRs #36–#38 have single-parent integration commits; the remaining 54 reachable integrations are two-parent merge commits. PR #2 is an ancestor but its domain change was explicitly reverted by PR #3. A merged PR, a change present on main, and a currently active behavior are different historical facts.

## Candidate-specific validation

Dates identify PR merges in `America/Fortaleza`. Counts and checks come from each candidate's description; do not add totals from different candidates or infer that checks were rerun at merge time.

| PR | Date | Reported tests | Additional evidence and scope |
| --- | --- | ---: | --- |
| [PR #59](https://github.com/VarnerDamascenoJr/OptiFlow/pull/59) | 2026-11-09 | 85 | Six regressions, two pre-fix reproductions, scenario/benchmark/simulation/risk checks |
| [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60) | 2026-11-10 | 97 | Real OR-Tools/API, seven benchmark comparisons, Docker execution at cost 744 with OPTIMAL |
| [PR #61](https://github.com/VarnerDamascenoJr/OptiFlow/pull/61) | 2026-11-12 | 102 | Five integer-reconstruction regressions and strict detection of a real fractional violation |
| [PR #62](https://github.com/VarnerDamascenoJr/OptiFlow/pull/62) | 2026-11-12 | 116 | Fourteen forecasting cases, temporal isolation, CLI text/JSON, prior solver/simulation checks |
| [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63) | 2026-11-13 | 121 | Production image/HTTP smoke, OR-Tools at cost 744 with OPTIMAL, production-only audit with zero findings |

Earlier PRs generally list commands without numeric totals. Their descriptions remain the source for those claims; no pass counts were reconstructed from current test files. The November 13 audit is a dated production-only result, not a new audit of the repository today.

## CI at the recorded baseline

[PR #63 CI](https://github.com/VarnerDamascenoJr/OptiFlow/actions/runs/43514509226) and [main CI](https://github.com/VarnerDamascenoJr/OptiFlow/actions/runs/43514985168) succeeded. The committed workflow installs Node and Python/OR-Tools, runs tests (including the backend build hook), sample planning, enumeration/OR-Tools comparisons, simulation, risk comparison, forecasting, and whitespace checks. It does not run Docker image checks or the complete multi-repository rehearsal.

## Statistical studies and versioned evidence

The following source artifacts were inspected and linked at the baseline; their computations were not rerun. Source study dates can predate the corresponding PR merge.

| Study | Source evidence | Interpretation boundary |
| --- | --- | --- |
| Foundation, 2026-09-22 | [study](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-09-22-foundation-fixture/study.md) and [summary](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-09-22-foundation-fixture/evidence/summary.json) | Synthetic common format; no real population inference; original report records local uncommitted work |
| Funnel/planning, 2026-09-29 | [study](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-09-29-funnel-planning/study.md) and [summary](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-09-29-funnel-planning/evidence/summary.json) | Small synthetic fixture; exact enumeration remains recommended; the reliability signal is a fixture |
| Reliability/decision | [controlled study contract](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/reliability-decision-study.md) | Designed burn-rate/decision-loss example, not continuous production evidence |
| Stockout, 2026-10-01; PR merge 2026-10-02 | [study](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-10-01-stockout-risk/study.md) and [summary](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-10-01-stockout-risk/evidence/summary.json) | Synthetic fixture, declared loss penalty, limited Poisson approximation |
| Quasi-experimental, 2026-10-02 | [study](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-10-02-quasi-experimental/study.md) and [summary](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/studies/statistics/2026-10-02-quasi-experimental/evidence/summary.json) | Simulated intervention; observed association does not establish parallel trends or eliminate confounding |

Golden datasets test known formula outputs independently of services. The statistical report distinguishes inference, prediction, and preference-dependent decisions. Forecasting's synthetic example compares fixed models; choosing a winner on that validation set does not independently estimate future model-selection performance.

## Historical portfolio rehearsals and unavailable raw artifacts

The shared backlog reports portfolio execution, rendered diagrams, and demo rehearsal on **2026-09-21**. It also records rejection of 11 historical completed Sales records without items, followed by a valid-subset execution. This import preserves the dated claim, not an assertion that the original data was repaired.

Original evidence locations recorded in source include:

- `/Users/varnerdamasceno/github-varner/evidence/p4.3-sales-data-optiflow-2026-09-17/`
- `/Users/varnerdamasceno/github-varner/evidence/p4.4-optiflow-execution-metrics-2026-09-17/`
- `/Users/varnerdamasceno/github-varner/evidence/p0.2-main-demo-runbook-2026-09-21/`
- `/Users/varnerdamasceno/github-varner/evidence/p5.1-local-execution-2026-09-21/`
- `/Users/varnerdamasceno/github-varner/evidence/p5.2-architecture-diagrams-2026-09-21/`
- `/Users/varnerdamasceno/github-varner/evidence/p5.3-recordable-demo-rehearsal-2026-09-21/`
- `/Users/varnerdamasceno/github-varner/evidence/p5.4-ci-badges-2026-09-21/`
- `/Users/varnerdamasceno/github-varner/evidence/s5.3-statistical-demo-rehearsal-2026-10-06/`

Those raw directories were unavailable here; no local OptiFlow directory was found under `/home/varner/.codex/reports`. Raw logs, screenshots, and datasets were not copied. Planned verification commands and source status updates are not new executions by this import.

## Delivery register

Every repository PR appears once. **Main** means its integration commit is an ancestor of `b96520f`; **Branch only** means the merge occurred outside that baseline. Dates are the GitHub merge timestamps converted to `America/Fortaleza`. Documentation PRs about Sales/platform tasks retain those owners.

| PR | Merge date | Target branch | Baseline | Delivered or recorded concern |
| --- | --- | --- | --- | --- |
| [PR #1](https://github.com/VarnerDamascenoJr/OptiFlow/pull/1) | 2026-09-08 | `main` | Main | Deterministic delivery core |
| [PR #2](https://github.com/VarnerDamascenoJr/OptiFlow/pull/2) | 2026-09-10 | `main` | Main | Sales-decision domain experiment; reverted by #3 |
| [PR #3](https://github.com/VarnerDamascenoJr/OptiFlow/pull/3) | 2026-09-10 | `main` | Main | Revert of the sales-decision experiment |
| [PR #4](https://github.com/VarnerDamascenoJr/OptiFlow/pull/4) | 2026-09-10 | `main` | Main | Execution metadata and metrics |
| [PR #5](https://github.com/VarnerDamascenoJr/OptiFlow/pull/5) | 2026-09-11 | `main` | Main | Sales RabbitMQ-context status |
| [PR #6](https://github.com/VarnerDamascenoJr/OptiFlow/pull/6) | 2026-09-11 | `main` | Main | Sales tracing status |
| [PR #7](https://github.com/VarnerDamascenoJr/OptiFlow/pull/7) | 2026-09-14 | `main` | Main | Sales publish-reliability status |
| [PR #8](https://github.com/VarnerDamascenoJr/OptiFlow/pull/8) | 2026-09-14 | `main` | Main | Sales failure-scenario status |
| [PR #9](https://github.com/VarnerDamascenoJr/OptiFlow/pull/9) | 2026-09-14 | `main` | Main | Sales business-dashboard status |
| [PR #10](https://github.com/VarnerDamascenoJr/OptiFlow/pull/10) | 2026-09-15 | `docs/p1.7-business-dashboard` | Branch only | Platform PostgreSQL task status |
| [PR #11](https://github.com/VarnerDamascenoJr/OptiFlow/pull/11) | 2026-09-15 | `docs/p2.1-postgres-health` | Branch only | Platform log-correlation task status |
| [PR #12](https://github.com/VarnerDamascenoJr/OptiFlow/pull/12) | 2026-09-15 | `docs/p2.2-trace-log-correlation` | Branch only | Platform instrumented-API task status |
| [PR #13](https://github.com/VarnerDamascenoJr/OptiFlow/pull/13) | 2026-09-15 | `docs/p2.3-instrumented-demo-api` | Branch only | Platform dashboard task status |
| [PR #14](https://github.com/VarnerDamascenoJr/OptiFlow/pull/14) | 2026-09-15 | `docs/p2.4-technical-business-dashboards` | Branch only | Platform SLO/error-budget task status |
| [PR #15](https://github.com/VarnerDamascenoJr/OptiFlow/pull/15) | 2026-09-15 | `docs/p2.5-slo-error-budget` | Branch only | Platform symptom-alert task status |
| [PR #16](https://github.com/VarnerDamascenoJr/OptiFlow/pull/16) | 2026-09-15 | `main` | Main | Mathematical formulation |
| [PR #17](https://github.com/VarnerDamascenoJr/OptiFlow/pull/17) | 2026-09-15 | `main` | Main | Deterministic benchmarks |
| [PR #18](https://github.com/VarnerDamascenoJr/OptiFlow/pull/18) | 2026-09-15 | `main` | Main | Bounded exact-enumeration adapter |
| [PR #19](https://github.com/VarnerDamascenoJr/OptiFlow/pull/19) | 2026-09-15 | `main` | Main | Heuristic versus solver comparison |
| [PR #20](https://github.com/VarnerDamascenoJr/OptiFlow/pull/20) | 2026-09-16 | `main` | Main | Configurable constraints |
| [PR #21](https://github.com/VarnerDamascenoJr/OptiFlow/pull/21) | 2026-09-17 | `main` | Main | Optimization history repository |
| [PR #22](https://github.com/VarnerDamascenoJr/OptiFlow/pull/22) | 2026-09-17 | `main` | Main | Scenario/run HTTP API |
| [PR #23](https://github.com/VarnerDamascenoJr/OptiFlow/pull/23) | 2026-09-17 | `main` | Main | In-memory execution queue |
| [PR #24](https://github.com/VarnerDamascenoJr/OptiFlow/pull/24) | 2026-09-17 | `main` | Main | Seeded fixed-plan simulation |
| [PR #25](https://github.com/VarnerDamascenoJr/OptiFlow/pull/25) | 2026-09-17 | `main` | Main | VaR/CVaR decision analysis |
| [PR #26](https://github.com/VarnerDamascenoJr/OptiFlow/pull/26) | 2026-09-17 | `main` | Main | Local scenario comparison interface |
| [PR #27](https://github.com/VarnerDamascenoJr/OptiFlow/pull/27) | 2026-09-17 | `main` | Main | Docker, CI, and local delivery |
| [PR #28](https://github.com/VarnerDamascenoJr/OptiFlow/pull/28) | 2026-09-18 | `main` | Main | Sales/platform trace-integration status |
| [PR #29](https://github.com/VarnerDamascenoJr/OptiFlow/pull/29) | 2026-09-18 | `main` | Main | Platform Sales-journey dashboard status |
| [PR #30](https://github.com/VarnerDamascenoJr/OptiFlow/pull/30) | 2026-09-18 | `main` | Main | Sales export importer |
| [PR #31](https://github.com/VarnerDamascenoJr/OptiFlow/pull/31) | 2026-09-18 | `main` | Main | OptiFlow execution metrics |
| [PR #32](https://github.com/VarnerDamascenoJr/OptiFlow/pull/32) | 2026-09-18 | `main` | Main | Portfolio local-execution guides |
| [PR #33](https://github.com/VarnerDamascenoJr/OptiFlow/pull/33) | 2026-09-18 | `main` | Main | Recordable portfolio demo script |
| [PR #34](https://github.com/VarnerDamascenoJr/OptiFlow/pull/34) | 2026-09-18 | `main` | Main | Consistent portfolio CI references |
| [PR #35](https://github.com/VarnerDamascenoJr/OptiFlow/pull/35) | 2026-09-20 | `main` | Main | Shared source helpers and dispatch |
| [PR #36](https://github.com/VarnerDamascenoJr/OptiFlow/pull/36) | 2026-09-22 | `main` | Main | Sales analytics-export status |
| [PR #37](https://github.com/VarnerDamascenoJr/OptiFlow/pull/37) | 2026-09-22 | `main` | Main | Sales funnel-uncertainty status |
| [PR #38](https://github.com/VarnerDamascenoJr/OptiFlow/pull/38) | 2026-09-22 | `main` | Main | Sales survival-analysis status |
| [PR #39](https://github.com/VarnerDamascenoJr/OptiFlow/pull/39) | 2026-09-23 | `main` | Main | Platform rolling-SLO status |
| [PR #40](https://github.com/VarnerDamascenoJr/OptiFlow/pull/40) | 2026-09-23 | `main` | Main | Platform burn-rate status |
| [PR #41](https://github.com/VarnerDamascenoJr/OptiFlow/pull/41) | 2026-09-23 | `main` | Main | Sales-prior simulation calibration |
| [PR #42](https://github.com/VarnerDamascenoJr/OptiFlow/pull/42) | 2026-09-23 | `main` | Main | Monte Carlo error and convergence |
| [PR #43](https://github.com/VarnerDamascenoJr/OptiFlow/pull/43) | 2026-09-28 | `main` | Main | Embedded analytics-prior consumer |
| [PR #44](https://github.com/VarnerDamascenoJr/OptiFlow/pull/44) | 2026-09-28 | `main` | Main | Platform latency-distribution status |
| [PR #45](https://github.com/VarnerDamascenoJr/OptiFlow/pull/45) | 2026-09-29 | `main` | Main | Paired strategy inference |
| [PR #46](https://github.com/VarnerDamascenoJr/OptiFlow/pull/46) | 2026-09-29 | `main` | Main | Decision loss and profiles |
| [PR #47](https://github.com/VarnerDamascenoJr/OptiFlow/pull/47) | 2026-09-29 | `main` | Main | Temporal decision backtest |
| [PR #48](https://github.com/VarnerDamascenoJr/OptiFlow/pull/48) | 2026-09-29 | `main` | Main | Decision sensitivity |
| [PR #49](https://github.com/VarnerDamascenoJr/OptiFlow/pull/49) | 2026-09-29 | `main` | Main | Funnel/planning study |
| [PR #50](https://github.com/VarnerDamascenoJr/OptiFlow/pull/50) | 2026-10-01 | `main` | Main | Reliability-informed decision study |
| [PR #51](https://github.com/VarnerDamascenoJr/OptiFlow/pull/51) | 2026-10-02 | `main` | Main | Stockout/capacity study |
| [PR #52](https://github.com/VarnerDamascenoJr/OptiFlow/pull/52) | 2026-10-02 | `main` | Main | Quasi-experimental study |
| [PR #53](https://github.com/VarnerDamascenoJr/OptiFlow/pull/53) | 2026-10-03 | `main` | Main | Shared parsing/formatting helpers |
| [PR #54](https://github.com/VarnerDamascenoJr/OptiFlow/pull/54) | 2026-10-03 | `main` | Main | Manual API route modules |
| [PR #55](https://github.com/VarnerDamascenoJr/OptiFlow/pull/55) | 2026-10-03 | `main` | Main | Validation and CLI helpers |
| [PR #56](https://github.com/VarnerDamascenoJr/OptiFlow/pull/56) | 2026-10-05 | `main` | Main | Statistical golden datasets |
| [PR #57](https://github.com/VarnerDamascenoJr/OptiFlow/pull/57) | 2026-10-06 | `main` | Main | Statistical report and platform-status updates |
| [PR #58](https://github.com/VarnerDamascenoJr/OptiFlow/pull/58) | 2026-10-06 | `main` | Main | Statistical demo/rehearsal record |
| [PR #59](https://github.com/VarnerDamascenoJr/OptiFlow/pull/59) | 2026-11-09 | `main` | Main | Non-metric final-distance correction |
| [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60) | 2026-11-10 | `main` | Main | Native OR-Tools CP-SAT integration |
| [PR #61](https://github.com/VarnerDamascenoJr/OptiFlow/pull/61) | 2026-11-12 | `main` | Main | Integer route reconstruction |
| [PR #62](https://github.com/VarnerDamascenoJr/OptiFlow/pull/62) | 2026-11-12 | `main` | Main | Temporal demand forecasting |
| [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63) | 2026-11-13 | `main` | Main | Modular NestJS backend |

## Direct deliveries and status boundaries

The initial August vision/conventions/technology notes are direct commits. Shared portfolio tracking entered through [`65c6c96`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/65c6c96041a1c972e0b711b90e2f4f15e4ddc31f); later status updates include [`a42a74b`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/a42a74bc961a77e1cdf6475007885a761800ad45). The cost-aware strategy arrived through direct merge [`6cf804a`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/6cf804a9f541581e2f01c477500b0f3618768051). September 21 guide/render/rehearsal/CI closure is recorded in [`79e9fa5`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/79e9fa56acfd1cd8673136c1689153fdf0ea9428), [`098bde7`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/098bde7b0827a72c5bcdaa1b2fab7495a81d8bc2), [`80ad588`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/80ad588620291bd795b15fe4d95ea7abd7cc79bc), [`89a79d0`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/89a79d08d69ef6e67af88e36d8fe7b7b7f53fcdd), and [`d2f00c4`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/d2f00c4e50182abd0de6c57f7dc40a44c2fdcd48). Statistical foundation documents use [`71fb464`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/71fb464f07c33209a954749346eca27b681697b6), [`28a8cbc`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/28a8cbc29e1a01be02bd9ac8a9344ed777d0de53), and [`4e16f19`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/4e16f19f8b0d56c973ddabe9539eb1a10eecf9ef).

PRs #10–#15 are not ancestors of the main baseline despite their merged GitHub state; later direct backlog changes can record the same external milestones without integrating those merge objects. PR #2 and its revert #3 are both ancestors. Dates and presence come from source evidence rather than PR numbering or completion wording.

This archive preserves the source task identifiers and checked state as historical evidence. It does not assign new task closure, rerun other repositories, or authorize new source-project publication.
