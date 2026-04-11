---
layout: default
title: direct-debit use-case
permalink: /use-case/direct-debit
---

# direct-debit


## state

The state of this order

Currently defined states
- `order/state:open`
- `order/state:closed`
- `order/state:invoiced`



### When kind = `order/kind:direct-debit`

- `order/direct-debit-state:draft`

  The order can be modified. It will be picked up by the batch process once the invoice date has passed (batch window: Monday–Friday, 13:00–13:30).

- `order/direct-debit-state:pending`

  The order has been submitted and can no longer be modified. It is awaiting collection.

- `order/direct-debit-state:collection`

  The direct debit has been submitted to the bank and is in the collection phase. Any received funds may still be subject to the SEPA B2B return period.

- `order/direct-debit-state:completed`

  The payment has been settled to the supplier and the process is fully completed.

- `order/direct-debit-state:rejected`

  The order has been rejected and will not be processed further. Contact AI2 for more information.

- `order/direct-debit-state:cancelled`

  The order has been cancelled and will not be processed.

