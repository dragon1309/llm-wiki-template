---
title: "Selective Product Enablement (RB-1210)"
date_added: 2026-04-24
tags: [feature, product-management, rb-1210, platform-dashboard]
status: canonical
summary: "Technical specification for per-operator product enablement and disablement."
---

# 🛠️ Selective Product Enablement (RB-1210)

## 1. Overview
The **RB-1307** requirement enables **Company** users to selectively toggle the availability of specific products or product groups for individual **Operators**. This allows for granular control over the gaming catalog offered by different partners.

## 2. System Architecture & Data Flow
The feature relies on a cross-service synchronization pattern using **Redis** as the invalidation signal.

1.  **BO Frontend (`a-pilot-bo-gui`)**: Provides the management UI in the Operator Settings.
2.  **Product Service (`apilotto-product`)**: The Source of Truth for product status.
3.  **Redis**: Acts as the distributed cache and invalidation layer.
4.  **Game Hall Service (`game-hall-service`)**: The player-facing backend that filters products.
5.  **Player Frontend (`a-pilot-player-gui`)**: Dynamically renders the available catalog.

## 3. Implementation Details

### A. Product Microservice (Go)
- **New Read API**: `GET /v1/product/enabled_product/{account_code}`
    - Joins the `products` table with `products_accounts` to return the specific status for the operator.
- **Bulk Update API**: `POST /v1/product/product_account/enabled/bulk`
    - Updates multiple product rows in `products_accounts` in one transaction.
- **Cache Invalidation**: On every update, delete the Redis key: `listProductAccount:{account_code}`.

### B. Game Hall Service (Java)
- **Cache Logic Update**: Modify `CompanyBOProductService.java`.
- **Change**: Remove the "permanent" in-memory cache variable `cacheProductAccount`.
- **Result**: The service will now always check Redis via `orchestratorService.listProductByAccountResponseRedis()`. If Redis is empty (invalidated by Go), it fetches fresh data from the Product API.

### C. BO Frontend (Angular)
- **New Tab**: Add a "Product Management" tab to the **Operator Settings** page.
- **UI Components**: 
    - Use `ngbNav` for the tab structure.
    - Implement grouped checkboxes with an **Indeterminate State** (dash) for mixed groups.
    - Single "Save Changes" button for bulk updates.

## 4. Conflict Resolution (Global vs. Local)
The system follows a **Global-Override** logic:
- If a product is **Disabled Globally** (by Company), it cannot be enabled for any operator.
- If a product is **Enabled Globally**, it can be selectively **Disabled Locally** for specific operators.
- **Logic**: `FINAL_STATUS = (GLOBAL_ENABLED && OPERATOR_ENABLED)`

## 5. Verification Checklist
- [ ] DB: `products_accounts` table updates correctly.
- [ ] Redis: Key `listProductAccount:{code}` is deleted on save.
- [ ] Java: `game-hall-service` reflects changes without restart.
- [ ] Player GUI: Menu and product cards update dynamically.

---
**Related Documents**:
- [[platform-dashboard-api-workflow]]
- [[kkcash-system-architecture]]
- [[RB-1210 Impact Assessment]] (Raw Source)
