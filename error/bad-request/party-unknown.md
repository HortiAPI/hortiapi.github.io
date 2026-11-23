---
layout: default
title: bad-request/party-unknown
permalink: /error/bad-request/party-unknown
---

# bad-request
## party-unknown

The supplier or the customer of the request can not be found with the data that was sent.

The server looks for each party in three steps and goes to the next step when a value is empty or no company is found with it:

1. `id` of the party
2. `gln` of the party
3. the resource [`ai2/account-number`](/resource/ai2/account-number) of the party

The error is given when none of the steps finds a company, for the supplier or for the customer.

The `id` is the id of the company on this server. Send the GLN or the AI2 account number when you can, these are the same on every server.

### See also

- [direct-debit use case](/use-case/direct-debit)
- [resource ai2/account-number](/resource/ai2/account-number)
