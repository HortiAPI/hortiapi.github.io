---
layout: default
title: Connect without ApiKey
permalink: /sample/connect-without-apikey
---

# Connect without ApiKey

Connecting to the HortiApi without apikey

# GET https://v3.sandbox.hortiapi.net/me

Request headers
```
Accept: application/json
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.14; .NET 8.0.12; +https://hortiapi.com)
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
  "company": null,
  "user": null
}
```

