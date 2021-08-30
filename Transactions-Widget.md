# Widget Transactions

## Create Transaction

| Param           | Description                                                                                                                                           | Type   | Required |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------: |
| client          | Client data to connect transaction                                                                                                                    | Client |        ❌ |
| client.phone    | Client phone is used as main identifier                                                                                                               | string |        ❌ |
| client.email    | Client email is used as secondary identifier and could be omitted                                                                                     | string |        ❌ |
| amount          | Transaction amount                                                                                                                                    | number |        ✔️ |
| currencyCode    | Transaction currency code, should be one of available currencies for your account                                                                     | string |        ✔️ |
| orderId         | Identifier in your system, should be unique for each transaction. If duplicated identifier is sent, the existing transaction returns                  | string |        ✔️ |
| redirectUrl     | URL to which client will be returned after successful or pending transaction                                                                          | string |        ✔️ |
| failRedirectUrl | URL to which client will be returned if transaction fails and it is known at the redirect moment                                                      | string |        ❌ |
| confirmationUrl | URL to which webhook with transaction data will be sent. Should be some API handler to perform actions, depends on transaction status or other params | string |        ✔️ |
| data            | Any data in JSON string format, will be added to confirmation body, when the webhook is triggered                                                     | string |        ❌ |

Request:

```http
POST /v1/transactions/widget

Authorization: Bearer {{YOUR_PUBLIC_KEY}}
X-Signature: {{CALCULATED_SIGNATURE}}
Content-type: application/json

{
  "client": {
    "phone": "+380505555555",
    "email": "test@securepaycard.com"
  },
  "amount": 10,
  "currencyCode": "EUR",
  "orderId": "c757d923-5deb-4774-80fe-162a19293c2e",
  "redirectUrl": "https://some-partner.securepaycard.com/redirect",
  "confirmationUrl": "https://some-partner.securepaycard.com/confirm"
}
```

Response

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "url": "https://payment.widget/link"
}
```
