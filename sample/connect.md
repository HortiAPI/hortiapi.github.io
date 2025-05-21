---
layout: default
title: Connect Sample
permalink: /sample/connect
---

# Connect Sample

Connect Sample

# GET https://sandbox.hortiapi.net/v3/me

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.11; .NET 8.0.12; +https://hortiapi.com)
Accept-Encoding: gzip, deflate, br
```

Response headers
```
Date: Wed, 21 May 2025 22:15:39 GMT
Transfer-Encoding: chunked
Content-Type: application/json; charset=utf-8
```

Response content
``` json
{
  "resources": [
    "horti-api/health:healthy"
  ],
  "application": {
    "resources": [
    ],
    "id": "",
    "name": "sandbox.hortiapi.com application"
  },
  "companies": [
    {
      "resources": [],
      "id": "uWXsD0b-UEiIjVKA3smDDg",
      "name": "Lakerfield B.V.",
      "applications": null
    }
  ],
  "user": {
    "resources": [],
    "id": "IQ0hBMwEN0yJP2ty3rSZEg",
    "name": "Michael Lakerveld"
  }
}
```

