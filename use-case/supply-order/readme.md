---
layout: default
title: supply-order use-case
permalink: /use-case/supply-order
summary: Buyers retrieve available supply from a supplier and place an order for specific products.
sample: get-supply-and-order
---

# Supply Order

The supply-order use-case enables buyers to retrieve available supply from a supplier and place an order for specific products. Buyers query a supply stream to see real-time availability and can immediately order items from the returned supply lines.

## How it works

The process starts by querying a supply stream via `POST /supply` with a `streamId`. The server responds with a Server-Sent Event (SSE) stream containing available supply lines. Each supply line includes detailed product information (VBN code, manufacturer GLN, features), pricing, quantity available, packing configuration, and delivery terms.

Once a buyer identifies a supply line they want to order, they can place an order by creating an order via `POST /order`. The order references the supply line and specifies the desired quantity. The price is validated against the supply line price to ensure agreement between buyer and supplier.

### Supply stream query

Retrieve available supply from a specific supplier by posting the supply stream ID. The response is a Server-Sent Event stream containing supply lines with:

- Product details (VBN code, genus, cultivar, trade name)
- Available quantity and unit (e.g., box, bunch)
- Pricing information (provisional or fixed)
- Packing configuration (bunch, box, layer, carrier codes)
- Delivery terms and trade locations
- Product photos and notes

### Placing an order

After selecting a supply line, create an order via `POST /order`. To link the order to a specific supply line, the order line references the supply line ID and specifies the desired quantity. The price is included with `type` set to `invoice` for invoiced pricing.

## See also

- [Get supply and order sample](/sample/get-supply-and-order) — full request/response walkthrough
