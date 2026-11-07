# Application security — Exchange Matching

[Archive index](README.md) · [Project overview](../README.md) · [October journal](../2026-10.md) · [November journal](../2026-11.md)

Request handling, communication, input parsing, and protocol boundaries. Records describe the reviewed dependency mechanisms; application reachability remains qualified in the evidence.

These are archived scanner records, not confirmations of exploitable application paths. `Done` records compatible remediation or a documented disposition. See the [archive scope and audit outcome](README.md#scope-and-audit-outcome).

## Contents

- [HTTP clients, proxies, and redirects](#http-clients-proxies-and-redirects)
- [HTTP transport, TLS, and caching](#http-transport-tls-and-caching)
- [Realtime protocols and streaming resource limits](#realtime-protocols-and-streaming-resource-limits)
- [URI normalization and host boundaries](#uri-normalization-and-host-boundaries)
- [Request parsing and multipart uploads](#request-parsing-and-multipart-uploads)

## HTTP clients, proxies, and redirects

Proxy trust, request adapters, inherited request options, redirect credentials, and cross-site request handling.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-003 | High | critical | backend | Triage and resolve proxy-addr vulnerable to IP spoofing via IPv4-mapped IPv6 trust subnet — [GHSA-jqcg-44mw-7w3h](https://github.com/advisories/GHSA-jqcg-44mw-7w3h). | Done |
| SEC-004 | High | high | frontend | Triage and resolve Axios: HTTP/2 adapter bypasses configured DNS lookup and proxy controls — [GHSA-3pq3-5fj3-cg6v](https://github.com/advisories/GHSA-3pq3-5fj3-cg6v). | Done |
| SEC-005 | High | high | frontend | Triage and resolve Axios: Denial of Service via Unhandled 'error' Event in HTTP/2 ClientHttp2Session Initialization — [GHSA-542g-h47m-68v8](https://github.com/advisories/GHSA-542g-h47m-68v8). | Done |
| SEC-006 | High | high | frontend | Triage and resolve Axios: ReDoS in fromDataURI data: URL parser freezes the Node event loop (DoS) — [GHSA-c29m-xwm3-cm6r](https://github.com/advisories/GHSA-c29m-xwm3-cm6r). | Done |
| SEC-007 | High | high | frontend | Triage and resolve Axios: Node HTTP adapter prototype-pollution gadget allows request socket hijack via inherited createConnection — [GHSA-m8m8-qj5v-23w3](https://github.com/advisories/GHSA-m8m8-qj5v-23w3). | Done |
| SEC-008 | High | high | frontend | Triage and resolve Axios: ReDoS (O(N²)) in shouldBypassProxy host normalization, reachable via untrusted redirect Location — [GHSA-mghh-pgcx-3jjj](https://github.com/advisories/GHSA-mghh-pgcx-3jjj). | Done |
| SEC-009 | High | high | frontend | Triage and resolve Axios: maxRedirects: 0 is not enforced by the fetch adapter, allowing redirect-based SSRF — [GHSA-r4gj-5m52-g5wh](https://github.com/advisories/GHSA-r4gj-5m52-g5wh). | Done |
| SEC-010 | High | high | frontend | Triage and resolve Axios: Prototype Pollution Gadget in axios toFormData Options — [GHSA-x97p-jq2g-jp4f](https://github.com/advisories/GHSA-x97p-jq2g-jp4f). | Done |
| SEC-027 | High | high | frontend | Triage and resolve follow-redirects sensitiveHeaders regex escaping can expose credential headers — [GHSA-8r9p-f939-6h3c](https://github.com/advisories/GHSA-8r9p-f939-6h3c). | Done |
| SEC-028 | High | high | frontend | Triage and resolve follow-redirects: Cross-realm sensitiveHeaders arrays are discarded and custom credentials can follow redirects — [GHSA-mrwp-f3q8-3g9p](https://github.com/advisories/GHSA-mrwp-f3q8-3g9p). | Done |
| SEC-029 | High | high | frontend | Triage and resolve follow-redirects array-form headers bypass cross-origin credential stripping — [GHSA-q3jh-wrc6-jgq8](https://github.com/advisories/GHSA-q3jh-wrc6-jgq8). | Done |
| SEC-037 | High | high | frontend | Triage and resolve React Router: RSC Mode CSRF Bypass Allows Action Execution Before 400 Response — [GHSA-qwww-vcr4-c8h2](https://github.com/advisories/GHSA-qwww-vcr4-c8h2). | Done |
| SEC-050 | Medium | moderate | frontend | Triage and resolve Axios: CIDR-form NO_PROXY entries are ignored, causing proxy exclusion bypass for internal IP ranges — [GHSA-44g4-m2mj-wpvx](https://github.com/advisories/GHSA-44g4-m2mj-wpvx). | Done |
| SEC-051 | Medium | moderate | frontend | Triage and resolve Axios: Fetch Adapter Header Injection via Inherited FormData getHeaders — [GHSA-4hqw-qxg8-jxx2](https://github.com/advisories/GHSA-4hqw-qxg8-jxx2). | Done |
| SEC-052 | Medium | moderate | frontend | Triage and resolve Axios: Prototype-Pollution Gadget in the Default Instance Allows Inherited Object.prototype.method to Override HTTP Method — [GHSA-9fr6-4gfg-395g](https://github.com/advisories/GHSA-9fr6-4gfg-395g). | Done |
| SEC-053 | Medium | moderate | frontend | Triage and resolve Axios: Header Injection via Inherited headers After Minimal Interceptor — [GHSA-j8rh-479h-cp32](https://github.com/advisories/GHSA-j8rh-479h-cp32). | Done |
| SEC-054 | Medium | moderate | frontend | Triage and resolve Axios: Prototype pollution gadget in fetch adapter can alter outbound requests — [GHSA-vh66-26gq-q6x8](https://github.com/advisories/GHSA-vh66-26gq-q6x8). | Done |

### Original evidence notes

- [HTTP clients, proxies, and templates](validation-and-publication.md#http-clients-proxies-and-templates)
- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)
- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## HTTP transport, TLS, and caching

TLS verification, response handling, decompression, retry interceptors, shared caches, and cookie boundaries.

Undici is jsdom-only development tooling in this application. Updating its npm package does not update the Undici runtime bundled separately with Node.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-039 | High | high | frontend | Triage and resolve undici vulnerable to TLS certificate validation bypass via dropped tls options in Agent — [GHSA-2m5v-pch6-74hx](https://github.com/advisories/GHSA-2m5v-pch6-74hx). | Done |
| SEC-040 | High | high | frontend | Triage and resolve undici vulnerable to cross-user information disclosure and parse-time crash via degenerate private cache directives — [GHSA-4cwx-7wf7-3272](https://github.com/advisories/GHSA-4cwx-7wf7-3272). | Done |
| SEC-041 | High | high | frontend | Triage and resolve undici vulnerable to cache poisoning and cross-user disclosure via cross-origin redirects — [GHSA-4w7w-5xrc-9h26](https://github.com/advisories/GHSA-4w7w-5xrc-9h26). | Done |
| SEC-042 | High | high | frontend | Triage and resolve undici vulnerable to Denial of Service via TLS 1.2 certificate-changing renegotiation — [GHSA-qrxm-fqhp-jwvm](https://github.com/advisories/GHSA-qrxm-fqhp-jwvm). | Done |
| SEC-044 | High | high | frontend | Triage and resolve undici vulnerable to TLS certificate validation bypass via dropped connect options in BalancedPool — [GHSA-w293-vg96-wgc3](https://github.com/advisories/GHSA-w293-vg96-wgc3). | Done |
| SEC-045 | High | high | frontend | Triage and resolve undici vulnerable to Denial of Service via unhandled error on excessive content-encodings — [GHSA-xjj6-f33q-929c](https://github.com/advisories/GHSA-xjj6-f33q-929c). | Done |
| SEC-069 | Medium | moderate | frontend | Triage and resolve undici vulnerable to cross-user cookie disclosure via Set-Cookie caching in shared caches — [GHSA-2jfj-6hjv-fm6j](https://github.com/advisories/GHSA-2jfj-6hjv-fm6j). | Done |
| SEC-071 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via unbounded decompression of compressed responses — [GHSA-3xpg-4rpp-hhhm](https://github.com/advisories/GHSA-3xpg-4rpp-hhhm). | Done |
| SEC-073 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via unhandled exception in the decompress interceptor — [GHSA-55wc-3pg8-jfw6](https://github.com/advisories/GHSA-55wc-3pg8-jfw6). | Done |
| SEC-074 | Medium | moderate | frontend | Triage and resolve undici vulnerable to downstream response desynchronization via retry interceptor — [GHSA-8xcm-r25x-g524](https://github.com/advisories/GHSA-8xcm-r25x-g524). | Done |
| SEC-076 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Subresource Integrity bypass via non-lowercase algorithm tokens — [GHSA-f72v-6w45-q472](https://github.com/advisories/GHSA-f72v-6w45-q472). | Done |
| SEC-077 | Medium | moderate | frontend | Triage and resolve undici vulnerable to cross-user information disclosure via whitespace around equals in Cache-Control directives — [GHSA-jr45-8vmc-qm54](https://github.com/advisories/GHSA-jr45-8vmc-qm54). | Done |
| SEC-078 | Medium | moderate | frontend | Triage and resolve undici vulnerable to CRLF Injection via blob-like body 'type' property — [GHSA-m8rv-5g2x-5cg5](https://github.com/advisories/GHSA-m8rv-5g2x-5cg5). | Done |
| SEC-079 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via orphaned RetryHandler response body — [GHSA-pmjh-fq2x-6v4x](https://github.com/advisories/GHSA-pmjh-fq2x-6v4x). | Done |
| SEC-081 | Medium | moderate | frontend | Triage and resolve undici vulnerable to cookie attribute injection via unsanitized domain and unparsed setCookie fields — [GHSA-v3r7-h72x-cjcm](https://github.com/advisories/GHSA-v3r7-h72x-cjcm). | Done |
| SEC-092 | Low | low | frontend | Triage and resolve undici vulnerable to response truncation via oversized chunked responses in the dump interceptor — [GHSA-2gqq-gqf2-x968](https://github.com/advisories/GHSA-2gqq-gqf2-x968). | Done |
| SEC-093 | Low | low | frontend | Triage and resolve undici vulnerable to caching and replay of unsafe HTTP method responses — [GHSA-8436-99hf-9mmv](https://github.com/advisories/GHSA-8436-99hf-9mmv). | Done |
| SEC-094 | Low | low | frontend | Triage and resolve undici vulnerable to downstream response splitting via retry interceptor — [GHSA-r53p-7pc4-xj5r](https://github.com/advisories/GHSA-r53p-7pc4-xj5r). | Done |

### Original evidence notes

- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## Realtime protocols and streaming resource limits

Engine.IO protocol negotiation and Undici WebSocket/EventSource resource handling.

Engine.IO is a runtime dependency. Undici findings here concern development tooling; the archive does not imply that every listed transport is used by the application.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-019 | High | high | backend | Triage and resolve Socket.IO: Engine.IO Protocol Revision Mismatch DoS — [GHSA-2gc4-cqfq-p2gv](https://github.com/advisories/GHSA-2gc4-cqfq-p2gv). | Done |
| SEC-043 | High | high | frontend | Triage and resolve undici vulnerable to Denial of Service via unrequested WebSocket subprotocol — [GHSA-rfgv-xxqx-mfg5](https://github.com/advisories/GHSA-rfgv-xxqx-mfg5). | Done |
| SEC-070 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via unhandled error in WebSocket permessage-deflate decompression — [GHSA-3wwx-pv8p-q78v](https://github.com/advisories/GHSA-3wwx-pv8p-q78v). | Done |
| SEC-072 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via unbounded memory in the EventSource parser — [GHSA-4qv8-2p9j-2685](https://github.com/advisories/GHSA-4qv8-2p9j-2685). | Done |
| SEC-075 | Medium | moderate | frontend | Triage and resolve undici WebSocket client vulnerable to Denial of Service via unbounded automatic PONG buffering — [GHSA-9fm3-97px-rjf6](https://github.com/advisories/GHSA-9fm3-97px-rjf6). | Done |
| SEC-080 | Medium | moderate | frontend | Triage and resolve undici vulnerable to Denial of Service via WebSocketStream unclean close — [GHSA-rx4f-c7p8-82vq](https://github.com/advisories/GHSA-rx4f-c7p8-82vq). | Done |

### Original evidence notes

- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)
- [Remaining dependency remediation](validation-and-publication.md#remaining-dependency-remediation)

## URI normalization and host boundaries

Host, scheme, authority, and relative-path normalization in fast-uri.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-020 | High | high | backend | Triage and resolve fast-uri vulnerable to host confusion via skipped IDN canonicalization on scheme-relative references — [GHSA-5jgf-p345-68v8](https://github.com/advisories/GHSA-5jgf-p345-68v8). | Done |
| SEC-021 | High | high | backend | Triage and resolve fast-uri vulnerable to host confusion via backslash authority introducer — [GHSA-7p8r-x3mc-p8w7](https://github.com/advisories/GHSA-7p8r-x3mc-p8w7). | Done |
| SEC-022 | High | high | backend | Triage and resolve fast-uri vulnerable to server-side request forgery via malformed IPv6 normalization — [GHSA-f65p-4m7j-42xc](https://github.com/advisories/GHSA-f65p-4m7j-42xc). | Done |
| SEC-023 | High | high | backend | Triage and resolve fast-uri vulnerable to server-side request forgery via repeated hostname percent-decoding — [GHSA-fph4-wmhf-6fwf](https://github.com/advisories/GHSA-fph4-wmhf-6fwf). | Done |
| SEC-024 | High | high | backend | Triage and resolve fast-uri vulnerable to host confusion via percent-encoded scheme normalization — [GHSA-jqff-g426-hqxp](https://github.com/advisories/GHSA-jqff-g426-hqxp). | Done |
| SEC-025 | High | high | backend | Triage and resolve fast-uri vulnerable to authority injection via an unvalidated port in serialize — [GHSA-qw65-cvwx-89v3](https://github.com/advisories/GHSA-qw65-cvwx-89v3). | Done |
| SEC-026 | High | high | backend | Triage and resolve fast-uri vulnerable to host confusion via literal backslash authority delimiter — [GHSA-v2hh-gcrm-f6hx](https://github.com/advisories/GHSA-v2hh-gcrm-f6hx). | Done |
| SEC-058 | Medium | moderate | backend | Triage and resolve fast-uri vulnerable to inconsistent host case normalization via percent-encoded octets — [GHSA-hrr3-gc8f-f4qj](https://github.com/advisories/GHSA-hrr3-gc8f-f4qj). | Done |
| SEC-059 | Medium | moderate | backend | Triage and resolve fast-uri vulnerable to URI scheme spoofing via percent-encoded scheme decoding — [GHSA-w74x-v6f9-j3xg](https://github.com/advisories/GHSA-w74x-v6f9-j3xg). | Done |
| SEC-060 | Medium | moderate | backend | Triage and resolve fast-uri vulnerable to host confusion via unchecked WHATWG host canonicalization — [GHSA-wjr9-j795-jxcr](https://github.com/advisories/GHSA-wjr9-j795-jxcr). | Done |
| SEC-089 | Low | low | backend | Triage and resolve fast-uri vulnerable to scheme injection via an unescaped first-segment colon in suffix references — [GHSA-333x-w4r6-6crp](https://github.com/advisories/GHSA-333x-w4r6-6crp). | Done |
| SEC-090 | Low | low | backend | Triage and resolve fast-uri vulnerable to improper path equivalence in relative reference normalization — [GHSA-xhq7-xmqj-769h](https://github.com/advisories/GHSA-xhq7-xmqj-769h). | Done |

### Original evidence notes

- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)

## Request parsing and multipart uploads

Compressed request parsing, URL-encoded fields, multipart limits, aborted uploads, and asynchronous filters.

**SEC-032 qualification:** Multer 2.5.0 leaves array indices unbounded by default. The current application has no upload middleware, and tested multipart inputs were rejected without a crash. Future upload routes require explicit array-index and nesting limits; the update alone did not make those defaults safe.

| ID | Priority | Severity | Scope | Activity | Status |
| --- | --- | --- | --- | --- | --- |
| SEC-011 | High | high | backend | Triage and resolve body-parser vulnerable to Denial of Service via trailing bytes after a compressed request body — [GHSA-27r3-jxmh-p828](https://github.com/advisories/GHSA-27r3-jxmh-p828). | Done |
| SEC-032 | High | high | backend | Triage and resolve multer vulnerable to Denial of Service via oversized array index in field names — [GHSA-535w-7cp7-47q4](https://github.com/advisories/GHSA-535w-7cp7-47q4). | Done |
| SEC-033 | High | high | backend | Triage and resolve multer vulnerable to Denial of Service via a pending asynchronous fileFilter after request teardown — [GHSA-q7qp-rjg7-q26m](https://github.com/advisories/GHSA-q7qp-rjg7-q26m). | Done |
| SEC-034 | High | high | backend | Triage and resolve multer vulnerable to Denial of Service via file descriptor leak on aborted uploads — [GHSA-qfvm-cv95-jqjf](https://github.com/advisories/GHSA-qfvm-cv95-jqjf). | Done |
| SEC-035 | High | high | backend | Triage and resolve multer vulnerable to Denial of Service via crafted multipart field names — [GHSA-wc9g-mqfw-jrwm](https://github.com/advisories/GHSA-wc9g-mqfw-jrwm). | Done |
| SEC-064 | Medium | moderate | backend | Triage and resolve multer vulnerable to Denial of Service via orphaned disk writes on aborted uploads — [GHSA-3pph-fpjx-jg34](https://github.com/advisories/GHSA-3pph-fpjx-jg34). | Done |
| SEC-066 | Medium | moderate | backend | Triage and resolve qs: Denial of Service via Attacker Controlled isBuffer — [GHSA-4mjr-xmp4-gh2g](https://github.com/advisories/GHSA-4mjr-xmp4-gh2g). | Done |
| SEC-067 | Medium | moderate | backend | Triage and resolve qs : qs.stringify with arrayFormat 'comma' throws an uncaught TypeError on array elements carrying a non-callable own toString (DoS) — [GHSA-6pq8-jhm2-2vcw](https://github.com/advisories/GHSA-6pq8-jhm2-2vcw). | Done |
| SEC-068 | Medium | moderate | backend | Triage and resolve qs array-limit bypass via bracket-key comma parsing — [GHSA-x5fp-wj9c-mxmx](https://github.com/advisories/GHSA-x5fp-wj9c-mxmx). | Done |
| SEC-091 | Low | low | backend | Triage and resolve multer vulnerable to file size limit bypass via async fileFilter race condition — [GHSA-qvfw-j98x-7q72](https://github.com/advisories/GHSA-qvfw-j98x-7q72). | Done |

### Original evidence notes

- [Request parsing and pattern expansion](validation-and-publication.md#request-parsing-and-pattern-expansion)
- [Protocols, parsers, and uploads](validation-and-publication.md#protocols-parsers-and-uploads)
