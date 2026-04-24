---
title: "Admin Central Aggregation Workflow (Go)"
source: "raw/repos/RBTH/centralize/admin-central-server/"
date_added: 2026-04-17
tags: [concept, api, workflow, go, aggregation]
aliases: [Go Aggregator Workflow, Parallel Sync]
status: canonical
related:
  - "[[admin-central-core]]"
  - "[[platform-dashboard-api-workflow]]"
summary: "The high-performance aggregation workflow used by the Go server to fetch real-time data across multiple platforms simultaneously."
---

# Admin Central Aggregation Workflow (Go)

## Definition
The **Admin Central Aggregation Workflow** is a real-time, high-concurrency process used to collect business intelligence from multiple distributed KK-Cash platforms. It is optimized for speed and real-time dashboard responsiveness.

## Core Logic: The Fan-out Pattern
Unlike linear synchronization, the Go server uses a **Fan-out/Fan-in** pattern to minimize response latency.

### 1. Trigger (On-Demand)
The workflow is usually triggered by a request from the **Admin Central UI** or a high-level reporting service.
- **Primary Endpoint:** `/api/v1/client/dashboardByPlatform`

### 2. Parallel Fetching (Goroutines)
When the endpoint is hit, the Go server performs the following:
- **Platform Discovery:** Identifies all active platforms for the current user's scope.
- **Concurrency:** Launches a separate **Goroutine** for each platform simultaneously.
- **Network Call:** Each routine makes a concurrent HTTP request to the platform's API (e.g., `GetListDashboardMonthly`).
- **Safety:** Uses a `sync.WaitGroup` and `sync.Mutex` to coordinate and collect results safely without data races.

### 3. Merging (Aggregation)
Once all goroutines return (or timeout), the results are merged:
- **Summation:** Global metrics like `SumTotalDeposit`, `SumTotalWithdraw`, and `SumTotalProfit` are calculated in memory.
- **Normalization:** Data from different versions of sub-platforms is normalized into a consistent JSON structure.
- **Response:** A single, consolidated response is returned to the client.

## Role in the Ecosystem
The Go Aggregator is the **Real-time Engine**. It provides the most up-to-date view of the entire RBTH ecosystem by querying live data from the edges (KK-Cash) rather than relying on a static historical database.

## References
- `raw/repos/RBTH/centralize/admin-central-server/domains/client/usecases/usecase_dashboardV2.go`
- `raw/repos/RBTH/centralize/admin-central-server/constants/const.go`
- `raw/repos/RBTH/centralize/admin-central-server/routers/router_client.go`
