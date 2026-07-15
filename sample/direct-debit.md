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
x-company-id: MqVI_H7Tmk6vQFoQEZPQ2A
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.81; .NET 8.0.28; +https://hortiapi.com)
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
  "orderDate": "2026-07-15T00:00:00+02:00",
  "dispatchDate": "2026-07-15T00:00:00+02:00",
  "deliveryDate": "2026-07-15T00:00:00+02:00",
  "invoiceDate": "2026-07-18T00:00:00+02:00",
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
        "manufacturer": {
          "gln": "8718288056672"
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

---

> Response headers (201)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Location: /order/p_ekZDtxgUqla9EFIb3ezw
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

> Response content
``` json
{
  "id": "p_ekZDtxgUqla9EFIb3ezw",
  "state": "",
  "kind": "",
  "action": "",
  "orderDate": "2026-07-14T22:00:00+00:00",
  "dispatchDate": "2026-07-14T22:00:00+00:00",
  "deliveryDate": "2026-07-14T22:00:00+00:00",
  "invoiceDate": "2026-07-17T22:00:00+00:00",
  "description": "my order",
  "total": {
    "lines": 0,
    "pieces": 0,
    "net": {
      "value": 0,
      "currency": "EUR"
    }
  },
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "9999999999909",
    "name": "Test kweker"
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "9999999999908",
    "name": "Test koper"
  },
  "lines": []
}
```

## Get status of direct-debit

Use the received id (p_ekZDtxgUqla9EFIb3ezw) and use it to get the status of the direct-debit

> GET https://v3.sandbox.hortiapi.net/order/p_ekZDtxgUqla9EFIb3ezw?includeLines=True

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: MqVI_H7Tmk6vQFoQEZPQ2A
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.81; .NET 8.0.28; +https://hortiapi.com)
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
  "id": "p_ekZDtxgUqla9EFIb3ezw",
  "state": "",
  "kind": "",
  "action": "",
  "orderDate": "2026-07-14T22:00:00+00:00",
  "dispatchDate": "2026-07-14T22:00:00+00:00",
  "deliveryDate": "2026-07-14T22:00:00+00:00",
  "invoiceDate": "2026-07-17T22:00:00+00:00",
  "description": "my order",
  "total": {
    "lines": 1,
    "pieces": 5,
    "net": {
      "value": 3.755,
      "currency": "EUR"
    }
  },
  "supplier": {
    "id": "623cDkSZ40O8jrBJZdV9NA",
    "gln": "9999999999909",
    "name": "Test kweker"
  },
  "customer": {
    "id": "0HN-sJqu3UuOq2z3cQQsXg",
    "gln": "9999999999908",
    "name": "Test koper"
  },
  "lines": [
    {
      "id": "z0yqcgIJtkaStEd84RNm-Q",
      "order": "p_ekZDtxgUqla9EFIb3ezw",
      "state": "",
      "kind": "",
      "action": "",
      "article": {
        "features": [
          {
            "type": "B01",
            "value": "RO"
          },
          {
            "type": "B03",
            "value": "209"
          },
          {
            "type": "T01",
            "value": "001"
          },
          {
            "type": "T02",
            "value": "001"
          }
        ],
        "regulatoryFeatures": [
          {
            "p": "required",
            "f": "S20"
          },
          {
            "p": "empty",
            "f": ""
          },
          {
            "p": "required",
            "f": "S05"
          },
          {
            "p": "recommended",
            "f": "S19"
          },
          {
            "p": "required",
            "f": "L11"
          }
        ],
        "id": "2fd8Au0fvEC97JpuHP6iSA",
        "list": "vbn",
        "code": "27157",
        "group": "cut-flowers",
        "groupCode": "10100101",
        "name": "Rosa grootbloemig Red Naomi!",
        "tradeName": "R GR RED NAOMI!",
        "genus": "Rosa",
        "cultivar": "'Schemocba'"
      },
      "price": {
        "type": "invoice",
        "minimum": {
          "unit": "box",
          "value": 1
        },
        "amount": {
          "value": 0.751,
          "currency": "EUR"
        }
      },
      "supplier": {},
      "buyer": {},
      "product": {
        "industryId": "27157",
        "supplierId": "",
        "customerId": "",
        "manufacturerId": "",
        "type": "product",
        "description": "",
        "manufacturer": {
          "id": "8Cq7MJ8WV027jmDyXeQEBg",
          "gln": "8718288056672",
          "name": "#Test kweker"
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
        "value": 0
      },
      "packing": {
        "bunch": {
          "code": "800",
          "quantity": 1
        },
        "box": {
          "code": "996",
          "quantity": 100
        },
        "layer": {
          "code": "19",
          "quantity": 1
        },
        "carrier": {
          "code": "1",
          "quantity": 1
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

