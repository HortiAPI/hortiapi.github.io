---
layout: default
title: direct-debit use-case
permalink: /use-case/direct-debit
profile: direct-debit
sample: direct-debit
---

# Direct Debit

The direct-debit order kind (`order/kind:direct-debit`) enables suppliers and buyers in the horticultural supply chain to settle transactions through SEPA B2B direct debit. Instead of the buyer initiating the payment, the supplier submits an order that triggers a bank collection from the buyer's account once the invoice date has passed.

The direct-debit process is operated by [AI2](https://ai2.nl), the independent payment collection service for the ornamental horticulture sector. AI2 runs the batch collection process, interfaces with the bank, and handles settlement to the supplier. If an order is rejected, contact AI2 for follow-up.

### How it works

A direct-debit order is created via `POST /order` with `kind: order/kind:direct-debit`. The order starts in `draft` state, which allows it to be modification, including adding, updating, or removing order lines. Each line specifies the product (identified by VBN industry code and manufacturer GLN), price type `invoice`, quantity in boxes, packing configuration, and trade references.

The supplier and customer are matched by their AI2 account numbers (e.g. `ai2/account-number:99991`), allowing the server to resolve company details and GLNs automatically.

Once the invoice date has passed, a batch process run by AI2 (Monday–Friday, 13:00–13:30, provisional; final timing to be confirmed) picks up all eligible draft orders and advances them to `pending`. At that point the order is locked and can no longer be modified. The collection is then submitted to the bank, and the order moves into the `collection` state, during which the SEPA B2B or SEPA Core return period still applies. Once the funds have been settled to the supplier, the order reaches `completed`.

The AI2 batch number is incremented for every batch run. Normally, one batch is processed per business day, although technically multiple batches can be processed on the same day. The corresponding batch numbers are added to the order's resources using `ai2/collection-batch:1234` for collection batches and `ai2/payment-batch:1238` for payment batches. Together with the batch number, the point in time the batch ran is added, in UTC: `ai2/collection-date:2026-11-24T14:30:00Z` and `ai2/payment-date:2026-11-26T14:30:00Z`.

### Order status

Use `GET /order/{id}` to retrieve the latest status of the order. The status is updated as the order progresses thought the AI2 processing stages.

## Order states

The follwing `order.state` values apply when `kind` is `order/kind:direct-debit`

- `order/direct-debit-state:draft`

  The order can be modified. It will be picked up by the AI2 batch process once the invoice date has passed (batch window: Monday–Friday, 13:00–13:30, provisional; final timing to be confirmed).

- `order/direct-debit-state:awaiting-processing`

  The order has been submitted and can no longer be modified. It is awaiting collection.

- `order/direct-debit-state:collection-in-progress`

  The direct debit has been submitted to the bank and is in the collection phase. Any received funds may still be subject to the SEPA B2B return period.

- `order/direct-debit-state:payout-settled`

  The payment has been settled to the supplier and the process is fully completed.

- `order/direct-debit-state:rejected`

  The order has been rejected and will not be processed further. Contact AI2 for more information.

- `order/direct-debit-state:deleted`

  The order has been deleted and will not be processed.

{::nomarkdown}
{% include use-case-profile.html %}
{:/nomarkdown}

### See also

- [Direct-debit sample](/sample/direct-debit) — full request/response walkthrough
- [resource ai2/account-number](/resource/ai2/account-number)
- [resource ai2/collection-batch](/resource/ai2/collection-batch)
- [resource ai2/collection-date](/resource/ai2/collection-date)
- [resource ai2/payment-batch](/resource/ai2/payment-batch)
- [resource ai2/payment-date](/resource/ai2/payment-date)
