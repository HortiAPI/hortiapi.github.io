---
layout: default
title: Resource strings
permalink: /resource-string
---

# Resource strings

Many fields in HortiApi hold a resource string: one text that says which kind of thing it is and which value it has. `order/state:draft` is the state of an order with the value `draft`. Fields such as `kind` and `state` hold one resource string, and the field `resources` on most models holds a list of them.

This page describes how a resource string is built and how to read, compare and change it. The values that HortiApi defines are listed under [resources](/resource).

## How a resource string is built

```text
company/role:buyer,seller
└──┬──┘ └┬─┘ └─────┬────┘
 target name     values
```

| Part | Example | Rules |
| --- | --- | --- |
| Identifier | `company/role` | The target and the name with one `/` between them. Only `a-z`, `0-9` and `-`. |
| Values | `buyer,seller` | Everything after the first `:`. One or more values, separated by `,`. |
| Parameters | `?copies=2&duplex=true` | Optional, per value. Written after the value, like the query of a web address. |

The identifier says what the values mean. `order/state:draft` and `stock/state:draft` are different resources.

A text without `:`, or with an identifier that does not have exactly one `/`, is not a resource string. Treat it the same as a missing value.

## Send lower case

Write the identifier, the values and the parameter keys in lower case: `order/state:draft`, not `Order/State:Draft`.

The identifier is always read as lower case. The values are not: [contains](#compare) ignores the difference between upper and lower case, but [equal](#compare) does not. A value in lower case gives the same result with both.

## More than one value

A resource can have more than one value. Each value has a name, and a name occurs only once.

```text
company/role:buyer
company/role:buyer,seller
```

The order of the values has no meaning. To check for a value, check that the resource contains it. Do not compare the whole text: `company/role:buyer,seller` and `company/role:seller,buyer` mean the same but are different texts.

## Parameters

A value can carry parameters: extra settings that belong to that value. The name is what the value is; the parameters say how.

```text
example/action:print?copies=2&duplex=true
example/action:print?copies=2,mail?to=sales
```

The names in these examples only show the form; they are not defined resources.

- The parameters start at `?`. Each parameter is `key=value` and they are separated by `&`.
- A key occurs only once per value. When a key is repeated, the last one counts.
- A key without a value (`?urgent`) has the value "" and counts as true when read as yes or no.
- Numbers use `.` as decimal separator: `?weight=1.5`.
- Yes or no is `true` or `false`. `1` and `0` are also read as yes and no.

## Special characters

The characters `,` `?` `&` `=` `:` and `/` have a meaning in a resource string. When a value name, a parameter key or a parameter value contains one of them, it is percent-encoded (RFC 3986), the same way as in a web address.

| Character | Written as |
| --- | --- |
| `,` | `%2C` |
| `?` | `%3F` |
| `&` | `%26` |
| `=` | `%3D` |
| `:` | `%3A` |
| `/` | `%2F` |
| space | `%20` |
| `%` | `%25` |

When you read a resource string, split it first and decode after that:

1. Split at the first `:` into the identifier and the values.
2. Split the values at `,`.
3. Split each value at the first `?` into the name and the parameters.
4. Split the parameters at `&` and each parameter at the first `=`.
5. Decode every name, key and parameter value.

This way an encoded `%2C` stays part of a name and does not start a new value.

## The `resources` list

The field `resources` is a list of resource strings. An identifier occurs only once in the list, with all its values in one text.

```json
{
  "resources": [
    "company/role:buyer,seller",
    "ai2/account-number:12345"
  ]
}
```

When you read a list, also accept an identifier that occurs more than once and join the values: `company/role:buyer` and `company/role:seller` together mean `company/role:buyer,seller`. The field `useCases` of the [discovery](/use-case/discovery) document is written this way, with one text per use case.

A resource without values is not in the list.

### Change the list

| Action | What happens | Example on `company/role:buyer` |
| --- | --- | --- |
| Add | The values are added to the values that are there. A value with the same name is replaced, with its parameters. | add `company/role:seller` → `company/role:buyer,seller` |
| Set | All values of the identifier are replaced. | set `company/role:seller` → `company/role:seller` |
| Remove | The given values are taken away. When no value is left, the identifier leaves the list. | remove `company/role:buyer` → not in the list |

## Compare

There are two ways to compare, and they answer different questions.

**Contains** answers "does this resource have this value?". Use it for the `resources` list and for resources with more than one value.

- The identifier must be there, and every value you ask for must be there. Other values may be there too.
- Parameters you ask for must be there with the same value. Other parameters may be there too.

| List has | Asked | Result |
| --- | --- | --- |
| `company/role:buyer,seller` | `company/role:seller` | yes |
| `company/role:buyer` | `company/role:buyer,seller` | no, `seller` is missing |
| `example/action:print?copies=2` | `example/action:print` | yes |
| `example/action:print` | `example/action:print?copies=2` | no, `copies` is missing |

**Equal** answers "is this exactly this resource?". Use it for a field with one value, such as `kind` or `state`. It compares the whole text: the identifier, all values in the same order and all parameters must be the same.

Contains ignores the difference between upper and lower case in the values. Equal does not: `order/state:Draft` is not equal to `order/state:draft`. This is why values are sent in lower case.

## Resources of other parties

HortiApi defines the resources listed under [resources](/resource). Another party can define its own resources with its own target, for example `flora-nexus/use-case:auction`. Choose a target that makes clear who defines the resource, and do not use a target that HortiApi already uses.

A client or server that does not know a resource leaves it as it is and does not fail on it.

## In .NET

The package `HortiApi.Resources` has `ResourceString`, `ResourceValue` and `ResourceCollection`, which do all of the above, and `WellKnownResources` with a constant for every defined resource. See the [C# examples](/dotnet) for how to use them.
