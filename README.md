# HortiAPI Reference

Welcome to the interactive reference for the HortiAPI OpenAPI definitions. This site renders the API design authored and maintained in the [HortiAPI/HortiAPI](https://github.com/HortiAPI/HortiAPI) repository, where the schema, resources, and implementation guidelines are collaboratively developed. Use the links below to explore endpoints, schemas, and examples for each version.

Supports the Linnaeus model for standardized flower & plant classification. Linnaeus provides a rigorously defined ontology for horticultural entities—distinguishing fixed taxonomic attributes (genus, species) from variable transactional data (inventory, pricing). By aligning with this industry‑recognized standard, HortiAPI ensures that data exchanged among growers, exporters, wholesalers, and service providers remains interoperable and unambiguous, reducing integration effort and preventing misclassification across the supply chain.

## ▶️ Versioned API Docs

* [HortiApi v3 (latest)](/v3) *OpenAPI 3.1 schema*
* [HortiApi v2 (legacy)](/v2) *swagger 2.0 schema*
* [HortiApi v1 (legacy)](/v1) *swagger 2.0 schema*

## 🔍 Exploring the API

Each version’s viewer provides:

* **Endpoint list**: Browse by tag (Catalog, Supply, Stock, Orders, Documents, Companies, Users)
* **Schema details**: Field definitions, data types, and resource references
* **Try-it-out**: Execute sample requests against your local or staging HortiAPI server

## 🧩 Official .NET Libraries

For C#/.NET consumers and servers, HortiAPI publishes these NuGet packages:

| Package                                                                       | Contents                                          |
| ----------------------------------------------------------------------------- | ------------------------------------------------- |
| [`HortiApi.Models`](https://www.nuget.org/packages/HortiApi.Models)           | Shared data models (DTOs) for client and server   |
| [`HortiApi.Resources`](https://www.nuget.org/packages/HortiApi.Resources)     | Well-known resource string definitions            |
| [`HortiApi.Client.Rest`](https://www.nuget.org/packages/HortiApi.Client.Rest) | Client implementation for HortiAPI endpoints      |
| [`HortiApi.Server`](https://www.nuget.org/packages/HortiApi.Server)           | Abstract ASP.NET 8.0 server base classes          |

## ⚙️ Generating other clients

Import the OpenAPI file into your tool of choice:

* **.NET**: NSwag or AutoRest → generates C# client/server stubs
* **JavaScript/TypeScript**: OpenAPI Generator → fetch-based SDK
* **Python/Java**: OpenAPI Generator templates

Use [`definitions/hortiapi-v3-rc.27.yaml`](/definitions/hortiapi-v3-rc.27.yaml) for the latest.

## 📋 Samples

See the API in action with these practical [example](/sample) scenarios. These include:

* [Connecting](/sample/connect.md)
* [Catalog search](/sample/catalog-search.md)
* [Get supply and order](/sample/get-supply-and-order.md)
* [much more...](/sample)

## 📚 Resources

The v3 schema references shared [resource](/resource). These include:

* Company kinds, roles, and statuses
* Order states and document types

These standardized identifiers ensure semantic consistency across all implementations.

## ⚠️ Errors

HortiAPI uses structured error responses (RFC7807 Problem Details) that reference these standardized [error](/error) types. These include:

* Bad Request
* Forbidden
* Not Implemented

## ℹ️ Support

For issues or questions on the spec itself, open an issue in the main API repo: [HortiAPI/HortiAPI](https://github.com/HortiAPI/HortiAPI/issues).
