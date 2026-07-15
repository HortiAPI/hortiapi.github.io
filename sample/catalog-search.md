---
layout: default
title: Get all catalog items
permalink: /sample/catalog-search
---

# Get all catalog items

Get all catalog items with HortiApi

> POST https://v3.sandbox.hortiapi.net/catalog/search

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
  "kind": "",
  "state": ""
}
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
[
  {
    "id": "KLvbZZQPMkmBNiA5J7m_SA",
    "kind": "",
    "state": "",
    "action": "",
    "supplier": {
      "id": "MqVI_H7Tmk6vQFoQEZPQ2A",
      "gln": "8713783483923",
      "name": "Lakerfield B.V."
    },
    "product": {
      "industryId": "27157",
      "supplierId": "FA3",
      "customerId": "",
      "manufacturerId": "",
      "type": "product",
      "description": "",
      "manufacturer": {
        "id": "MqVI_H7Tmk6vQFoQEZPQ2A",
        "gln": "8713783483923",
        "name": "Lakerfield B.V."
      },
      "features": [
        {
          "type": "S20",
          "value": "040"
        },
        {
          "type": "S05",
          "value": "023"
        },
        {
          "type": "L11",
          "value": "020"
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
    "packings": [
      {
        "bunch": {
          "code": "800",
          "quantity": 20
        },
        "box": {
          "code": "800",
          "quantity": 4
        },
        "layer": {
          "code": "",
          "quantity": 9
        },
        "carrier": {
          "code": "1",
          "quantity": 3
        }
      }
    ],
    "prices": [
      {
        "type": "provisional",
        "minimum": {
          "unit": "box",
          "value": 1
        },
        "amount": {
          "value": 0.32,
          "currency": "EUR"
        }
      }
    ],
    "references": [],
    "notes": [],
    "photos": [
      {
        "url": "https://sandbox.hortiapi.com/photo/sq1k/TPR0CUZ0sEyo28ozk8v5XA.jpg"
      }
    ]
  }
]
```

