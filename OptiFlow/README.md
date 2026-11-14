# OptiFlow

An operational optimization and statistical decision project for delivery/allocation scenarios: compare heuristics, bounded enumeration, and OR-Tools, then evaluate declared costs, constraints, uncertainty, and decision preferences.

**Source:** [VarnerDamascenoJr/OptiFlow](https://github.com/VarnerDamascenoJr/OptiFlow)  
**Local checkout:** `/home/varner/aprendizagem/projetos/OptiFlow`  
**History collected:** 2026-11-14  
**Source baseline:** [`b96520f`](https://github.com/VarnerDamascenoJr/OptiFlow/commit/b96520fec39e2b865104e45b5c8e6dfeb511c096), the merge of [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63) into `main` on **2026-11-13** in `America/Fortaleza`.

## Reading guide

| Record | Coverage |
| --- | --- |
| [August 2026](2026-08.md) | Vision, mathematical learning path, and technology evaluation |
| [September 2026](2026-09.md) | Deterministic core, reverted domain experiment, portfolio integration, simulation, and inference |
| [October 2026](2026-10.md) | Controlled studies, shared helpers, golden data, and statistical communication |
| [November 2026](2026-11.md) | Route correctness, OR-Tools, numeric precision, forecasting, and NestJS backend |
| [Activity archive](completed-activities/README.md) | Four broad areas, task ownership, validation evidence, and the complete PR register |

## Current architecture and decisions

The recorded snapshot uses Node.js 24, a JavaScript optimization/statistics core, a TypeScript NestJS backend, and Python OR-Tools CP-SAT. The local browser console is served by the API. Persisted scenarios/results use JSON; pending work uses an in-memory queue.

- Keep one scenario/route contract across strategies and report solver status/bounds explicitly.
- Preserve delivery planning as the executable domain. The September sales-decision reframe was reverted; Sales inputs later entered through imports and priors.
- Limit exact enumeration to small instances and distinguish it from November's native OR-Tools integration.
- Reconstruct the integer solver model using its scales before converting to public units; retain strict capacity/time/distance checks.
- Make uncertainty, priors, seeds, sample sizes, loss preferences, and statistical limits visible in reports.
- Separate chronological forecasting validation from population claims or automatic creation of operational orders.
- Share a repository/queue per NestJS application while keeping optimization rules outside the framework.

## Latest recorded validation

On **2026-11-13**, [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63) reports **121 passing tests**, a production Docker build, and container HTTP checks for the console, health, scenarios, an OR-Tools run, and metrics. OR-Tools returned `OPTIMAL` with cost **744**. The same PR records `npm audit --omit=dev` with zero findings for that dependency set.

[PR CI](https://github.com/VarnerDamascenoJr/OptiFlow/actions/runs/43514509226) and [main CI](https://github.com/VarnerDamascenoJr/OptiFlow/actions/runs/43514985168) passed. The committed workflow installs Node/Python/OR-Tools, runs `npm test` (including its backend-build hook), the sample, enumeration/OR-Tools benchmarks, simulation, risk comparison, forecasting, and whitespace checking. It does not itself prove a container build or complete portfolio rehearsal.

These are historical results, not new executions by this import. See [validation and publication](completed-activities/validation-and-publication.md) for candidate-specific counts, raw-evidence locations, and synthetic-study limits.

## Import and task boundaries

The source checkout remains on local `main` at `6ae6998`, **64 commits behind** the recorded `origin/main` reference. The baseline was confirmed against GitHub without switching or updating source files. Among **63 merged repository PRs**, **57** have integration commits reachable from the baseline; **PRs #10–#15** are merged into intermediate documentation branches only. PRs #36–#38 have single-parent integration commits; the other 54 reachable integrations have two parents. PR #2 is reachable but was reverted by PR #3.

The portfolio and statistics backlogs live here but span three repositories. P1 and S1 principally describe Sales; P2 and S2 principally describe the observability platform. Their status updates are not OptiFlow implementations. The [archive task map](completed-activities/README.md#task-sources-and-ownership) retains all 36 portfolio and 28 statistical identifiers in compact groups.

Detailed backlog checkboxes are recorded as found, while some overview text retains earlier status wording. The README still leaves API/UI-flow tests unchecked despite later API tests. This history records delivered evidence and does not automatically reconcile or close those source entries.

JSON history assumes one writer; pending jobs are not recovered after a crash. Solvers run synchronously inside the API process. Transactional persistence, a durable queue, and isolated workers remain future work. Demand forecasting uses a synthetic baseline fixture, and the integrated research examples state their own assumptions and validity limits.

Versioned study summaries were inspected in source. Older raw portfolio/rehearsal artifacts refer to `/Users/varnerdamasceno/github-varner/evidence/`, which was unavailable here; no local OptiFlow directory was found under `/home/varner/.codex/reports`. Raw evidence was not copied into this repository. Existing histories and source task statuses were preserved.

## Source documentation at the baseline

- [Project README](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/README.md)
- [NestJS architecture and runtime limits](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/backend-architecture.md)
- [Mathematical formulation](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/mathematical-formulation.md)
- [OR-Tools model and guarantees](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/or-tools-solver.md)
- [Demand forecasting](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/demand-forecasting.md)
- [Portfolio backlog](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/portfolio-project-backlog.md)
- [Statistical backlog](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/portfolio-statistics-masters-backlog.md)
- [Statistical technical report](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/portfolio-statistical-technical-report.md)
- [Actual CI workflow](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/.github/workflows/ci.yml)
