---
layout: default
title: Direct debit
permalink: /sample/direct-debit
---

# Direct debit

Create a order for direct debt with HortiApi

# POST https://v3.sandbox.hortiapi.net/order

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.30; .NET 8.0.12; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

Request content
``` json
{
  "id": "",
  "state": "",
  "kind": "order/kind:direct-debit",
  "action": "",
  "orderDate": "2025-08-06T00:00:00\u002B02:00",
  "shipDate": "0001-01-01T00:00:00\u002B00:00",
  "invoiceDate": "2025-08-09T00:00:00\u002B02:00",
  "description": "my order",
  "supplier": {
    "id": "",
    "resources": [
      "ai2/account-number:99999"
    ]
  },
  "customer": {
    "id": "",
    "resources": [
      "ai2/account-number:99999"
    ]
  },
  "total": {
    "lines": 0,
    "pieces": 0,
    "price": 0
  },
  "lines": [
    {
      "id": "",
      "order": "",
      "state": "",
      "kind": "",
      "action": "",
      "price": {
        "type": "invoice",
        "amount": {
          "value": 0.751,
          "currency": "EUR"
        }
      },
      "supplier": {
        "id": ""
      },
      "buyer": {
        "id": ""
      },
      "product": {
        "industryId": "27157",
        "type": "product",
        "description": {
          "value": "",
          "language": "NL"
        },
        "features": [
          {
            "type": "S20",
            "value": "060"
          },
          {
            "type": "S05",
            "value": "023"
          },
          {
            "type": "S19",
            "value": "035"
          },
          {
            "type": "L11",
            "value": "010"
          },
          {
            "type": "S98",
            "value": "A1"
          },
          {
            "type": "S62",
            "value": "NL"
          }
        ],
        "classifications": []
      },
      "quantity": {
        "unit": "box",
        "value": 5
      },
      "packing": {
        "box": {
          "code": "996",
          "quantity": 100
        }
      },
      "references": [
        {
          "name": "VN",
          "value": "123456789"
        },
        {
          "name": "ACL",
          "value": "987654321"
        },
        {
          "name": "ON",
          "value": "987654321"
        }
      ],
      "notes": [],
      "photos": [],
      "delivery": {
        "terms": "undefined"
      }
    }
  ]
}
```
Response headers (501)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Transfer-Encoding: chunked
Content-Type: application/problem+json
```

Response content
``` json
{
  "context": [],
  "type": "https://hortiapi.com/error/not-implemented",
  "title": "Not Implemented",
  "status": 501,
  "detail": "The endpoint \u0027/horti-api/v3/order\u0027 is not implemented yet.",
  "instance": "/horti-api/v3/order"
}
```

