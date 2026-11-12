# Validation and Publication — Sales Event

[Archive index](README.md) · [Project overview](../README.md)

## Evidence method

Collected on **2026-11-10** from Git at `d542ee3`, source documentation, GitHub metadata/descriptions for all 37 PRs, available PR checks, the latest main run, and shared backlog records. There are **36 merged PRs**, all reachable from the baseline, and **one closed, unmerged PR (#15)**. Earlier direct commits are also recorded in the monthly journals.

Dates use `America/Fortaleza`. GitHub `mergedAt` defines PR integration dates; author/commit dates identify implementation and direct delivery. PR #37's UTC merge date of October 15 is October 14 locally. PR descriptions can retain older proposed base branches or pre-merge statements; the final GitHub state determines the register.

Reported validation remains attributed to its candidate and original source. This collection did not run application tests, builds, dependency scans, data generation, live SMTP/provider validation, or a real-backend/browser rehearsal. No numerical test totals were inferred from test functions or added across candidates.

## Candidate-specific validation

| Candidate | Reported or observed result | Limit |
| --- | --- | --- |
| June documentation analysis | Reports `make test` and API/worker/migrate image builds passing | Integration explicitly not run; execution date unspecified; June 13 is the documentation commit date |
| PR #1 | Reports formatting, unit tests, lint, Compose configuration validation | No PR check returned by the current API response |
| PR #2 | Empty description | Reconstruct implementation from Git; no candidate validation statement imported |
| PR #3 | Reports unit tests/lint | Local integration blocked by missing Compose plugin |
| PR #4 | Reports formatting/unit/lint and dedicated-worker image build | Process extraction preserves schema, retry policy, and locking |
| PR #5 | Reports unit/lint/integration and manual sales/payment/email/check-in/retry smoke | Original September 10 smoke directory unavailable |
| PRs #6–#8 | Report unit/lint/integration and correlated/OTLP manual smokes | Original September 11 directories unavailable; later P1.1/P1.2 September 16 validation is attributed to the shared backlog |
| PR #9 | Reports focused/full unit, lint, and integration checks including unbound routing | External network prerequisite documented; confirms do not imply consumer completion |
| PR #10 / P1.6 | Reports full controlled-failure script, delayed-consumer rerun, unit/lint/integration | Retry deadlines accelerated after real failure to shorten the demo |
| PR #11 / P1.7 | Reports dashboard JSON checks, unit/lint, Grafana discovery, payment/outbox smokes, manual check-in, and Prometheus observations | Description's earlier stacked base differs from final `main` target |
| PR #12 / P4.1 | Reports unit/lint/integration/configuration and Tempo/Loki/Prometheus integrated smoke | Original September 17 evidence unavailable |
| PR #13 / P4.3 | References formatting/unit/lint logs and planning-export summary | Consumer validation belongs to OptiFlow; no integration run asserted by the PR description |
| PR #14 / closed #15 | Describe documentation/CI preparation and whitespace checks | #15 is not a merged delivery; actual CI entered through direct commits |
| PRs #16–#18 | Report formatting/unit/whitespace checks; returned PR checks succeeded | Synthetic statistical/contract tests do not establish empirical model calibration |
| PR #19 | Reports focused/full Go tests, formatting, whitespace checks; PR check succeeded | Shared CLI/HTTP reader and access control delivery |
| PRs #20–#21 | Report unit/lint/formatting/whitespace; PR checks succeeded | Baseline demand/stockout models retain documented limitations |
| PR #22 | Reports local unit/lint/formatting/whitespace; available PR check failed | Docker Hub image pull failed before Go tests; later steps skipped |
| PRs #23–#28 | Report unit/lint, with additional focused/formatting/whitespace checks where listed; returned PR checks succeeded | Refactor validation is candidate-specific |
| PRs #29–#30 | Report focused/full unit and lint; PR checks succeeded | No full large live-dataset/browser rehearsal inferred |
| PR #31 | Reports shell syntax, focused/full unit, whitespace checks; PR check succeeded | Does not report running the added live API-key smoke |
| PR #32 | Reports focused generator/full unit/whitespace; PR check succeeded | No new real data-generation or screenshot run imported |
| PRs #33–#34 | Report unit/lint; PR checks succeeded | Fortaleza dates are October 12, although UTC dates extend into October 13 |
| PR #35 | Reports Docker full Go tests, formatting/whitespace; PR check succeeded | HTTP metric contract preserved |
| PR #36 | Reports shuffled package tests and **98.2% observability statement coverage**; PR/main checks succeeded | Exporter construction failures uncovered; percentage is package-specific |
| PR #37 | Reports shuffled full Go tests, **100% analyticsdb statement coverage**, pre-refactor test success, byte-identical SQL, whitespace; PR/main checks succeeded | Reader tests use interface doubles, not external PostgreSQL; percentage is package-specific |

PR checks below are the conclusions returned during collection, not a claim that every historical run passed. An empty check list means no check was returned, not that a test run was proven absent or successful.

### PR #22 infrastructure failure

The [failed PR run](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36425014523) at `b341c18` failed inside `make test` while Docker tried to download `golang:1.22-alpine`. Its log records a Docker Hub token-request connection reset and Docker exit 125. Go tests did not start; lint, network creation, integration, and image builds were skipped. Keep that failure visible alongside the local validation claims. A later green main run does not retroactively change this candidate's conclusion.

### Latest main validation

The [PR #37 run](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38667791073) and [main run at `d542ee3`](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38668042281) succeeded. The main job passed unit tests, lint, external-network setup, integration tests, and API/worker/retry-worker image builds; cleanup also passed. This matches the [committed workflow](https://github.com/VarnerDamascenoJr/sales-event-project/blob/d542ee346bcd3ededc746b6cb31cec33ee7d0eac/.github/workflows/ci.yml). It does not establish a dependency audit, production deployment, or a React Dash browser run.

## Original evidence locations

The following are source-reported locations under `/Users/varnerdamasceno/github-varner/evidence/`. That directory and `/home/varner/.codex/reports` were unavailable in this workspace. Raw logs/screenshots were not reviewed or copied.

| Source | Original path suffix | Reported purpose |
| --- | --- | --- |
| PR #5 | `p1.1-manual-smoke-2026-09-10/` | Main sales flow and dedicated retry worker |
| PR #6 | `p1.2-correlation-journey-2026-09-11/` | End-to-end correlation |
| PR #7 | `p1.3-rabbitmq-context-2026-09-11/` | AMQP context smoke |
| PR #8 | `p1.4-opentelemetry-sales-2026-09-11/` | Collector/Tempo/Loki/Grafana smoke |
| PR #12 | `p4.1-sales-platform-traces-2026-09-17/` | Shared observability platform integration |
| PR #13 / shared P4.3 backlog | `p4.3-sales-data-optiflow-2026-09-17/SUMMARY.md` | Planning export and consumer workflow; accompanying formatting/unit/lint logs |
| Shared P5.4 backlog | `p5.4-ci-badges-2026-09-21/` | Portfolio CI runs and badges |
| React Dash correction backlog | `react-dash-sales-api-simulation-2026-10-06/` | Large-dataset integrated rehearsal findings |

## Delivery register

Every merged PR appears exactly once, ordered by GitHub merge timestamp converted to `America/Fortaleza`. All final targets are `main`. Integration references are GitHub's `mergeCommit` objects; #14 and #16–#18 have one parent, so they must not be omitted by relying only on `git log --merges`. The other 32 entries have two-parent merge commits.

| PR | Merge date | Target | Integration commit | Delivered concern | Available PR check |
| --- | --- | --- | --- | --- | --- |
| [PR #1](https://github.com/VarnerDamascenoJr/sales-event-project/pull/1) | 2026-09-08 | `main` | [`0b1f9bc`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/0b1f9bc962c5af980460bb2d5a4ae114b1542a98) | Add OpenTelemetry integration | Not returned |
| [PR #2](https://github.com/VarnerDamascenoJr/sales-event-project/pull/2) | 2026-09-10 | `main` | [`0d3f4a6`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/0d3f4a6f8d55397672d2b8584fde89b877b40de0) | Add correlation metadata to sales flow | Not returned |
| [PR #3](https://github.com/VarnerDamascenoJr/sales-event-project/pull/3) | 2026-09-10 | `main` | [`1e0803e`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/1e0803e5f2b55c032f6e56eb485c7b5c8f7c9444) | Propagate correlation metadata through worker logs | Not returned |
| [PR #4](https://github.com/VarnerDamascenoJr/sales-event-project/pull/4) | 2026-09-10 | `main` | [`26d6623`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/26d6623259f5d021da237c308aa63f8dd3c05aa1) | Split email retry into dedicated worker | Not returned |
| [PR #5](https://github.com/VarnerDamascenoJr/sales-event-project/pull/5) | 2026-09-11 | `main` | [`31e291e`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/31e291e6861ec38d1caae6bf83d6a73bb9e78ca2) | Add email retry integration smoke | Not returned |
| [PR #6](https://github.com/VarnerDamascenoJr/sales-event-project/pull/6) | 2026-09-11 | `main` | [`d564548`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d564548685adff4beb48662539b5cad1f0ce9572) | Strengthen sale journey correlation | Not returned |
| [PR #7](https://github.com/VarnerDamascenoJr/sales-event-project/pull/7) | 2026-09-11 | `main` | [`eb627a6`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/eb627a619abdabeaf4dffb2b43aad4b5d404a5ba) | Propagate RabbitMQ correlation context | Not returned |
| [PR #8](https://github.com/VarnerDamascenoJr/sales-event-project/pull/8) | 2026-09-11 | `main` | [`0968cfd`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/0968cfde5315cd4e1cafaca7ea936c075aac2911) | Add OpenTelemetry business spans | Not returned |
| [PR #9](https://github.com/VarnerDamascenoJr/sales-event-project/pull/9) | 2026-09-14 | `main` | [`f0a05e4`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/f0a05e44988cb9b7b582fcd9ba1516e86ab5cff0) | Require RabbitMQ publish confirmations | Not returned |
| [PR #10](https://github.com/VarnerDamascenoJr/sales-event-project/pull/10) | 2026-09-14 | `main` | [`a208072`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/a2080726933cc0f9b27f5415a2401d3ca7841d19) | Add controlled failure scenarios | Not returned |
| [PR #11](https://github.com/VarnerDamascenoJr/sales-event-project/pull/11) | 2026-09-14 | `main` | [`f92496a`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/f92496a64f627ccce1da63ac9a654a5c0b62e31f) | Add business journey dashboard | Not returned |
| [PR #12](https://github.com/VarnerDamascenoJr/sales-event-project/pull/12) | 2026-09-18 | `main` | [`1b3ceda`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/1b3cedadb81577fc9e7791cb5eb8b7ac95fdf7dc) | Connect sales telemetry to portfolio platform | Not returned |
| [PR #13](https://github.com/VarnerDamascenoJr/sales-event-project/pull/13) | 2026-09-18 | `main` | [`00f3b35`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/00f3b356f381810e890404aa4bd1352ecf204d0c) | Export sales history for OptiFlow | Not returned |
| [PR #14](https://github.com/VarnerDamascenoJr/sales-event-project/pull/14) | 2026-09-22 | `main` | [`e033538`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/e0335380a034252f6ee81bd037cd1663405284eb) | Link final portfolio guides | Not returned |
| [PR #16](https://github.com/VarnerDamascenoJr/sales-event-project/pull/16) | 2026-09-22 | `main` | [`2f47222`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/2f47222bf2f80b47da6a5b15beeb99401f492dd4) | Add sales analytics export | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/35750465920/job/106822930044) |
| [PR #17](https://github.com/VarnerDamascenoJr/sales-event-project/pull/17) | 2026-09-22 | `main` | [`dbf115e`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/dbf115e8ff3c3aa1c760c53ba7a51477496c8654) | Add funnel conversion uncertainty | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/35770732384/job/106891486463) |
| [PR #18](https://github.com/VarnerDamascenoJr/sales-event-project/pull/18) | 2026-09-22 | `main` | [`a8319f7`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/a8319f7fde7c28051bd58138484c6169954f05fb) | Add survival analytics export | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/35773629814/job/106901190083) |
| [PR #19](https://github.com/VarnerDamascenoJr/sales-event-project/pull/19) | 2026-09-25 | `main` | [`c51bb39`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/c51bb39cd857748e5452b69aeafb480216c3e3a1) | Expose analytics export API | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36136929064/job/108077115753) |
| [PR #20](https://github.com/VarnerDamascenoJr/sales-event-project/pull/20) | 2026-09-28 | `main` | [`9d7af89`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/9d7af89523e8678b7fa05832aa554c6ef2aa3a2a) | Add demand forecast baseline to analytics export | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36416739436/job/108909557768) |
| [PR #21](https://github.com/VarnerDamascenoJr/sales-event-project/pull/21) | 2026-09-28 | `main` | [`8ebe4b6`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/8ebe4b651db9c515abbcfbeea661778db4e3aa29) | Add stockout risk analytics | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36420847781/job/108922901671) |
| [PR #22](https://github.com/VarnerDamascenoJr/sales-event-project/pull/22) | 2026-09-28 | `main` | [`64ca4cd`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/64ca4cde30805cc66a688861bd65e413392841ba) | Export optiflow simulation priors | [FAILURE](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36425014523/job/108936708197) |
| [PR #23](https://github.com/VarnerDamascenoJr/sales-event-project/pull/23) | 2026-09-30 | `main` | [`1691c4b`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/1691c4bdbc1eff00146154557e91c48e7661bdf0) | Refactor type definitions into dedicated files | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36762447460/job/110048167263) |
| [PR #24](https://github.com/VarnerDamascenoJr/sales-event-project/pull/24) | 2026-09-30 | `main` | [`c17f66b`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/c17f66b124060574de51ede3761fabf27bca1915) | Split HTTP API router responsibilities | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36763324761/job/110051131913) |
| [PR #25](https://github.com/VarnerDamascenoJr/sales-event-project/pull/25) | 2026-09-30 | `main` | [`92e8a81`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/92e8a814caf7c96c2b4044c19cda589543ce5321) | Group HTTP API routes by domain | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36764589073/job/110055432644) |
| [PR #26](https://github.com/VarnerDamascenoJr/sales-event-project/pull/26) | 2026-09-30 | `main` | [`5843381`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/58433813c20055755cb20f61b145cd53d6c9fa8b) | Use correlation header constants and split router tests | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36768005004/job/110066942636) |
| [PR #27](https://github.com/VarnerDamascenoJr/sales-event-project/pull/27) | 2026-10-01 | `main` | [`25df287`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/25df287e2b1cd7b7da5046aeff7dff423fd460b6) | Split rabbitmq messaging responsibilities | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36854945930/job/110345097115) |
| [PR #28](https://github.com/VarnerDamascenoJr/sales-event-project/pull/28) | 2026-10-01 | `main` | [`d8c868e`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d8c868e8b1fc1f1970268821298bd2ea033adea8) | Split observability responsibilities | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/36857469664/job/110353300849) |
| [PR #29](https://github.com/VarnerDamascenoJr/sales-event-project/pull/29) | 2026-10-07 | `main` | [`bbf9c4e`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/bbf9c4e0e5dddbd415a5ec017efbb4aa5f38a9ac) | Fix NaN in sales analytics export | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/37520941264/job/112465859131) |
| [PR #30](https://github.com/VarnerDamascenoJr/sales-event-project/pull/30) | 2026-10-07 | `main` | [`0ddf555`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/0ddf5556c77c264c3784d85bc22e34f4a7eab47f) | Return 500 when analytics export JSON cannot marshal | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/37614128543/job/112768258247) |
| [PR #31](https://github.com/VarnerDamascenoJr/sales-event-project/pull/31) | 2026-10-08 | `main` | [`8697df3`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/8697df38e1f68c064c56543fbd460464172590fd) | Align local demo API keys | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/37851056366/job/113563771146) |
| [PR #32](https://github.com/VarnerDamascenoJr/sales-event-project/pull/32) | 2026-10-09 | `main` | [`8961488`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/8961488d192509241efbddf835945e3aff697b11) | Add analytics demo data generator | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/37941419434/job/113856471124) |
| [PR #33](https://github.com/VarnerDamascenoJr/sales-event-project/pull/33) | 2026-10-12 | `main` | [`5f98b27`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/5f98b27cd5530e136d60bba873fb51eef9b6c768) | Refactor analytics forecast and funnel responsibilities | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38329258317/job/115075002993) |
| [PR #34](https://github.com/VarnerDamascenoJr/sales-event-project/pull/34) | 2026-10-12 | `main` | [`d1c2334`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d1c233492bce33ad98c9e7d125c5ea1c054e436b) | Refactor analytics priors and stockout responsibilities | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38332487893/job/115085135887) |
| [PR #35](https://github.com/VarnerDamascenoJr/sales-event-project/pull/35) | 2026-10-13 | `main` | [`81c8f38`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/81c8f3875fe096186277f6ae7bf3223c06b6414a) | Separate HTTP metrics middleware from metric definitions | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38482657073/job/115588695960) |
| [PR #36](https://github.com/VarnerDamascenoJr/sales-event-project/pull/36) | 2026-10-13 | `main` | [`5497dcf`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/5497dcf2acda4dacc65b6a2a722b5e1f7789d539) | Cover logging, metrics and telemetry | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38490012594/job/115612728388) |
| [PR #37](https://github.com/VarnerDamascenoJr/sales-event-project/pull/37) | 2026-10-14 | `main` | [`d542ee3`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d542ee346bcd3ededc746b6cb31cec33ee7d0eac) | Split export responsibilities and add tests | [SUCCESS](https://github.com/VarnerDamascenoJr/sales-event-project/actions/runs/38667791073/job/116203600473) |

## Direct commits and publication boundary

The [May](../2026-05.md), [June](../2026-06.md), and [August](../2026-08.md) journals preserve work outside the PR sequence. P5.4 CI entered `main` through [`4c99c0c`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/4c99c0c336d1e02a200ba4dd5246ec95dedbb423) and [`22e0d44`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/22e0d4421e42dedd34751a1de0a7af669a2d291c) on September 21. [PR #15](https://github.com/VarnerDamascenoJr/sales-event-project/pull/15) is closed without merge; its earlier `4444e72` proposal is not an ancestor of `d542ee3`. It is not counted as a merged PR or substituted for the delivered commits.

The source working tree stayed clean on `refactor/analyticsdb-export` at `9c85b4b`. Fetch updated `origin/main` from `5497dcf` to `d542ee3`; source files and branch selection were preserved. The 36 integration objects were checked for reachability from that baseline.

At collection on **2026-11-10**, the history addition remained local and uncommitted on `docs/sales-event-project-history`; no new commits, pull requests, or publication were created. On **2026-11-11**, the owner authorized publishing that history branch with one file per commit and opening a PR for review. No source backlog was pruned or shared task status changed.
