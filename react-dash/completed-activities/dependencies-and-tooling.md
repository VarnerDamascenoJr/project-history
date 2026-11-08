# Dependencies and Tooling — React Dash

[Archive index](README.md) · [Project overview](../README.md)

## Vite, TypeScript, and context-owned types

August 2024 added TypeScript configuration; May 2026 performed the actual application/test migration and replaced the Create React App build with Vite. PR #30 later consolidated interfaces, aliases, props, and state contracts into context-owned files and constrained chart keys to their data series. Production JS/CSS hashes were reported unchanged for that refactor.

**References:** [configuration](../2024-08.md), [migration](../2026-05.md), [PR #30](https://github.com/VarnerDamascenoJr/react-dash/pull/30), [type organization](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/type-organization.md).

## Frontend style and browser tooling

PR #9 added the Playwright baseline and stabilized MUI imports/Vite optimization. PR #13 introduced incremental rem-first checks with explicit `px-ok` exceptions. PRs #14–#18 converted the existing style layers. Browser coverage remains fixture-first; optional Sales API execution is separate.

CFX6's repeatable-install goal is not imported as fully closed: browser installation is documented, but the latest local evidence still required installed Chrome and a temporary configuration on Ubuntu 20.04.

**References:** [PR #9](https://github.com/VarnerDamascenoJr/react-dash/pull/9), [PR #13](https://github.com/VarnerDamascenoJr/react-dash/pull/13), [PR #14](https://github.com/VarnerDamascenoJr/react-dash/pull/14), [PR #15](https://github.com/VarnerDamascenoJr/react-dash/pull/15), [PR #16](https://github.com/VarnerDamascenoJr/react-dash/pull/16), [PR #17](https://github.com/VarnerDamascenoJr/react-dash/pull/17), [PR #18](https://github.com/VarnerDamascenoJr/react-dash/pull/18), [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25).

## Repository workflow and frontend CI

PR #26 added local React/frontend-validation skills and a documentation retrieval CLI using trusted source configuration and lockfile versions. PR #27 added ESLint and the frontend CI job. At the baseline, CI uses Node 22, installs dependencies, and runs lint, type checking, and Vitest. Build, browser, and real Sales API validation are not steps in that workflow.

**References:** [PR #26](https://github.com/VarnerDamascenoJr/react-dash/pull/26), [PR #27](https://github.com/VarnerDamascenoJr/react-dash/pull/27), [committed CI job](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/.github/workflows/ci.yml).

## Shared utilities and maintenance limits

Shared formatters reuse `Intl` instances per locale. Generic CSV, JSON/Blob downloads, and preference storage are consolidated in `src/utils`; analytics policies stay in their owning feature. Common UI is colocated with its types, styles, and tests. This records the final organization, including follow-ups nested in the shared-components branch.

Recharts zero-size warnings in JSDOM and large-build warnings remain in the dated evidence; PR #25 also notes outdated Browserslist data. A successful test run does not complete CFX7's warning-cleanup criteria.

**References:** [PR #32](https://github.com/VarnerDamascenoJr/react-dash/pull/32), [PR #33](https://github.com/VarnerDamascenoJr/react-dash/pull/33), [PR #34](https://github.com/VarnerDamascenoJr/react-dash/pull/34), [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25), [reuse and utility boundaries](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/reusability.md).
