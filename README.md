# CoreWeave AI Enablement Dashboard

Internal monthly dashboard for AI agent reporting — OKR & leadership review.

---

## What this is

A self-contained, single-file HTML dashboard that shows:
- Executive KPI summary
- Full agent inventory (hub + spoke)
- Adoption & usage charts
- Org-level adoption breakdown
- Business impact by agent
- Enablement milestones
- Risks & callouts

---

## How data updates

Data is pulled automatically from the CoreWeave AI agent tracking Google Sheet via two paths:

### Path 1 — Live fetch (when opened directly in Chrome)
The dashboard fetches a published CSV from the Google Sheet's CACHE tab on every page load. The CACHE tab is refreshed daily by a Google Apps Script trigger.

### Path 2 — Hardcoded fallback (when embedded in Confluence or Union)
When the page is embedded in an iframe, browsers block external fetch requests. The dashboard falls back to the last hardcoded snapshot baked into `index.html`.

---

## How to update the data (monthly)

### Automatic (recommended)
The Google Apps Script runs daily at 6am and:
1. Reads the HUB and SPOKE tabs from the Google Sheet
2. Writes fresh JSON to the CACHE tab
3. Pushes updated HTML to the Confluence page

No manual action needed.

### Manual (if Apps Script is not running)
1. Open Apps Script (Extensions → Apps Script in the Google Sheet)
2. Run `pushDashboardToConfluence`
3. Check the Execution log for `SUCCESS`

---
---

## Setup (already done — for reference only)

### Apps Script
- Reads HUB + SPOKE tabs
- Writes JSON to CACHE tab
- Pushes full dashboard HTML to Confluence via REST API
- Runs daily at 6am via time-driven trigger



## Contacts
