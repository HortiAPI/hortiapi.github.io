---
layout: default
title: Modify stock quantity
permalink: /sample/stock-modify-quantity
---

# Modify stock quantity

Modify the first stock item, add 1 additional box to the stock item

> POST https://v3.sandbox.hortiapi.net/stock/search

> Request headers
```
Accept: application/json
Prefer: max-results=10
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.55; .NET 8.0.25; +https://hortiapi.com)
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
    "id": "y0HD8VE2ekW81fikt6bamA",
    "kind": "",
    "state": "",
    "action": "",
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
    "quantity": {
      "unit": "box",
      "value": 51
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
          "value": 2.8,
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
]
```

> POST https://v3.sandbox.hortiapi.net/stock

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.55; .NET 8.0.25; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

> Request content
``` json
{
  "id": "y0HD8VE2ekW81fikt6bamA",
  "kind": "",
  "state": "",
  "action": "stock/action:quantity-set",
  "quantity": {
    "unit": "box",
    "value": 52
  }
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
{
  "id": "y0HD8VE2ekW81fikt6bamA",
  "kind": "",
  "state": "",
  "action": "",
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
  "quantity": {
    "unit": "box",
    "value": 52
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
        "value": 2.8,
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

