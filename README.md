# HortiAPI Reference

Welcome to the interactive reference for the HortiAPI OpenAPI definitions. This site renders the API design authored and maintained in the [HortiAPI/HortiAPI](https://github.com/HortiAPI/HortiAPI) repository, where the schema, resources, and implementation guidelines are collaboratively developed. Use the links below to explore endpoints, schemas, and examples for each version.

## ▶️ Versioned API Docs

* [HortiApi v3 (release candidate)](/v3) — Latest OpenAPI 3.1 schema
* [HortiApi v2 (legacy)](/v2)
* [HortiApi v1 (legacy)](/v1)

## 🔍 Exploring the API

Each version’s viewer provides:

* **Endpoint list**: Browse by tag (Catalog, Supply, Stock, Orders, Documents, Companies, Users)
* **Schema details**: Field definitions, data types, and resource references
* **Try-it-out**: Execute sample requests against your local or staging HortiAPI server

## 📚 Resources (v3)

The v3 schema references shared [resources](/resources). These include:

* Company kinds, roles, and statuses
* Order states and document types
* Unit measures, currency codes, and packaging types

They ensure consistency across implementations.

## ⚙️ Generating Clients

Import the OpenAPI file into your tool of choice:

* **.NET**: NSwag or AutoRest → generates C# client/server stubs
* **JavaScript/TypeScript**: OpenAPI Generator → fetch-based SDK
* **Python/Java**: OpenAPI Generator templates

Use [`definitions/hortiapi-v3-rc.0.yaml`](/definitions/hortiapi-v3-rc.0.yaml) for the latest.

### 🧩 Ready-made .NET Packages

For C#/.NET consumers and servers, HortiAPI publishes these NuGet packages:

| Package                                                                       | Contents                                          |
| ----------------------------------------------------------------------------- | ------------------------------------------------- |
| [`HortiApi.Models`](https://www.nuget.org/packages/HortiApi.Models)           | Shared data models (DTOs) for client and server   |
| [`HortiApi.Resources`](https://www.nuget.org/packages/HortiApi.Resources)     | Well-known resource string definitions            |
| [`HortiApi.Client.Rest`](https://www.nuget.org/packages/HortiApi.Client.Rest) | Client implementation for HortiAPI endpoints      |
| [`HortiApi.Server`](https://www.nuget.org/packages/HortiApi.Server)           | Abstract ASP.NET 8.0 server base classes          |

## ℹ️ Support

For issues or questions on the spec itself, open an issue in the main API repo: [HortiAPI/HortiAPI](https://github.com/HortiAPI/HortiAPI/issues).
