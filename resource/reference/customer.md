---
layout: default
title: reference/customer
permalink: /resource/reference/customer
---

# reference
## customer

The id that the customer uses in its own system for an order or an order line.

The customer chooses the value. The server keeps it and returns it with the order or the order line, so the customer can match it with its own records. The server does not use the value to find an order.

Example: `reference/customer:PO-2026-00123`

A value is percent-encoded, see [resource strings](/resource-string).

### See also

- [resource reference/supplier](/resource/reference/supplier)
- [direct-debit use case](/use-case/direct-debit)
