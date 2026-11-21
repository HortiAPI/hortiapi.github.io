---
layout: default
title: Streaming
permalink: /streaming
---

# Streaming

Operations that return many items can answer in two ways: as a list in JSON, or as a stream of Server-Sent Events (SSE). The client chooses with the `Accept` header. This page describes what is the same for all of these operations.

The operations are `POST /supply` and every search: `/article/search`, `/catalog/search`, `/company/search`, `/data/search`, `/document/search`, `/facility/search`, `/good/search`, `/invoice/search`, `/order/search`, `/order-line/search`, `/stock/search`, `/supply/transaction/search` and `/user/search`.

## List or stream

| `Accept` | Answer | The client |
| --- | --- | --- |
| `application/json` (default) | One response with a list | asks again when it wants newer data |
| `text/event-stream` | A connection that stays open and delivers events | keeps listening |

A search returns a list of the items themselves in JSON. `POST /supply` returns a list of events, each with `id`, `event` and `data`.

## Does the server have a stream

Not every server has a stream for every capability. The [discovery](/use-case/discovery) document lists the capabilities with a stream in `sse`:

```json
{
  "capabilities": ["order", "order-line", "supply"],
  "sse": ["supply"]
}
```

A request with `Accept: text/event-stream` for a capability that is not in `sse` is answered with 406 [not-acceptable](/error/not-acceptable). The client then sends the request again with `Accept: application/json`.

## Events

One event in a stream:

```
id: 42
event: update
data: {"id":"AAAAAQAAACDdIPd8jNGDlA", ...}
```

| Field | Meaning |
| --- | --- |
| `id` | Id of the event. Remember the last one to continue later. |
| `event` | The event type, see below. |
| `retry` | Optional. Time in milliseconds to wait before connecting again. |
| `data` | The item as JSON, the same model as in the JSON list. Empty for `reset` and `live`. |

The event types:

| `event` | Meaning |
| --- | --- |
| `add` | A new item. |
| `update` | An item the client may already have, with its new content. |
| `delete` | The item is no longer there. |
| `reset` | Marker without data: the server starts the stream again from the beginning. |
| `live` | Marker without data: everything the server has, has been sent. |

### From reset to live

A stream has two phases, separated by the two markers.

1. **Catching up.** After `reset` the server sends everything it has, from its database or cache. In this phase a client receives `add` events, or `update` when the server is certain the client already has the item. It never receives `delete`.
2. **Live.** After `live` every event is a change that someone or something made in the system at that moment: `add`, `update` or `delete`.

A server can send `reset` at any moment, also in the middle of a stream, and then starts again with catching up. Servers try to avoid this, but it can not always be prevented.

What a client does with `reset` is its own choice:

- **Simple:** throw away everything it has at `reset` and build it up again from the events that follow.
- **Fewer changes:** keep everything at `reset`, process the `add` and `update` events, and at `live` remove the items for which nothing was received since the `reset`.

A server sends a comment line `: ping` when there is nothing to send for a while (60 seconds in HortiApi.Server). A client ignores it; it only keeps the connection open.

## Continue where you stopped

Send the `id` of the last event you processed in the header `Last-Event-ID`. The server continues after that event. Without the header the stream starts from the beginning.

This works for both answers: after a broken stream, and to ask for the next part of a JSON list of events.

A server only keeps events for a limited time; for a supply stream that is 30 minutes. When it can no longer continue from the given event id, it answers with 410 [gone](/error/gone). The client then sends the request again without `Last-Event-ID` and starts from the beginning.

## Limit the number of results

`Prefer: max-results=200` asks the server to return at most that number of items. The header `Preference-Applied` in the response tells whether the server has done so.

## In .NET

`HortiApi.Client.Rest` has a method for each answer. `Observe` opens the stream and gives every event with its type:

```csharp
await foreach (var item in client.Supply.Observe(new SupplyFilter { StreamId = streamId }))
{
  switch (item.EventType)
  {
    case HortiApiStreamEventType.Add:
    case HortiApiStreamEventType.Update:
      Store(item.Data);
      break;
    case HortiApiStreamEventType.Delete:
      Remove(item.Data.Id);
      break;
    case HortiApiStreamEventType.Reset:
      // start of a new stream
      break;
    case HortiApiStreamEventType.Live:
      // up to date
      break;
  }
}
```

`Pull` asks for the JSON list, one request at a time. Remember the `EventId` of the last event and pass it to continue:

```csharp
string? lastEventId = null;

await foreach (var supplyEvent in client.Supply.Pull(new SupplyFilter { StreamId = streamId }, new HortiApiStreamStart()))
{
  Console.WriteLine($"{supplyEvent.EventType} {supplyEvent.Data?.Id}");
  lastEventId = supplyEvent.EventId;
}

// later: only what came after the last event, at most 200 events
var next = client.Supply.Pull(
  new SupplyFilter { StreamId = streamId },
  new HortiApiStreamContinue { LastEventId = lastEventId },
  HortiApiClientPreferOptions.WithMaxResults(200));
```

## Open questions

These points are not decided yet.

- Does `delete` carry the whole item or only its `id`?
- With JSON: how often may a client ask again, and does a search (a list without events) support `Last-Event-ID`?
- Is a stream ever closed by the server, and what does a client do then?
