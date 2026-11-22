---
layout: default
title: Compatibility
permalink: /compatibility
---

# Compatibility

HortiAPI grows: a later version can add a property to a model. This page describes the rules that keep a client working when that happens.

## Rules

- **A client ignores properties it does not know.** A response can hold a property that was not in the schema the client was built with. The client skips it and reads the rest.
- **A server can add properties in a later version.** A new property is not a breaking change. Removing a property, renaming it or changing its type is a breaking change.
- **An item is complete without the new property.** A client that skips a new property still gets an item it can use. A new property adds something, it does not change the meaning of the properties that were already there.

The models in the schema do not set `additionalProperties: false`, so a validator accepts a response with an unknown property.

## Reserved properties

Some properties are in the schema before they are used. A server does not send them yet and a client ignores them.

| Model | Property | Meant for |
| --- | --- | --- |
| `Catalog` | `variants` | Other ways to deliver the same catalog item, for example packed dry in a box instead of on water in a bucket |
| `Supply` | `variants` | Other ways to deliver the same supply |

The item itself is always complete and can be used without its variants.

## Generated clients

The .NET libraries ignore unknown properties when they read JSON.

For a client generated from the schema, check what the generator does with an unknown property:

- **[OpenAPI Generator](https://openapi-generator.tech/)** reads a model without `additionalProperties` as closed by default, and some of its clients then reject an unknown property. Set `disallowAdditionalPropertiesIfNotPresent` to `false`:

  ```bash
  openapi-generator-cli generate -i hortiapi-v3-latest.yaml -g java --additional-properties=disallowAdditionalPropertiesIfNotPresent=false
  ```

- **Other generators and hand-written clients:** turn off the option of the JSON library that fails on unknown properties, if it has one.
