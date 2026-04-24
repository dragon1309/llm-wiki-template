---
title: "EDay API System"
source: "raw/papers/api-backend-documentation-v1-2.md"
date_added: 2026-04-15
tags: [concept, architecture, b2b, microservices]
aliases: [API Project, EDay API, Whitelabel API]
status: draft
related:
  - "[[kkcash-system-architecture]]"
  - "[[admin-central-core]]"
summary: "Hệ thống B2B hỗ trợ các nền tảng whitelabel, nâng cấp từ mô hình Cash market sang mô hình cung cấp dịch vụ Lotto/Game qua API."
---

# EDay API System

## Definition
**EDay API System** (gọi tắt là dự án "API") là một nền tảng B2B được phát triển để nâng cấp các sản phẩm Lotto từ mô hình phục vụ thị trường tiền mặt (Cash market) sang mô hình hỗ trợ các nền tảng **Whitelabel**. Hệ thống cho phép các đối tác bên thứ ba tích hợp các sản phẩm giải trí của EDay thông qua giao thức API (Transfer hoặc Seamless).

## Architecture & Infrastructure

### 1. API Gateway (Kong)
Hệ thống sử dụng **Kong** làm API Gateway tập trung để quản lý và điều phối tất cả các yêu cầu gửi đến hệ thống. Kong chịu trách nhiệm định tuyến (routing) và bảo mật cho các dịch vụ phía sau.

### 2. Microservices (Company BO Namespace)
Hệ thống được chia nhỏ thành các microservices chuyên biệt để quản lý BackOffice (BO):
- **api:** Định nghĩa endpoint và đóng vai trò router chính cho các dịch vụ BO.
- **product:** Quản lý thông tin sản phẩm, chu kỳ (periods) và xử lý kết quả.
- **report:** Xử lý các yêu cầu báo cáo (Win/Loss, vé người chơi, báo cáo tổng hợp).
- **authenticate & login:** Quản lý phiên làm việc, xác thực JWT, 2FA và mật khẩu.
- **accounts:** Xử lý các thao tác CRUD cho tài khoản người dùng BO.
- **gameconfig:** Cấu hình game (Dynamic Rate Limit, Reward Package, Risk Number).
- **audit:** Ghi nhật ký hoạt động (Login Logs, Action Logs).
- **orchestrator:** Cổng kết nối cho GameHall, thực hiện xác thực IP whitelist và session validation.

### 3. GameHall Architecture
- **Frontend:** Truy cập qua domain dạng `{oper_code}.{edaygh-domain}.com`.
- **Backend:** Mỗi Operator chạy như một dịch vụ riêng biệt trong namespace GameHall, hỗ trợ phiên bản ứng dụng khác nhau và loại hình API (Transfer/Seamless) riêng.

## User Groups (BackOffice)
Hệ thống phục vụ ba nhóm người dùng chính với quyền hạn khác nhau:
1. **Company Users:** Chủ sở hữu sản phẩm, có quyền hạn cao nhất toàn hệ thống.
2. **Agent Users:** Quản lý việc mở tài khoản cho Operator, xem báo cáo cấp đại lý.
3. **Operator Users:** Quản lý người chơi trực tiếp và vận hành các hoạt động hàng ngày.

## Connections to Existing Systems
- **KKCash Integration:** EDay API là bước tiến hóa từ mô hình Cash truyền thống (KKCash) sang mô hình cung cấp API cho các đối tác lớn.
- **Centralized Management:** Tương tự như `admin-central-core`, EDay API quản lý nhiều đối tác whitelabel nhưng ở mức độ tích hợp kỹ thuật sâu hơn qua API Gateway.

## System Data Flow (The "Big Picture")
1.  **User Activity:** A player bets on a site powered by **Whitelabel (EDay API)**.
2.  **Transaction Recording:** The local database (MariaDB/PostgreSQL) records the bet in real-time.
3.  **Synchronization:** Every X minutes, the **Platform Dashboard API** triggers a "Sync Job" to pull turnover data.
4.  **Aggregation:** Data from all sub-platforms is normalized and saved into the **Dashboard DB**.
5.  **Reporting:** Management monitors total Win/Loss across the entire RBTH empire via the Dashboard UI.

## Analysis: Consensus & Contradictions

### 🤝 5 Most Significant Points of Consensus
1.  **Microservices Architecture:** Every source confirms a decoupled microservices model.
    - *Citation:* "Hệ thống EDay API được xây dựng trên kiến trúc microservices với hai nhóm dịch vụ chính: BackOffice Services (Go) và GUI Services (Angular)." (`wiki/tools/eday-api-microservices.md`).
2.  **Dual Wallet Integration:** Consensus on supporting two primary B2B integration modes.
    - *Citation:* "enum SystemApiType { TRANSFER_WALLET=0; SINGLE_WALLET=1; }" (`orchestrator.proto`).
3.  **Kong Gateway:** All references identify Kong as the centralized security perimeter.
    - *Citation:* "Hệ thống sử dụng Kong làm API Gateway tập trung..." (`wiki/concepts/eday-api-system.md`).
4.  **MariaDB for Transactions:** Consensus that transactional engines rely on MariaDB/MySQL.
    - *Citation:* "spring.datasource.url=jdbc:mariadb://localhost:3306/system_operator" (`game-hall-service/application.properties`).
5.  **Whitelabel Business Model:** Designed exclusively for third-party partners.
    - *Citation:* "Nền tảng B2B được phát triển để nâng cấp... sang mô hình whitelabel." (`wiki/concepts/eday-api-system.md`).

### ⚠️ Major Contradictions & Conflict Analysis
#### 1. Primary Backend Language
- **Claim A (Go Focus):** "Phần lớn các dịch vụ backend được viết bằng Go..." (`wiki/tools/eday-api-microservices.md`).
- **Claim B (Java Core):** The critical `orchestrator-service` and `game-hall-service` are built in Java (`orchestrator-service/build.gradle`).
- **Explanation:** **Contextual Focus.** Most services (Product, Account, Report) are Go-based, but the core integration gateway remains Java, likely for library compatibility.

#### 2. Service Communication Protocol
- **Claim A (RESTful):** "...cung cấp các API RESTful để quản lý danh sách platform..." (`wiki/tools/platform-dashboard-api.md`).
- **Claim B (Protobuf/Binary):** "err = proto.Unmarshal(ctx.Request.Body(), req)" (`apilotto-product/product_service.go`).
- **Explanation:** **Internal vs. External Context.** REST/JSON is used for external interfaces, while Protobuf-over-HTTP is used for internal service-to-service calls.

#### 3. Project Identity/Naming
- **Claim A (EDay API):** "EDay API System... là một nền tảng B2B..." (`wiki/concepts/eday-api-system.md`).
- **Claim B (A-Pilot):** "aws eks update-kubeconfig... --name a-pilot-dev-test" (`apilotto-workspace/README.MD`).
- **Explanation:** **Commercial vs. Technical Naming.** EDay API is the product name; A-Pilot is the technical codename for infrastructure/K8s.

## Source Gaps & Research Needs
- **Partner Onboarding:** Missing documentation on the manual process for issuing `secret_key`s to operators.
- **Idempotency Logic:** Unclear how the system prevents double-deductions during network timeouts in Seamless mode.
- **Data Lake:** The `DatalakeApi` is a "black box" with no source code in the repository.

## References
- `raw/repos/API/` (Microservices root)
- `raw/repos/API/orchestrator-service/src/main/resources/orchestrator.proto`
- `raw/repos/RBTH/centralize/platform-dashboard-api/`
