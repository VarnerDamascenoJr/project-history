# Exchange Matching

A BTC/USD limit-order exchange built to explore financial correctness, transactional matching, asynchronous delivery, and a realtime trading interface.

**Source:** [VarnerDamascenoJr/exchange-matching](https://github.com/VarnerDamascenoJr/exchange-matching)  
**Local checkout:** `/home/varner/aprendizagem/projetos/exchange-matching`  
**Initial history import:** 2026-11-02  
**Initial source baseline:** [`f01c2be`](https://github.com/VarnerDamascenoJr/exchange-matching/commit/f01c2be174b162710ec3555165bdca7769014864), the merge of [PR #36](https://github.com/VarnerDamascenoJr/exchange-matching/pull/36).  
**History updated:** 2026-11-07  
**Latest recorded source:** [`7b93546`](https://github.com/VarnerDamascenoJr/exchange-matching/commit/7b93546c5092e182ea5dae59633e50c61a38969d), the merge of [PR #39](https://github.com/VarnerDamascenoJr/exchange-matching/pull/39) on 2026-11-06 in `America/Fortaleza`.

## Reading guide

| Record | What it covers |
| --- | --- |
| [July 2026](2026-07.md) | Initial API, authentication, matching engine, and exchange interface |
| [September 2026](2026-09.md) | Project identity and documentation cleanup |
| [October 2026](2026-10.md) | Repository boundaries, financial precision, matching concurrency, durable retries, and isolated testing |
| [November 2026](2026-11.md) | QA and dependency fixes, matching recovery, monetary invariants, and wallet balance breakdown |
| [Completed activities](completed-activities/README.md) | The initial import's 103 completed records and original evidence, organized into four broad areas |

## Technical context

The backend uses NestJS, TypeScript, Prisma, PostgreSQL, Redis, BullMQ, and Socket.IO. The frontend uses React, TypeScript, Vite, Material UI, TanStack Query, and Socket.IO Client.

The HTTP API and matching worker run separately. PostgreSQL holds durable business state. Redis supports queue delivery and cross-process events. Matching reserves balances, follows price-time priority, supports partial fills, and charges maker and taker fees of 0.5% and 0.3% respectively.

## Major decisions

- Serialize matching through both BullMQ global concurrency and a PostgreSQL transaction lock. Direct service calls must respect the same market lock.
- Wait for locked makers and revalidate eligibility to preserve price-time priority during concurrent cancellation.
- Keep financial values exact through storage, settlement, form submission, and display. Sum USD volume from costs truncated per fill: `SUM(TRUNC(amount * price, 8))`.
- Persist delivery intent and retry deadlines so a Redis interruption can recover without restarting the application.
- Run database and browser validation against disposable infrastructure, followed by manual exploration.
- Resolve dependency findings through compatible updates and verified dispositions. Preserve the distinction between scanner output and an exploitable application path.
- Exercise delivery failures through real API and worker processes. Recover confirmed lost Redis jobs with reviewed, bounded matching-intent restoration batches.
- Verify per-account ledgers and global conservation using an independent integer oracle over persisted operation sequences.
- Explain available, reserved, and total BTC/USD balances separately, preserving exact decimal totals in the responsive interface.

Details and tradeoffs are recorded in the monthly journals. The source repository remains authoritative for implementation and runtime instructions.

## Latest recorded validation

The latest delivery, [PR #39](https://github.com/VarnerDamascenoJr/exchange-matching/pull/39), records **64 frontend tests** and **2 real API/worker browser journeys** passing on **2026-11-06**, along with frontend lint/build, Playwright type checking, backend build, and layout checks at 320, 390, 768, and 1600 pixels. Backend, frontend, and browser PR checks all passed.

The preceding backend delivery, [PR #38](https://github.com/VarnerDamascenoJr/exchange-matching/pull/38), records **341 database E2E/oracle tests** and **413 backend unit tests** passing on **2026-11-05**. Its 38 focused monetary checks are included in the 341, rather than additional tests. These are dated results for their respective deliveries; they are not a newly executed combined validation. See the [November journal](2026-11.md) for each PR's scope and evidence.

### Earlier full security validation

The full validation on **2026-11-01** passed **783 suite tests**, **78 additional security and compatibility checks**, and **37 manual or exploratory scenarios**. The exact validated file contents were later published in PR #36. Backend, frontend, and browser CI passed both before and after the merge on **2026-11-02**.

At that validation, the full audit retained **2 distinct advisories with documented dispositions**: legacy Minimatch and locally patched Deepmerge. Production-only audits reported zero findings. All 95 SEC activities were marked `Done`; this does not mean the full audit returned zero findings.

These results were imported from existing evidence. No application validation or dependency audit was rerun to create or update this history repository; the November 1 audit is not a new audit of PR #39.

## Active work and import boundary

`BE-09`, `BE-10`, `BE-11`, and `BE-12` remained pending at import and are still marked `Pending` in the local backlog inspected on 2026-11-07. Their current descriptions and status belong in the exclusively local `BACKLOG.md` in the source checkout. Neither the earlier general validation nor the later recovery and monetary suites automatically completes BE-12's full regression coverage task.

The original backlog has been preserved for review. A proposed version containing only the four pending activities was prepared outside both repositories. Completed records and historical notes were copied into this history repository before any proposed removal from the active backlog.

The initial import covers the available Git history from July through November and every completed BE/SEC record in the current backlog. Seven older QA findings had already been removed from that backlog; the journals summarize their confirmed fixes and distinguish preparation issues from application defects. Their full original evidence remains in the existing local reports.

The 2026-11-07 update adds PRs #37–#39 to the monthly journal. No new completed BE/SEC identifiers were present in the local backlog, so the 103-record initial activity archive remains unchanged. Validation for these deliveries comes from their PR descriptions and successful GitHub checks; no corresponding new local report was found in the existing evidence directory.

## Source documentation at the baseline

- [Project README](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/README.md)
- [Decimal policy](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/docs/decimal-policy.md)
- [SEC-001–005 review](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/docs/security-sec-001-005.md)
- [SEC-011–015 review](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/docs/security-sec-011-015.md)
- [SEC-016–035 review](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/docs/security-sec-016-035.md)
- [Remaining advisory review](https://github.com/VarnerDamascenoJr/exchange-matching/blob/f01c2be174b162710ec3555165bdca7769014864/docs/security-sec-remaining.md)

## Source documentation at the latest recorded commit

- [Project README](https://github.com/VarnerDamascenoJr/exchange-matching/blob/7b93546c5092e182ea5dae59633e50c61a38969d/README.md)
- [Matching delivery and recovery](https://github.com/VarnerDamascenoJr/exchange-matching/blob/7b93546c5092e182ea5dae59633e50c61a38969d/docs/matching-recovery.md)
- [Monetary invariants and reproducible sequences](https://github.com/VarnerDamascenoJr/exchange-matching/blob/7b93546c5092e182ea5dae59633e50c61a38969d/docs/monetary-invariants.md)
