# Validation and publication — Exchange Matching

[Archive index](README.md) · [Project overview](../README.md) · [October journal](../2026-10.md) · [November journal](../2026-11.md)

These seven original backlog notes were imported on **2026-11-02**. Their bodies are preserved verbatim. Counts, pending states, branch names, and publication instructions describe their historical stage; they do not authorize new actions. The [November journal](../2026-11.md) explains the resulting deliveries.

## Contents

- [QA revalidation](#qa-revalidation)
- [HTTP clients, proxies, and templates](#http-clients-proxies-and-templates)
- [Request parsing and pattern expansion](#request-parsing-and-pattern-expansion)
- [Protocols, parsers, and uploads](#protocols-parsers-and-uploads)
- [Remaining dependency remediation](#remaining-dependency-remediation)
- [Full publication-candidate validation](#full-publication-candidate-validation)
- [Authorized publication](#authorized-publication)

## QA revalidation

**Original note:** Latest full validation — 2026-11-01

- Removed the seven completed QA findings; their historical details are preserved in the local validation report.
- 778 automated tests and 20 manual/exploratory scenarios passed. No new or recurrent functional defect was confirmed.
- Dependency audit still reports the same 95 advisories already tracked above; no duplicate or new security activity was added.
- Local evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_14-08-14_revalidation/RELATORIO.md`.


## HTTP clients, proxies, and templates

**Original note:** Security remediation — SEC-001–SEC-005 — 2026-11-01

- Triaged all five advisories, their installed paths, upstream fixes and application reachability. No exploit path was confirmed in the current application configuration: Handlebars is ts-jest development tooling, Express trust proxy is disabled, and frontend Axios uses browser adapters rather than Node HTTP/2.
- Compatible changes only: Handlebars 4.7.9 → 4.7.10, proxy-addr 2.0.7 → 2.0.8, Axios 1.18.1 → 1.20.0; declared Axios minimum is now ^1.20.0. No framework upgrade or override.
- SEC-001–SEC-005 are resolved. Shared dependency fixes also removed SEC-006–SEC-010, SEC-050–SEC-054 and SEC-062 from the scanner. Those eleven collateral resolutions were verified by advisory URL; their application exploitability was not independently triaged in this block.
- Audit: 95 → 79 distinct advisories, zero new; backend 49 → 47 flagged packages, frontend 32 → 31. All other SEC entries and BE tasks are preserved. Next five pending entries: SEC-011–SEC-015.
- Clean installs, lint, types, builds, 778 existing automated tests and five controlled before/after security probes passed. Then 20 manual scenarios passed against disposable infrastructure. No new or recurring functional defect was confirmed.
- Local probe corrections: the independent API startup probe initially omitted required POSTGRES_* environment keys; after supplying the documented configuration it passed. Redis recovery initially sampled the matching intent before acknowledgement completed; waiting for OPEN plus intent removal passed. Original failed probe attempts remain in the evidence; neither was an application defect.
- Local Node 22.14.0 / npm 10.9.2; README recommends Node 22.20.0.
- Evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_14-25-34_sec-001-005/RELATORIO.md`.
- Publication withdrawn at user request: PR #35 closed without merge, remote branch deleted and four local commits undone with changes preserved. Keep all work uncommitted; no further commits, push or PR are authorized. BACKLOG remains local, untracked and ignored.


## Request parsing and pattern expansion

**Original note:** Security remediation — SEC-011–SEC-015 — 2026-11-01

- Individually triaged SEC-011–SEC-015, their installed paths, upstream patches and application reachability. SEC-011 affects the runtime default Nest/Express parser before routing/authentication; a controlled child reproduced the unhandled decompressor error. Brace-expansion is development tooling; no request/queue input is used as a glob pattern.
- Compatible transitive updates only: body-parser 2.3.0 → 2.4.0; brace-expansion 1.1.16 → 1.1.21, 2.1.2 → 2.1.7 and 5.0.7 → 5.0.12. Required child updates: content-type 2.0.0 → 2.1.0 and qs 6.15.3 → 6.17.1. Parent ranges, Node 22 support and module entrypoints were reviewed. No framework, minimatch or glob upgrade, no override or forced audit fix.
- SEC-011–SEC-015 resolved. Shared dependency updates also removed SEC-056 and SEC-066–SEC-068 by advisory URL; the qs findings were not independently triaged for exploitability in this block.
- Audit: 79 → 70 distinct advisories, zero new; backend 47 → 44 flagged packages, frontend 31 → 30. Cumulative: 95 → 70 distinct advisories, 25 Done and 70 Pending. All original records and BE tasks preserved. Next block: SEC-016–SEC-020.
- Clean installs, Prisma, lint, types, builds and all 778 existing automated tests passed again. Thirteen controlled before/after security probes passed after reproducing the old defects. Intentional OOM/stack failures were confined to children with bounded heaps and disabled core dumps.
- After automation, 29 manual scenarios passed: the 20 exchange/recovery scenarios plus nine real API HTTP checks for compressed requests, trailing bytes before routing/authentication, malformed compression, decompressed size limits, unsupported encoding and URL-encoded validation. No new or recurring functional defect confirmed. All disposable infrastructure removed; no development data used.
- Local Node 22.14.0 / npm 10.9.2. README recommends Node 22.20.0.
- Evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_14-40-05_sec-011-015/RELATORIO.md`.
- User instruction: keep all changes uncommitted. No further commit, push or PR was created. HEAD remains c17992e; PR #35 is closed without merge and its remote branch was deleted. BACKLOG remains exclusively local, ignored and untracked.


## Protocols, parsers, and uploads

**Original note:** Security remediation — SEC-016–SEC-035 — 2026-11-01

- Individually triaged the next 20 pending advisories, their installed paths, upstream fixes and application reachability. Engine.IO's transport upgrade path is runtime and precedes Socket.IO JWT handling. Browserslist, fast-uri and js-yaml are configuration/build/test tooling; frontend follow-redirects is the unused Node Axios path. Prisma configuration is local CLI input, not HTTP. The app has no upload/Multer middleware or interceptors.
- Compatible-line updates: Browserslist 4.28.6 → 4.29.5 and its required browser datasets; Engine.IO 6.6.9 → 6.6.11; fast-uri 3.1.3 → 3.1.9; follow-redirects 1.16.0 → 1.16.2; js-yaml 3.15.0 → 3.15.2 and 4.3.0 → 4.3.2.
- Two reviewed scoped overrides address upstream exact pins: @prisma/config@6.19.3 → deepmerge-ts 8.0.2; @nestjs/platform-express → multer 2.5.0. The deepmerge major's Map/metadata/into changes are outside the API used by the Prisma config loader; six actual config/merge fixtures have identical before/after output. Prisma/client, Nest core/common/testing, Socket.IO and websocket adapter versions remain unchanged.
- A candidate using the old Nest adapter plus Multer 2.5 returned HTTP 500 for an unexpected upload field in an isolated fixture. It was rejected and fixed before manual testing by the targeted platform-express 11.1.28 → 11.2.8 update (declared minimum ^11.2.8), which maps stable error codes. The final fixture returns 400, as required. This did not affect an existing application route; no upload route exists.
- SEC-032 qualification: Multer 2.5.0 leaves fieldArrayIndexLimit unbounded by default. The unbounded controlled probe still stalled; a bounded probe and real Nest fixture with fieldArrayIndexLimit: 1000 reject the payload safely. Current API multipart inputs do not reach Multer and were verified to return 400 while health remains available. Any future upload feature must explicitly configure array-index and nesting limits. The version update alone is not a claim that default Multer is safe for this input.
- SEC-016–SEC-035 resolved by secure versions plus the documented SEC-032 reachability/configuration condition. Shared updates also remove SEC-055, SEC-058–SEC-060, SEC-064 and SEC-089–SEC-091 by advisory URL; no independent application exploitability triage is claimed for those eight collateral findings.
- Audit: 70 → 42 distinct advisories, zero new; backend 44 → 34 flagged packages, frontend 30 → 26. Cumulative: 95 → 42 distinct advisories, 53 Done and 42 Pending. All 95 original records and all BE tasks are preserved. Next pending record: SEC-036.
- Automated first: clean installs, Prisma generation, lint, types, builds and all 778 existing tests passed. Twenty-two advisory probes, six Prisma compatibility fixtures and five Nest/Multer integration fixtures passed. Backend validation and Chromium were repeated after the adapter correction.
- Then 34 manual scenarios passed: 20 exchange/recovery scenarios, nine HTTP regressions and five real Engine.IO/multipart scenarios. Valid EIO4 upgrade works; EIO3 and missing-version upgrades return 400. No new or recurring functional defect confirmed in the final app. All disposable processes, containers and networks removed; no development data used.
- Local Node 22.14.0 / npm 10.9.2; README recommends Node 22.20.0. Evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_15-36-03_sec-016-035/RELATORIO.md`.
- All changes remain local, unstaged and uncommitted. No commit, push, PR or merge was performed for this block. HEAD remains c17992e. BACKLOG remains ignored and untracked.


## Remaining dependency remediation

**Original note:** Security remediation — remaining 42 records — 2026-11-01

- Individually triaged the final 42 pending advisory descriptions, fixed releases, installed paths and actual application use. No additional confirmed functional application defect was found. All 95 original SEC records and all BE tasks remain present; BE statuses are unchanged.
- React Router/DOM 7.18.5, Zod 4.6.7, Vitest/mocker 4.1.12, Undici 7.30.1, PostCSS 8.5.32, nanoid 3.3.20 and source-map-js 1.2.2 stay in their existing major lines. Minimum manifest versions are raised for direct security upgrades. Undici is jsdom-only tooling, not the browser HTTP adapter or API client; npm does not update Node's separately bundled Undici.
- Vite moves from 5.4.21 to the smallest corrected major line, 6.4.5 (minimum ^6.4.4), with its supported esbuild 0.25.12. Existing React plugin and Vitest accept Vite 6; `vite: $vite` aligns the graph and removes the old nested Vite 8/Rolldown. Vite migration changes were checked against this SPA's actual config. No forced audit fix, incompatible isolated esbuild override, Vite 8 or Vitest 5 migration.
- SEC-061: reviewed modern Glob consumers (Nest CLI/Jest) move from 10.5.0/13.0.6 to 14.0.3 via a version-scoped override. All used sync APIs, ordinary file results and complete test discovery/build work. The old abort fixture performs 16 extra reads after rejection; the corrected walker performs zero. Unaffected Glob 7 is preserved.
- SEC-063: modern Minimatch 9/10 moves to 11.0.3; backend override is scoped to >=9 <11 and frontend to @typescript-eslint/typescript-estree. Legacy callable 3.1.5 is preserved for ESLint/old tooling: it has neither firstPhasePreProcess nor optimizationLevel, the actual affected algorithm. The scanner's broad <11 range still flags 3.x; its false-positive disposition is code-qualified and explicit. Normal glob fixtures match before/after; controlled amplification stays within the configured 64-pattern cap.
- SEC-088: Deepmerge has no fixed published release. A local checksum-verified, idempotent postinstall patch fixes source/target forbidden keys and safe own-property writes in all three entrypoints of 4.3.1. Unknown source/version fails installation before file writes. Five persistent tests cover the reproduced defect, both bundles, compatibility and patch lifecycle. `npm ci --omit=dev` succeeds and skips this absent dev dependency. Scripts must be enabled, or run `npm run postinstall` explicitly after --ignore-scripts. Raw audit still flags the unchanged upstream version; this is a local correction, not an upstream release fix.
- Audit: 42 → 2 distinct raw advisories, 40 removed, zero new. The two retained entries are SEC-063 (false positive on the remaining legacy line) and SEC-088 (locally patched). Backend 34 → 33 flagged packages, frontend 26 → 14; these mostly inherit the two remaining advisories, not 47 independent defects. No high/critical findings. Production-only audits return zero in both projects. Cumulative: 93 of the original 95 advisories are no longer flagged; the other two have verified, documented dispositions. All 95 SEC activities are Done, zero Pending; do not claim npm audit is clean.
- Automation first: clean installs, Prisma generation, lint, types, builds, all 778 existing tests and five new patch tests pass. Additional external checks: 22 before/after library security probes, nine Vite/esbuild checks, normal merge/glob/matching comparisons and bounded preprocessing. Security payloads run only in bounded children/temp fixtures/loopback servers with dummy credentials. Windows/WSL-specific exploits were reviewed in patched sources/releases but not executed on Linux.
- Then 34 manual/exploratory scenarios pass: 20 exchange/session/layout/production/recovery, nine HTTP-parser and five Engine.IO/multipart scenarios. Screenshots inspected. Rounded USD volume remains 125.06666666 in the SQL fixture; concurrent reservation/refund and maker price/time priority pass. Same-endpoint Redis pause/unpause recovers matching/realtime without process restart; outboxes drain. No browser errors or unexpected 5xx. All disposable processes/containers/networks removed; development data was not used.
- Candidate/tooling corrections retained in evidence: initial npm 10 peer resolution crashed while considering optional Vite 8 devtools; the aligned Vite override resolves it. npm ls then reported the version-qualified hoisted frontend Minimatch override as invalid; a parent-scoped override fixes metadata with every locked package entry identical, verified by another clean install and clean dependency-tree checks. An initial TLS probe mishandled Node lookup({all:true}); the corrected harness reproduces dropped verification callbacks before and rejection after. These are not production application regressions.
- Local Node 22.14.0/npm 10.9.2; README recommends Node 22.20.0. Rollup reports an upstream Zod PURE-comment annotation warning and drops the comment; build/tests pass. Existing SEC-032 qualification remains: future Multer upload routes require explicit array-index and nesting limits.
- Evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_17-53-48_sec-remaining/RELATORIO.md`. Repository review: docs/security-sec-remaining.md. Keep all changes local, unstaged and uncommitted. No commit, push, PR or merge performed. HEAD stays c17992e. BACKLOG remains exclusively local, untracked and ignored.


## Full publication-candidate validation

**Original note:** Full revalidation before publication — 2026-11-01

- Repeated clean npmci installs in both projects, Prisma generation, backend/frontend lint, types, builds and full dependency-tree checks. All783 suite cases passed:413 backend unit,13 isolated-runner,293 disposable-database E2E,57 frontend,2 isolated Chromium journeys and5 Deepmerge patch tests. Independent production omit-dev install also passed.
- Repeated78 additional security/compatibility checks from all remediation blocks, plus ordinary merge/glob/pattern comparisons and bounded Minimatch preprocessing. The brace group now has9 cases because2.x is no longer installed; do not reuse the previous13-case count. All current-version probes passed. No dependency version or code was changed.
- Automated checks completed first. Then37 manual/exploratory scenarios passed: all34 prior scenarios plus SELL taker/BUY maker partial settlement and two pending-request duplicate-click checks. Browser screenshots inspected; zero browser runtime errors or unexpected5xx.
- Financial checks passed: per-fill rounding125.06666666USD in the base decimal scenario; final total143.36666666USD after all added trades agrees between SQL and authenticated API. Concurrent reservations accept10/11 and refund exactly; maker price/time priority and fees in both trading directions are correct. Pending submission/cancellation sends onlyone POST/DELETE and disables repeated clicks.
- Same-endpoint Redis pause/unpause preserves durable queue intent/retry deadlines and recovers matching/realtime without process restart. Final disposable DB: no negative balances, residual reserves, active orders or dead letters; matching/realtime outboxes drained. All disposable containers/networks/processes removed; preexisting Docker listing unchanged; development data not used.
- A supplemental final-volume harness initially omitted authentication and received the correct401. Using an authenticated user and explicitly checking200 before comparing SQL passed; original failed harness attempt is preserved. No new or recurring application defect was confirmed, so no functional backlog item was added.
- Audit unchanged:2 distinct raw advisories (SEC063 legacy-line false positive and SEC088 locally patched), no new/high/critical findings; production-only auditszero in both projects. Existing dispositions/qualifications preserved, including explicit limits for any future Multer upload feature.
- Node22.14.0/npm10.9.2 locally; README recommends22.20.0. Windows/WSL-specific attacks not executed on Linux. Upstream PURE/deprecation warnings remain documented and non-fatal.
- Evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-01_19-43-13_full-revalidation/RELATORIO.md`. All252 non-ignored tracked/new files remained byte-identical. Only this local BACKLOG note changed. All95 SEC records and BE statuses are preserved. HEADc17992e unchanged, indexempty; no commit, push, PR or merge. BACKLOG remains ignored/untracked.


## Authorized publication

**Original note:** Publication authorized and completed — 2026-11-02

- User explicitly authorized creating a new branch, committing each modification and opening/merging the PR, superseding the earlier no-publication instruction. Created fix/security-advisory-remediation and12 descriptive English commits, exactly one file per commit.
- PR #36 merged with a merge commit, preserving all12 individual commits. Merge: f01c2be174b162710ec3555165bdca7769014864. Main is synchronized with origin/main and the working tree is clean.
- Backend/frontend/browser CI checks all passed before merge (run41535080302), and all three passed again on the merged main commit (run41535449509). No force/admin bypass, squash or rewritten commits.
- Confirmed all252 validated files remain byte-identical to the full revalidation:783 suite tests,78 extra checks and37 manual scenarios already passed. No code/package changes were made while publishing. Existing two raw audit dispositions remain documented; production audits were zero in that validation.
- BACKLOG was excluded from every commit, the PR file list and the merged tree. It remains ignored/untracked. All95 SEC records and all BE tasks/statuses are preserved. Only this local publication note was added after merge.
- PR: https://github.com/VarnerDamascenoJr/exchange-matching/pull/36 . Local publication evidence: `/home/varner/.codex/reports/exchange-matching/2026-11-02_publication-security-remediation/RELATORIO.md`.
