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

## Response statuses

| HTTP Status | Description                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------- |
| 200, 201    | Successful response                                                                                                    |
| 400         | Failed request. Contains either invalid or wrong data that cannot be processed. Details are provided in response body. |
| 500         | Something occasionally went wrong during request processing                                                            |
