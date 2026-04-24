---
title: "Platform Dashboard API Workflow (Rails)"
source: "raw/repos/RBTH/centralize/platform-dashboard-api/"
date_added: 2026-04-17
tags: [concept, api, workflow, rails, legacy]
aliases: [Rails Sync Workflow, Dashboard Persistence]
status: reviewed
related:
  - "[[admin-central-core]]"
summary: "The internal workflow of the Ruby on Rails reporting API, focusing on its proactive sync jobs and data persistence."
---

# Platform Dashboard API Workflow (Rails)

## Definition
The **Platform Dashboard API (Rails)** is a dedicated reporting and persistence service. Its primary responsibility is to fetch operational data from KK-Cash platforms and maintain a historical record of business metrics in a central PostgreSQL database.

## Core Logic: The Sync Cycle
The Rails service operates on a **Pull-and-Store** model. It does not wait for incoming data; it actively reaches out to sub-platforms.

### 1. Scheduler (`Whenever` Gem)
A background scheduler triggers two main jobs:
- **`SyncMasterJob`**: Every 1 minute. Syncs data for KOL/Teachers (Arjan).
- **`SyncWebJob`**: Every 1 minute. Syncs data for Web platform performance.

### 2. Network Integration (`RestClient`)
For every enabled platform in the database, the model `app/models/platform.rb` performs a **Direct HTTP GET** request:
- **Endpoint:** `#{api_url}/api/aff/getAllArjan`
- **Security:** Uses a standard Bearer Token stored in the `platforms` table.
- **Mechanism:** Linear execution (a sequential `each` loop).

### 3. Data Persistence (PostgreSQL)
Once data is received, the Rails API performs the following:
- **Validation:** Checks if a record for the current date/code already exists.
- **Storage:** Upserts data into the **`platform_dashboard_api`** logical database (specifically the `master_stats` or `web_stats` tables).
- **Isolation:** This database is dedicated to the reporting layer and is not shared with the management or operational services.
- **Reporting:** Provides RESTful endpoints (e.g., `/api/v1/summary_web_report`) for the Dashboard UI to query this saved data.

## Role in the Ecosystem
The Rails API acts as the **Historical Archive**. While newer services aggregate data in real-time, this service provides the database of record for charting business growth over days, weeks, and months.

## References
- `raw/repos/RBTH/centralize/platform-dashboard-api/app/jobs/sync_master_job.rb`
- `raw/repos/RBTH/centralize/platform-dashboard-api/app/models/platform.rb`
- `raw/repos/RBTH/centralize/platform-dashboard-api/db/schema.rb`
