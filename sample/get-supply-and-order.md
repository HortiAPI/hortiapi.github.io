---
layout: default
title: Get supply and order
permalink: /sample/get-supply-and-order
---

# Get supply and order

Retrieve a supply stream and order 1 box of the last supply line

> POST https://v3.sandbox.hortiapi.net/supply

> Request headers
```
Accept: text/event-stream
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.52; .NET 8.0.24; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

> Request content
``` json
{
  "streamId": "WfWSKJG730SLr9rML9JNFg"
}
```

---

> Response headers (200)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Cache-Control: no-cache
Transfer-Encoding: chunked
X-Accel-Buffering: no
Content-Type: text/event-stream; charset=utf-8
```

> Response content
```
event: update
data: {"id":"AAAAAwAAACBkQuRQ3ZazSQ","state":"","article":{"features":[{"type":"B01","value":"RO"},{"type":"B03","value":"737"},{"type":"B10","value":"RO"},{"type":"B11","value":"737"},{"type":"T01","value":"001"},{"type":"T02","value":"001"}],"regulatoryFeatures":[{"p":"required","f":"S20"},{"p":"empty","f":""},{"p":"empty","f":""},{"p":"required","f":"S67"},{"p":"required","f":"L11"}],"id":"FdCsMnxfyEuM0EH6gXAMsw","list":"vbn","code":"113069","group":"cut-flowers","groupCode":"10106003","name":"Hypericum x inodorum Magical Seasons","tradeName":"HYP MAG SEASONS","genus":"Hypericum","species":"x inodorum","cultivar":"'Kolmsea'"},"supplier":{"id":"uWXsD0b-UEiIjVKA3smDDg","gln":"8713783483923","name":"Lakerfield B.V."},"product":{"industryId":"113069","supplierId":"113069","customerId":"","manufacturerId":"","type":"product","description":"Hyp Mag Royal Seasons","manufacturer":{"id":"AAAAAAAAAAAAAAAAAAAAAA","gln":"8713782626420","name":"Wildfire Flowers"},"features":[{"type":"S20","value":"050"},{"type":"S97","value":"018"},{"type":"S62","value":"KE"},{"type":"S22","value":"029"}],"classifications":[{"system":"CBS","value":"06031970"}]},"quantity":{"unit":"box","value":9},"packing":{"bunch":{"code":"800","quantity":1},"box":{"code":"588","quantity":100,"measurements":[{"type":"length","value":40,"unit":"cm"},{"type":"height","value":38,"unit":"cm"},{"type":"width","value":27,"unit":"cm"}]},"layer":{"code":"19","quantity":1},"carrier":{"code":"1","quantity":1}},"prices":[{"type":"invoice","minimum":{"unit":"box","value":1},"maximum":{"unit":"box","value":9},"amount":{"value":0.23,"currency":"EUR"}}],"references":[],"notes":[{"code":"productgroep naam","value":"Hypericum"}],"photos":[{"url":"https://webshop.rotoflowers.nl/Pictures/K571611_113069_50_H_2.jpg"}],"deliveries":[{"terms":"ddp","tradeLocation":{"gln":"8714231208754","name":""},"latestOrder":"2026-03-02T05:00:00+00:00","latestDelivery":"2026-03-02T07:00:00+00:00"},{"terms":"ddp","tradeLocation":{"gln":"8714231208754","name":""},"latestOrder":"2026-03-02T08:00:00+00:00","latestDelivery":"2026-03-02T10:00:00+00:00"},{"terms":"ddp","tradeLocation":{"gln":"8714231208754","name":""},"latestOrder":"2026-03-02T22:59:00+00:00","latestDelivery":"2026-03-03T07:00:00+00:00"}]}


```

> POST https://v3.sandbox.hortiapi.net/supply/order

> Request headers
```
Accept: application/json
Authorization: bearer set_here_your_api__key
x-company-id: uWXsD0b-UEiIjVKA3smDDg
User-Agent: HortiApiClient/1.0.0.0, (HortiApi/3.0.0-rc.52; .NET 8.0.24; +https://hortiapi.com)
Transfer-Encoding: chunked
Accept-Encoding: gzip, deflate, br
Content-Type: application/json; charset=utf-8
```

> Request content
``` json
{
  "supply": "AAAAAwAAACBkQuRQ3ZazSQ",
  "state": "",
  "quantity": {
    "unit": "box",
    "value": 1
  },
  "price": {
    "type": "invoice",
    "amount": {
      "value": 0.23,
      "currency": "EUR"
    }
  }
}
```

---

> Response headers (404)
```
Date: Tue, 27 May 2025 10:26:46 GMT
Transfer-Encoding: chunked
Content-Type: application/problem+json
```

> Response content
``` json
{
  "context": [
    {
      "name": "User",
      "value": "Michael Lakerveld (michael)"
    },
    {
      "name": "Company",
      "value": "Lakerfield B.V. (lakerfield)"
    }
  ],
  "type": "https://hortiapi.com/error/not-found/supply",
  "title": "Supply stream not found",
  "status": 404,
  "instance": "/horti-api/v3/supply/order"
}
```

