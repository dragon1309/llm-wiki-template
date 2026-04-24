---
title: "Seamless Wallet Flow"
source: "raw/repos/API/game-hall-service/src/main/java/com/kkworld/apilot/oper/lottoapiserver/service/seamless/SingleWalletService.java"
date_added: 2026-04-17
tags: [concept, architecture, fintech, api, b2b]
aliases: [Single Wallet, Seamless Wallet, Partner Callback]
status: canonical
related:
  - "[[eday-api-system]]"
summary: "The technical callback mechanism allowing external partners to maintain player balances while integrating RBTH game products."
---

# Seamless Wallet Flow

## Definition
The **Seamless Wallet** (or **Single Wallet**) flow is a B2B integration model where the **Partner (Operator)** remains the single source of truth for player balances. The RBTH system communicates via real-time callbacks to verify funds and process transactions.

## Architecture
- **Service Hub:** `game-hall-service` (Java/Spring)
- **Primary Logic:** `SingleWalletService.java`
- **Data Persistence:** `TransactionSeamlessWallet` (local log of external calls)

## Callback Lifecycle

### 1. Balance Check (`GET /edApi/GetPlayerBalance/{player}`)
- **Purpose:** Display accurate user funds in the GameHall.
- **Trigger:** Game load or manual refresh.
- **Timeout:** 10s (`RestTemplate` default in `SingleWalletService`).

### 2. Bet Request (`POST /edApi/BetRequest`)
- **Purpose:** Deduct funds when a user places a bet.
- **Action:** RBTH sends Bill ID, Amount, and Player ID.
- **Validation:** If the partner returns success, the bet is finalized in the RBTH `LottoBill` table.

### 3. Settlement / Award (`POST /edApi/RoundUpdate`)
- **Purpose:** Credit winnings to the partner's wallet.
- **Logic:** Executed asynchronously after a lottery period is closed and prizes are calculated.
- **Tracking:** `CallbackRequestTrack` table ensures that if the partner's server is down, the prize isn't "lost"—it can be retried.

### 4. Cancellation/Void (`POST /edApi/BetRequest` with Cancel Flag)
- **Purpose:** Refund money if a bet is cancelled by the user or the period is voided.

## Security & Auth (`ED Signature`)
All callbacks are secured via an **Authorization** header:
`Authorization: ED {oper_code}:{signature}`

- **Signature Generation:** `Base64(HMAC-SHA1(secret_key, verb + contentMD5 + contentType + path))`
- **Secret Key:** Shared between RBTH and the Partner during onboarding.

## Error Handling & Retries
- **Persistence:** Failed callbacks are logged in the `CallbackLog` table.
- **Async Execution:** Most callbacks use `@Async` and `CompletableFuture` to prevent blocking the core engine.
- **Timeout Policy:** Fixed 10s timeout for all partner communication.

## References
- `raw/repos/API/game-hall-service/src/main/java/com/kkworld/apilot/oper/lottoapiserver/service/seamless/SingleWalletService.java`
- `raw/repos/API/orchestrator-service/src/main/resources/orchestrator.proto`
- `raw/repos/API/game-hall-service/src/main/java/com/kkworld/apilot/oper/lottoapiserver/service/FinanceService.java`
