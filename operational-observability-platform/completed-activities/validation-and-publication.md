# Validation and Publication — Operational Observability Platform

[Archive index](README.md) · [Project overview](../README.md)

## Evidence method

Collected on **2026-11-15** from source Git/documents, all **31 PR records**, available GitHub checks, and the failed-main job metadata/log. Baseline: `53ec569fb2d43253c4e91110db297baf89213e44`. Application tests, migrations, telemetry smoke, Docker, and audits were not executed for this import.

PR descriptions list historical validation commands, usually without numeric pass totals. Those command lists are not acceptance commands newly executed by this repository. PRs #1 and #4 have empty descriptions in the inspected metadata; changed files/title support their milestones without a separate execution claim.

## Latest CI evidence

| Evidence | Date in Fortaleza | Result | Verified scope |
| --- | --- | --- | --- |
| [PR #31 check](https://github.com/VarnerDamascenoJr/operational-observability-platform/actions/runs/37361881113) | 2026-10-05 | SUCCESS | The PR's Lint, test and build check concluded successfully |
| [Main run at 53ec569](https://github.com/VarnerDamascenoJr/operational-observability-platform/actions/runs/37366144235) | 2026-10-05 | FAILURE | Quality, configuration validation, stack startup, and migrations passed; observability smoke failed with exit code 4 |

The failed job was inspected directly. Its metadata identifies `Run observability smoke test` as the failed step; the available log reports exit code 4 without establishing the underlying cause. Logs were printed and teardown completed. No root-cause fix or successful main rerun is claimed here.

The workflow's quality command includes lint, formatting, unit/API E2E tests, and build. The separate telemetry smoke exercises the running stack. Passing the quality step does not turn the failed overall main execution into a successful validation. The September P5.4 completion note remains a dated earlier CI review.

## Candidate validation and corrections

| Delivery | Reported evidence | Boundary |
| --- | --- | --- |
| [PR #2](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/2) | Quality, configuration validation, ready stack, telemetry smoke | Local telemetry-stack delivery |
| [PR #6](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/6) | Unit/API E2E/build/lint/format/check; manual SQL check | PostgreSQL health and startup migration delivery |
| [PR #12](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/12) | Quality, configuration validation, smoke | Fixes the earlier PostgreSQL readiness race; no inferred explanation of October's exit code 4 |
| [PR #14](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/14), [PR #15](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/15), [PR #16](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/16) | Integrated telemetry/dashboard checks and source evidence locations | Producer work retains Sales/OptiFlow ownership; raw local artifacts unavailable here |
| [PR #20](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/20) | Focused tests, build/API E2E, configuration validation, quality, smoke | Multi-window burn-rate delivery |
| [PR #21](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/21) | Lint, format, unit tests, build, configuration validation | A smoke assertion was added; its description does not separately report executing smoke |
| [PR #27](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/27) | `npm run check` | EWMA delivery |
| [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28) | Build, unit tests, lint, format, API E2E | Hypothesis confidence and shared validation |
| [PR #29](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/29) | Build, unit tests, lint, format | Records a cursor microsecond-precision concern |
| [PR #30](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/30) | Build, unit/API E2E, lint, format, whitespace | Preserves cursor microseconds, batches reads, and adds transactional fixes |
| [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31) | Focused/full unit tests, build, lint, format, API E2E, whitespace | Candidate description; PR/main CI outcomes remain distinct above |

No suite totals were inferred from current test files. The later cursor correction is preserved alongside the earlier review concern. Historical statements that an incident branch had no PR apply to the September audit stage; PR #13 later provides the merge record.

## Source planning and shared evidence

The source checklist retains **42 checked and 34 unchecked items**. It is not rewritten to match every later delivery. Shared task snapshots are pinned to OptiFlow `b96520f`, and their P2/P4/S2 ownership is mapped in the [archive index](README.md#task-sources-and-ownership).

Historical raw evidence locations include:

- `/Users/varnerdamasceno/github-varner/evidence/p4.1-sales-platform-traces-2026-09-17/`
- `/Users/varnerdamasceno/github-varner/evidence/p4.2-sales-journey-dashboard-2026-09-17/`
- `/Users/varnerdamasceno/github-varner/evidence/p4.4-optiflow-execution-metrics-2026-09-17/`
- `/Users/varnerdamasceno/github-varner/evidence/p5.4-ci-badges-2026-09-21/`

These directories were unavailable locally, and no platform report directory was found under `/home/varner/.codex/reports`. PR descriptions retain their integration claims, including the September 17 versus September 18 evidence/merge date distinction. Raw logs/screenshots were not copied into Project History. Source-owned task statuses were not changed.

## PR register

All **31 records** appear once. **Main** means the PR's integration commit is an ancestor of `53ec569`; **Branch only** identifies PR #18; **Closed** identifies PR #17, which never merged. All 29 main integrations have two parents. Dates are GitHub merge timestamps converted to `America/Fortaleza`; a closed record has no merge date.

| PR | Merge date | Target branch | Presence | Delivered or proposed concern |
| --- | --- | --- | --- | --- |
| [PR #1](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/1) | 2026-08-22 | `main` | Main | Quality tooling and API E2E |
| [PR #2](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/2) | 2026-08-22 | `main` | Main | Local telemetry stack |
| [PR #3](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/3) | 2026-09-08 | `main` | Main | Database and correlation foundation |
| [PR #4](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/4) | 2026-09-10 | `main` | Main | HTTP correlation metadata |
| [PR #5](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/5) | 2026-09-10 | `main` | Main | Demo transactions and RED metrics |
| [PR #6](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/6) | 2026-09-14 | `main` | Main | Runtime PostgreSQL health |
| [PR #7](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/7) | 2026-09-14 | `main` | Main | W3C trace/log correlation |
| [PR #8](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/8) | 2026-09-14 | `main` | Main | Instrumented demo transactions |
| [PR #9](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/9) | 2026-09-14 | `main` | Main | Technical and business dashboards |
| [PR #10](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/10) | 2026-09-14 | `main` | Main | SLO and error budget model |
| [PR #11](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/11) | 2026-09-14 | `main` | Main | Symptom-based alerts |
| [PR #12](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/12) | 2026-09-14 | `main` | Main | CI PostgreSQL readiness fix |
| [PR #13](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/13) | 2026-09-18 | `main` | Main | Guided incident investigation |
| [PR #14](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/14) | 2026-09-18 | `main` | Main | Sales telemetry ingestion |
| [PR #15](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/15) | 2026-09-18 | `main` | Main | Sales journey dashboard |
| [PR #16](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/16) | 2026-09-18 | `main` | Main | OptiFlow execution dashboard |
| [PR #18](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/18) | 2026-09-22 | `docs/link-final-portfolio-guides` | Branch only | CI workflow links on intermediate branch |
| [PR #19](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/19) | 2026-09-23 | `main` | Main | Rolling SLO evaluation history |
| [PR #20](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/20) | 2026-09-23 | `main` | Main | Multi-window burn rate |
| [PR #21](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/21) | 2026-09-28 | `main` | Main | Latency distribution and tail metrics |
| [PR #22](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/22) | 2026-09-29 | `main` | Main | App/types/metrics organization |
| [PR #23](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/23) | 2026-09-30 | `main` | Main | SLO domain modules |
| [PR #24](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/24) | 2026-09-30 | `main` | Main | App route modules |
| [PR #25](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/25) | 2026-09-30 | `main` | Main | Observability hooks |
| [PR #26](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/26) | 2026-09-30 | `main` | Main | Incident domain modules |
| [PR #27](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/27) | 2026-10-03 | `main` | Main | EWMA process control |
| [PR #28](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/28) | 2026-10-04 | `main` | Main | Hypothesis confidence and validation |
| [PR #29](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/29) | 2026-10-04 | `main` | Main | Keyset pagination and not-found handling |
| [PR #30](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/30) | 2026-10-04 | `main` | Main | Cursor precision and transactional SQL fixes |
| [PR #31](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/31) | 2026-10-05 | `main` | Main | Operational risk forecast |
| [PR #17](https://github.com/VarnerDamascenoJr/operational-observability-platform/pull/17) | — | `main` | Closed | Final portfolio-guide links; proposal closed |

## Direct Git deliveries and baseline

Initialization and the source checklist are direct commits [`a9d72cc`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/a9d72cce6931d741cfcb1d44a55459a04b913bdf) and [`5f3ed84`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/5f3ed84e116d9d78c4b024a7263c79acfcdd42fc). The main CI badge was added by [`bd712ce`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/bd712ce2118c7d805c61b25b759468d5616dc468), separate from the closed/stacked guide PRs. Latest baseline: [`53ec569`](https://github.com/VarnerDamascenoJr/operational-observability-platform/commit/53ec569fb2d43253c4e91110db297baf89213e44).

The register preserves 30 merged PR states while distinguishing 29 main integrations from one branch-only merge. Closed PR #17 remains evidence of a proposal rather than an implemented main change. Earlier PR instructions such as waiting for review describe their original stage and authorize no new publication.
