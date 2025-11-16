# ClickFunnels 2.0 Filtering Documentation

## Overview

The ClickFunnels API provides a filtering mechanism for list endpoints that allows querying by specific attributes. Filters are designed to be straightforward and performant.

## Query Parameters

Filters are specified using bracket notation in query parameters:
- `filter[attribute_name]=value`

## Filter Syntax

### Single Value Filtering

Query a specific attribute with one value:

```
https://myteam.myclickfunnels.com/api/v2/workspaces/3/contacts?filter[email_address]=[email protected]
```

### Multiple Values (OR Logic)

Filter by multiple values for the same attribute, separated by commas:

```
filter[email_address]=[email protected],[email protected]
```

This returns records matching *either* email address.

### Multiple Attributes (AND Logic)

Combine different filter attributes to narrow results:

```
filter[email_address]=[email protected],[email protected]&filter[id]=1
```

As noted: "Those filters are `AND` filters, which give you the intersection of multiple records."

Only records satisfying *all* conditions are returned.

## Availability

Filters are only available on endpoints where documented. Check the "Request" section of API documentation to confirm filter support and available filterable attributes.

## Important Considerations

- **URL Encoding**: Special characters require encoding (`[` = `%5B`, `]` = `%5D`)
- **Unicode Characters**: Email addresses with unicode characters need additional encoding
- **Special Symbols**: Characters like `%` and `+` require proper encoding

## Example Usage

**cURL with automatic encoding:**
```bash
curl -g 'https://myteam.myclickfunnels.com/api/v2/workspaces/3/contacts?filter[email_address]=[email protected]' \
  --header 'Authorization: Bearer ...' \
  --header 'User-Agent: YourAppYourOrg'
```

---

**Source:** https://developers.myclickfunnels.com/docs/filtering
**Scraped:** 2025-11-16
