---
title: "Admin Central Core"
source: "raw/repos/RBTH"
date_added: 2026-04-15
tags: [concept, architecture, management, backend]
aliases: [Admin Central, Centralize Core]
status: draft
related:
  - "[[kkcash-system-architecture]]"
summary: "Hệ thống quản trị trung tâm đa nền tảng, quản lý đối tác và tích hợp dịch vụ (Go & Next.js)."
---

# Admin Central Core

## Definition
**Admin Central** là một hệ thống quản lý trung tâm (Centralized Management System) được thiết kế để điều hành đồng thời nhiều nền tảng (Platforms) và đối tác (Partners). Nó đóng vai trò như một lớp quản trị cấp cao, cho phép giám sát các hoạt động kinh doanh, quản lý danh sách đen (Blacklist), và theo dõi doanh thu thông qua các báo cáo hóa đơn (Invoice).

## Architecture & Logic
Hệ thống này được tách biệt khỏi các cụm server vận hành trực tiếp (như KKCash) để đảm bảo tính độc lập và khả năng mở rộng cho nhiều đối tác khác nhau.

### 1. Admin-Central-Server (Go Backend)
Phát triển bằng ngôn ngữ **Go** (Golang), tập trung vào hiệu suất và khả năng mở rộng.
- **Trách nhiệm:** Cung cấp API quản trị trung tâm, quản lý xác thực đối tác, theo dõi lịch sử truy cập menu, và xử lý các nghiệp vụ liên quan đến Platform/Product.
- **Cấu trúc:** Sử dụng kiến trúc domain-driven với các thành phần:
  - `domains/`: Chứa các logic nghiệp vụ cụ thể như `bank`, `blacklist`, `client`, `invoice`, `partner`, `platform`, `product`, `user`.
  - `routers/`: Định nghĩa các endpoint API tương ứng với từng domain.
  - `models/`: Định nghĩa cấu trúc dữ liệu GORM cho PostgreSQL.

### 2. Admin-Central-UI (React Frontend)
Ứng dụng web dành cho cấp quản lý, phát triển bằng **Next.js** (React).
- **Tính năng:** Cung cấp bảng điều khiển (Dashboard) để theo dõi tổng thể, quản lý cấu hình các nền tảng con, và tra cứu dữ liệu từ Central Server.

## Key Domains
- **Partner & Platform:** Quản lý mối quan hệ với các đối tác và các nền tảng con mà họ vận hành.
- **Blacklist Management:** Duy trì danh sách đen người dùng hoặc tài khoản bị hạn chế trên toàn bộ hệ thống.
- **Invoice & Product:** Theo dõi và quản lý doanh thu, danh mục sản phẩm của từng nền tảng.
- **Menu Usage History:** Ghi nhận lịch sử thao tác của các quản trị viên để đảm bảo tính minh bạch và an ninh.

## Technical Stack
- **Backend:** Go 1.22+, GORM (ORM), Air (Hot reload).
- **Frontend:** Next.js, React, Yarn.
- **Database:** PostgreSQL (lưu trữ dữ liệu trung tâm, yêu cầu `hstore` extension).
- **Deployment:** Hỗ trợ Docker (đa nền tảng amd64/arm64) và CI/CD tự động.

## References
- `raw/repos/RBTH/centralize/admin-central-server/`
- `raw/repos/RBTH/centralize/admin-central-server-ui/`
- `raw/repos/RBTH/docker-compose.yml`
