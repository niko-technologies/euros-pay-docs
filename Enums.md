# Enums

## Transaction statuses

| Status     | Description                                      |
| ---------- | ------------------------------------------------ |
| initial    | Default status when transaction created.         |
| processing | Transaction is being processed.                  |
| failed     | Transaction processing failed (final).           |
| expired    | Time for transaction processing expired (final). |
| success    | Transaction processed successfully (final).      |

## Transaction types

| Type        |
| ----------- |
| payment     |
| forward-p2p |

## Transaction confirmation statuses

Define the status of merchant service webhook handling about transaction.

| Status  | Description                                                                                                                 |
| ------- | --------------------------------------------------------------------------------------------------------------------------- |
| initial | Webhook hasn't been sent yet.                                                                                               |
| failed  | Webhook handling failed. Request will be retried according to specified backoff strategy until reaching the attempts limit. |
| success | Webhook handled successfully.                                                                                               |

## P2P Destination statuses

| Status   | Description                                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------------------------------ |
| initial  | Default status for newly created destination.                                                                            |
| declined | Defines that destination was declined and no longer available for matching.                                              |
| used     | Destination is used and waiting to be paid or failed.                                                                    |
| paid     | Marks destination as paid.                                                                                               |
| failed   | Marks that transaction is failed. Destination will be returned to the initial status to be available for matching again. |

## Response statuses

| HTTP Status | Description                                                                                                                                     |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 200, 201    | Successful response                                                                                                                             |
| 400         | Failed request. Contains either invalid or wrong data that cannot be processed. Details are provided in response body.                          |
| 401         | Authorization error. Could be as a result of invalid or inactive auth token provided or wrong signature. Details are provided in response body. |
| 403         | Forbidden action requested.                                                                                                                     |
| 500         | Something occasionally went wrong during request processing                                                                                     |
