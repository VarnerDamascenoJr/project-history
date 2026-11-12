# Project History

A personal record of completed work, technical decisions, validation results, and lessons learned across software projects.

Start with a project overview, then follow its monthly journal. Detailed activity archives preserve the original task identifiers and supporting notes.

## Projects

| Project | Description | Recorded period | Latest delivery |
| --- | --- | --- | --- |
| [Exchange Matching](exchange-matching/README.md) | BTC/USD exchange with a separate API and matching worker | July–November 2026 | Available, reserved, and total wallet balances, merged on November 6 |
| [React Dash](react-dash/README.md) | Frontend-only Sales Event analytics dashboard with fixture/API loading and browser exports | October 2023–November 2026 | Optional Sales API evidence automation, merged on November 4 |
| [Sales Event](sales-event-project/README.md) | Event-driven ticket sales backend with payments, ticket delivery, observability, and analytics exports | May–October 2026 | Analytics database exporter refactor and coverage, merged on October 14 |

## Organization

```text
project-history/
├── README.md
├── exchange-matching/
│   ├── README.md
│   ├── YYYY-MM.md
│   └── completed-activities/
│       ├── README.md
│       ├── backend.md
│       ├── application-security.md
│       ├── dependencies-and-tooling.md
│       └── validation-and-publication.md
├── react-dash/
│   ├── README.md
│   ├── YYYY-MM.md
│   └── completed-activities/
│       ├── README.md
│       ├── frontend.md
│       ├── application-security.md
│       ├── dependencies-and-tooling.md
│       └── validation-and-publication.md
└── sales-event-project/
    ├── README.md
    ├── YYYY-MM.md
    └── completed-activities/
        ├── README.md
        ├── backend.md
        ├── application-security.md
        ├── dependencies-and-tooling.md
        └── validation-and-publication.md
```

Only months with recorded work have a journal. Each project uses the same small structure: an overview, monthly entries, and an activity archive when needed. Organize growing archives into a folder with a short index and four broad areas: backend or frontend according to the project, application security, dependencies and tooling, and validation and publication. Specific problems belong in sections within those areas.

## Writing conventions

- Write all documentation, filenames, and future commit messages in English.
- Use `YYYY-MM-DD` dates in the `America/Fortaleza` time zone.
- Describe the problem, resulting behavior, relevant decisions, validation, and references.
- Preserve original task identifiers such as `BE-08` and `SEC-088`.
- Link to source commits, pull requests, and technical documentation. Use commit-pinned links for evidence that should remain stable.
- Distinguish implementation dates, validation dates, and merge dates.
- Report validation as a dated result; importing a result does not mean the checks were rerun.
- Keep pending work in the project's active backlog. Historical mentions of pending work are dated context.
- Preserve earlier entries when recording a later correction or follow-up.

A new entry can be as small as:

```markdown
## YYYY-MM-DD — Delivery title

**Problem:** What needed to change.

**Outcome:** What was delivered and why the approach was chosen.

**Validation:** Checks actually performed and any relevant limits.

**References:** Task IDs, pull requests, commits, and supporting evidence.
```

## Initial import

Prepared on **2026-11-02** from the local Exchange Matching Git history, its local backlog, repository documentation, and existing validation reports. Earlier entries reconstructed from Git are identified as retrospective summaries.

Updated on **2026-11-07** through Exchange Matching PR #39, including the matching recovery and monetary invariant deliveries in PRs #37 and #38. The update uses the pulled source history, committed documentation, and GitHub PR descriptions and check results; it does not rerun application validation.

React Dash was imported on **2026-11-07** through source commit `fa02c9d`, covering the available history from October 2023 and all 34 merged PRs. The import distinguishes intermediate-branch merges, main integration dates, reported validation, and simulated API evidence. No application validation was rerun.

Sales Event was collected on **2026-11-10** through source commit `d542ee3`, covering May–October 2026 and all **36 merged PRs**. Its archive includes the complete integration register with dates, commits, and available checks, distinguishes closed PR #15 from direct CI commits, and maps the original P1/P4/P5, S1, and CFX identifiers to their source-owned deliveries. Prepared as a local draft on `docs/sales-event-project-history`, the addition was authorized for publication with one file per commit and a review PR on **2026-11-11**. No application validation was rerun.

The initial import was prepared as a **local draft for review**. On **2026-11-07**, the owner created the [public remote repository](https://github.com/VarnerDamascenoJr/project-history), configured it as `origin`, and authorized the initial commits, one file per commit, on `docs/exchange-matching-history`.

Detailed logs, screenshots, database fixtures, and raw reports remain in their existing local evidence directories. The journals identify those locations without copying their contents into this repository. Some original reports are in Portuguese; the journal summaries are in English.
