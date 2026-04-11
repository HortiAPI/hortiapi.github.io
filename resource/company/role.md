---
layout: default
title: company/role
permalink: /resource/company/role
---

# `company/role`

Reference resource for classifying the role of a company in a specific commercial, operational, or logistics context.

## Purpose

`company/role` provides a controlled vocabulary for contextual company roles.  
Values are intended for use in:

- transactions
- orders
- shipments
- auction flows
- platform interactions
- process-specific business rules

## Format

A role value can contain one or more role identifiers.

Single role:

```text
company/role:<name>
````

Multiple roles:

```text
company/role:<name>[,<name>...]
```

Examples:

```text
company/role:buyer
company/role:seller
company/role:sender
company/role:buyer,seller
company/role:seller,sender
```

### Notes

- Multiple roles are comma-separated.
- Role names must not contain spaces.
- Role order has no semantic meaning.
- Duplicate role names are not allowed.

## Values

| Value                      | Description                                                          |
| -------------------------- | -------------------------------------------------------------------- |
| `company/role:buyer`       | Party acting as buyer in a transaction.                              |
| `company/role:seller`      | Party acting as seller in a transaction.                             |
| `company/role:agent`       | Party acting as commercial intermediary or representative.           |
| `company/role:auction`     | Party facilitating an auction transaction.                           |
| `company/role:platform`    | Party facilitating interaction on a digital marketplace or platform. |
| `company/role:sender`      | Party sending or dispatching the goods.                              |
| `company/role:receiver`    | Party receiving the goods.                                           |
| `company/role:transporter` | Party physically transporting the goods.                             |

## Modeling notes

* Roles are context-specific and not static master data.
* A company can have multiple roles at the same time.
* Use `company/kind` for structural company classification.
* Use `company/role` for behavior within a specific process, transaction, or shipment.
* `sender` and `seller` are not equivalent:

  * `seller` is the commercial selling party
  * `sender` is the operational party dispatching the goods
* `receiver` and `buyer` are not necessarily the same party.
* `agent`, `auction`, and `platform` can participate without being legal buyer or seller.

## Full list

```text
company/role:agent
company/role:auction
company/role:buyer
company/role:platform
company/role:receiver
company/role:seller
company/role:sender
company/role:transporter
```

## Usage rules

* Assign one or more roles per business context.
* Do not derive `company/role` directly from `company/kind`.
* Prefer explicit assignment when a role has process or legal impact.
* Use the smallest set of roles needed for the process being modeled.

## Example

A company with `company/kind:wholesaler` can have:

* `company/role:buyer` in a purchase flow
* `company/role:seller` in a sales flow
* `company/role:sender` in a shipment
* `company/role:receiver` in an inbound delivery

A company with `company/kind:transporter` will typically have:

* `company/role:transporter`
