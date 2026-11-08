# Validation and Publication — React Dash

[Archive index](README.md) · [Project overview](../README.md)

## Evidence method

Imported on **2026-11-07** from Git, source documentation at `fa02c9d`, all 34 merged PR descriptions, and the latest GitHub check/run results. PR descriptions report prior validation; this import did not rerun application tests, builds, dependency audits, or backend integration. No standalone local React Dash report directory was found under `/home/varner/.codex/reports`.

The October 6 rehearsal path is recorded in the source backlog as `/Users/varnerdamasceno/github-varner/evidence/react-dash-sales-api-simulation-2026-10-06/`. It was not available for inspection, so its raw outputs/screenshots were not revalidated or copied. Acceptance commands in the backlog are planned checks, not execution evidence.

## Candidate-specific validation

Dates below are PR merge dates in `America/Fortaleza`. The counts come from each PR's candidate description, not necessarily a new run on its merge date. Totals from different candidates must not be added together.

| PR | Merge date | Reported automated results | Limits |
| --- | --- | --- | --- |
| [PR #19](https://github.com/VarnerDamascenoJr/react-dash/pull/19) | 2026-09-27 | 10 full browser-suite tests | Auth delivery; desktop/mobile baseline |
| [PR #20](https://github.com/VarnerDamascenoJr/react-dash/pull/20) | 2026-09-27 | 12 full browser-suite tests | Adds theme scenarios to the preceding baseline |
| [PR #28](https://github.com/VarnerDamascenoJr/react-dash/pull/28) | 2026-10-17 | 27 Vitest; 16 browser | Fixture/intercepted API; known warnings |
| [PR #29](https://github.com/VarnerDamascenoJr/react-dash/pull/29) | 2026-10-17 | 43 Vitest; 22 browser | Fixture/intercepted API; known warnings |
| [PR #31](https://github.com/VarnerDamascenoJr/react-dash/pull/31) | 2026-10-17 | 61 Vitest; 26 browser | Merged into the type branch; visual production checks reported |
| [PR #33](https://github.com/VarnerDamascenoJr/react-dash/pull/33) | 2026-10-18 | 75 Vitest; 26 browser | Merged into the shared-components branch; legacy List browser check reported |
| [PR #34](https://github.com/VarnerDamascenoJr/react-dash/pull/34) | 2026-10-18 | 76 Vitest; 26 browser | Merged into the shared-components branch; compiled-CSS preservation reported |
| [PR #30](https://github.com/VarnerDamascenoJr/react-dash/pull/30) | 2026-11-03 | 45 Vitest; 22 browser | Description concerns the earlier type candidate; nested login later reports higher totals |
| [PR #32](https://github.com/VarnerDamascenoJr/react-dash/pull/32) | 2026-11-03 | 75 Vitest; 26 browser | Description concerns the earlier shared-UI candidate; nested PR #34 reports 76 Vitest |
| [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25) | 2026-11-04 | 76 Vitest; 28 baseline browser passed; 2 optional API cases skipped | Optional cases and PNG command separately passed against a simulated HTTP API |

Earlier PRs list validation commands without numeric totals. Their descriptions remain the source for those claims; no counts were reconstructed from test files or commit messages.

## Latest API evidence and execution limits

PR #25 reports passing lint, type checking, extra E2E compilation, style checks, production build, and whitespace checks. Production JS/CSS hashes remained unchanged. Both optional scenarios and the command producing five PNGs passed against a simulated HTTP server using the fixture. The real Sales backend was not running.

Browser execution used installed Chrome with a temporary 90-second setting because the expected Playwright Chromium did not support the host Ubuntu 20.04. This is not evidence of a clean supported-browser installation on that host. Known Recharts, bundle-size, and Browserslist warnings remained.

[PR Frontend checks](https://github.com/VarnerDamascenoJr/react-dash/actions/runs/41945639420) concluded successfully. [Main CI](https://github.com/VarnerDamascenoJr/react-dash/actions/runs/41945863657) also succeeded at `fa02c9d`. The committed job covers dependency installation, lint, TypeScript, and Vitest; it does not cover browser execution, build, real API integration, or a dependency audit.

## Delivery register

Every merged PR reachable from the baseline appears once below. Dates are GitHub merge timestamps converted to `America/Fortaleza`. Target branches distinguish intermediate branch deliveries from arrival on `main`; implementation commits can predate either event. PRs are ordered by merge date, not numeric ID.

| PR | Merge date | Target branch | Delivered concern |
| --- | --- | --- | --- |
| [PR #1](https://github.com/VarnerDamascenoJr/react-dash/pull/1) | 2026-09-24 | `main` | Sales analytics model and fixture |
| [PR #2](https://github.com/VarnerDamascenoJr/react-dash/pull/2) | 2026-09-24 | `main` | Optional Sales API client |
| [PR #3](https://github.com/VarnerDamascenoJr/react-dash/pull/3) | 2026-09-24 | `main` | Analytics overview |
| [PR #4](https://github.com/VarnerDamascenoJr/react-dash/pull/4) | 2026-09-24 | `main` | Browser exports |
| [PR #5](https://github.com/VarnerDamascenoJr/react-dash/pull/5) | 2026-09-25 | `main` | Demo readiness documentation |
| [PR #6](https://github.com/VarnerDamascenoJr/react-dash/pull/6) | 2026-09-25 | `main` | API controls and non-secret settings |
| [PR #7](https://github.com/VarnerDamascenoJr/react-dash/pull/7) | 2026-09-25 | `main` | Focused Home sections |
| [PR #8](https://github.com/VarnerDamascenoJr/react-dash/pull/8) | 2026-09-25 | `main` | MUI dashboard shell |
| [PR #9](https://github.com/VarnerDamascenoJr/react-dash/pull/9) | 2026-09-26 | `main` | Agent workflow and browser baseline |
| [PR #10](https://github.com/VarnerDamascenoJr/react-dash/pull/10) | 2026-09-26 | `main` | Responsive panel and table layout |
| [PR #11](https://github.com/VarnerDamascenoJr/react-dash/pull/11) | 2026-09-26 | `main` | Centralized event-table copy |
| [PR #12](https://github.com/VarnerDamascenoJr/react-dash/pull/12) | 2026-09-26 | `main` | Sidebar section navigation |
| [PR #13](https://github.com/VarnerDamascenoJr/react-dash/pull/13) | 2026-09-26 | `main` | Incremental rem style validation |
| [PR #14](https://github.com/VarnerDamascenoJr/react-dash/pull/14) | 2026-09-27 | `main` | Home rem conversion |
| [PR #15](https://github.com/VarnerDamascenoJr/react-dash/pull/15) | 2026-09-27 | `main` | Global rem conversion |
| [PR #16](https://github.com/VarnerDamascenoJr/react-dash/pull/16) | 2026-09-27 | `main` | Login rem conversion |
| [PR #17](https://github.com/VarnerDamascenoJr/react-dash/pull/17) | 2026-09-27 | `main` | Reusable component rem conversion |
| [PR #18](https://github.com/VarnerDamascenoJr/react-dash/pull/18) | 2026-09-27 | `main` | Legacy page rem conversion |
| [PR #19](https://github.com/VarnerDamascenoJr/react-dash/pull/19) | 2026-09-27 | `main` | Auth/session browser coverage |
| [PR #20](https://github.com/VarnerDamascenoJr/react-dash/pull/20) | 2026-09-27 | `main` | Theme browser coverage |
| [PR #21](https://github.com/VarnerDamascenoJr/react-dash/pull/21) | 2026-10-06 | `main` | Integrated-demo correction backlog |
| [PR #22](https://github.com/VarnerDamascenoJr/react-dash/pull/22) | 2026-10-07 | `main` | Empty API response fallback |
| [PR #23](https://github.com/VarnerDamascenoJr/react-dash/pull/23) | 2026-10-08 | `main` | Local demo-key documentation |
| [PR #24](https://github.com/VarnerDamascenoJr/react-dash/pull/24) | 2026-10-09 | `main` | Demo generator instructions and English docs |
| [PR #26](https://github.com/VarnerDamascenoJr/react-dash/pull/26) | 2026-10-10 | `main` | Repository skills and library documentation retrieval |
| [PR #27](https://github.com/VarnerDamascenoJr/react-dash/pull/27) | 2026-10-11 | `main` | Frontend lint and CI |
| [PR #28](https://github.com/VarnerDamascenoJr/react-dash/pull/28) | 2026-10-17 | `main` | Home loading/export hooks |
| [PR #29](https://github.com/VarnerDamascenoJr/react-dash/pull/29) | 2026-10-17 | `main` | Portuguese/English localization |
| [PR #31](https://github.com/VarnerDamascenoJr/react-dash/pull/31) | 2026-10-17 | `refactor/domain-types` | Login composition and complete return destinations |
| [PR #33](https://github.com/VarnerDamascenoJr/react-dash/pull/33) | 2026-10-18 | `refactor/shared-components-utils` | Reusable List page introduction |
| [PR #34](https://github.com/VarnerDamascenoJr/react-dash/pull/34) | 2026-10-18 | `refactor/shared-components-utils` | Common UI contexts and translated List introduction |
| [PR #30](https://github.com/VarnerDamascenoJr/react-dash/pull/30) | 2026-11-03 | `main` | Context-owned types and chart contracts |
| [PR #32](https://github.com/VarnerDamascenoJr/react-dash/pull/32) | 2026-11-03 | `main` | Shared UI and utility consolidation |
| [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25) | 2026-11-04 | `main` | Optional Sales API evidence automation |

## Integration and import boundary

PR #31 merged into `refactor/domain-types`; PRs #33 and #34 merged into `refactor/shared-components-utils`. They reached `main` through PRs #30 and #32 on November 3. The latest main delivery is PR #25 on November 4, not PR #34 despite its higher number.

The source baseline is [`fa02c9d`](https://github.com/VarnerDamascenoJr/react-dash/commit/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2). The history import preserves original task identifiers and dated limits, leaves task closure to the source backlog, and does not publish changes in the source application repository.
