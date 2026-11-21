---
layout: default
title: gone
permalink: /error/gone
---

# gone

What the request asks for was available before, but is no longer available on this server. Sending the same request again will not help.

For a [stream](/streaming) this means the server can not continue from the event id in `Last-Event-ID`, because it no longer has the events that came after it. For a supply stream a server keeps the events for 30 minutes.

Send the request again without `Last-Event-ID` to start from the beginning.
