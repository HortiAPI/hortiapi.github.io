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
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.52; .NET 8.0.24; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

> Request content
``` json
{
  "state": "order/direct-debit-state:draft",
  "kind": "order/kind:direct-debit",
  "action": "",
  "orderDate": "2026-03-02T00:00:00+01:00",
  "shipDate": "2026-03-02T00:00:00+01:00",
  "invoiceDate": "2026-03-05T00:00:00+01:00",
  "description": "my order",
  "resources": [
    "reference/supplier:7890"
  ],
  "supplier": {
    "resources": [
      "ai2/account-number:99992"
    ]
  },
  "customer": {
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
      "resources": [
        "reference/supplier:1234",
        "reference/buyer:3456"
      ],
      "supplier": {},
      "buyer": {},
      "product": {
        "industryId": "27157",
        "type": "product",
        "description": "",
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

---

> Response headers (201)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Location: /order/yS_eSuF2X0iE43lJWv5QOw
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

> Response content
``` json
{
  "id": "yS_eSuF2X0iE43lJWv5QOw",
  "state": "",
  "kind": "",
  "action": "",
  "orderDate": "2026-03-01T23:00:00+00:00",
  "shipDate": "2026-03-01T23:00:00+00:00",
  "invoiceDate": "2026-03-04T23:00:00+00:00",
  "description": "my order",
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "8718288056672",
    "name": "Test kweker"
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "8718288056689",
    "name": "Test koper"
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

Use the received id (yS_eSuF2X0iE43lJWv5QOw) and use it to get the status of the direct-debit

> GET https://v3.sandbox.hortiapi.net/order/yS_eSuF2X0iE43lJWv5QOw?IncludeLines=True

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.52; .NET 8.0.24; +https://hortiapi.com)
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
  "id": "yS_eSuF2X0iE43lJWv5QOw",
  "state": "",
  "kind": "",
  "action": "",
  "orderDate": "2026-03-01T23:00:00+00:00",
  "shipDate": "2026-03-01T23:00:00+00:00",
  "invoiceDate": "2026-03-04T23:00:00+00:00",
  "description": "my order",
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "8718288056672",
    "name": "Test kweker"
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "8718288056689",
    "name": "Test koper"
  },
  "total": {
    "lines": 0,
    "pieces": 0,
    "price": 0
  },
  "lines": []
}
```

