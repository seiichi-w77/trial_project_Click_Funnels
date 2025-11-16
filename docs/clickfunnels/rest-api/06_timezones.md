# ClickFunnels API Time Zones Documentation

## Overview

The ClickFunnels API handles time zones with a human-readable format rather than standard TZ notation. When retrieving or passing time zone data through resources like `Team` or `Contact`, the format appears as descriptive names.

## Time Zone Format

**Display Format:** `"Eastern Time (US & Canada)"` (human-friendly)

**Standard TZ Equivalent:** `"America/New_York"` (internal mapping)

The API supports a curated subset of **134 meaningful time zones** rather than the complete IANA database.

## Available Time Zones

The platform provides a comprehensive mapping between display names and TZ identifiers:

### Americas
- Pacific Time (US & Canada) → America/Los_Angeles
- Mountain Time (US & Canada) → America/Denver
- Central Time (US & Canada) → America/Chicago
- Eastern Time (US & Canada) → America/New_York
- Atlantic Time (Canada) → America/Halifax
- Newfoundland → America/St_Johns

### Europe
- London → Europe/London
- Paris → Europe/Paris
- Berlin → Europe/Berlin
- Moscow → Europe/Moscow
- Athens → Europe/Athens

### Asia-Pacific
- Tokyo → Asia/Tokyo
- Hong Kong → Asia/Hong_Kong
- Singapore → Asia/Singapore
- Sydney → Australia/Sydney
- Auckland → Pacific/Auckland

### Africa & Middle East
- Cairo → Africa/Cairo
- Nairobi → Africa/Nairobi
- Dubai/Abu Dhabi → Asia/Muscat
- Tehran → Asia/Tehran

### Special Cases
- UTC → Etc/UTC
- International Date Line West → Etc/GMT+12

## Implementation Notes

When working with the API:
- Always use the **human-friendly name** for API requests and responses
- The system automatically maps these to standard TZ identifiers internally
- All 134 supported zones are documented in JSON/YAML format for reference
- No timezone conversion is performed by the API—values represent local time in the specified zone

---

**Source:** https://developers.myclickfunnels.com/docs/timezones
**Scraped:** 2025-11-16
