---
title: "User-GUI Architecture Analysis & Refactoring Roadmap"
source: "compiled-from-chat"
date_added: 2026-04-16
tags: [concept, architecture, refactoring, user-gui, angular]
aliases: [User-GUI Analysis, UI Refactoring]
status: canonical
related:
  - "[[kkcash-system-architecture]]"
summary: "Phân tích chuyên sâu về kiến trúc Multi-Tenant hiện tại của user-gui (245+ tenants) và lộ trình chuyển đổi sang kiến trúc Headless/Config-driven để tối ưu hóa bảo trì và mở rộng."
---

# User-GUI Architecture Analysis

## 1. Hiện trạng Kiến trúc (Multi-Tenant Monorepo)
Hệ thống `user-gui` hiện đang quản lý hơn 245 môi trường (brands/platforms) khác nhau bằng mô hình **Environment-based Overrides**. 

### Điểm mạnh (Strengths)
- **Khả năng tùy biến cực cao:** Mỗi đối tác có thể có giao diện HTML/CSS riêng biệt mà không ảnh hưởng đến logic của đối tác khác.
- **Cô lập tài nguyên:** Logo, banner và cấu hình được phân tách rõ ràng theo từng folder environment.
- **Tính ổn định cục bộ:** Lỗi giao diện ở một brand không gây sập hệ thống cho các brand khác.

### Điểm yếu (Weaknesses)
- **Vi phạm nguyên tắc DRY (Don't Repeat Yourself):** Tồn tại hơn 240 bản sao của các file core như `login.component.html` và `main.component.html`.
- **Nợ kỹ thuật (Technical Debt):** Sử dụng các pattern cũ, hardcode text tiếng Thái, gây khó khăn cho việc quốc tế hóa (i18n).
- **Hiệu suất Build:** Số lượng file khổng lồ làm chậm quá trình biên dịch và CI/CD.
- **Khó bảo trì:** Việc cập nhật một tính năng chung yêu cầu chỉnh sửa thủ công hàng trăm file.

---

## 2. Lộ trình Tái cấu trúc (Refactoring Roadmap)

### Giai đoạn 1: Chuyển đổi sang CSS Variables & Design System
- Thay thế toàn bộ hex code cứng trong các file `.scss` bằng các biến CSS (Custom Properties).
- Xây dựng một bảng màu (Color Palette) trung tâm có khả năng ghi đè theo từng tenant.

### Giai đoạn 2: Headless/Config-Driven Components
- Hợp nhất 240+ file HTML thành **5-10 Master Layouts** chuẩn.
- Sử dụng file cấu hình JSON (`config.json`) để quyết định:
    - Layout nào sẽ được sử dụng.
    - Hiển thị/ẩn các tính năng (Toggle Features).
    - Các asset URL (Logo, Icon).

### Giai đoạn 3: Hiện đại hóa Internationalization (i18n)
- Sử dụng dữ liệu trích xuất từ các công cụ scan (như `thai_text_extraction.csv`) để tạo file ngôn ngữ tập trung.
- Thay thế static text bằng `translate` pipe của Angular.

### Giai đoạn 4: Thư viện hóa (Nx/Angular Workspace)
- Tách logic nghiệp vụ (Auth, API Service) vào các thư viện dùng chung (Libraries).
- Các App Tenant chỉ chứa phần branding và cấu hình nhẹ.

---

## 3. Kết luận
Việc chuyển đổi từ mô hình "Copy-Paste HTML" sang "Data-Driven UI" sẽ giúp giảm **90% lượng code dư thừa**, tăng tốc độ phát triển tính năng mới gấp **10 lần** và sẵn sàng cho việc mở rộng ra các thị trường quốc tế.
