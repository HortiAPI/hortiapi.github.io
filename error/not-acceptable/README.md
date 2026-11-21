---
layout: default
title: not-acceptable
permalink: /error/not-acceptable
---

# not-acceptable

The server can not answer in the format the request asks for with the `Accept` header.

This happens when a request has `Accept: text/event-stream` for a capability that has no Server-Sent Events stream on this server. The capabilities with a stream are listed in `sse` of the [discovery](/use-case/discovery) document.

Send the request again with `Accept: application/json` to receive the result as a list.

See [streaming](/streaming) for how lists and streams work.
