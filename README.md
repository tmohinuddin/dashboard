# CoreWeave AI Enablement Dashboard

Internal monthly dashboard for AI agent reporting — OKR & leadership review.

**Live URL:** https://tmohinuddin.github.io/dashboard

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

## Files

| File | Purpose |
|------|---------|
| `index.html` | Self-contained dashboard — all CSS, JS, and data inline |
| `README.md` | This file |

---

## Setup (already done — for reference only)

### Google Sheet
- Sheet ID: `1N2FQ8ecJlio6uG9D5apNUOZ4apBvBldDdkKSFs6rhLw`
- Tabs: HUB, SPOKE, CACHE
- CACHE tab published as CSV for live fetch

### Apps Script
- Reads HUB + SPOKE tabs
- Writes JSON to CACHE tab
- Pushes full dashboard HTML to Confluence via REST API
- Runs daily at 6am via time-driven trigger

### GitHub Pages
- Repo: `tmohinuddin/dashboard`
- Branch: `main`
- File: `index.html` (root)
- URL: `https://tmohinuddin.github.io/dashboard`

### Confluence
- Page: AI Enablement Dashboard — Monthly Review
- URL: `https://coreweave.atlassian.net/wiki/spaces/IT/pages/1888944130`
- Updated automatically via Apps Script daily

---

## Contacts

| Role | Name |
|------|------|
| Dashboard owner | tmohinuddin@coreweave.com |
| Google Sheet | CoreWeave IT AI Team |
| Apps Script | Attached to the Google Sheet |
