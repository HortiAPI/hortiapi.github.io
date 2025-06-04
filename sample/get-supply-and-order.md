---
layout: default
title: Get supply and order
permalink: /sample/get-supply-and-order
---

# Get supply and order

Retrieve a supply stream and order 1 box of the last supply line

# POST https://v3.sandbox.hortiapi.net/supply

Request headers
```
Accept: application/vnd.hortiapi.event+json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.14; .NET 8.0.12; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

Request content
``` json
{
  "streamId": "WfWSKJG730SLr9rML9JNFg",
  "method": "sync-start",
  "limit": 1000,
  "resources": []
}
```
Response headers (200)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

Response content
``` json
[
  {
    "type": "update",
    "entity": {
      "id": "AAAAAQAAACCbcsO97USSrQ",
      "state": "",
      "article": {
        "f1": "S20",
        "f2": "",
        "f3": "S05",
        "f4": "S19",
        "f5": "L11",
        "f6": "",
        "f7": "",
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
        "resources": [],
        "id": "2fd8Au0fvEC97JpuHP6iSA",
        "list": "vbn",
        "code": "27157",
        "group": null,
        "name": "Rosa grootbloemig Red Naomi!",
        "tradeName": "R GR RED NAOMI!"
      },
      "supplier": {
        "id": "uWXsD0b-UEiIjVKA3smDDg",
        "gln": "8713783483923",
        "name": "Lakerfield B.V."
      },
      "product": {
        "industryId": "27157",
        "supplierId": "FA1",
        "customerId": "",
        "manufacturerId": "",
        "type": "product",
        "description": {
          "value": "",
          "language": "NL"
        },
        "manufacturer": {
          "id": "uWXsD0b-UEiIjVKA3smDDg",
          "gln": "8713783483923",
          "name": "Lakerfield B.V."
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
        "value": 8
      },
      "packing": {
        "bunch": {
          "code": "800",
          "quantity": 10
        },
        "bundle": null,
        "box": {
          "code": "560",
          "quantity": 8
        },
        "layer": {
          "code": "",
          "quantity": 9
        },
        "carrier": {
          "code": "",
          "quantity": 3
        }
      },
      "prices": [
        {
          "type": "provisional",
          "minimum": {
            "unit": "box",
            "value": 1
          },
          "maximum": null,
          "amount": {
            "value": 1,
            "currency": "EUR"
          }
        }
      ],
      "references": [],
      "notes": [],
      "photos": [
        {
          "url": "https://sandbox.hortiapi.com/photo/sq1k/8KaXG-Ci6ESTofOnPO8iSg.jpg"
        }
      ],
      "deliveries": [],
      "resources": []
    }
  }
]
```

# POST https://v3.sandbox.hortiapi.net/supply/order

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.14; .NET 8.0.12; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

Request content
``` json
{
  "id": "",
  "supply": "AAAAAQAAACCbcsO97USSrQ",
  "state": "",
  "quantity": {
    "unit": "box",
    "value": 1
  },
  "price": {
    "type": "invoice",
    "amount": {
      "value": 1,
      "currency": "EUR"
    }
  }
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
  "detail": "The endpoint \u0027/horti-api/v3/supply/order\u0027 is not implemented yet.",
  "instance": "/horti-api/v3/supply/order"
}
```

