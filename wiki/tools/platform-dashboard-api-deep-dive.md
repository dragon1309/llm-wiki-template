---
title: "Platform Dashboard API Deep Dive"
source: "compiled-from-code"
date_added: 2026-04-16
tags: [tool, api, rails, deep-dive, security]
aliases: [Dashboard API Deep Dive, API Auth Mechanism]
status: canonical
related:
  - "[[platform-dashboard-api]]"
  - "[[platform-dashboard-ui-deep-dive]]"
summary: "Phân tích chi tiết kiến trúc API, cơ chế bảo mật JWT, các endpoint và quy trình setup local cho Platform Dashboard Backend."
---

# Platform Dashboard API Deep Dive

## 1. API Exposure & Structure
Hệ thống được thiết kế theo mô hình **Private API** phục vụ cho Dashboard nội bộ. 

- **Public Endpoints:** 
    - `POST /auth/login`: Xác thực người dùng và cấp Token.
    - `GET /api/v1/ping`: Kiểm tra trạng thái server (Health-check).
- **Private Endpoints (V1 Namespace):** Hầu hết các API còn lại đều nằm trong namespace `/api/v1/` và yêu cầu xác thực. Các nhóm chính bao gồm:
    - **User Management:** `/api/v1/users`, `/api/v1/user/my_profile`.
    - **Platform Management:** `/api/v1/platforms`, `/api/v1/platform/setting/:id`.
    - **Report & Sync:** `/api/v1/summary_web_report`, `/api/v1/summary_sync_master`. Đây là các API thực hiện tác vụ nặng, gọi sang các platform con.

## 2. Cơ chế Authentication (Security)
Backend sử dụng **JWT (JSON Web Token)** kết hợp với `bcrypt` để bảo mật.

- **Luồng xác thực:** 
    1. Client gửi `username`/`password` đến `/auth/login`.
    2. Server kiểm tra trong DB, nếu đúng sẽ gọi `jwt_encode` (trong `JsonWebToken` concern) để tạo token.
    3. Token chứa `user_id` và có thời hạn hết hạn.
- **Middleware:** `ApplicationController` sử dụng `before_action :authenticate_request` để chặn mọi request không có Header `Authorization: Bearer <token>`.
- **CORS:** Cấu hình qua `rack-cors` cho phép frontend (Next.js) truy cập từ các domain được chỉ định.

## 3. Quy trình Setup Local (Step-by-Step)

### Cách 1: Docker (Nhanh nhất)
1.  Sửa file `docker-compose.yml` tại `raw/repos/RBTH/centralize/platform-dashboard-api/`:
    - Thêm `build: .` vào service `app`.
    - Đảm bảo port `5432` của Postgres không bị trùng với project khác.
2.  Chạy lệnh: `docker compose up -d --build`.
3.  Khởi tạo database:
    ```bash
    docker compose exec app bundle exec rails db:create db:migrate
    ```

### Cách 2: Chạy trực tiếp (Manual)
1.  **Ruby:** Yêu cầu bản `3.0.1`.
2.  **Database:** Cấu hình `config/database.yml` trỏ về Postgres local.
3.  **Cài đặt:**
    ```bash
    bundle install
    rails db:create db:migrate
    ```
4.  **Khởi động:**
    - Server: `rails s -p 3000`
    - Worker (Sidekiq): `bundle exec sidekiq` (Yêu cầu Redis đang chạy).

## 4. Các điểm cần lưu ý
- **Sidekiq Web UI:** Có thể truy cập tại `/admin/sidekiq` để quản lý các task đồng bộ dữ liệu chạy ngầm.
- **Hstore:** Postgres cần extension `hstore` để lưu cột `settings`.
- **Master Key:** Cần file `config/master.key` để giải mã credentials nếu chạy ở môi trường staging/production.
