---
layout: default
title: Direct debit
permalink: /sample/direct-debit
---

# Direct debit

Create a order for direct debt with HortiApi

## Submit draft direct-debt to server

Prepare a complete draft (state = order/direct-debit-state:draft) direct-debit (kind = order/kind:direct-debit) including all order-lines and submit it to the server.

> POST https://v3.sandbox.hortiapi.net/order

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.31; .NET 8.0.19; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

> Request content
``` json
{
  "id": "",
  "state": "order/direct-debit-state:draft",
  "kind": "order/kind:direct-debit",
  "action": "",
  "orderDate": "2025-08-12T00:00:00+02:00",
  "shipDate": "2025-08-12T00:00:00+02:00",
  "invoiceDate": "2025-08-15T00:00:00+02:00",
  "description": "my order",
  "supplier": {
    "id": "",
    "resources": [
      "ai2/account-number:99992"
    ]
  },
  "customer": {
    "id": "",
    "resources": [
      "ai2/account-number:99991"
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
      },
      "resources": [
        "reference/supplier:1234",
        "reference/buyer:3456"
      ]
    }
  ],
  "resources": [
    "reference/supplier:7890"
  ]
}
```

---

> Response headers (201)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Location: /order/HQq4A1oWCk23HOFxUUDdlQ
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

> Response content
``` json
{
  "id": "HQq4A1oWCk23HOFxUUDdlQ",
  "state": "order/direct-debit-state:draft",
  "kind": "order/kind:direct-debit",
  "action": "",
  "orderDate": "2025-08-11T22:00:00+00:00",
  "shipDate": "2025-08-11T22:00:00+00:00",
  "invoiceDate": "2025-08-14T22:00:00+00:00",
  "description": "my order",
  "resources": null,
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "8718288056672",
    "name": "Test kweker",
    "resources": null
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "8718288056689",
    "name": "Test koper",
    "resources": null
  },
  "total": {
    "lines": 0,
    "pieces": 0,
    "price": 0
  },
  "lines": []
}
```

## Get status of direct-debit

Use the received id (HQq4A1oWCk23HOFxUUDdlQ) and use it to get the status of the direct-debit

> GET https://v3.sandbox.hortiapi.net/order/HQq4A1oWCk23HOFxUUDdlQ?IncludeLines=True

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.31; .NET 8.0.19; +https://hortiapi.com)
Accept-Encoding: gzip, deflate, br
```


---

> Response headers (200)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

> Response content
``` json
{
  "id": "HQq4A1oWCk23HOFxUUDdlQ",
  "state": "order/direct-debit-state:collection-in-progress",
  "kind": "order/kind:direct-debit",
  "action": "",
  "orderDate": "2025-08-11T22:00:00+00:00",
  "shipDate": "2025-08-11T22:00:00+00:00",
  "invoiceDate": "2025-08-14T22:00:00+00:00",
  "description": "my order",
  "resources": null,
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "8718288056672",
    "name": "Test kweker",
    "resources": null
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "8718288056689",
    "name": "Test koper",
    "resources": null
  },
  "total": {
    "lines": 0,
    "pieces": 0,
    "price": 0
  },
  "lines": []
}
```

