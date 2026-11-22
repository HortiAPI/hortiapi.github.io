---
layout: default
title: ai2/payment-date
permalink: /resource/ai2/payment-date
---

# ai2
## payment-date

The point in time at which the batch ran in which the transaction is paid to the client/supplier.

The value is a point in time in UTC, see [date and time](/resource-string#date-and-time):

```text
ai2/payment-date:2026-11-24T14:30:00Z
```

More than one batch can run on a day. Each batch has its own point in time.

### See also

- [ai2/payment-batch](/resource/ai2/payment-batch)
- [direct-debit use case](/use-case/direct-debit)
