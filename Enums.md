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
