# P2P

## Get allowed inputs

| Param        | Description            | Type   | Required |
| ------------ | ---------------------- | ------ | -------: |
| amount       | Amount                 | number |        ✔️ |
| currencyCode | Currency to be applied | string |        ✔️ |

Request:

```http
GET /forward-p2p/allowed-inputs?amount=1000&currencyCode=RUB

Authorization: Bearer {{YOUR_PUBLIC_KEY}}
```

Response

```json
{
  "inputs": [
    {
      "id": "ae96cad0-67cf-4232-b69b-5234a22be6d9",
      "amount": "1020",
      "currencyCode": "RUB",
      "lockDuration": 60,
      "activeUntil": "2021-11-01T16:47:50.114Z"
    },
    {
      "id": "2fef3924-398d-42ba-a6bf-289f6cb3652a",
      "amount": "990",
      "currencyCode": "RUB",
      "lockDuration": 60,
      "activeUntil": "2021-11-01T16:47:50.114Z"
    }
  ]
}
```

## Create Destination

Adds destination to registry for future use in `forward-p2p` transactions.
Destinations from registry will be available in [allowed inputs request](#get-allowed-inputs)

| Param        | Description                  | Type   | Required |
| ------------ | ---------------------------- | ------ | -------: |
| amount       | Amount                       | number |        ✔️ |
| currencyCode | Currency code                | string |        ✔️ |
| account      | Card number to receive funds | string |        ✔️ |
| referenceId  | ID in your system            | string |        ❌ |

Request:

```http
POST {{host}}/forward-p2p/destination
Authorization: Bearer {{YOUR_PUBLIC_KEY}}
X-Signature: UV4p5IbaIvox2KJWKctocTvRxM/7WkepE63Aabr0BZ8=
content-type: application/json

{
  "account": "4111111111111111",
  "amount": 1021,
  "currencyCode": "RUB"
}
```

Response

```json
{
  "amount": 1021,
  "currencyCode": "RUB",
  "account": "4111111111111111",
  "fee": 1,
  "referenceId": null,
  "confirmationUrl": null,
  "lockedUntil": null,
  "id": "f3d6563d-5c3f-41c6-87e5-76cd83727c24",
  "status": "initial",
  "createdAt": "2021-11-04T15:35:15.522Z",
  "updatedAt": "2021-11-04T15:35:15.522Z"
}
```
