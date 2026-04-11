---
layout: default
title: company/kind
permalink: /resource/company/kind
---

# `company/kind`

Reference resource for classifying companies by functional role in the supply chain or supporting processes.

## Purpose

`company/kind` provides a controlled vocabulary for company classification.  
Values are intended for use in:

- validation
- filtering
- access rules
- UI labeling
- reporting
- integrations

## Format

Each value uses the following format:

```text
company/kind:<name>
````

Example:

```text
company/kind:grower
company/kind:wholesaler
company/kind:florist
```

## Values

| Value                           | Description                                                                    |
| ------------------------------- | ------------------------------------------------------------------------------ |
| `company/kind:admin`            | Internal administrative or system management role.                             |
| `company/kind:administration`   | Administrative or backoffice organization.                                     |
| `company/kind:agent`            | Commercial agent or intermediary.                                              |
| `company/kind:auction`          | Auction organization.                                                          |
| `company/kind:breeder`          | Breeder; develops new varieties or cultivars.                                  |
| `company/kind:demo`             | Demo or test organization.                                                     |
| `company/kind:exporter`         | Exporting company.                                                             |
| `company/kind:florist`          | Florist; specialized flower retailer.                                          |
| `company/kind:grower`           | Grower; produces crops or plants.                                              |
| `company/kind:importer`         | Importing company.                                                             |
| `company/kind:logistic`         | Logistics provider for storage, handling, or distribution.                     |
| `company/kind:platform`         | Digital platform or marketplace.                                               |
| `company/kind:propagator`       | Propagator; multiplies plant material or young plants.                         |
| `company/kind:retailer`         | Retail company or point of sale.                                               |
| `company/kind:service_provider` | Service provider, such as ICT, technical, advisory, or certification services. |
| `company/kind:supplier`         | General supplier of goods or services.                                         |
| `company/kind:transporter`      | Transport company responsible for physical transport.                          |
| `company/kind:wholesaler`       | Wholesale company selling to business customers.                               |

## Modeling notes

* Use role-based terms, not process names.
* Prefer specific values over generic ones.
* `florist` is a specialized form of `retailer` and is kept separate intentionally.
* `wholesaler` is generic by design; use it for flower wholesalers as well.
* Use `supplier` only when no more specific classification applies.

## Full list

```text
company/kind:admin
company/kind:administration
company/kind:agent
company/kind:auction
company/kind:breeder
company/kind:demo
company/kind:exporter
company/kind:florist
company/kind:grower
company/kind:importer
company/kind:logistic
company/kind:platform
company/kind:propagator
company/kind:retailer
company/kind:service_provider
company/kind:supplier
company/kind:transporter
company/kind:wholesaler
```

## Extension rules

Add a new value only if the role:

* is functionally distinct
* is not already covered by an existing value
* affects business logic, filtering, integrations, or reporting
* is stable enough to be a reference value
