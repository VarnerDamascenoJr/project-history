# React Dash

A frontend-only analytics dashboard for the `sales-analytics-export.v1` contract produced by Sales Event. The default experience uses a versioned local fixture; an optional API path loads operational analytics for viewing and browser-side export.

**Source:** [VarnerDamascenoJr/react-dash](https://github.com/VarnerDamascenoJr/react-dash)  
**Local checkout:** `/home/varner/aprendizagem/projetos/react-dash`  
**History imported:** 2026-11-07  
**Source baseline:** [`fa02c9d`](https://github.com/VarnerDamascenoJr/react-dash/commit/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2), the merge of [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25) into `main` on 2026-11-04 in `America/Fortaleza`.

## Reading guide

| Record | Coverage |
| --- | --- |
| [October 2023](2023-10.md) | Create React App initialization and package setup |
| [November 2023](2023-11.md) | Administrative dashboard components, navigation, and mock tables |
| [December 2023](2023-12.md) | Original pages, forms, global styling, and theme context |
| [April 2024](2024-04.md) | README update |
| [August 2024](2024-08.md) | Initial TypeScript configuration |
| [May 2026](2026-05.md) | Vite/TypeScript migration |
| [June 2026](2026-06.md) | Demo authentication, shell redesign, and architecture documentation |
| [September 2026](2026-09.md) | Sales analytics, exports, responsive UI, style checks, and browser coverage |
| [October 2026](2026-10.md) | Integrated-demo findings, fallback, localization, CI, and stacked refactors |
| [November 2026](2026-11.md) | Main-branch integrations and optional Sales API evidence automation |
| [Activity archive](completed-activities/README.md) | Four broad areas, task boundaries, validation, and the 34-PR delivery register |

## Technical context and decisions

React 18, TypeScript, Vite, MUI/Data Grid, Recharts, Sass, i18next, Vitest, and Playwright form the current stack. The active routes are the demo login and protected `/` dashboard; sidebar domain entries navigate to sections. Legacy users/products/forms remain in source but are outside the active product.

- Keep fixture loading deterministic and API integration optional, with readable fallback.
- Keep analytics types, transformers, client, and exporters in their domain; share UI and utilities only where responsibilities match.
- Store non-secret filters and language preferences safely; keep the API key in memory. `VITE_*` values are browser-visible.
- Treat client-side login as a demonstration, not a server-enforced security boundary. This repository has no backend, database, ORM, or migrations.
- Bundle Portuguese/English catalogs, translate feedback at render time, preserve BRL and raw export data, and use context-owned type contracts.
- Keep baseline browser tests independent of the Sales service; run real-API evidence as an explicit optional path.

## Latest recorded validation

On **2026-11-04**, [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25) reports **76 Vitest tests** and **28 baseline browser tests** passing, with **2 optional API tests skipped** without a credential. Those optional scenarios and five PNG captures passed separately against a **simulated HTTP server**, not the real Sales backend. Local runs used installed Chrome with a temporary configuration because of the host's Playwright Chromium support limit.

Lint, type checking, additional E2E compilation, style-unit checks, and build passed according to the PR. [Main CI](https://github.com/VarnerDamascenoJr/react-dash/actions/runs/41945863657) succeeded at the recorded baseline; that workflow runs lint, type checking, and Vitest. It does not establish browser/build results. Known Recharts JSDOM, bundle-size, and Browserslist warnings remain documented. See [validation and publication](completed-activities/validation-and-publication.md) for candidate-specific counts and limits.

These results are imported evidence. No application tests, build, audit, or real-backend rehearsal were rerun to create this history.

## Import boundary and open work

The import uses `origin/main` at `fa02c9d`, confirmed against GitHub. The source checkout remains on `refactor/shared-components-utils` at `a7fa030`; it is eight commits behind the recorded baseline. No checkout switch or source edits were needed. All **34 merged PRs** are reachable from the baseline, including PRs #31, #33, and #34 first merged into intermediate branches.

The source backlog mixes original planning with later progress. RD1, RD3, RD4, and RD5 explicitly describe completion; RD0 retains a completion criterion. RD2's technical base and later UI controls are delivered, but its original wiring note remains. RD4.1 is still described as in progress despite its completed sub-deliveries. This history does not rewrite those statuses.

| Correction | Imported evidence and boundary |
| --- | --- |
| CFX1 | Numeric/JSON correction belongs to Sales Event; no backend completion imported here. |
| CFX2 | Frontend empty-response fallback delivered in PR #22; backend HTTP serialization behavior is outside this import. |
| CFX3 | Dashboard demo-key documentation/tests aligned in PR #23; no cross-repository completion inferred. |
| CFX4 | Dashboard generator instructions delivered in PR #24; generator ownership remains Sales Event. |
| CFX5 | Automation delivered in PR #25; latest execution used a simulated API, not the real backend. |
| CFX6 | Browser installation is documented; latest local validation still used a host-specific Chrome workaround. |
| CFX7 | Recharts JSDOM warning remains in the latest validation. |
| CFX8 | Newest-first table ordering is a recorded request; no verified completion imported. |
| CFX9 | Demo-state reset is cross-repository planning; no verified completion imported. |

The authoritative task descriptions remain in the [source backlog](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/analytics-dashboard-backlog.md). Historical recommendations are not new task-completion decisions. No local React Dash report directory was found under `/home/varner/.codex/reports`; the October rehearsal path recorded in the source was unavailable here. PR descriptions and committed documentation supply the dated evidence, with successful latest CI checked separately.

## Source documentation at the baseline

- [Project README](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/README.md)
- [Architecture](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/architecture.md)
- [Localization](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/localization.md)
- [Type ownership](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/type-organization.md)
- [Shared UI and utilities](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/reusability.md)
- [Testing and optional API evidence](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/testing.md)
- [Demo checklist](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/demo-checklist.md)
- [Actual frontend CI scope](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/.github/workflows/ci.yml)
