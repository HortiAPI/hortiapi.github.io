---
layout: default
title: Get catalog item
permalink: /sample/catalog-get
---

# Get catalog item

Get a catalog item with HortiApi

# GET https://v3.sandbox.hortiapi.net/catalog/ePmGqwO54kuKVBWCJk9BSA

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.30; .NET 8.0.12; +https://hortiapi.com)
Accept-Encoding: gzip, deflate, br
```

Response headers (200)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

Response content
``` json
{
  "resources": [],
  "id": "ePmGqwO54kuKVBWCJk9BSA",
  "kind": "",
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
    "group": "cut-flowers",
    "groupCode": "10100101",
    "name": "Rosa grootbloemig Red Naomi!",
    "tradeName": "R GR RED NAOMI!",
    "genus": "Rosa",
    "species": null,
    "cultivar": "\u0027Schemocba\u0027"
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
  ]
}
```

