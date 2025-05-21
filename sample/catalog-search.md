---
layout: default
title: Get all catalog items
permalink: /sample/catalog-search
---

# Get all catalog items

Get all catalog items with HortiApi

# POST https://sandbox.hortiapi.net/v3/catalog/search

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.11; .NET 8.0.12; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

Request content
``` json
{
  "resources": [],
  "id": "",
  "state": "",
  "manufacturer": null,
  "method": "none",
  "limit": 1000
}
```
Response headers
```
Date: Wed, 21 May 2025 22:15:42 GMT
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

Response content
``` json
[
  {
    "resources": [],
    "id": "ePmGqwO54kuKVBWCJk9BSA",
    "state": "",
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
        "minimum": null,
        "maximum": null,
        "amount": {
          "value": 1,
          "currency": "EUR"
        }
      }
    ],
    "references": [
      {
        "name": "IRN",
        "value": "6ctjog7aulueje5b6ottz3zcji"
      }
    ],
    "notes": [],
    "photos": [
      {
        "url": "https://vmp4dev.app/photo/sq1k/8KaXG-Ci6ESTofOnPO8iSg.jpg"
      }
    ]
  }
]
```

