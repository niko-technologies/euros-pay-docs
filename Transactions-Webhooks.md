# Transaction Webhooks

Webhook is sent to `confirmationUrl` passed in body when transaction is created.

Webhook is sent when transaction status changes (not only to final one).

Webhook is signed and signature added to the `x-signature` header and is generated depends on data of the request and partner `secret key`.

Webhook is retried up to 30 times when the handle of webhook is unsuccessful by your side.


## Webhook body

| Param        | Description                                | Type   |
| ------------ | ------------------------------------------ | ------ |
| amount       | Paid amount                                | number |
| currencyCode | Transaction currency code                  | string |
| id           | ID of transaction in our system            | string |
| orderId      | ID of transaction in your system           | string |
| status       | Transaction status                         | string |
| partnerData  | Data passed to transaction at the creation | JSON   |

## Webhook signature header

| Name            | Description                             | Type   |
| --------------- | --------------------------------------- | ------ |
| x-signature     | Signature from body                     | string |


Example:

```json
{
  "amount": 10,
  "currencyCode": "EUR",
  "id": "00000000-0000-0000-0000-000000000000",
  "orderId": "c757d923-5deb-4774-80fe-162a19293c2e",
  "status": "success",
  "partnerData": {
    "any": {
      "json": "passed by you"
    }
  }
}
```

## Successful handling

To confirm that webhook has been handled successfully your service should respond with status `201` and body:

```json
{
  "confirmed": true
}
```

If status or response body differs, the webhook will be marked as failed and retried after some time (depends on retry strategy settings).
So, keep in mind that unsuccessful webhook handling along with partial changing of your data leads to inconsistent state of your application and could cause serious logic faults.

## Creating signature

The signature is formed in the same way as on the creation of a transaction, differences only in the body of the request

* [Authorization](Authorization#creating-signature)
