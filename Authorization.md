# Authorization

## General overview

Requests are authorized by adding `Authorization` header with `Bearer` token with partners `public key` value.

All non-GET requests should be verified by adding signature to headers.

Signature added to the `X-Signature` header and is generated depends on data of the request and partner `secret key`.

* Example of GET request w/o signature:

```http
GET /v1/transactions/c757d923-5deb-4774-80fe-162a19293c2e

Authorization: Bearer {{YOUR_PUBLIC_KEY}}
```

The signature is not required, because no data will be changed or created during GET request, so we don't have to validate the request body and params.

* Example of non-GET request with signature:

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

## Creating signature

Signature is created using `SHA256` HMAC (hash-based message authentication code) encoded in `base64` format.

Example of creating signature in Node.js:

```js
const { createHmac } = require('crypto');

const secretKey = 'YOUR_SECRET_KEY';

const data = {
  client: {
    phone: '+380505555555',
    email: 'test@securepaycard.com'
  },
  amount: 10,
  currencyCode: 'EUR',
  orderId: 'c757d923-5deb-4774-80fe-162a19293c2e',
  redirectUrl: 'https://some-partner.securepaycard.com/redirect',
  confirmationUrl: 'https://some-partner.securepaycard.com/confirm'
}

const signature = createHmac('sha256', secretKey)
  .update(JSON.stringify(data), 'utf8')
  .digest('base64')

console.log(signature); // 6nMyYkUf91GCcBUz+sQ0iJ5GZFaYcRJuXF89KzoJw8c=
```