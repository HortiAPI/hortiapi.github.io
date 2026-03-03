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
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.53; .NET 8.0.24; +https://hortiapi.com)
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
      "description": "",
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
    "packing": {
      "bunch": {
        "code": "800",
        "quantity": 10
      },
      "box": {
        "code": "560",
        "quantity": 8,
        "measurements": [
          {
            "type": "grossWeight",
            "value": 2.5,
            "unit": "kg"
          }
        ]
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
        "amount": {
          "value": 2,
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
  },
  {
    "id": "vvhNqi8PjkiVXhe2T0Chqg",
    "kind": "",
    "state": "",
    "supplier": {
      "id": "uWXsD0b-UEiIjVKA3smDDg",
      "gln": "8713783483923",
      "name": "Lakerfield B.V."
    },
    "product": {
      "industryId": "107291",
      "supplierId": "FA2",
      "customerId": "",
      "manufacturerId": "",
      "type": "product",
      "description": "",
      "manufacturer": {
        "id": "uWXsD0b-UEiIjVKA3smDDg",
        "gln": "8713783483923",
        "name": "Lakerfield B.V."
      },
      "features": [
        {
          "type": "S01",
          "value": "010"
        },
        {
          "type": "S02",
          "value": "030"
        },
        {
          "type": "S09",
          "value": "005"
        },
        {
          "type": "S05",
          "value": "023"
        },
        {
          "type": "S11",
          "value": "002"
        },
        {
          "type": "S17",
          "value": "003"
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
          "value": "PA"
        },
        {
          "type": "B03",
          "value": "849"
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
          "f": "S01"
        },
        {
          "p": "required",
          "f": "S02"
        },
        {
          "p": "required",
          "f": "S09"
        },
        {
          "p": "required",
          "f": "S05"
        },
        {
          "p": "required",
          "f": "S11"
        },
        {
          "p": "required",
          "f": "S17"
        }
      ],
      "id": "EKq9ojpZ0UqWPzRMJUTooA",
      "list": "vbn",
      "code": "107291",
      "group": "house-plants",
      "groupCode": "20900201",
      "name": "Phalaenopsis Anthura Santos",
      "tradeName": "PHAL AN SANTOS",
      "genus": "Phalaenopsis",
      "cultivar": "'Phalcrazoh'"
    },
    "packing": {
      "bunch": {
        "code": "800",
        "quantity": 1
      },
      "box": {
        "code": "315",
        "quantity": 15,
        "measurements": [
          {
            "type": "grossWeight",
            "value": 2.5,
            "unit": "kg"
          }
        ]
      },
      "layer": {
        "code": "",
        "quantity": 4
      },
      "carrier": {
        "code": "",
        "quantity": 6
      }
    },
    "prices": [
      {
        "type": "provisional",
        "minimum": {
          "unit": "box",
          "value": 1
        },
        "amount": {
          "value": 1.85,
          "currency": "EUR"
        }
      }
    ],
    "references": [],
    "notes": [],
    "photos": [
      {
        "url": "https://sandbox.hortiapi.com/photo/sq1k/lo_ZwyJZDEGxM6Ms2JEaEA.jpg"
      }
    ]
  }
]
```

