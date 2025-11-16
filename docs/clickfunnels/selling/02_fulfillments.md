# ClickFunnels 2.0 Fulfillments Documentation

## Overview

The fulfillments feature enables order fulfillment in ClickFunnels. According to the documentation, "A fulfillment is created when an order or a part of the order is being fulfilled."

### Key Fulfillment Characteristics

- **Status Management**: Fulfillments begin with a "fulfilled" status and can be canceled, transitioning to a "cancelled" state
- **Flexibility**: A single fulfillment can completely fulfill one order, partially fulfill an order, or contain items from multiple orders
- **Completion Criteria**: An order reaches fulfilled status once all invoice line items have been fulfilled in their required quantities

## Fulfillment States

The system tracks fulfillment progress through distinct statuses on invoice line items:

- `unfulfilled` — Items awaiting fulfillment
- `partially_fulfilled` — Some quantity fulfilled
- `fulfilled` — All items fulfilled
- `complete` — Final fulfilled state
- `ignored` — Items not requiring fulfillment

**Important Note**: The `fulfillment_status` field appears on all line items regardless of whether the associated product variant requires fulfillment.

## Fulfillment Flow

The typical fulfillment workflow follows these steps:

1. An API client creates an invoice for an order containing line items with `unfulfilled` status
2. Fulfillment occurs either through the ClickFunnels UI or programmatically via the Fulfillment API
3. Subsequent invoice queries reflect the updated `fulfilled` status

## Subscription vs. One-Time Orders

**Subscription Orders**: Await a subscription-paid event before fulfillment, as multiple invoices may exist across the order's lifetime

**One-Time Orders**: Can begin fulfillment after a single successful payment, as all invoice items are paid simultaneously

## API Access

Fulfillment operations are managed through the Fulfillment API and related resources, enabling programmatic order fulfillment management alongside UI-based fulfillment.

---

**Source:** https://developers.myclickfunnels.com/docs/fulfillments
**Scraped:** 2025-11-16
