---
layout: default
title: Connect Sample
permalink: /sample/connect
---

# Connect Sample

Connect Sample

# GET https://v3.sandbox.hortiapi.net/me

Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
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
  "application": {
    "id": "",
    "name": "sandbox.hortiapi.com application",
    "resources": [
    ]
  },
  "companies": [
    {
      "id": "uWXsD0b-UEiIjVKA3smDDg",
      "name": "Lakerfield B.V.",
      "applications": null,
      "resources": null
    },
    {
      "id": "_N_8wOAl6kiaAXnXzHxLSQ",
      "name": "Algemeen koper",
      "applications": null,
      "resources": null
    }
  ],
  "company": null,
  "user": {
    "id": "IQ0hBMwEN0yJP2ty3rSZEg",
    "name": "Michael Lakerveld",
    "resources": null
  },
  "resources": [
    "horti-api/health:healthy"
  ]
}
```

# GET https://v3.sandbox.hortiapi.net/me

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
  "application": {
    "id": "",
    "name": "sandbox.hortiapi.com application",
    "resources": [
    ]
  },
  "companies": [
    {
      "id": "uWXsD0b-UEiIjVKA3smDDg",
      "name": "Lakerfield B.V.",
      "applications": null,
      "resources": null
    },
    {
      "id": "_N_8wOAl6kiaAXnXzHxLSQ",
      "name": "Algemeen koper",
      "applications": null,
      "resources": null
    }
  ],
  "company": {
    "id": "uWXsD0b-UEiIjVKA3smDDg",
    "name": "Lakerfield B.V.",
    "applications": null,
    "resources": null
  },
  "user": {
    "id": "IQ0hBMwEN0yJP2ty3rSZEg",
    "name": "Michael Lakerveld",
    "resources": null
  },
  "resources": [
    "horti-api/health:healthy"
  ]
}
```

