---
title: "OAuth 2.0 Authorization Server Metadata Migrations"
category: std

docname: draft-skokan-oauth-discovery-migrations-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: ""
workgroup: "Web Authorization Protocol"
keyword:
  - discovery
  - migrations
venue:
  group: "Web Authorization Protocol"
  type: ""
  mail: "oauth@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/oauth/"
  github: "panva/draft-skokan-oauth-discovery-migrations"
  latest: "https://panva.github.io/draft-skokan-oauth-discovery-migrations/draft-skokan-oauth-discovery-migrations.html"

author:
  -
    fullname: "Filip Skokan"
    organization: Okta
    email: "panva.ip@gmail.com"

normative:

informative:

entity:
  SELF: "[draft-skokan-oauth-discovery-migrations-latest]"

--- abstract

This document defines a mechanism for OAuth 2.0 Authorization Server Metadata {{!RFC8414}} to
optionally indicate the availability of updated metadata and a mechanism for an OAuth 2.0 client
to retrieve and use the updated metadata. The updated metadata can be used for endpoint migration
purposes or gradual rollout of new authorization server features.

--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Examples

## Authorization Server Metadata Request & Response with available migrations

Metadata Request

    GET /.well-known/oauth-authorization-server HTTP/1.1
    Host: server.example.com

Metadata Response

    HTTP/1.1 200 OK
    Content-Type: application/json
    Vary: OAuth-Client-ID

    {
      "issuer": "https://server.example.com",
      "authorization_endpoint": "https://server.example.com/authorize",
      "migrations_available": true
    }

## Authorization Server Metadata Request & Response with migrations used (response straight away)

Metadata Request

    GET /.well-known/oauth-authorization-server HTTP/1.1
    Host: server.example.com
    OAuth-Client-ID: s6BhdRkqt3

Metadata Response

    HTTP/1.1 200 OK
    Content-Type: application/json
    Vary: OAuth-Client-ID

    {
      "issuer": "https://server.example.com",
      "authorization_endpoint": "https://server.example.com/v2/authorize"
    }

## Authorization Server Metadata Request & Response with migrations used (response through a redirect)

Metadata Request

    GET /.well-known/oauth-authorization-server HTTP/1.1
    Host: server.example.com
    OAuth-Client-ID: s6BhdRkqt3

Redirect Response

    HTTP/1.1 307 Temporary Redirect
    Location: /migrations/s6BhdRkqt3
    Cache-Control: no-store

Redirected Metadata Request

    GET /migrations/s6BhdRkqt3 HTTP/1.1
    Host: server.example.com
    OAuth-Client-ID: s6BhdRkqt3

Metadata Response

    HTTP/1.1 200 OK
    Content-Type: application/json
    Cache-Control: no-store

    {
      "issuer": "https://server.example.com",
      "authorization_endpoint": "https://server.example.com/v2/authorize"
    }


# Security Considerations

TODO Security


# IANA Considerations

TODO This document has no IANA actions (for now).


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
