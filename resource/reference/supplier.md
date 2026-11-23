---
layout: default
title: reference/supplier
permalink: /resource/reference/supplier
---

# reference
## supplier

The id that the supplier uses in its own system for an order or an order line.

The supplier chooses the value. The server keeps it and returns it with the order or the order line, so the supplier can match it with its own records. The server does not use the value to find an order.

Example: `reference/supplier:PO-2026-00123`

A value is percent-encoded, see [resource strings](/resource-string).

### See also

- [resource reference/customer](/resource/reference/customer)
- [direct-debit use case](/use-case/direct-debit)
