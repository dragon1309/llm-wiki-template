---
title: "Platform Dashboard UI Deep Dive"
source: "compiled-from-code"
date_added: 2026-04-16
tags: [tool, ui, nextjs, deep-dive]
aliases: [Dashboard UI Deep Dive, Frontend Architecture]
status: canonical
related:
  - "[[platform-dashboard-ui]]"
  - "[[platform-dashboard-api-deep-dive]]"
summary: "Phân tích sâu về kiến trúc Frontend Next.js, cơ chế quản lý Session và tích hợp API của Platform Dashboard."
---

# Platform Dashboard UI Deep Dive

## 1. Kiến trúc Frontend (Next.js)
Ứng dụng được xây dựng theo mô hình **Modular Next.js Architecture** với TypeScript.

- **Pages Structure:**
    - `/login`: Giao diện đăng nhập, sử dụng `next-auth` để xử lý session.
    - `/index`: Trang chủ Dashboard, hiển thị bảng danh sách Platform (`PlatformTable`).
    - `/platform/*`: Các trang quản lý chi tiết từng platform.
    - `/web/*` & `/master/*`: Các trang báo cáo tổng hợp.
- **Components:** Các thành phần UI được tách nhỏ trong `/components` để tái sử dụng (như `Layout`, `LoadingScreen`, `SlickSlider`).

## 2. Quản lý Trạng thái & Session
- **NextAuth.js:** Được tích hợp để quản lý vòng đời đăng nhập. Token nhận từ Rails API sẽ được lưu trong session của NextAuth.
- **SWR & Apisauce:** 
    - `apisauce` được dùng làm wrapper cho `axios` để gọi API đồng bộ.
    - `SWR` (trong một số màn hình) giúp fetch dữ liệu và tự động revalidate khi người dùng quay lại tab.

## 3. Tích hợp Backend
Quy trình gọi API diễn ra như sau:
1. Client-side gọi hàm trong `apis/platform.ts`.
2. Hàm này lấy `access_token` từ session hiện hành.
3. Gửi request REST đến Rails Backend.
4. Kết quả trả về được map vào các `interfaces/` (TypeScript) để đảm bảo type-safety.

## 4. Setup Local
1. Di chuyển vào thư mục: `raw/repos/RBTH/centralize/platform-dashboard/`.
2. Cài đặt dependency: `yarn install` hoặc `npm install`.
3. Cấu hình môi trường: Tạo file `.env.local` với:
   ```env
   NEXT_PUBLIC_API_URL=http://localhost:3000
   NEXTAUTH_SECRET=your_secret
   ```
4. Chạy dev server: `npm run dev`.
5. Truy cập: `http://localhost:3000`.

## 5. Đánh giá Technical
- **Ưu điểm:** Code sạch, phân tách layer rõ ràng (API layer, Interface layer, Component layer). Sử dụng Tailwind CSS giúp giao diện gọn nhẹ.
- **Hạn chế:** Một số trang vẫn sử dụng logic fetch dữ liệu trực tiếp trong `useEffect`, có thể chuyển sang `getServerSideProps` để tối ưu SEO và tốc độ tải trang ban đầu.
