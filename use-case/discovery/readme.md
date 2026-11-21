---
layout: default
title: discovery use-case
permalink: /use-case/discovery
profile: discovery
sample: connect
---

# Discovery and connect

Every HortiApi server describes itself. A client that knows the base URL of the API starts with the discovery document and reads there which use cases and capabilities the server has. With the API key the client then asks `/me` for which companies the key can be used. Both are on the same host as the rest of the API.

When a user only enters the website of a company, the client first has to find the API. It tries the entered address as base URL of the API; when that fails it reads `/.well-known/horti-api` on the root of that host and follows the link to the discovery document. The API can be on another host than the website, so a client shows the host it found before it sends the API key.

{::nomarkdown}
{% include use-case-profile.html %}
{:/nomarkdown}

## See also

- [Connect sample](/sample/connect) — full request/response walkthrough
- [Connect without ApiKey sample](/sample/connect-without-apikey)
