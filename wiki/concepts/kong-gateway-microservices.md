---
title: "Kong Gateway & Microservices Architecture"
source: "raw/repos/API/"
date_added: 2026-04-17
tags: [concept, architecture, kong, microservices, b2b]
aliases: [System Actors, API Gateway Logic]
status: canonical
related:
  - "[[eday-api-system]]"
  - "[[seamless-wallet-flow]]"
summary: "A deep dive into the EDay API (A-Pilot) architecture, explaining how Kong manages the edge and how microservices interact."
---

# Kong Gateway & Microservices Architecture

## 1. The Gateway: Kong API Gateway
**Kong** acts as the **"Security Perimeter"** and the **"Traffic Cop"** of the B2B ecosystem. No external partner can talk to the microservices directly; they must pass through Kong.

### Roles of Kong:
- **Centralized Entry Point:** Consolidates multiple microservice endpoints into a single public URL.
- **Authentication (The `apilot-auth` Plugin):** Kong uses a custom Lua plugin to verify the `ED Signature` on every request. It asks the **Orchestrator** service: *"Is this partner valid and is this request signed correctly?"*
- **Reverse Proxy:** Forwards valid requests to the correct internal service based on the URL path (e.g., `/api/v1/product` -> `apilotto-product`).

---

## 2. Microservice Structure (Internal Actors)
The system is built on a "Decoupled" model where each service owns a specific business domain.

| Actor | Technology | Key Role |
| :--- | :--- | :--- |
| **Orchestrator Service** | Java (Spring) | **The Validator.** The source of truth for Partner configurations and session security. It validates requests forwarded by Kong. |
| **apilotto-api** | Go (fasthttp) | **The Dispatcher.** The main router for the Lottery domain. It takes high-level commands and coordinates between sub-services. |
| **apilotto-product** | Go | **The Game Engine.** Manages lottery types, betting periods (Open/Close), and prize results. |
| **apilotto-report** | Go | **The Analyst.** Processes massive amounts of raw bet data to produce Win/Loss and Turnover reports. |
| **apilotto-account** | Go | **The Identity Manager.** Manages BackOffice users, permissions, and account types (Agent vs Operator). |
| **Game-Hall-Service** | Java (Spring) | **The Portal.** Serves the actual gaming interface and handles the **Seamless Wallet** callbacks to the partner's system. |

---

## 3. Communication Protocol (How they talk)
The system uses a **Hybrid Protocol** model to balance compatibility with performance:

1.  **External (Public): REST / JSON**
    - Partners use standard HTTP tools to call the API.
    - *Why:* Maximum compatibility with partner systems (PHP, Python, Java, etc.).
2.  **Internal (Private): Protobuf over HTTP**
    - Microservices talk to each other using binary serialized data.
    - *Why:* Extremely fast, low CPU overhead, and strictly typed (prevents data errors).

---

## 4. The Request Lifecycle (Example: Placing a Bet)

1.  **Actor: Partner System** sends a `BetRequest` (JSON) to `api.rbth.com/apilot/bet`.
2.  **Actor: Kong Gateway** catches the request.
3.  **Actor: `apilot-auth` (Lua Plugin)** extracts the signature and calls the **Orchestrator**.
4.  **Actor: Orchestrator** confirms the signature is valid.
5.  **Actor: Kong** forwards the request to **apilotto-product**.
6.  **Actor: apilotto-product** records the bet in the database and updates Redis.
7.  **Actor: Response** flows back through Kong to the Partner.

---

## 5. Summary of Actor Responsibilities
- **Kong:** Gates the system and keeps it secure.
- **Orchestrator:** Makes the "Intelligence" decisions about who is allowed in.
- **Go Microservices:** Perform the heavy lifting of gambling logic and data crunching.
- **Partner:** Provides the players and the money (in Seamless mode).

## References
- `raw/repos/API/kong-custom-auth-plugin/apilot-auth/handler.lua`
- `raw/repos/API/orchestrator-service/src/main/resources/orchestrator.proto`
- `wiki/concepts/eday-api-system.md`
