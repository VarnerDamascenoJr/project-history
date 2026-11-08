# Application Security — React Dash

[Archive index](README.md) · [Project overview](../README.md)

## Demo login and route boundaries

June 2026 added client-side demo authentication and protected/public route guards. Browser coverage later exercised invalid login, redirects, authenticated login-page access, logout, and session cleanup. These are demo UI/session behaviors, not backend authentication or authorization guarantees.

PR #31 improved required fields, pending-submit locking, retry feedback, and complete query/fragment return destinations. Its description also records regression coverage for malformed state, external destinations, and login loops; the server-side security boundary remains outside this frontend repository.

**References:** [June journal](../2026-06.md), [PR #19](https://github.com/VarnerDamascenoJr/react-dash/pull/19), [PR #31](https://github.com/VarnerDamascenoJr/react-dash/pull/31), [auth coverage and limits](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/testing.md).

## API-key handling and fallback

The optional API sends `X-API-Key`; only non-secret settings are selected for persistence. The key remains in page memory through loading/localization and is not included in preference storage. `VITE_*` settings are browser-visible and unsuitable for secrets. CFX3 aligned documentation and tests with the seeded development convention; it did not introduce real credentials into the history.

CFX2's empty-response handling provides readable frontend fallback. The related backend serialization/status-code correction belongs to Sales Event and is not claimed as complete here.

**References:** [PR #2](https://github.com/VarnerDamascenoJr/react-dash/pull/2), [PR #6](https://github.com/VarnerDamascenoJr/react-dash/pull/6), [PR #22](https://github.com/VarnerDamascenoJr/react-dash/pull/22), [PR #23](https://github.com/VarnerDamascenoJr/react-dash/pull/23), [PR #28](https://github.com/VarnerDamascenoJr/react-dash/pull/28), [PR #29](https://github.com/VarnerDamascenoJr/react-dash/pull/29), [PR #32](https://github.com/VarnerDamascenoJr/react-dash/pull/32).

## Evidence capture without retaining the key

CFX5's PR #25 clears the API-key field before screenshots, disables traces/video in API and evidence specs, ignores generated evidence, and keeps the real-API path opt-in. The default browser suite uses an intercepted response rather than requiring credentials or a running backend.

The latest optional-scenario run and five PNGs used a simulated HTTP server. They validate the browser workflow under that setup, not the real Sales service or all possible credential-exposure paths.

**References:** [PR #25](https://github.com/VarnerDamascenoJr/react-dash/pull/25), [evidence execution boundaries](https://github.com/VarnerDamascenoJr/react-dash/blob/fa02c9d6a0c42cbcc02a8532e3efc25b60df49e2/docs/testing.md).

## Security evidence scope

No dependency-security remediation campaign, clean audit result, or production-authentication implementation is imported for React Dash. This history records the documented boundaries and delivered regressions; it does not infer security guarantees from a passing UI suite.
