---
title: "KKCash Lotto Products"
source: "compiled"
date_added: 2026-04-15
tags: [tool, products, lotto, gambling]
aliases: [Lotto Catalog, KKCash Games]
status: draft
related:
  - "[[kkcash-system-architecture]]"
summary: "Danh mục các sản phẩm xổ số (Lotto) được hỗ trợ trên hệ thống KKCash, bao gồm Xổ số Thái Lan, Lào, Việt Nam và các loại xổ số tự chọn."
---

# KKCash Lotto Products

## Overview
**KKCash Lotto Products** là danh mục các loại hình xổ số và trò chơi dự đoán kết quả được tích hợp trong hệ thống KKCash. Các sản phẩm này đa dạng về nguồn gốc (quốc gia), tần suất mở thưởng (hàng ngày, hàng tuần, hàng tháng) và cơ chế trả thưởng tự động (Auto Pay).

## Primary Product Categories

### 1. National Lotto (Xổ số quốc gia)
Đây là các loại hình xổ số dựa trên kết quả chính thức của các quốc gia trong khu vực:
- **Thai Lotto (หวยไทย):** Xổ số chính thống Thái Lan, mở thưởng vào ngày 1 và 16 hàng tháng. Thời gian đóng cổng đặt cược thường là 15:30.
- **Lao Lotto (หวยลาว):** Mở thưởng vào thứ Hai và thứ Năm hàng tuần. Đóng cổng lúc 20:10.
- **Hanoi Lotto (หวยฮานอย):** Xổ số Việt Nam, mở thưởng hàng ngày vào lúc 18:00.
- **Malaysia Magnum:** Mở thưởng vào thứ Tư, thứ Bảy và Chủ Nhật.

### 2. Custom & High-Frequency Lotto
Các loại hình xổ số do hệ thống tự vận hành hoặc có tần suất mở thưởng cực cao:
- **YeeKee (จับยี่กี):** Loại hình xổ số phổ biến tại Thái Lan với tần suất mở thưởng nhiều lần trong ngày (thường là 88-96 vòng/ngày).
- **Stock Lotto:** Dựa trên chỉ số đóng cửa của các thị trường chứng khoán (SET, Nikkei, Hang Seng...).

## Key Configuration Attributes
Mỗi sản phẩm trong hệ thống được định nghĩa qua các thông số kỹ thuật (dựa trên bảng `kkcash_product`):
- **Product Code:** Mã định danh duy nhất (ví dụ: `TH`, `LA`, `VN`, `YK`).
- **Affiliate Rate:** Tỷ lệ hoa hồng mặc định cho các đại lý đối với từng loại sản phẩm.
- **Period Logic:** Cấu hình JSON (`period_ex`) định nghĩa ngày mở thưởng (`dow`), thời gian bắt đầu (`startTime`), kết thúc (`endTime`) và thời gian trả thưởng (`rewardTime`).
- **Auto Pay:** Cấu hình cho phép hệ thống tự động tính toán và trả thưởng ngay sau khi có kết quả.

## Advantages & Limitations
### Advantages
- **Đa dạng:** Hỗ trợ hầu hết các loại hình xổ số phổ biến tại Đông Nam Á.
- **Tự động hóa:** Tích hợp sâu với `SummaryService` để tự động trả thưởng và tính hoa hồng.
- **Tùy biến:** Cho phép cấu hình linh hoạt thời gian đóng/mở cổng theo từng nền tảng whitelabel.

### Limitations
- **Phụ thuộc nguồn kết quả:** Các loại xổ số quốc gia phụ thuộc vào tính minh bạch và thời gian công bố của đơn vị phát hành gốc.

## References
- `raw/repos/kkcash-product-row-1.md` (Thai Lotto)
- `raw/repos/kkcash-product-row-2.md` (Lao Lotto)
- `raw/repos/kkcash-product-row-3.md` (Hanoi Lotto)
- `raw/repos/kkcash-product-row-4.md` (Malaysia Magnum)
