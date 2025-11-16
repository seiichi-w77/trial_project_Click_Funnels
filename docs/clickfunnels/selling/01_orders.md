# ClickFunnels Orders Documentation

## Overview

"ClickFunnels orders enable customers to purchase products and subscriptions through funnels, manual orders and the public API."

Orders represent transactions created through three primary payment processor types: Stripe, Payments AI, and External Order systems.

## Order Types by Payment Processor

### Stripe Orders
Orders processed through Stripe gateway feature their own service/billing status values and webhook event types. These orders integrate with Stripe's payment infrastructure.

### Payments AI Orders
Orders utilizing Payments AI ("an advanced way to get payments for your business, leveraging AI") have distinct statuses and webhook events. These orders support both one-time and subscription-based transactions.

### External Orders (Beta)
External orders allow merchants to process payments outside ClickFunnels while leveraging platform features like automations and CRM. Distinguished by `payment_processor` set to `"external"`.

## Core Concepts

### Order Invoices
Invoices are issued against orders and function as payment snapshots. Key distinctions include:

- **One-time orders** typically have one invoice with a single payment transaction
- **Subscription orders** can have multiple invoices
- Invoice line items differ from order line items; they represent a historical snapshot while orders can be updated (e.g., subscription upgrades/downgrades)

### Live Mode
Orders exist in two modes: `live_mode` true (impacts analytics) or false (test orders with no impact).

### Line Items
Orders contain line items reflecting purchased items—a mix of subscriptions and one-time products. These determine whether an order is classified as "one-time-order" or "subscription-order."

## Payments AI Order States

### One-Time Order Flow
1. Customer requests one-time sales items (status: `pending`)
2. Either:
   - Customer pays invoice → items assigned `completed` status
   - Customer cancels → items assigned `canceled` status

### Invoice Lifecycle

**Standard Payment Flow:**
- Upcoming invoice issued (status: `unpaid`)
- Invoice paid in full (status: `paid`)
- May be refunded or disputed

**Partial Payment Scenario:**
- Invoice issued (`unpaid`)
- Partial payment made (status: `partially-paid`)
- Either remaining amount paid or refunded

**Past Due Flow:**
- Invoice issued (`unpaid`)
- Exceeds 24-hour window (status: `past-due`)
- If unpaid within grace period (status: `abandoned`)

## External Orders Management

### Prerequisites
- API key required (no payment gateway setup needed)
- Client must architect state transitions
- Minimal API-side automation

### Integration Features

**Course/Community/Asset Access:**
Create an `Orders::Invoice` with status `"paid"` containing relevant `Products::Variant` records linked to digital assets.

**Revoking Access:**
Set invoice status to `"refunded"` or order `service_status` to `"churned"` or `"completed"`.

**Confirmation Emails:**
Setting invoice status to `"paid"` triggers order confirmation emails to the associated contact.

**Webhook Events:**
State changes trigger corresponding webhook events (e.g., `orders/invoice.paid`).

**Subscription Cancellation:**
Switch `service_status` to `"canceled"`, which auto-updates:
- `canceled_at` timestamp
- `churned_at` timestamp
- `cancel_reason` to "other"

### Limitations (Currently Beta)
- No native discount management
- Historical order imports face timestamp constraints
- Analytics unavailable (require `Orders::Transaction` resources)

## Future Roadmap

Expected enhancements include discount management, improved historical data imports, and analytics integration—though these weren't included in the initial release.

---

**Source:** https://developers.myclickfunnels.com/docs/orders
**Scraped:** 2025-11-16
