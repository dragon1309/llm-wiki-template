---
title: "EDay API Microservices"
source: "raw/repos/API/"
date_added: 2026-04-15
tags: [tool, microservices, architecture, go, angular]
aliases: [API Services, EDay Services]
status: canonical
related:
  - "[[eday-api-system]]"
  - "[[kong-gateway-microservices]]"
summary: "Detailed inventory and roles of microservices within the EDay API (Project API) ecosystem."
---

# EDay API Microservices

## Overview
The **EDay API** system is built on a high-performance microservices architecture. It is divided into two primary groups: **BackOffice Services** (developed in Go for speed) and **GUI Services** (developed in Angular for rich user interaction). These services communicate via a secured Kong API Gateway.

## Core Microservices (Go/Java)
Most backend services follow a standardized Go project structure (`cmd/`, `configs/`, `models/`, `repositories/`, `routers/`, `services/`).

| Service | Technology | Role & Responsibility |
| :--- | :--- | :--- |
| **`apilotto-api`** | Go (fasthttp) | **Master Router.** Aggregates BackOffice (BO) requests and routes them to sub-services. |
| **`apilotto-product`** | Go (gRPC/HTTP) | **Game Engine.** Manages lottery types, betting periods, and result processing. |
| **`apilotto-report`** | Go | **Analytics Engine.** Calculates Win/Loss, turnover, and generates player bills. |
| **`apilotto-gameconfig`**| Go | **Risk Manager.** Manages rate limits, reward packages, and risk numbers. |
| **`apilotto-account`** | Go | **Identity Manager.** Handles BO user CRUD, password recovery, and email verification. |
| **`apilotto-audit`** | Go | **Audit Trail.** Records all user actions and system changes for compliance. |
| **`orchestrator-service`**| Java (Spring) | **B2B Gateway.** Orchestrates partner connections and handles request signature validation. |
| **`game-hall-service`** | Java (Spring) | **Operator Portal.** Direct integration point for specific partners; handles Seamless Wallet callbacks. |

## Frontend & Demo (Angular)
| GUI Service | Target User | Description |
|-------------|-----------------|-------|
| **`a-pilot-bo-gui`** | System Admins | Global management interface for the entire B2B ecosystem. |
| **`a-pilot-player-gui`**| Players | The "GameHall" interface where users interact with lottery products. |
| **`a-pilot-demo`** | Developers | Integration sandbox for testing API features and flows. |

## Technical Implementation Patterns
- **High Concurrency:** Go services utilize `fasthttp` and Goroutines to handle high-frequency betting traffic.
- **Strict Typing:** Internal communication uses **Protobuf-over-HTTP** to ensure data integrity across Go and Java services.
- **Containerization:** Every service is fully Dockerized with a localized `Makefile` for standardized CI/CD workflows.

## Developer Quick-Start
- **Game Logic:** See `raw/repos/API/apilotto-product/services/product_service.go`.
- **API Surface:** Check `raw/repos/API/apilotto-api/routers/router_bo.go`.
- **B2B Contract:** Read `raw/repos/API/orchestrator-service/src/main/resources/orchestrator.proto`.

## References
- `raw/repos/API/` (Microservices root)
- `wiki/concepts/eday-api-system.md`
- `wiki/concepts/kong-gateway-microservices.md`
- `wiki/concepts/seamless-wallet-flow.md`
