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


# Security Considerations

TODO Security


# IANA Considerations

TODO This document has no IANA actions (for now).


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
