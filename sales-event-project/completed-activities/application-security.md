# Application Security — Sales Event

[Archive index](README.md) · [Project overview](../README.md)

## API access, payment callbacks, and operational protections

The May deliveries added hashed API keys with `ADMIN`, `SUPPORT`, `CHECK_IN`, and `PAYMENT_PROVIDER` roles, signed payment webhooks, email-event webhook authentication, configurable public rate limiting, metrics protections, and stronger example secrets. Database constraints enforce ticket/check-in uniqueness and valid business states.

The later analytics route requires `SUPPORT` or `ADMIN`. Local `dev-*` keys are seeded development examples. Their presence is not a production credential-management or payment-provider integration claim.

**References:** [May journal](../2026-05.md), [`daa9cf1`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/daa9cf1fdad56d3ec41d38c4efa69ef0397f6e80), [`d1d48f4`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/d1d48f4dbe90d99432902c06d4c02983310ac1fc), [`62bbbc4`](https://github.com/VarnerDamascenoJr/sales-event-project/commit/62bbbc4a2d1f4eb179683fa10a89d4edaf573de3), [PR #19](https://github.com/VarnerDamascenoJr/sales-event-project/pull/19).

## Context and sensitive logging

Correlation remains available through HTTP, AMQP, persisted outbox state, and business spans. The logging handlers redact sensitive attributes rather than placing buyer/secret details into diagnostic output. Responsibility splits and later tests exercise handler groups, fan-out, correlation, redaction, and telemetry export through a local test collector.

**References:** [PR #3](https://github.com/VarnerDamascenoJr/sales-event-project/pull/3), [PR #28](https://github.com/VarnerDamascenoJr/sales-event-project/pull/28), [PR #36](https://github.com/VarnerDamascenoJr/sales-event-project/pull/36).

## Analytics failure handling and demo credentials

| Original correction | Problem and delivered Sales behavior | Boundary |
| --- | --- | --- |
| CFX1 | Non-finite probabilities/priors broke JSON. Sanitized numeric output and hardened invalid/extreme Poisson demand, with analytics and CLI regression coverage in [PR #29](https://github.com/VarnerDamascenoJr/sales-event-project/pull/29). | The PR's tests do not independently establish the backlog's full large-dataset/browser rehearsal. |
| CFX2 | Encoding failure could leave HTTP 200 with an empty body. Marshal before writing success; return safe HTTP 500 JSON with contextual logs in [PR #30](https://github.com/VarnerDamascenoJr/sales-event-project/pull/30). | React Dash fallback is a separate frontend change. |
| CFX3 | Examples used keys that did not match seeds. Align docs/tests to seeded `dev-*` keys and add valid/invalid-key smoke in [PR #31](https://github.com/VarnerDamascenoJr/sales-event-project/pull/31). | PR validation reports shell syntax/tests, not a live execution of that smoke script. |
| CFX4 | Demo generation depended on an ad hoc script. Add a versioned Go command/shell wrapper, focused tests, configurable waits/rate handling, and redacted configuration in [PR #32](https://github.com/VarnerDamascenoJr/sales-event-project/pull/32). | Dashboard instructions and visual evidence retain frontend ownership. |

These IDs originate in the React Dash correction backlog. Delivered code is archived here without changing its task text or treating every shared acceptance criterion as newly satisfied.

## Demo-state and assurance boundaries

CFX9 requests broader demo isolation and explicit safe reset. The Sales generator offers `--reset-demo-inventory` for seeded inventory, but that does not establish removal of all old sales/events or coordinated dashboard-state cleanup. Preserve this as partial evidence rather than a closed task.

This history imports implementation and reported checks. It contains no new penetration test, dependency vulnerability scan, production hardening certification, or live provider validation.
