---
title: "Platform Dashboard API"
source: "raw/repos/RBTH/centralize/platform-dashboard-api"
date_added: 2026-04-16
tags: [tool, api, rails, dashboard]
aliases: [Dashboard API Rails, Platform API]
status: canonical
related:
  - "[[platform-dashboard-ui]]"
  - "[[platform-dashboard-api-workflow]]"
summary: "Backend API phục vụ Platform Dashboard, được xây dựng trên Ruby on Rails với các tính năng quản lý platform, user và đồng bộ báo cáo."
---

# Platform Dashboard API

## Overview
**Platform Dashboard API** là dịch vụ backend trung tâm dành cho hệ thống Dashboard quản lý nhiều nền tảng (platforms). Được xây dựng bằng framework **Ruby on Rails 7**, hệ thống này cung cấp các API RESTful để quản lý danh sách platform, phân quyền người dùng và tổng hợp các báo cáo kinh doanh từ các nguồn dữ liệu khác nhau.

## Role In Context
Trong hệ sinh thái **RBTH**, công cụ này đóng vai trò là lớp xử lý dữ liệu (Data Processing Layer) cho giao diện người dùng Dashboard. Nó thực hiện các tác vụ nặng như đồng bộ hóa dữ liệu (Synchronization) và tính toán báo cáo thông qua các background jobs.

## Technical Specifications
- **Framework:** Ruby on Rails 7.0.3.1 (Ruby 3.0.1).
- **Database:** PostgreSQL (Active Record).
- **Background Processing:** Sidekiq (với Sidekiq-Cron để lập lịch tác vụ).
- **Authentication:** JWT (JSON Web Token).
- **Deployment:** Capistrano (hỗ trợ rbenv, passenger, sidekiq).
- **Communication:** REST Client để tương tác với các dịch vụ bên ngoài.

## Key Features
### 1. Platform Management
- Quản lý thông tin chi tiết các platform (Name, Code, Settings).
- Hỗ trợ đính kèm Logo, Banner thông qua **Active Storage** (với xử lý ảnh `image_processing`).
- Hệ thống phân loại platform (Web Platforms, Master Platforms).

### 2. User & Authorization
- Quản lý người dùng và phân quyền truy cập theo từng platform cụ thể.
- Chức năng đổi mật khẩu, kích hoạt/vô hiệu hóa tài khoản.
- Profile management cho người dùng hiện hành.

### 3. Report & Synchronization
- **Endpoints:** 
  - `summary_web_report`: Báo cáo tổng hợp cho phía Web.
  - `summary_master_report`: Báo cáo tổng hợp cho phía Master.
- **Sync Logic:** Hỗ trợ các tác vụ `sync_master` và `sync_web` (có thể lọc theo code hoặc thời gian) để đồng bộ dữ liệu từ các server con.
- **Sidekiq Web UI:** Giao diện giám sát các tiến trình chạy ngầm tại `/admin/sidekiq`.

## Advantages / Limitations
- **Advantages:** 
  - Khả năng mở rộng tốt nhờ Sidekiq xử lý bất đồng bộ.
  - Cấu trúc API rõ ràng, dễ tích hợp với các frontend hiện đại (Next.js).
  - Quy trình triển khai (Deployment) tự động hóa cao.
- **Limitations:** 
  - Phụ thuộc vào Redis để vận hành Sidekiq.
  - Yêu cầu cấu hình Ruby/Rails môi trường sản xuất khá phức tạp (Passenger/Nginx).

## References
- `raw/repos/RBTH/centralize/platform-dashboard-api/config/routes.rb`
- `raw/repos/RBTH/centralize/platform-dashboard-api/Gemfile`
- `raw/repos/RBTH/centralize/platform-dashboard-api/README.md`
