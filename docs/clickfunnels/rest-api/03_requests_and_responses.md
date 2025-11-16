# ClickFunnels API: Requests and Responses Documentation

## Overview

The ClickFunnels API communicates exclusively through JSON format. All requests require the `Content-Type: application/json` header and must be transmitted over HTTPS connections.

## HTTP Status Codes

### Success Responses (2xx)

| Code | Status | Use Case |
|------|--------|----------|
| 200 | OK | Standard successful responses for GET, PUT, PATCH operations |
| 201 | Created | Confirms successful resource creation via POST requests |
| 204 | No Content | Successful operations without response body (typically DELETE calls) |

### Client Errors (4xx)

| Code | Status | Meaning |
|------|--------|---------|
| 400 | Bad Request | "The request is structured incorrectly, e.g. the body or query params are invalid" |
| 401 | Unauthorized | Missing or invalid Authorization Bearer token; see Authentication docs |
| 403 | Forbidden | Insufficient permissions to access the requested resource |
| 404 | Not Found | Requested resource does not exist |
| 409 | Conflict | Current application state conflicts with requested action |
| 422 | Unprocessable Entity | Valid structure but fails business logic validation |
| 429 | Too Many Requests | Rate limit threshold exceeded; review Rate Limiting documentation |

### Server Errors (5xx)

Server-side failures require support intervention. Contact via discussion forum or ClickFunnels support.

## Key Requirements

- **Content Type**: JSON exclusively
- **Protocol**: HTTPS only
- **Format**: All requests/responses in JSON structure

---

**Source:** https://developers.myclickfunnels.com/docs/requests-and-responses
**Scraped:** 2025-11-16
