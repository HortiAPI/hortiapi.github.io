---
layout: default
title: direct-debit use-case
permalink: /use-case/direct-debit
---

# Direct Debit

The direct-debit order kind (`order/kind:direct-debit`) enables suppliers and buyers in the horticultural supply chain to settle transactions through SEPA B2B direct debit. Instead of the buyer initiating payment, the supplier submits an order that triggers a bank collection from the buyer's account once the invoice date has passed.

The direct-debit process is operated by [AI2](https://ai2.nl), the independent payment collection service for the ornamental horticulture sector. AI2 runs the batch collection, interfaces with the bank, and handles the settlement to the supplier. If an order is rejected, contact AI2 for follow-up.

### How it works

A direct-debit order is created via `POST /order` with `kind: order/kind:direct-debit`. The order starts in `draft` state, which allows full modification — including adding, updating, or removing order lines. Each line specifies the product (identified by VBN industry code and manufacturer GLN), price type `invoice`, quantity in boxes, packing configuration, and trade references.

Supplier and customer are matched by their AI2 account numbers (e.g. `ai2/account-number:99991`), allowing the server to resolve company details and GLNs automatically.

Once the invoice date has passed, a batch process run by AI2 (Monday–Friday, 13:00–13:30, provisional; final timing to be confirmed soon) picks up all draft orders and advances them to `pending`. At that point the order is locked and can no longer be modified. The collection is then submitted to the bank and moves into `collection` state, during which the SEPA B2B return period still applies. Once funds are settled to the supplier, the order reaches `completed`.

### Order status

Use `GET /order/{id}` to retrieve the latest status of the order. The status is updated after batch processing has completed.

## Order states

The order.state when kind = `order/kind:direct-debit`

- `order/direct-debit-state:draft`

  The order can be modified. It will be picked up by the AI2 batch process once the invoice date has passed (batch window: Monday–Friday, 13:00–13:30, provisional; final timing to be confirmed soon).

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

### See also

- [Direct-debit sample](/sample/direct-debit) — full request/response walkthrough
- [order/direct-debit-state resources](/resource/order) — all valid state values
