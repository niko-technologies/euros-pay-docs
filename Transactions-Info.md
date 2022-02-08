# Transactions Info

## Get Transaction Details

| Param                   | Description                                                                                                                                           | Type   |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| id                      | Transaction id in SecurePayCard system                                                                                                                | string |
| orderId                 | Identifier in your system.                                                                                                                            | string |
| amount                  | Transaction amount                                                                                                                                    | number |
| currencyCode            | Transaction currency code.                                                                                                                            | string |
| fee                     | Transaction fee                                                                                                                                       | number |
| isFeeIncluded           | If fee included in amount `true` else `false`                                                                                                         | bool   |
| customerIp              | Customer ip                                                                                                                                           | string |
| locale                  | Customer locale                                                                                                                                       | string |
| description             | Additional message from partner system for describing transaction                                                                                     | string |
| redirectUrl             | URL to which client will be returned after successful or pending transaction                                                                          | string |
| failRedirectUrl         | URL to which client will be returned if transaction fails and it is known at the redirect moment                                                      | string |
| confirmationUrl         | URL to which webhook with transaction data will be sent. Should be some API handler to perform actions, depends on transaction status or other params | string |
| type                    | Transaction type. `payment` used by default. Enum [Transaction types](Enums.md#Transaction types)                                                     | string |
| status                  | Transaction status. Enum [Transaction Statuses](Enums.md#Transaction statuses)                                                                        | string |
| confirmationStatus      | Transaction confirmation status in partner system. Enum [Transaction confirmation statuses](Enums.md#Transaction confirmation statuses)               | string |
| partnerData             | Any data in JSON string format, will be added to confirmation body, when the webhook is triggered                                                     | string |
| receiptAdditionalFields | Object with custom partner data for client receipt                                                                                                    | object |
| client                  | Client data to connect transaction. Can be `null`.                                                                                                    | Client |
| client.phone            | Client phone is used as main identifier                                                                                                               | string |
| client.email            | Client email is used as secondary identifier and could be omitted                                                                                     | string |
| card                    | Card data for this transaction. Can be `null`.                                                                                                        | object |
| card.maskedPan          | Masked card pan.                                                                                                                                      | string |
| createdAt               | Date of transaction creation. Format `2022-01-27T11:18:13.637Z`                                                                                       | string |

Request:

```http
POST /v1/transactions/{{OUR_TRANSACTION_ID}}
Authorization: Bearer {{YOUR_PUBLIC_KEY}}
Content-type: application/json
```

Response:

```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "orderId": "AotiD2kuaqu8aeb",
  "amount": 1639,
  "currencyCode": "UAH",
  "fee": 0,
  "isFeeIncluded": false,
  "customerIp": null,
  "locale": "ua",
  "description": null,
  "redirectUrl": null,
  "failRedirectUrl": null,
  "confirmationUrl": null,
  "type": "payment",
  "status": "success",
  "confirmationStatus": "success",
  "partnerData": {},
  "receiptAdditionalFields": {},
  "createdAt": "2022-01-27T11:18:13.637Z",
  "card": null,
  "client": null
}
```
