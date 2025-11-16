# Authentication Documentation

## Overview

The ClickFunnels 2.0 API uses Bearer token authentication for API requests. This document covers the authentication methods and requirements for accessing the API.

## Bearer Token Authentication

### Basic Usage

Make requests by including a Bearer token in the Authorization header:

```shell
curl 'https://myteam.myclickfunnels.com/api/v2/teams' \
  --header 'Authorization: Bearer AVJrj0ZMJ-xoraUk1xxVM6UuL9KXmsWmnJvvSosUO6X' \
  --header 'User-Agent: YourAppYourOrg'
```

### Response Example

```json
[
  {
    "id": 3,
    "name": "My Team"
  }
]
```

## Required Headers

### User-Agent Header

**Critical requirement**: All API requests must include a User-Agent header. The system enforces this as a security measure. Provide an identifiable value like `YourAppYourOrg`.

## Token Scope and Access

**Team-Level Authorization**: Default access tokens operate at the team level, granting access to workspace data associated with that specific team across all its workspaces.

## Alternative Authentication Methods

### OAuth 2.0

For third-party integrations, the API supports OAuth 2.0 flows. These tokens may carry different authorization scopes depending on the integration requirements. Refer to the [OAuth 2.0 documentation](/docs/oauth-20) for implementation details.

## Getting Started

For step-by-step instructions on obtaining your API key, see the [Getting Started guide](/docs/getting-started).

## Related Documentation

- [Rate Limiting](/docs/rate-limiting)
- [Requests and Responses](/docs/requests-and-responses)
- [OAuth 2.0](/docs/oauth-20)

---

**Source:** https://developers.myclickfunnels.com/docs/authentication
**Scraped:** 2025-11-16
