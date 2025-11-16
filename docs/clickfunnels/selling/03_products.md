# ClickFunnels Product API Documentation

## Overview

The Product API enables creation and management of sellable products within ClickFunnels workspaces. This guide covers essential workflows for integrations handling products, fulfillments, and orders.

## Product Hierarchy

ClickFunnels organizes products in a four-tier structure:

1. **Product** - Top-level entity containing general product information
2. **Product Variant** - Each product includes one or more variants (default variant auto-generated)
3. **Product Price** - Pricing data associated with specific variants
4. **Fulfillment Location** - Physical or digital fulfillment origin points

## Key Implementation Requirements

### Variant ID Tracking
"When integrating with external systems, you should track the `variant_id` (or `default_variant_id`) returned from the API." This identifier is required when creating prices, fulfillments, and order line items rather than the product ID itself.

### Default Variant Creation
"Every product automatically gets a default variant upon creation. You cannot skip this creation." The API response includes the `default_variant_id` for immediate reference.

## Creation Workflows

### Simplified Workflow (Single Variant)

For integrations supporting single variants:

1. **Create Product** → Receives `default_variant_id` in response
2. **Create Product Price** → Reference the variant with `variant_id` parameter

### Full Workflow (Multiple Variants)

For multi-variant support:

1. **Create Product** → Obtain product ID and default variant
2. **Create Additional Variants** → Pass `product_id` and `fulfillment_location_ids`
3. **Create Prices** → Assign pricing to each variant separately

### Fulfillment Location Setup

Initial customer integration requires:

1. Create fulfillment location representing shipment origin
2. Store the location ID for future reference
3. Assign to variants via `fulfillment_location_ids` parameter during creation or updates

## Product Properties & Variants

### Property Definition

Properties define variant distinctions (size, color, material). These are established at the product level during creation.

**Creating a Product with Properties:**

```json
POST /api/v2/workspaces/{workspace_id}/products
{
  "product": {
    "name": "T-Shirt",
    "variant_properties": [
      { "name": "Size" },
      { "name": "Color" }
    ]
  }
}
```

**Response includes property IDs:**

```json
{
  "id": 12345,
  "name": "T-Shirt",
  "default_variant_id": 67890,
  "variant_properties": [
    { "id": 100, "name": "Size" },
    { "id": 101, "name": "Color" }
  ]
}
```

### Creating Variants with Property Values

Non-default variants require values for ALL product properties:

```json
POST /api/v2/products/{product_id}/variants
{
  "products_variant": {
    "product_id": 12345,
    "properties_values": [
      { "property_id": 100, "value": "Large" },
      { "property_id": 101, "value": "Red" }
    ],
    "fulfillment_location_ids": [5555]
  }
}
```

**Response:**

```json
{
  "id": 67891,
  "product_id": 12345,
  "name": "T-Shirt - Large / Red",
  "default": false,
  "properties_values": [
    { "property_id": 100, "value": "Large" },
    { "property_id": 101, "value": "Red" }
  ],
  "fulfillment_location_ids": [5555]
}
```

**Important constraints:**
- All properties must receive values
- Variant names auto-generate from property values
- Default variants lack `properties_values` (inherit from product)
- Values are case-insensitive with normalized whitespace

### Updating Properties

```json
PATCH /api/v2/products/{product_id}
{
  "product": {
    "variant_properties": [
      { "id": 100, "name": "Size" },
      { "id": 101, "name": "Color" },
      { "name": "Material" }
    ]
  }
}
```

Limitation: "You cannot remove a property that has multiple values assigned across variants" as this would delete affected variants.

## Related API Endpoints

- **Create Products:** [Create Products API Reference](/reference/createproducts)
- **Product Variants:** [Create Product Variants API](/reference/createproductsvariants)
- **Pricing:** [Create Product Prices API](/reference/createproductsprices)
- **Fulfillment Locations:** [Create Fulfillment Locations API](/reference/createfulfillmentslocations)
- **Fulfillments:** [Create Fulfillments API](/reference/createfulfillments) and [Fulfillments Overview](/docs/fulfillments)

---

**Source:** https://developers.myclickfunnels.com/docs/products
**Scraped:** 2025-11-16
