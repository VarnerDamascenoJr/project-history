# Dependencies and Tooling — OptiFlow

[Archive index](README.md) · [Project overview](../README.md)

## Runtime, framework, and solver dependencies

The deterministic JavaScript core started on Node.js 24. The November snapshot pins NestJS 12.5.0 and TypeScript for the backend, with Python 3.10+ and OR-Tools CP-SAT 9.15.6755 for the native solver. CLI heuristics/enumeration remain distinct from the Python-backed strategy.

`pretest` and `preapi` build the backend. Direct callers of the internal application factory must build first and adopt the asynchronous NestJS factory with `app.listen()`/`app.close()`. Public npm commands perform the required build automatically.

**References:** [PR #1](https://github.com/VarnerDamascenoJr/OptiFlow/pull/1), [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60), [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63), [scripts and pinned Node dependencies](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/package.json), [pinned solver dependency](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/requirements-solver.txt).

## Shared helpers and module ownership

Source helper extraction, common parsing/formatting, route modules, and CLI validation were delivered incrementally. NestJS later took ownership of the route table while reusing handlers and optimization rules. Keep those dated responsibilities distinct when reading older documents.

**References:** [PR #35](https://github.com/VarnerDamascenoJr/OptiFlow/pull/35), [PR #53](https://github.com/VarnerDamascenoJr/OptiFlow/pull/53), [PR #54](https://github.com/VarnerDamascenoJr/OptiFlow/pull/54), [PR #55](https://github.com/VarnerDamascenoJr/OptiFlow/pull/55), [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63).

## Docker, CI, and standalone execution

P3.12 introduced Docker/Compose, persisted history volume, CI, and `demo:local`. OR-Tools later entered the image and workflow; the NestJS migration added the TypeScript build stage and production-only runtime dependencies. The OR-Tools PR reports successful image execution as an unprivileged user.

The final CI job installs Node and Python 3.12, creates the solver environment, and runs tests, sample scenario, enumeration/OR-Tools comparisons, simulation, risk, forecasting, and whitespace checks. Backend compilation occurs through `npm test`'s pretest hook. Docker build/container checks in PR descriptions are separate local evidence, not a workflow step.

**References:** [PR #27](https://github.com/VarnerDamascenoJr/OptiFlow/pull/27), [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60), [PR #62](https://github.com/VarnerDamascenoJr/OptiFlow/pull/62), [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63), [actual workflow](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/.github/workflows/ci.yml), [production image build](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/Dockerfile), [local delivery guide](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/local-delivery.md).

## Portfolio and statistical tooling

P0/P5 provide correlation conventions, runbooks, local guides, diagrams, rehearsals, and workflow references across projects. S0 and S5 establish research questions, a shared statistical dictionary, reproducible-study format, golden data, and the technical/demo reports.

The source keeps implementation and status updates for Sales and the observability platform in shared backlogs. Their PRs and checked items retain their original ownership; six platform-documentation PR merges remain outside the main baseline.

**References:** [PR #32](https://github.com/VarnerDamascenoJr/OptiFlow/pull/32), [PR #33](https://github.com/VarnerDamascenoJr/OptiFlow/pull/33), [PR #34](https://github.com/VarnerDamascenoJr/OptiFlow/pull/34), [PR #56](https://github.com/VarnerDamascenoJr/OptiFlow/pull/56), [PR #57](https://github.com/VarnerDamascenoJr/OptiFlow/pull/57), [PR #58](https://github.com/VarnerDamascenoJr/OptiFlow/pull/58), [reproducible-study format](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/portfolio-reproducible-study-format.md), [statistical golden data](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/golden-datasets.md).
