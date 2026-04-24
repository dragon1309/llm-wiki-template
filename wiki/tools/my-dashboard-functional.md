---
title: "MyDashboard Functional Specification"
source: "raw/articles/MyDashboard_Functional.md"
date_added: 2026-04-16
tags: [tool, functional, dashboard, kol, marketing]
aliases: [MyDashboard BO, KOL Monitoring System, Teacher Dashboard]
status: canonical
related:
  - "[[platform-dashboard-api]]"
  - "[[platform-dashboard-ui]]"
summary: "Tài liệu đặc tả chức năng của hệ thống MyDashboard, tập trung vào việc giám sát hiệu suất tuyển thành viên của KOL (Teachers) và Merchant."
---

# MyDashboard Functional Specification

## 1. Overview
**MyDashboard Back Office (BO)** là hệ thống giám sát và báo cáo dành riêng cho các **KOLs (Key Opinion Leaders)** — trong tài liệu còn gọi là **Teachers** — và các **Merchants**. Mục tiêu chính là cung cấp sự minh bạch về hiệu suất tuyển dụng thành viên mới (Member Acquisition).

## 2. Key Metrics & Monitoring
Hệ thống tập trung vào các chỉ số tăng trưởng thành viên theo thời gian thực (cập nhật mỗi **1 phút**):
- **Daily New Members:** Số lượng thành viên mới đăng ký trong ngày.
- **Weekly New Members:** Số lượng thành viên mới trong tuần.
- **Monthly New Members:** Số lượng thành viên mới trong tháng.
- **Referral Fees:** Tổng phí giới thiệu (hoa hồng) dành cho KOL.

## 3. Core Dashboards
### 3.1 Top 8 New Members
Bảng xếp hạng tất cả các Website (Merchants) dựa trên số lượng thành viên mới hàng ngày và hàng tháng.

### 3.2 Top 8 Teacher (Daily/Weekly)
Bảng xếp hạng các KOL/Teacher trên toàn hệ thống. Có hai chế độ xem:
- Theo ngày (Daily ranking).
- Theo tuần (Weekly ranking).

### 3.3 Top 10 by Websites (MH) Teacher
Bảng xếp hạng KOL thuộc về một Website cụ thể được chọn. Dashboard này hiển thị chi tiết cả **Referral Fee** của từng KOL.

## 4. UI/UX Features
- **Refresh Button:** Cập nhật thủ công danh sách.
- **Multi-open:** Cho phép mở tất cả các website đã chọn trong tab mới.
- **Action Columns:** Các nút thao tác nhanh để truy cập sâu vào từng website/dashboard.

## 5. Role in Ecosystem
MyDashboard đóng vai trò là "lớp hiển thị hiệu suất marketing" (Marketing Performance Layer). Nó có khả năng tiêu thụ dữ liệu từ các dịch vụ đồng bộ báo cáo của `platform-dashboard-api` để trình bày cho đối tượng người dùng là đối tác kinh doanh (Merchants) và người quảng bá (KOLs).

## References
- `raw/articles/MyDashboard_Functional.md`
