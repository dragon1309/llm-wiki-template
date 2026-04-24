---
title: "KKCash System Architecture"
source: "raw/repos/RBTH"
date_added: 2026-04-15
tags: [concept, architecture, fintech, gambling]
aliases: [KKCash, Cash Server Architecture]
status: draft
related:
  - "[[admin-central-core]]"
summary: "Kiến trúc hệ thống quản lý tiền mặt và giao dịch cá cược đa nền tảng dựa trên Grails và Angular."
---

# KKCash System Architecture

## Definition
**KKCash** là một hệ thống quản lý giao dịch tài chính và vận hành nền tảng cá cược, được thiết kế theo mô hình client-server với các thành phần chuyên biệt cho quản trị viên (Admin) và người dùng cuối (Member). Hệ thống tập trung vào việc xử lý các luồng nạp/rút tiền, quản lý đại lý (Affiliate), và tích hợp các loại hình giải trí như Lotto, Minigame, và Sportbook.

## Architecture & Components
Hệ thống KKCash bao gồm ba thành phần chính hoạt động phối hợp:

### 1. KK-Cash-Server (Backend)
Đóng vai trò là trung tâm xử lý logic (Core Engine), được xây dựng trên framework **Grails** (chạy trên JVM 17).
- **Trách nhiệm:** Quản lý cơ sở dữ liệu, xác thực người dùng, xử lý giao dịch tài chính, tính toán hoa hồng đại lý, và cung cấp API cho các frontend.
- **Cấu trúc:** Sử dụng kiến trúc MVC của Grails với các Domain Classes cho mô hình dữ liệu (User, Wallet, BankAccount) và Services cho logic nghiệp vụ phức tạp.

### 2. Admin-GUI (Quản trị)
Ứng dụng web dành cho nhân viên vận hành và quản trị viên, phát triển bằng **Angular**.
- **Tính năng:** Quản lý danh sách thành viên, phê duyệt giao dịch nạp/rút, cấu hình khuyến mãi (Promotion), xem báo cáo (Report), và quản lý nội dung web (Content Management).

### 3. User-GUI (Người dùng)
Giao diện dành cho người chơi, cũng được phát triển bằng **Angular** (phiên bản 9/10).
- **Tính năng:** Đăng ký/Đăng nhập, thực hiện giao dịch nạp/rút tiền, tham gia các trò chơi (Lotto, YeeKee, Sportbook), và theo dõi lịch sử ví (Wallet).

## Technical Stack
- **Backend:** Grails 4/5, Groovy, Gradle.
- **Frontend:** Angular, TypeScript, Yarn.
- **Database:** MariaDB (lưu trữ dữ liệu nghiệp vụ chính).
- **Infrastructure:** Docker Compose để điều phối các dịch vụ, hỗ trợ môi trường phát triển và triển khai đồng nhất.

## Key Mechanisms
- **Wallet System:** Quản lý số dư người dùng qua nhiều loại ví (Main Wallet, Game Wallet).
- **Banking Integration:** Hỗ trợ quản lý nhiều tài khoản ngân hàng (Company Bank Accounts) để nhận tiền nạp và thực hiện rút tiền.
- **Affiliate Management:** Hệ thống phân cấp đại lý với tính năng tính toán hoa hồng dựa trên doanh thu hoặc lợi nhuận.

## References
- `raw/repos/RBTH/docker-compose.yml`
- `raw/repos/RBTH/cash/kk-cash-server/`
- `raw/repos/RBTH/cash/admin-gui/`
- `raw/repos/RBTH/cash/user-gui/`
