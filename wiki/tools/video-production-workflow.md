---
title: "Quy trình sản xuất Video nhất quán"
source: "compiled"
date_added: 2026-04-25
tags: [workflow, video, ai]
status: draft
related:
  - "[[ai-storybook-video-tools]]"
  - "[[ai-lip-sync-technology]]"
  - "[[character-design-system]]"
summary: "Quy trình 4 bước để sản xuất video từ kịch bản với sự nhất quán về nhân vật và chất lượng hình ảnh."
---

## Tổng quan
Quy trình này được thiết kế để sản xuất video số lượng lớn (100+ video/tháng) mà vẫn đảm bảo nhân vật không bị biến đổi (face drift) và phong cách hình ảnh đồng nhất.

## Quy trình 4 bước (Modular Pipeline)

### Bước 1: Thiết kế & Khóa nhân vật (Character Design & Identity Lock)
Trước khi tạo video, cần có một bộ nhận diện nhân vật chuẩn.
- **Công cụ**: Leonardo AI (Character Reference) hoặc NeoLemon.
- **Sản phẩm**: Một bộ ảnh "Identity Anchor" gồm mặt trước, mặt nghiêng và các biểu cảm cơ bản.

### Bước 2: Tạo hoạt cảnh (Scene Generation)
Chuyển đổi các mô tả trong kịch bản thành các đoạn clip ngắn (3-10 giây).
- **Công cụ**: Runway Gen-3 Alpha, Luma Dream Machine hoặc Sora.
- **Kỹ thuật**: Sử dụng hình ảnh từ Bước 1 làm tham chiếu để AI giữ đúng nhân vật trong mọi cảnh quay.

### Bước 3: Lồng tiếng & Âm thanh (Audio Production)
- **Công cụ**: ElevenLabs (giọng đọc cảm xúc), Suno/Udio (nhạc nền).
- **Lưu ý**: Giọng đọc cần phù hợp với độ tuổi và tính cách nhân vật (ví dụ: Lily 5 tuổi, Leo 2-3 tuổi).

### Bước 4: Đồng bộ môi & Hậu kỳ (Lip Sync & Assembly)
- **Đồng bộ môi**: Sử dụng OpenArt hoặc Hedra để khớp khẩu hình nhân vật với file âm thanh từ Bước 3.
- **Biên tập**: Sử dụng CapCut hoặc Vizard để ghép các đoạn clip, thêm phụ đề, hiệu ứng chuyển cảnh và nhạc nền.

## Các biến thể quy trình
- **Quy trình Tự động (All-in-One)**: Dành cho sản xuất nhanh, sử dụng ReadKidz hoặc Katalist AI.
- **Quy trình Chuyên nghiệp (Modular)**: Dành cho chất lượng cao, thực hiện đủ 4 bước trên với các công cụ chuyên dụng nhất.
