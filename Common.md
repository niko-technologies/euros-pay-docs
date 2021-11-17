# Common endpoints

## Get Balance

Retrieve balance for all or specified currencies. If `currencyCodes` param not passed, return balances for all currencies.

| Param         | Description                               | Example | Required |
| ------------- | ----------------------------------------- | ------- | -------- |
| currencyCodes | Get balance only for specified currencies | EUR,RUB | ❌        |

Request:

```http
GET /v1/balance
Authorization: Bearer {{YOUR_PUBLIC_KEY}}
```

Response:

```json
{
  "EUR": 100,
  "RUB": 9999
}
```
