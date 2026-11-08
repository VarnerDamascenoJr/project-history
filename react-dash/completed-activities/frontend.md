# Frontend — React Dash

[Archive index](README.md) · [Project overview](../README.md)

## Original dashboard and modern application shell

The 2023 foundation introduced navigation, charts, widgets, mock tables, and legacy pages. Vite/TypeScript migration followed in May 2026, then demo login and reusable shell composition in June. The active Sales analytics experience is distinct from those legacy mock entities.

**References:** [2023 journals](../2023-11.md), [migration](../2026-05.md), [shell delivery](../2026-06.md).

## Analytics contract and fixture-first product

RD1 established `sales-analytics-export.v1`, local fixture data, and pure transformations for KPIs, windows, funnel/survival, event rows, and CSV rows. RD2 added the optional API client and readable fallback; PR #6 supplied visual filters and non-secret preference persistence. RD3 redesigned the overview and redirected generic users/products navigation away from the active route tree.

**References:** [PR #1](https://github.com/VarnerDamascenoJr/react-dash/pull/1), [PR #2](https://github.com/VarnerDamascenoJr/react-dash/pull/2), [PR #3](https://github.com/VarnerDamascenoJr/react-dash/pull/3), [PR #6](https://github.com/VarnerDamascenoJr/react-dash/pull/6).

## Browser exports and demo readiness

RD4 delivers raw JSON, event/window CSV, deterministic filenames, and chart PNG downloads. RD5 documents fixture/API setup and the demo checklist. CFX2's frontend fix handles empty successful responses without breaking the fixture fallback. CFX4's dashboard documentation explains the Sales generator rather than implementing it here.

**References:** [PR #4](https://github.com/VarnerDamascenoJr/react-dash/pull/4), [PR #5](https://github.com/VarnerDamascenoJr/react-dash/pull/5), [PR #22](https://github.com/VarnerDamascenoJr/react-dash/pull/22), [PR #24](https://github.com/VarnerDamascenoJr/react-dash/pull/24).

## Responsive MUI layout and navigation

RD4.1 sub-deliveries split Home sections, moved shell elements to MUI, centralized table copy, shared panel presentation, contained table scrolling, and added real section anchors. The rem migration spans Home, global tokens, login, reusable components, and legacy pages. These deliveries do not override the umbrella task's source status of in progress.

**References:** [PR #7](https://github.com/VarnerDamascenoJr/react-dash/pull/7), [PR #8](https://github.com/VarnerDamascenoJr/react-dash/pull/8), [PR #10](https://github.com/VarnerDamascenoJr/react-dash/pull/10), [PR #11](https://github.com/VarnerDamascenoJr/react-dash/pull/11), [PR #12](https://github.com/VarnerDamascenoJr/react-dash/pull/12), [PR #14](https://github.com/VarnerDamascenoJr/react-dash/pull/14), [PR #15](https://github.com/VarnerDamascenoJr/react-dash/pull/15), [PR #16](https://github.com/VarnerDamascenoJr/react-dash/pull/16), [PR #17](https://github.com/VarnerDamascenoJr/react-dash/pull/17), [PR #18](https://github.com/VarnerDamascenoJr/react-dash/pull/18).

## Localization and shared UI

PR #28 separated loading/settings and export orchestration into hooks. PR #29 added bundled `pt-BR`/`en-US` catalogs, translated feedback, regional formats, and Data Grid localization, preserving BRL and raw JSON/CSV contracts. Later deliveries centralized reusable components and utility functions, extracted List's introduction, and colocated common UI by responsibility.

PRs #31, #33, and #34 merged into intermediate branches in October. PRs #30 and #32 brought their stack into `main` on November 3. The [delivery register](validation-and-publication.md#delivery-register) retains both target branches and dates.

**References:** [PR #28](https://github.com/VarnerDamascenoJr/react-dash/pull/28), [PR #29](https://github.com/VarnerDamascenoJr/react-dash/pull/29), [PR #30](https://github.com/VarnerDamascenoJr/react-dash/pull/30), [PR #31](https://github.com/VarnerDamascenoJr/react-dash/pull/31), [PR #32](https://github.com/VarnerDamascenoJr/react-dash/pull/32), [PR #33](https://github.com/VarnerDamascenoJr/react-dash/pull/33), [PR #34](https://github.com/VarnerDamascenoJr/react-dash/pull/34), [final shared component boundaries](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/reusability.md).
