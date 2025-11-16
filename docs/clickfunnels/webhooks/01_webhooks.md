# ClickFunnels Webhooks Documentation

## Overview

"ClickFunnels webhooks allow you to react to many events in the ClickFunnels app on your own server, Zapier and other similar tools."

## Setup & Configuration

### Initial Setup

To begin using webhooks, identify the events you wish to monitor, then configure a webhook endpoint to receive those events.

### Programmatic Endpoint Configuration

Configure webhook endpoints through the ClickFunnels API using the `Webhooks::Outgoing::Endpoints` endpoint. Specify the `event_type_ids` corresponding to events you want to monitor.

Alternatively, webhooks can be configured directly in the ClickFunnels UI.

## Event Payload Structure

### Payload Format

Webhook payloads arrive as POST requests containing a `Webhooks::Outgoing::Event` structure:

```json
{
  "data": { /* subject data */ },
  "event_id": "unique-identifier",
  "event_type": "subject.action",
  "subject_id": 236296209,
  "subject_type": "Contact",
  "created_at": "2024-04-04T19:16:31.000Z",
  "page_id": null,
  "funnel_id": null
}
```

### Event Type Naming

Event types follow the pattern `subject.action` (e.g., `contact.identified`, `order.created`). The `data` property contains the relevant resource payload matching API documentation schemas.

### V1 vs. V2 Webhooks

V1 webhooks have different payload structures and are deprecated. Use V2 webhooks where possible.

## Retry Logic & Delivery Guarantees

### Success Criteria

No retries occur if your endpoint responds with these status codes: 200, 201, 202, 203, 204, 205, 206, 207, or 226.

### Retry Schedule

For all other responses, ClickFunnels attempts redelivery according to this timeline:

| Attempt | Wait Time |
|---------|-----------|
| 0 | 1 second |
| 1 | 15 seconds |
| 2 | 1 minute |
| 3 | 5 minutes |
| 4 | 15 minutes |
| 5 | 1 hour |
| 6 | 12 hours |
| 7 | 24 hours |

### Event Recovery

"ClickFunnels webhook events can arrive out of order." If you miss events due to downtime exceeding retry windows, replay them via the `Webhooks::Outgoing::Event` resource logs.

## Additional Resources

- **Webhook Event Types**: Reference documentation lists all available event subscriptions
- **Signature Verification**: Security documentation covers payload authentication
- **API Reference**: Complete endpoint details at `/reference/listwebhooksoutgoingendpoints`

---

**Source:** https://developers.myclickfunnels.com/docs/webhooks
**Scraped:** 2025-11-16
