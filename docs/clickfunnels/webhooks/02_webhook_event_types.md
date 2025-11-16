# ClickFunnels 2.0 Webhook Event Types Documentation

## Overview

ClickFunnels provides webhook functionality for real-time event notifications. The platform supports both V1 and V2 webhook versions, though V1 is "discouraged" with "no new webhooks launched in the V1 version."

---

## Appointments::ScheduledEvent

**Available Versions:** V2 only

Triggered when appointment scheduling events occur.

### Events

| Event | Description |
|-------|-------------|
| `appointments/scheduled_event.created` | New appointment scheduled |
| `appointments/scheduled_event.canceled` | Appointment canceled |
| `appointments/scheduled_event.rescheduled` | Appointment date/time changed |

**Payload includes:** Event ID, scheduled times, contact details, timezone, comments, status, and attendee limits.

---

## Blogs::Post

**Available Versions:** V2

Manages blog content lifecycle events.

### Events

| Event | Description |
|-------|-------------|
| `blogs/post.created` | New blog post created |
| `blogs/post.updated` | Blog post modified |
| `blogs/post.deleted` | Blog post removed |
| `blogs/post.published` | Post moved to published state |

**Payload includes:** Title, content, SEO metadata, visibility status, publication timestamp, author information, and tags/categories.

---

## Contact

**Available Versions:** V1, V2

Tracks contact data modifications.

### Events

| Event | Description |
|-------|-------------|
| `contact.created` | New contact added |
| `contact.updated` | Contact information changed |
| `contact.deleted` | Contact removed |
| `contact.identified` | Contact identified by email/phone |

---

## Contact::AppliedTag

**Available Versions:** V2

Manages tag assignments to contacts.

### Events

| Event | Description |
|-------|-------------|
| `contacts/applied_tag.created` | Tag assigned to contact |
| `contacts/applied_tag.deleted` | Tag removed from contact |

---

## Communities::Post

**Available Versions:** V2

Tracks community discussion posts.

### Events

| Event | Description |
|-------|-------------|
| `communities/post.created` | New community post created |

**Payload includes:** Title, body text, URL, group/topic information, contact ID, and timestamps.

---

## Communities::Posts::Comment

**Available Versions:** V2

Monitors community post comments.

### Events

| Event | Description |
|-------|-------------|
| `communities/posts/comment.created` | Comment added to post |

**Payload includes:** Comment text, URL, associated post/group, contact ID, and timestamps.

---

## Course

**Available Versions:** V2

Manages course lifecycle and enrollment.

### Events

| Event | Description |
|-------|-------------|
| `course.created` | New course created |
| `course.updated` | Course information modified |
| `course.deleted` | Course removed |
| `course.published` | Course published |
| `courses/enrollment.created` | Student enrolls in course |
| `courses/enrollment.updated` | Enrollment record changed |
| `courses/enrollment.deleted` | Enrollment terminated |
| `courses/enrollment.suspended` | Enrollment paused |
| `courses/enrollment.course_completed` | Student completes course |
| `courses/section.created` | Course section added |
| `courses/section.updated` | Section modified |
| `courses/section.deleted` | Section removed |
| `courses/section.published` | Section published |
| `courses/lesson.created` | Lesson added |
| `courses/lesson.updated` | Lesson modified |
| `courses/lesson.deleted` | Lesson removed |
| `courses/lesson.published` | Lesson published |

**Available Versions for Enrollment/Section/Lesson:** V1, V2 (Enrollment); V2 (Section/Lesson)

---

## Fulfillment

**Available Versions:** V2

Tracks physical product fulfillment.

### Events

| Event | Description |
|-------|-------------|
| `fulfillment.created` | Fulfillment record created for paid orders |
| `fulfillment.updated` | Fulfillment status changed |

---

## Product & Products::Variant

**Available Versions:** V2

Manages product catalog changes.

### Product Events

| Event | Description |
|-------|-------------|
| `product.created` | New product added |
| `product.updated` | Product information modified |

### Variant Events

| Event | Description |
|-------|-------------|
| `products/variant.created` | Product variant created (size, color, etc.) |
| `products/variant.updated` | Variant information modified |

---

## Orders::Invoices::Restock

**Available Versions:** V2

Tracks inventory restoration from canceled/refunded orders.

### Events

| Event | Description |
|-------|-------------|
| `orders/invoices/restock.created` | Restock initiated |
| `orders/invoices/restock.updated` | Restock status changed |

---

## Form Submission

**Available Versions:** V1, V2

Captures form data submissions.

### Events

