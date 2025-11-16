# Pagination Documentation

## Overview

The ClickFunnels 2.0 API implements **cursor-based pagination** for navigating through large list responses.

## Pagination Method

The API uses cursor-based pagination rather than offset-based pagination, enabling efficient navigation through datasets.

## Key Parameters

**`after`** - The cursor parameter that retrieves records following a specified ID value. This parameter functions identically whether results are ordered ascending or descending.

## Response Limits

- **Maximum objects per response**: 20 items
- **Default ordering**: Ascending by ID
- **Customizable ordering**: Results can be sorted descending via `sort_order=desc` parameter

## Response Headers

The API provides two header-based navigation options:

1. **`Pagination-Next`** - Contains the ID of the last object in the current response, simplifying cursor retrieval
2. **`Link`** - Supplies a pre-formatted URL for the next page with the `rel="next"` relationship, eliminating manual URL construction

## Usage Example

Initial request returns the first 20 contacts:
```
GET /api/v2/workspaces/3/contacts
```

Retrieve subsequent page using the last ID from previous response:
```
GET /api/v2/workspaces/3/contacts?after=55
```

## Directional Navigation

The `after` parameter consistently retrieves the "next page" of results regardless of sort direction—whether ascending or descending order is applied.

---

**Source:** https://developers.myclickfunnels.com/docs/pagination
**Scraped:** 2025-11-16
