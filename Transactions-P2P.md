# P2P

## Get allowed inputs

| Param        | Description            | Type   | Required |
| ------------ | ---------------------- | ------ | -------: |
| amount       | Amount                 | number |     true |
| currencyCode | Currency to be applied | string |     true |

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
