---
layout: default
title: C# examples
permalink: /dotnet
---

# C# examples

Short examples for the checks that are not obvious when you use the [official .NET libraries](/#-official-net-libraries): recognising errors, reading resources and returning errors from a server. The complete HTTP requests and responses are in the [samples](/sample).

```csharp
using HortiApi;          // WellKnownResources, ResourceString
using HortiApi.Client;   // HortiApiClient
using HortiApi.Models;   // Order, HortiApiException, HortiApiProblemDetails
using HortiApi.Server;   // server only: IHortiApiServerOrder, Generate... methods
```

## Client

### Find the API from an address the user entered

`Discover` on the client factory accepts the base URL of the API or the website of a company. It first tries the address itself; when that is not a HortiApi it reads `/.well-known/horti-api` on the root of the host and follows the link. No API key is sent.

```csharp
var discovery = await factory.Discover("example-company.com");

// the API can be on another host than the address: show it before the API key is sent
Console.WriteLine($"Found {discovery.Service} at {discovery.ApiBaseUrl}");

var handle = await factory.Start(key: apiKey, baseUrl: discovery.ApiBaseUrl);
```

A `HortiApiException` tells that no HortiApi was found. See the use case [Discovery and connect](/use-case/discovery).

### Check that a server supports a use case

The [discovery](/use-case/discovery) document lists the [use cases](/use-case) a server supports. Every use case of HortiApi has a value in `WellKnownResources.HortiApi.UseCase`.

```csharp
var discovery = await client.Discovery.Get();

if (!discovery.UseCases.Contains(WellKnownResources.HortiApi.UseCase.DirectDebit))
{
  // this server does not support direct debit
}
```

For a use case of another party, build the value yourself: `ResourceString.Parse("flora-nexus/use-case:auction")`.

### Which exception belongs to which status

The client throws an exception for every response that is not a success. The exception holds the [problem details](/error) of the server in `Details`.

| Status | Exception |
| --- | --- |
| 400 | `HortiApiException` |
| 401 | `HortiApiUnauthorizedException` |
| 403 | `HortiApiForbiddenException` |
| 404 | `HortiApiNotFoundException` |
| 406 | `HortiApiNotAcceptableException` |
| 409 | `HortiApiConflictException` |
| 410 | `HortiApiGoneException` |
| 500 | `HortiApiInternalServerErrorException` |
| 501 | `HortiApiNotImplementedException` |

All of them derive from `HortiApiException`, so catch that one last. A 400 has no exception of its own.

### Recognise one specific error

Every documented [error](/error) has a value in `WellKnownResources.Errors`. `IsProblemType` compares the `type` of the problem details with such a value.

```csharp
try
{
  await client.Order.Delete(orderId);
}
catch (HortiApiException ex) when (ex.IsProblemType(WellKnownResources.Errors.Conflict.OrderNotDraft))
{
  // exactly this error: the order is no longer a draft
}
catch (HortiApiException ex) when (ex.IsProblemType(WellKnownResources.Errors.Forbidden.Any))
{
  // every error in the category forbidden
}
catch (HortiApiNotFoundException)
{
  // every 404
}
```

Pass an error to match that error, or `Any` of a category to match every error in it. The values are of the type `ProblemType`, so a plain string is not accepted.

### Read the details of an error

```csharp
catch (HortiApiException ex)
{
  var details = ex.Details;   // null when the server did not return problem details
  Console.WriteLine($"{details?.Status} {details?.Type}: {details?.Title} {details?.Detail}");

  foreach (var item in details?.Context ?? [])
    Console.WriteLine($"  {item.Name} = {item.Value}");
}
```

`Context` holds extra name/value pairs the server added, for example the field that was wrong.

### Check the kind or state of an order

`Kind` and `State` are strings that hold a [resource](/resource), for example `order/kind:direct-debit`. Compare them with `==` against the constant.

```csharp
var order = await client.Order.Get(orderId, includeLines: false);

if (order.Kind == WellKnownResources.Order.Kind.DirectDebit)
{
  // a direct-debit order
}

if (order.State == WellKnownResources.Order.DirectDebitState.Draft)
{
  // still a draft, it can be changed or deleted
}
```

Use `==` and not `Equals`: `WellKnownResources.Order.Kind.DirectDebit.Equals(order.Kind)` compares a `ResourceString` with a `string` and is always false.

### Read a resource

`Resources` is the list of resources on a model. A resource has an identifier (`ai2/collection-batch`) and one or more values.

```csharp
// is the identifier present, whatever the value
if (order.Resources.ContainsIdentifier(WellKnownResources.Ai2.CollectionBatch.Identifier))
{
  // the order has been sent to the bank
}

// the value, or null when the identifier is not present
string? batch = order.Resources.GetValueOrDefault(WellKnownResources.Ai2.CollectionBatch.Identifier);

// identifier and value both present
if (order.Resources.Contains(WellKnownResources.Ai2.AccountNumber.Build("12345")))
{
}
```

### Set or remove a resource

```csharp
// replaces the values of ai2/account-number
order.SetResource(WellKnownResources.Ai2.AccountNumber.Build("12345"));

// adds a value and keeps the existing ones
order.AddResource(WellKnownResources.Ai2.AccountNumber.Build("67890"));

// removes the identifier with all its values
order.RemoveResourceIdentifier(WellKnownResources.Ai2.AccountNumber.Identifier);
```

### Limit the number of results

```csharp
await foreach (var order in client.Order.Search(new OrderFilter(), HortiApiClientPreferOptions.WithMaxResults(50)))
  Console.WriteLine(order.Id);
```

This sends the `Prefer` header; the server may return fewer results.

## Server

A server implements the interfaces of `HortiApi.Server`, for example `IHortiApiServerOrder`. Every method returns an `IResult`.

### Tell which use cases you support

Fill `UseCases` of the discovery document. It is sent as a list with one string per use case.

```csharp
var document = new HortiApiDiscoveryDocument
{
  // ...
  UseCases = ResourceCollection.Create(
    WellKnownResources.HortiApi.UseCase.Discovery,
    WellKnownResources.HortiApi.UseCase.DirectDebit),
  Capabilities = ["discovery", "me", "order"],
  Sse = ["order"],
};
```

### Return an error

`GenerateProblem` on `HttpContext` returns an error. Pass a value of `WellKnownResources.Errors`; the method builds the `type`, the status of the category and the `application/problem+json` response.

```csharp
public Task<IResult> OrderDelete(HttpContext httpContext, string orderId, string xCompanyId, string xFacilityId)
{
  Order? order = Load(orderId);

  if (order is null)
    return httpContext.GenerateProblemTask(WellKnownResources.Errors.NotFound.Order, "Order not found");

  if (order.State != WellKnownResources.Order.DirectDebitState.Draft)
    return httpContext.GenerateProblemTask(WellKnownResources.Errors.Conflict.OrderNotDraft, "Order is not a draft");

  Delete(order);
  return Task.FromResult(Results.NoContent());
}
```

There are four forms: `GenerateProblem` returns an `IResult`, `GenerateProblemTask` a `Task<IResult>`, `GenerateProblemDetails` only the problem details, and `GenerateProblemObservable<T>` fails a stream with the error.

### An error of your own

Create a `ProblemType` for an error that is not in `WellKnownResources.Errors`. The category decides the status; the names are checked when the value is created.

```csharp
public static readonly ProblemType OrderTooLate = new("conflict", "order-too-late");

return httpContext.GenerateProblemTask(OrderTooLate, "The order was received after closing time");
```

A category that HortiApi does not know needs a status: `new ProblemType("my-category", "my-error", 422)`.

### Add details to an error

```csharp
return httpContext.GenerateProblemTask(
  WellKnownResources.Errors.Conflict.OrderNotDraft,
  "Order is not a draft",
  details =>
  {
    details.Detail = $"Order {orderId} has state {order.State}";
    details.Context.Add(new HortiApiProblemDetailsContext { Name = "state", Value = order.State ?? "" });
  });
```

### Check a resource in a request

```csharp
public Task<IResult> OrderUpdate(HttpContext httpContext, Order request, string idempotencyKey, string xCompanyId, string xFacilityId)
{
  if (!request.Resources.ContainsIdentifier(WellKnownResources.Ai2.AccountNumber.Identifier))
    return httpContext.GenerateProblemTask(WellKnownResources.Errors.BadRequest.Ai2AccountUnknown, "AI2 account number is missing");

  // ...
}
```

### An operation you do not support

```csharp
public Task<IResult> OrderGet(HttpContext httpContext, string orderId, string xCompanyId, string xFacilityId, string includeLines) =>
  httpContext.GenerateNotImplementedTask();
```

Operations of an interface you do not register return this 501 automatically.

### Respect the maximum number of results

```csharp
public Task<IResult> OrderSearch(HttpContext httpContext, OrderFilter request, PreferOptions prefer, string xCompanyId, string xFacilityId)
{
  var max = prefer?.MaxResults ?? 100;
  // ...
}
```
