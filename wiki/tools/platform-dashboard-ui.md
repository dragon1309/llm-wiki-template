---
title: "Platform Dashboard UI"
source: "raw/repos/RBTH/centralize/platform-dashboard"
date_added: 2026-04-16
tags: [tool, ui, nextjs, dashboard]
aliases: [Platform Dashboard Frontend, Dashboard NextJS]
status: canonical
related:
  - "[[platform-dashboard-api]]"
summary: "Giao diện quản trị Dashboard hiện đại được xây dựng bằng Next.js và Tailwind CSS, cung cấp cái nhìn tổng quan về các platform."
---

# Platform Dashboard UI

## Overview
**Platform Dashboard UI** là ứng dụng frontend dành cho hệ thống quản lý platform tập trung. Được xây dựng dựa trên framework **Next.js 12** và ngôn ngữ **TypeScript**, công cụ này cung cấp một trải nghiệm người dùng mượt mà, đáp ứng (responsive) và hiệu quả cho các quản trị viên hệ thống.

## Role In Context
Đây là điểm tiếp xúc chính (Main Interface) của người dùng với hệ thống Dashboard. Nó kết nối trực tiếp với **Platform Dashboard API** (Rails) để hiển thị các báo cáo, quản lý cài đặt platform và cấu hình tài khoản người dùng.

## Technical Specifications
- **Framework:** Next.js 12.2.5 (React 18).
- **Language:** TypeScript 4.8.
- **Styling:** Tailwind CSS 3.1, PostCSS.
- **Data Fetching:** SWR (cho real-time updates) và Apisauce.
- **State/Form Management:** React Hook Form.
- **UI Components:** 
  - Headless UI, Heroicons, FontAwesome.
  - MUI Datatables (cho các bảng dữ liệu phức tạp).
  - React Slick (carousels/sliders).
  - SweetAlert2 & React Toastify (thông báo người dùng).

## Key Features
### 1. Dashboard Visualization
- Hiển thị các chỉ số kinh doanh tổng quát từ nhiều platform.
- Các bảng dữ liệu (Datatables) hỗ trợ lọc, tìm kiếm và phân trang.
- Tích hợp các thành phần biểu đồ và sliders để theo dõi hiệu suất.

### 2. Platform Administration
- Giao diện quản lý danh sách Platform (Thêm/Sửa/Xóa).
- Cấu hình các thông số kỹ thuật và giao diện (Color, Order, Settings) cho từng platform.
- Upload và hiển thị tài nguyên hình ảnh (Logo, Banner).

### 3. User Management Interface
- Giao diện quản lý tài khoản quản trị viên.
- Phân quyền người dùng vào các platform cụ thể thông qua UI trực quan.

## Advantages / Limitations
- **Advantages:** 
  - Hiệu suất cao nhờ cơ chế Server-Side Rendering (SSR) và Static Generation của Next.js.
  - Giao diện hiện đại, dễ bảo trì với Tailwind CSS.
  - Trải nghiệm người dùng tốt (UX) với các thông báo và hiệu ứng chuyển cảnh mượt mà.
- **Limitations:** 
  - Yêu cầu môi trường Node.js để vận hành.
  - Phụ thuộc chặt chẽ vào cấu trúc dữ liệu trả về từ Rails API.

## References
- `raw/repos/RBTH/centralize/platform-dashboard/package.json`
- `raw/repos/RBTH/centralize/platform-dashboard/README.md`
- `raw/repos/RBTH/centralize/platform-dashboard/next.config.js`
