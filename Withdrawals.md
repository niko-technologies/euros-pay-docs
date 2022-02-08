# Withdrawals

## List withdrawals

```http
GET /v1/withdrawals
Authorization: Bearer {{YOUR_PUBLIC_KEY}}
Content-Type: application/json
```

```json
{
  "items": [
    {
      "id": "646123f2-fa78-47a6-babd-f39f63bc82b0",
      "amount": 100,
      "currencyCode": "UAH",
      "fee": null,
      "status": "completed",
      "notes": null,
      "type": "auto-card",
      "requisites": {
        "cardNumber": "4111111111111111"
      },
      "rejectReason": null,
      "updatedAt": "2022-02-04T15:13:15.811Z",
      "createdAt": "2022-02-04T15:13:01.027Z"
    }
  ],
  "count": 1
}
```

## Get withdrawal by id

| Param                 | Description                                                                 | Type          |
| --------------------- | --------------------------------------------------------------------------- | ------------- |
| id                    | id in securepaycard                                                         | string        |
| amount                | amount in specified currency code                                           | number(float) |
| currencyCode          | withdrawal currency `UAH`                                                   | string        |
| fee                   | fee amount                                                                  | number(float) |
| status                | Withdrawal status. Enum [Withdrawal statuses](Enums.md#Withdrawal statuses) | string        |
| notes                 | Additional info about withdrawal provided by partner                        | string        |
| type                  | Withdrawal types. Enum [Withdrawal types](Enums.md#Withdrawal types)        | string        |
| requisites            | Object with additional parameters depends on withdrawal type                | string        |
| requisites.cardNumber | Card number for auto-card withdrawal                                        | string        |
| createdAt             | withdrawal creation iso date string                                         | string        |
| rejectReason          | json array of reject reasons                                                | string        |

```http
GET /v1/withdrawals/{{id}}
Authorization: Bearer {{YOUR_PUBLIC_KEY}}
Content-Type: application/json
```

```json
{
  "id": "646123f2-fa78-47a6-babd-f39f63bc82b0",
  "amount": 100,
  "currencyCode": "UAH",
  "fee": null,
  "status": "completed",
  "notes": null,
  "type": "auto-card",
  "requisites": {
    "cardNumber": "4111111111111111"
  },
  "rejectReason": null,
  "updatedAt": "2022-02-04T15:13:15.811Z",
  "createdAt": "2022-02-04T15:13:01.027Z"
}
```

## Create withdrawals

| param                 | description                                       | type          |
| --------------------- | ------------------------------------------------- | ------------- |
| amount                | withdrawal amount                                 | number(float) |
| currencyCode          | withdrawal currency                               | string        |
| type                  | Withdrawal types for not use only `auto-card`     | string        |
| requisites            | json object for withdrawal requisites             | object        |
| requisites.cardNumber | card number for funding. Required for `auto-card` | string        |

Request:

```http
POST /v1/withdrawals

Authorization: Bearer {{YOUR_PUBLIC_KEY}}
X-Signature: {{CALCULATED_SIGNATURE}}
Content-type: application/json

{
  "amount": 100,
  "currencyCode":"UAH",
  "type":"auto-card",
  "requisites": {
    "cardNumber":"4111111111111111",
  }
}
```

Response:

```json
{
  "id": "646123f2-fa78-47a6-babd-f39f63bc82b0",
  "amount": 100,
  "currencyCode": "UAH",
  "fee": null,
  "status": "initial",
  "notes": null,
  "type": "auto-card",
  "requisites": {
    "cardNumber": "4111111111111111"
  },
  "rejectReason": null,
  "updatedAt": "2022-02-04T15:13:15.811Z",
  "createdAt": "2022-02-04T15:13:01.027Z"
}
```

## Test cards

If you are using sandbox environment and building your integration use cards specified below to set specific status to the withdrawal.

| Card             | Status  |
| ---------------- | ------- |
| 4111111111111111 | success |
| 4242424242424242 | failed  |
