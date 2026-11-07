# Backend — Exchange Matching

[Archive index](README.md) · [Project overview](../README.md) · [October journal](../2026-10.md) · [November journal](../2026-11.md)

Matching, balances, financial precision, concurrency, and delivery recovery.

## Contents

- [Matching concurrency and maker priority](#matching-concurrency-and-maker-priority)
- [Delivery recovery and retry handling](#delivery-recovery-and-retry-handling)
- [Financial precision and settled volume](#financial-precision-and-settled-volume)

## Matching concurrency and maker priority

Serial processing across workers and direct calls, waiting for locked makers, and incremental candidate loading.

| ID    | Priority | Short description                                                                | Expected result                                                                                                                                                                      | Status  |
| ----- | -------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| BE-01 | High     | Configure BullMQ global concurrency to 1.                                        | Multiple worker instances process only one matching job at a time.                                                                                                                   | Done    |
| BE-02 | High     | Add a PostgreSQL transaction lock for BTC/USD matching.                          | Matching remains sequential even when called outside BullMQ.                                                                                                                         | Done    |
| BE-03 | High     | Replace maker `SKIP LOCKED` with waiting and eligibility revalidation.           | Concurrent cancellation cannot cause a better eligible offer to be skipped.                                                                                                          | Done    |
| BE-04 | Medium   | Fetch and lock makers incrementally.                                             | Matching stops loading and locking offers once the taker is satisfied.                                                                                                               | Done    |

## Delivery recovery and retry handling

Outbox polling failures, worker infrastructure errors, and persistent realtime retry deadlines.

| ID    | Priority | Short description                                                                | Expected result                                                                                                                                                                      | Status  |
| ----- | -------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| BE-05 | High     | Handle startup and polling errors in both outbox dispatchers.                    | Database failures are logged, and dispatching resumes without unhandled promise rejections.                                                                                          | Done    |
| BE-06 | High     | Handle the BullMQ worker `error` event.                                          | Infrastructure errors receive explicit handling and useful logs.                                                                                                                     | Done    |
| BE-07 | Medium   | Add `nextAttemptAt` and exponential backoff to realtime outbox retries.          | Failed events retry after delays from 2 to 60 seconds, preserving the existing attempt limit and dead letter behavior.                                                               | Done    |

## Financial precision and settled volume

USD market volume must sum the truncated cost of each fill so reporting agrees with settlement.

| ID    | Priority | Short description                                                                | Expected result                                                                                                                                                                      | Status  |
| ----- | -------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| BE-08 | Medium   | Calculate USD market volume using rounded costs per fill.                        | Reported volume matches settled amounts; two fills of `0.1 × 0.33333333` total `0.06666666 USD`.                                                                                     | Done |

### Original evidence notes

- [QA revalidation](validation-and-publication.md#qa-revalidation)
