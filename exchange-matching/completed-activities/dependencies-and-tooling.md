# Dependencies and tooling — Exchange Matching

[Archive index](README.md) · [Project overview](../README.md) · [October journal](../2026-10.md) · [November journal](../2026-11.md)

Library behavior, build inputs, template processing, pattern matching, and development tools.

These are archived scanner records, not confirmations of exploitable application paths. `Done` records compatible remediation or a documented disposition. See the [archive scope and audit outcome](README.md#scope-and-audit-outcome).

## Contents

- [Pattern expansion and filesystem traversal](#pattern-expansion-and-filesystem-traversal)
- [Template injection and object merging](#template-injection-and-object-merging)
- [Validation and configuration resource limits](#validation-and-configuration-resource-limits)
- [Development server access and code execution](#development-server-access-and-code-execution)
- [Editor integration and command handling](#editor-integration-and-command-handling)
- [Source map processing and file access](#source-map-processing-and-file-access)

## Pattern expansion and filesystem traversal

Brace-expansion resource exhaustion, Glob cancellation, and Minimatch pattern amplification.

**SEC-063 disposition:** Modern Minimatch was updated; retained callable 3.1.5 lacks the affected preprocessing mechanism. Its raw advisory remained with a mechanism-specific false-positive disposition, rather than disappearing from the full audit.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-012 | High | high | backend, frontend | Triage and resolve brace-expansion: DoS via uncontrolled recursion in parseCommaParts causing stack exhaustion — [GHSA-6j4f-fj2g-mc7p](https://github.com/advisories/GHSA-6j4f-fj2g-mc7p). | Done |
| SEC-013 | High | high | backend, frontend | Triage and resolve brace-expansion: DoS via unbounded expansion length causing an out-of-memory process crash — [GHSA-mh99-v99m-4gvg](https://github.com/advisories/GHSA-mh99-v99m-4gvg). | Done |
| SEC-014 | High | high | backend, frontend | Triage and resolve brace-expansion: DoS via uncontrolled recursion on nested brace groups causing stack exhaustion — [GHSA-qhr7-859c-m2p7](https://github.com/advisories/GHSA-qhr7-859c-m2p7). | Done |
| SEC-015 | High | high | backend, frontend | Triage and resolve brace-expansion: DoS via unbounded intermediate arrays, bypassing the CVE-2026-14257 mitigation — [GHSA-rgw5-rvv9-x895](https://github.com/advisories/GHSA-rgw5-rvv9-x895). | Done |
| SEC-056 | Medium | moderate | backend, frontend | Triage and resolve brace-expansion: Quadratic-time expansion of the `{a},b}` rewrite causes CPU denial of service — [GHSA-q2hr-2g5m-vwhr](https://github.com/advisories/GHSA-q2hr-2g5m-vwhr). | Done |
| SEC-061 | Medium | moderate | backend | Triage and resolve Glob: AbortSignal cancellation bypass allows post-timeout filesystem traversal — [GHSA-3g3m-2fjr-6pw4](https://github.com/advisories/GHSA-3g3m-2fjr-6pw4). | Done |
| SEC-063 | Medium | moderate | backend, frontend | Triage and resolve minimatch has potential denial of service via globparts amplification — [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249). | Done |

### Original evidence notes

- [Request parsing and pattern expansion](validation-and-publication.md#request-parsing-and-pattern-expansion)
- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Template injection and object merging

Handlebars template compilation, recursive object merging, and prototype poisoning.

**SEC-088 disposition:** Deepmerge 4.3.1 was corrected with a checksum-verified, idempotent local postinstall patch across all three entrypoints. Unknown content or versions fail before writes. Installations using `--ignore-scripts` require explicit `npm run postinstall`. The unchanged upstream version remains flagged by the raw audit.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-001 | High | critical | backend | Triage and resolve Handlebars: JavaScript Injection via AST Type Confusion in compile (bypass of CVE-2026-33937) — [GHSA-8r5x-fm3f-whwj](https://github.com/advisories/GHSA-8r5x-fm3f-whwj). | Done |
| SEC-002 | High | critical | backend | Triage and resolve Handlebars: JavaScript Injection via Own Property Check Bypass — [GHSA-p8wg-vrv2-v86f](https://github.com/advisories/GHSA-p8wg-vrv2-v86f). | Done |
| SEC-018 | High | high | backend | Triage and resolve DeepmergeTS has stack exhaustion when merging recursive object graphs — [GHSA-ggr8-5vv4-36mx](https://github.com/advisories/GHSA-ggr8-5vv4-36mx). | Done |
| SEC-062 | Medium | moderate | backend | Triage and resolve Handlebars: JavaScript Injection via Unsafe Inline Embedding of Precompiled Templates — [GHSA-xw65-4hp5-5hc7](https://github.com/advisories/GHSA-xw65-4hp5-5hc7). | Done |
| SEC-088 | Low | low | backend | Triage and resolve deepmerge mergeObject() allows prototype poisoning of returned objects — [GHSA-gcqx-w48m-w2h4](https://github.com/advisories/GHSA-gcqx-w48m-w2h4). | Done |

### Original evidence notes

- [HTTP clients, proxies, and templates](validation-and-publication.md#http-clients-proxies-and-templates)
- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)
- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Validation and configuration resource limits

Browser configuration, YAML merge processing, identifier generation, and constrained collection validation.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-016 | High | high | backend, frontend | Triage and resolve Browserslist: Uncaught crash / prototype write via untrusted browserslist-stats.json custom stats (normalizeStats) — [GHSA-73wf-gq98-2v4g](https://github.com/advisories/GHSA-73wf-gq98-2v4g). | Done |
| SEC-017 | High | high | backend, frontend | Triage and resolve Browserslist: Unbounded memory growth (no cache eviction) via distinct query results, leading to eventual OOM — [GHSA-c83g-rgw3-j3cx](https://github.com/advisories/GHSA-c83g-rgw3-j3cx). | Done |
| SEC-030 | High | high | backend, frontend | Triage and resolve js-yaml: maxTotalMergeKeys does not limit CPU use for empty merge sources — [GHSA-2883-xcg3-v3hh](https://github.com/advisories/GHSA-2883-xcg3-v3hh). | Done |
| SEC-031 | High | high | backend, frontend | Triage and resolve JS-YAML: Quadratic CPU consumption in !!omap resolution (3.x and 4.x) — CVE-2026-59870 fix not backported — [GHSA-5p4m-2wfm-xmqj](https://github.com/advisories/GHSA-5p4m-2wfm-xmqj). | Done |
| SEC-036 | High | high | frontend | Triage and resolve nanoid: custom generators can loop indefinitely when size is zero — [GHSA-2v37-7h3g-55p8](https://github.com/advisories/GHSA-2v37-7h3g-55p8). | Done |
| SEC-047 | High | high | frontend | Triage and resolve Zod can exhaust memory while validating oversized constrained collections — [GHSA-mrhx-c7xc-m3w5](https://github.com/advisories/GHSA-mrhx-c7xc-m3w5). | Done |
| SEC-055 | Medium | moderate | backend, frontend | Triage and resolve baseline-browser-mapping process termination on invalid input causes denial of service — [GHSA-w5vr-8v7q-w6rv](https://github.com/advisories/GHSA-w5vr-8v7q-w6rv). | Done |

### Original evidence notes

- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)
- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Development server access and code execution

Mock registration, cross-origin development-server access, and filesystem boundary enforcement.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-048 | Medium | moderate | frontend | Triage and resolve Vitest: Path Traversal / Arbitrary File Read via @vitest/mocker Redirect Mock — [GHSA-82fw-gwwq-j7x9](https://github.com/advisories/GHSA-82fw-gwwq-j7x9). | Done |
| SEC-049 | Medium | moderate | frontend | Triage and resolve Vitest: Code injection via unauthenticated manual mock registration — [GHSA-qxg6-89mg-rqv8](https://github.com/advisories/GHSA-qxg6-89mg-rqv8). | Done |
| SEC-057 | Medium | moderate | frontend | Triage and resolve esbuild enables any website to send any requests to the development server and read the response — [GHSA-67mh-4wv8-2f99](https://github.com/advisories/GHSA-67mh-4wv8-2f99). | Done |
| SEC-082 | Medium | moderate | frontend | Triage and resolve Vite Vulnerable to Path Traversal in Optimized Deps `.map` Handling — [GHSA-4w7w-66w2-5vf9](https://github.com/advisories/GHSA-4w7w-66w2-5vf9). | Done |
| SEC-084 | Medium | moderate | frontend | Triage and resolve vite: `server.fs.deny` bypass on Windows alternate paths — [GHSA-fx2h-pf6j-xcff](https://github.com/advisories/GHSA-fx2h-pf6j-xcff). | Done |
| SEC-086 | Medium | moderate | frontend | Triage and resolve Vite: Files outside `server.fs.allow` could be served when project paths match system paths on non-Windows machine — [GHSA-rq7h-c2jc-7f22](https://github.com/advisories/GHSA-rq7h-c2jc-7f22). | Done |
| SEC-095 | Low | low | frontend | Triage and resolve Vite: Cross origin script execution through Vite custom middleware — [GHSA-9jrq-w75r-8gcw](https://github.com/advisories/GHSA-9jrq-w75r-8gcw). | Done |

### Original evidence notes

- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Editor integration and command handling

Editor invocation, Windows command escaping, path handling, and credential exposure.

Windows/WSL-specific cases were reviewed in source and releases but were not executed dynamically on Linux during the recorded validation.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-046 | High | high | frontend | Triage and resolve launch-editor: `fs.existsSync()` existence check can be bypassed on Windows — [GHSA-587h-7wmj-h5pm](https://github.com/advisories/GHSA-587h-7wmj-h5pm). | Done |
| SEC-083 | Medium | moderate | frontend | Triage and resolve launch-editor: escapeCmdArgs() omits % escaping on Windows — [GHSA-698v-4r3x-3vcv](https://github.com/advisories/GHSA-698v-4r3x-3vcv). | Done |
| SEC-085 | Medium | moderate | frontend | Triage and resolve launch-editor: Editor CLI flag misinterpretation causing arbitrary command execution for some editors — [GHSA-r825-w8mm-5pxw](https://github.com/advisories/GHSA-r825-w8mm-5pxw). | Done |
| SEC-087 | Medium | moderate | frontend | Triage and resolve launch-editor: NTLMv2 hash disclosure via UNC path handling on Windows — [GHSA-v6wh-96g9-6wx3](https://github.com/advisories/GHSA-v6wh-96g9-6wx3). | Done |

### Original evidence notes

- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Source map processing and file access

Resource exhaustion from indexed source maps and unintended source-map file reads.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-038 | High | high | frontend | Triage and resolve source-map-js allows event-loop denial of service through indexed source-map section offsets — [GHSA-68fv-2mgg-jv7q](https://github.com/advisories/GHSA-68fv-2mgg-jv7q). | Done |
| SEC-065 | Medium | moderate | frontend | Triage and resolve PostCSS: incomplete fix of GHSA-6g55-p6wh-862q — attacker-controlled sourceMappingURL reads arbitrary .map files when `from` is unset — [GHSA-fxqj-rqcc-2cmp](https://github.com/advisories/GHSA-fxqj-rqcc-2cmp). | Done |

### Original evidence notes

- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)
