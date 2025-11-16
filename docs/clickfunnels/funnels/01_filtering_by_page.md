# Filtering by Page Documentation

## Overview

The filtering by page feature enables developers to build automations based on order origination context. This involves identifying the correct page name or ID for filtering purposes across orders, webhook payloads, and automation platforms like Zapier.

## Order Resource Properties

Orders contain several properties that indicate their origination point:

```json
{
  "id": 7677,
  "public_id": "JBBEOJ",
  "workspace_id": 42,
  "origination_channel_id": 159,
  "origination_channel_type": "Funnel",
  "page_id": 93362,
  "order_type": "one-time-order",
  "page_name": "Josh's Checkout Element Page",
  "origination_channel_name": "Josh's Test Order Form Funnel 04202022",
  "order_page": {
    "id": 93362,
    "public_id": "edWLPo",
    "name": "Josh's Checkout Element Page"
  }
}
```

Key identifiers include the numeric page ID, public ID, and human-readable page name.

## Finding Page Information via UI

**Step 1: Locate the Target Page**
Navigate to and identify the page requiring filtering within your ClickFunnels workspace.

**Step 2: Enter Edit Mode**
Click the page to access the editor, where both the page name and public ID (visible in the URL path) are displayed.

## Critical Distinction: Page vs. Page Step

A significant difference exists between standalone pages and funnel workflow steps. Within ClickFunnels workflows, "Page" refers to individual workflow steps with unique names and URL paths—these differ from the editable page itself.

The Page API differentiates these using the `show_page_step` property, present only on `funnel_page` type pages:

```json
{
  "id": 61,
  "public_id": "HMjyNF",
  "workspace_id": 42000,
  "name": "Great Page",
  "type": "landing_page",
  "current_path": "/my-page-example",
  "show_page_step": {
    "name": "New Funnel Page",
    "current_path": "/new-funnel-page"
  }
}
```

Funnel pages maintain two distinct paths: `page.current_path` (standalone page) and `page.show_page_step.current_path` (funnel step path).

---

**Source:** https://developers.myclickfunnels.com/docs/filtering-by-page
**Scraped:** 2025-11-16
