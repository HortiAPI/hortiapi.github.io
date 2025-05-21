---
layout: default
title: Connect without ApiKey
permalink: /sample/connect-without-apikey
---

# Connect without ApiKey

Connecting to the HortiApi without apikey

# GET https://sandbox.hortiapi.net/v3/me

Request headers
```
Accept: application/json
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
  "companies": null,
  "user": null
}
```