| Event | Description |
|-------|-------------|
| `form_submission.created` | Form submitted |

---

## Sales::Opportunity (CRM)

**Available Versions:** V2

Manages sales pipeline opportunities.

### Events

| Event | Description |
|-------|-------------|
| `sales/opportunity.created` | New opportunity created |
| `sales/opportunity.updated` | Opportunity modified |
| `sales/opportunity.deleted` | Opportunity removed |
| `sales/opportunity.closed` | Opportunity closed (one-time only) |
| `sales/opportunity.moved_stage` | Opportunity stage changed |

---

## Order

**Available Versions:** V1, V2

Tracks order lifecycle across payment processors (Stripe, Payments.ai, External).

### Order Events

| Event | Payment Processors | Description |
|-------|-------------------|-------------|
| `order.created` | All | Order initiated |
| `order.updated` | All | Order information modified |
| `order.deleted` | All | Order removed |
| `order.completed` | All | One-time paid or subscription period ended |

### One-Time Order Events

| Event | Description |
|-------|-------------|
| `one-time-order.completed` | One-time order payment received |
| `one_time_order.refunded` | Refund issued |

### Subscription Events

| Event | Payment Processors | Description |
|-------|-------------------|-------------|
| `subscription.activated` | All | Subscription service status active |
| `subscription.canceled` | All | Subscription terminated |
| `subscription.reactivated` | All | Canceled/churned subscription renewed |
| `subscription.downgraded` | All | Changed to lower-value product |
| `subscription.upgraded` | All | Changed to higher-value product |
| `subscription.churned` | All | Subscription ended naturally |
| `subscription.modified` | PAI only | Subscription details changed |
| `subscription.completed` | All | Subscription period ended without cancellation |
| `subscription.first_payment_received` | All | First non-trial, non-setup payment received |
| `subscription.trial_started` | All | Trial period begins |
| `subscription.trial_ended` | All | Trial period concludes |
| `subscription.trial_converted` | All | Trial converted to active subscription |
| `subscription.line_items.changed` | All | Line items modified |

---

## Orders::Transaction

**Available Versions:** V1, V2

**Payment Processors:** Stripe, Payments.ai

Tracks financial transactions.

### Events

| Event | Description |
|-------|-------------|
| `orders/transaction.created` | Transaction recorded |
| `orders/transaction.updated` | Transaction modified |

---

## Invoice

**Available Versions:** V1, V2

Manages billing documents.

### Orders::Invoice Events

| Event | Payment Processors | Description |
|-------|-------------------|-------------|
| `orders/invoice.created` | All | Invoice generated |
| `orders/invoice.updated` | All | Invoice modified |
| `orders/invoice.refunded` | All | Refund processed |
| `orders/invoice.abandoned` | PAI only | Invoice abandoned |
| `orders/invoice.reissued` | PAI only | Invoice reissued |
| `orders/invoice.past_due` | All | Payment overdue |
| `orders/invoice.fulfilled` | All | All line items shipped |
| `orders/invoice.voided` | Stripe, External | Invoice invalidated |
| `orders/invoice.paid` | All | Invoice payment received |
| `renewal-invoice-payment-declined` | PAI, Stripe | Subscription renewal payment failed |

### Specialized Invoice Events

| Event | Description |
|-------|-------------|
| `one-time-order.invoice.paid` | One-time order invoice paid |
| `subscription.invoice.paid` | Subscription invoice paid |

---

## Workflow-Based

**Available Versions:** V1

Used for UI-based ClickFunnels Workflows.

### Events

| Event | Description |
|-------|-------------|
| `runs/step.dontrunme` | Workflow step executed |
| `workflows_integration_step.executed` | Integration step completed |
| `workflows/steps/integration_step.executed` | Integration step executed |
| `workflows/steps/deliver_webhook_step.executed` | Webhook delivery step executed |

---

## Platform::Application

**Available Versions:** V2

Manages OAuth platform integrations.

### Events

| Event | Description |
|-------|-------------|
| `platform_application.disconnected` | OAuth app disconnected from user's team |

**Payload includes:** Application ID, public ID, name, team/workspace IDs.

---

## Key Implementation Notes

- **V1 Deprecation:** Use V2 webhooks when available
- **Payment Processor Variations:** Webhook behavior differs across payment systems
- **Payload References:** Full payload structures documented in API reference pages
- **Signature Verification:** Implement verification as detailed in signature verification guide

---

**Source:** https://developers.myclickfunnels.com/docs/webhook-event-types
**Scraped:** 2025-11-16
