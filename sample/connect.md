---
layout: default
title: Connect Sample
permalink: /sample/connect
---

# Connect Sample

Connect Sample

> GET https://v3.sandbox.hortiapi.net/me

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.81; .NET 8.0.28; +https://hortiapi.com)
Accept-Encoding: gzip, deflate, br
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
  "application": {
    "id": "",
    "name": "sandbox.hortiapi.com application",
    "resources": [
    ]
  },
  "companies": [
    {
      "id": "Kh0jae0o_k6TNye_shXdLw",
      "name": "Demo koper"
    }
  ],
  "facilities": [
  ],
  "user": {
    "id": "O9c35_s_bU6faqPr8EgBxQ",
    "name": "Michael Lakerveld"
  },
  "resources": [
    "horti-api/health:healthy"
  ]
}
```

> GET https://v3.sandbox.hortiapi.net/me

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: Kh0jae0o_k6TNye_shXdLw
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.81; .NET 8.0.28; +https://hortiapi.com)
Accept-Encoding: gzip, deflate, br
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
  "application": {
    "id": "",
    "name": "sandbox.hortiapi.com application",
    "resources": [
    ]
  },
  "companies": [
    {
      "id": "Kh0jae0o_k6TNye_shXdLw",
      "name": "Demo koper"
    }
  ],
  "company": {
    "id": "Kh0jae0o_k6TNye_shXdLw",
    "name": "Demo koper"
  },
  "facilities": [
  ],
  "facility": null,
  "user": {
    "id": "O9c35_s_bU6faqPr8EgBxQ",
    "name": "Michael Lakerveld"
  },
  "resources": [
    "horti-api/health:healthy"
  ]
}
```

