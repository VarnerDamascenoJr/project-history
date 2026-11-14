# Application Security — OptiFlow

[Archive index](README.md) · [Project overview](../README.md)

## Input and resource boundaries

Scenario validation and shared API errors are preserved through the route-module and NestJS refactors. The final backend disables the automatic Express body parser and reuses the JSON reader's **1 MiB** bound with stable `invalid_json` and `body_too_large` errors. Domain numerical and constraint checks remain behind the HTTP boundary.

The recorded API is a local execution interface, with a default loopback bind. These delivery records establish parsing and execution limits; they contain no imported production authentication/authorization implementation.

**References:** [PR #22](https://github.com/VarnerDamascenoJr/OptiFlow/pull/22), [PR #54](https://github.com/VarnerDamascenoJr/OptiFlow/pull/54), [PR #55](https://github.com/VarnerDamascenoJr/OptiFlow/pull/55), [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63), [HTTP parsing and error contracts](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/backend-architecture.md), [local API configuration](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/scenario-run-api.md).

## Solver subprocess and numeric limits

The OR-Tools bridge passes JSON through process stdin/stdout without a shell. The Python executable is configured by environment/runtime setup, not supplied in an HTTP request. Precision, scaled integer, order-count, and search/runtime bounds have explicit errors; missing or invalid solver execution does not silently select another strategy.

PR #61 preserves strict validation in integer units rather than masking boundary failures with a fixed tolerance. The Python response and Node adapter must be updated together because scale metadata is an internal contract.

**References:** [PR #60](https://github.com/VarnerDamascenoJr/OptiFlow/pull/60), [PR #61](https://github.com/VarnerDamascenoJr/OptiFlow/pull/61), [process, precision, and timeout boundaries](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/or-tools-solver.md).

## Persistence and concurrency scope

Graceful NestJS shutdown drains locally accepted work, but forced termination can lose pending in-memory jobs. A configured concurrency count does not create isolated workers, and the single JSON writer contract is not a multi-replica transactional guarantee. These limits affect how the local API can be operated safely.

**Reference:** [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63), [runtime limits](https://github.com/VarnerDamascenoJr/OptiFlow/blob/b96520fec39e2b865104e45b5c8e6dfeb511c096/docs/backend-architecture.md).

## Dated dependency audit

PR #63 reports **zero findings** from `npm audit --omit=dev` for its production dependency set. That result is dated November 13 and scoped to the recorded candidate. This import does not establish a clean development audit, continuous vulnerability status, or security properties beyond the documented checks.

**Reference:** [PR #63](https://github.com/VarnerDamascenoJr/OptiFlow/pull/63).
