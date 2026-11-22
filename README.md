# HortiAPI

HortiAPI is the open API standard for exchanging catalog, supply, stock, order and document data in the horticulture industry. The API is generic on purpose: one set of endpoints and models serves many business scenarios.

A **use case** describes one such scenario: the steps of the workflow and, per step, the fields that are used. Implementing HortiAPI means implementing one or more use cases, so that is the place to start.

## 🎯 Choose your use case

{::nomarkdown}
{% include use-case-cards.html %}
{:/nomarkdown}

Is your scenario missing? [Open an issue](https://github.com/HortiAPI/HortiAPI/issues) to discuss a new use case.

## 🚀 How to implement a use case

1. **Read the workflow.** The use case page shows every step, who performs it (client or server) and which fields the step reads and returns. Fields that are not listed are ignored by the server.
2. **Connect.** Find the server and its settings through [discovery](/discovery) and `/.well-known/horti-api`, see the [connecting sample](/sample/connect).
3. **Build the `core` steps first.** These are the minimum for a working client. Steps marked `extended` are optional for a client; a server that offers the use case supports both.
4. **Compare with the sample.** Every use case links to a [sample](/sample) with the complete HTTP requests and responses.
5. **Handle the errors of the use case.** Each step lists the [errors](/error) that are specific to it.

## 📖 Reference

| Topic | What you find there |
| --- | --- |
| [API docs v3](/v3) | Interactive viewer of the OpenAPI 3.1 schema: endpoints by tag, field definitions and try-it-out. Legacy: [v2](/v2), [v1](/v1) (swagger 2.0) |
| [OpenAPI definition](/definitions/hortiapi-v3-latest.yaml) | The latest v3 schema as YAML, to generate a client or server |
| [Use cases](/use-case) | All use cases with their workflow and fields |
| [Samples](/sample) | HTTP transcripts, for example [connecting](/sample/connect), [catalog search](/sample/catalog-search) and [get supply and order](/sample/get-supply-and-order) |
| [Resources](/resource) | Standardized identifiers such as order kinds, order states and company roles |
| [Resource strings](/resource-string) | How a resource string is built, and how to read, compare and change it |
| [Errors](/error) | Error types of the RFC 7807 Problem Details responses |
| [Discovery](/discovery) | How a client finds a server through `/.well-known/horti-api` |
| [Streaming](/streaming) | Lists and Server-Sent Events: event types, continuing with `Last-Event-ID` and limiting results |

### 🧩 Official .NET libraries

| Package                                                                       | Contents                                          |
| ----------------------------------------------------------------------------- | ------------------------------------------------- |
| [`HortiApi.Models`](https://www.nuget.org/packages/HortiApi.Models)           | Shared data models (DTOs) for client and server   |
| [`HortiApi.Resources`](https://www.nuget.org/packages/HortiApi.Resources)     | Well-known resource string definitions            |
| [`HortiApi.Client.Rest`](https://www.nuget.org/packages/HortiApi.Client.Rest) | Client implementation for HortiAPI endpoints      |
| [`HortiApi.Server`](https://www.nuget.org/packages/HortiApi.Server)           | Abstract ASP.NET 8.0 server base classes          |

See the [C# examples](/dotnet) for recognising errors, reading resources and returning errors from a server.

### ⚙️ Other languages

For other languages, generate a client or server from [`definitions/hortiapi-v3-latest.yaml`](/definitions/hortiapi-v3-latest.yaml). Commonly used generators:

| Language | Generator |
| --- | --- |
| TypeScript / JavaScript | [openapi-typescript](https://openapi-ts.dev/) (types and fetch client) or [OpenAPI Generator](https://openapi-generator.tech/docs/generators) `typescript-fetch` |
| Java | [OpenAPI Generator](https://openapi-generator.tech/docs/generators) `java` (client) or `spring` (server) |
| Kotlin | [OpenAPI Generator](https://openapi-generator.tech/docs/generators) `kotlin` |
| Python | [openapi-python-client](https://github.com/openapi-generators/openapi-python-client) or [OpenAPI Generator](https://openapi-generator.tech/docs/generators) `python` |
| Go | [oapi-codegen](https://github.com/oapi-codegen/oapi-codegen) |
| PHP | [OpenAPI Generator](https://openapi-generator.tech/docs/generators) `php` |
| Swift | [Swift OpenAPI Generator](https://github.com/apple/swift-openapi-generator) |
| Several languages | [Kiota](https://learn.microsoft.com/openapi/kiota/overview) |

More generators are listed on [openapi.tools](https://openapi.tools/). The schema is OpenAPI 3.1, so check that the generator of your choice supports that version.

### 🌷 Product classification

HortiAPI supports the Linnaeus model for standardized flower & plant classification. Linnaeus distinguishes fixed taxonomic attributes (genus, species) from variable transactional data (inventory, pricing), so data exchanged among growers, exporters, wholesalers and service providers stays interoperable and unambiguous.

## ℹ️ Support

The schema, resources and implementation guidelines are developed in the [HortiAPI/HortiAPI](https://github.com/HortiAPI/HortiAPI) repository. For issues or questions on the spec itself, [open an issue](https://github.com/HortiAPI/HortiAPI/issues) there.
