# 🪵 Operations Log

> Chronological record of all automated wiki operations.

---

## [2026-04-14] update | Nâng cấp hệ thống Aliases
- **Cập nhật:** Bổ sung trường `aliases` vào Frontmatter cho toàn bộ 12 bài viết chính để tối ưu hóa khả năng tìm kiếm và gợi ý liên kết.
- **Cập nhật:** `_index.md` (Cập nhật cột Aliases tương ứng cho tất cả các bài viết).
- **Cấu trúc:** Thêm Frontmatter chuẩn cho [[character-design-system]].

## [2026-04-14] index | Xây dựng chỉ mục backlinks (Backlinks Index)
- **Tạo mới:** `_backlinks.json` chứa bản đồ ngược của toàn bộ liên kết giữa các bài viết.
- **Thống kê:** 12 bài viết, 23 liên kết ngược.
- **Phạm vi:** Toàn bộ thư mục `wiki/` (trừ các file meta).

## [2026-04-14] update | Cập nhật Visual Prompts & Character Design System
- **Tạo mới:** [[character-design-system]] (Hệ thống thông số hình ảnh nhất quán).
- **Cập nhật:** Bổ sung mục `## Visual Prompts` (Front, Side, Back, Expressions, Actions) cho 6 nhân vật: [[lily-linh]], [[leo-binh]], [[mom-lan]], [[dad-minh]], [[grandma-hoa]], [[mochi-pet]].
- **Cập nhật:** `_index.md` (Cập nhật danh mục Tools và tổng số bài viết).

## [2026-04-14] update | Đổi tên Em Minh thành Em Bình & Nâng cấp Dashboard 10/10
- **Đổi tên:** `leo-minh.md` -> `leo-binh.md`, cập nhật toàn bộ liên kết và nội dung liên quan (đảm bảo giữ nguyên "Ba Minh").
- **Nâng cấp:** Tối ưu hóa `_dashboard.md` với các câu lệnh Dataview động (Inline JS, Tables, Status Tracking) để đạt mức 10/10 về khả năng truy cập.
- **Cấu trúc:** Tạo thư mục `raw/images/` để quản lý hình ảnh nguồn và cập nhật tài liệu hệ thống.
- **Visuals:** Khóa ảnh chuẩn (Canonical V1) cho 6 nhân vật chính và nhúng trực tiếp vào Wiki để quản lý trực quan.
- **Cập nhật:** `_absorb_log.json`, `_index.md`.
## [2026-04-13] workflow | Lưu trữ Quy trình sản xuất Video (4-Step Workflow)
- **Tạo mới:** [[video-production-workflow]] (Quy trình 4 bước từ System Anchor đến QC & Compliance).
- **Cập nhật:** `wiki/_index.md` (Thêm vào mục Tools, tổng cộng 14 bài).
- **Mục đích:** Cung cấp hướng dẫn từng bước để người dùng copy-paste và theo dõi tính nhất quán khi làm việc với Gemini.

## [2026-04-13] compile | Cập nhật Bảng Biểu Cảm (Expression Sheets) cho toàn bộ nhân vật
...

- **Cập nhật:** Thêm section `## Bảng Biểu Cảm (Expression Sheet)` và nhúng các file ảnh tương ứng vào 6 bài viết nhân vật: [[lily-linh]], [[leo-binh]], [[mom-lan]], [[dad-minh]], [[grandma-hoa]], [[mochi-pet]].
- **Hành động:** Đã hấp thụ (absorb) 6 file ảnh từ `raw/images/` vào `_absorb_log.json`.

## [2026-04-13] update | Cập nhật Quy định phân phối & Safety Workflow
- **Tạo mới:** [[platform-distribution-guide]] (Hướng dẫn phân phối đa nền tảng, bao gồm quy định Việt Nam & Quốc tế).
- **Cập nhật:** Nâng cấp `.agents/workflows/cleanup.md` với tiêu chí **Prompt Safety & Platform Compliance** (kiểm tra minh bạch AI, an toàn trẻ em và tuân thủ Nghị định 147).
- **Cập nhật:** `wiki/_index.md` (Thêm bài mới vào mục Tools, cập nhật tổng số 13 bài).
- **Mục đích:** Đảm bảo mọi prompt và nội dung video đều tuân thủ các quy định pháp lý mới nhất năm 2026.
## [2026-04-13] design | Tạo Cẩm nang Điện ảnh & Bố Cục (Cinematography Guide)
- **Tạo mới:** [[cinematography-guide]] (Quy tắc 1/3, Fibonacci, Golden Ratio và kỹ thuật góc máy).
- **Cập nhật:** `wiki/_index.md` (Thêm vào mục Tools, tổng cộng 15 bài).
- **Mục đích:** Cung cấp các "Composition Tokens" để tích hợp vào Prompt, giúp hình ảnh AI có bố cục chuyên nghiệp.
## [2026-04-13] update | Khóa danh tính nhân vật Mẹ Lan (Identity Lock)
- **Cập nhật:** Chuẩn hóa các thông số ngoại hình cho Mẹ Lan trong [[mom-lan]], `outputs/gemini-prompts-bundle.md` và `outputs/TLE_Characters_Database.md` dựa trên kết quả tạo ảnh thành công.
- **Mục đích:** Đảm bảo gương mặt hiền hậu, kiểu tóc đuôi ngựa thấp và trang phục áo hồng luôn nhất quán trong các cảnh có người lớn giám sát.

- **Cập nhật:** Bổ sung các thông số "baby fat", "chubby cheeks" và tỷ lệ đầu/thân đặc thù cho trẻ 2-3 tuổi vào Prompt của Leo trong [[leo-binh]], `outputs/gemini-prompts-bundle.md` và `outputs/TLE_Characters_Database.md`.
- **Mục đích:** Khắc phục lỗi AI vẽ nhân vật quá lớn, đảm bảo sự chênh lệch chiều cao và độ tuổi rõ rệt giữa Lily và Leo.

- **Cập nhật:** Bổ sung chi tiết "bông hoa vàng nhỏ bên phải băng đô" vào tất cả các Prompt của Lily trong [[lily-linh]] và `outputs/gemini-prompts-bundle.md`.
- **Mục đích:** Tăng cường độ chi tiết và tính đặc trưng cho nhân vật chính, đảm bảo tính nhất quán khi tạo ảnh mới.

## [2026-04-25] autoresearch | create video from storybook — 2 vòng, 2 nguồn nạp
- **Nạp nguồn:** [[ai-storybook-video-tools-2026]], [[consistent-character-workflows]]
- **Báo cáo:** `outputs/reports/research-video-from-storybook-2026-04-25.md`
- **Kết quả:** Xác định quy trình 4 lớp (Modular Pipeline) và các công cụ Identity Anchor mới nhất.

## [2026-04-25] compile | 4 bài mới, cập nhật từ research video storybook
- **Bài mới:** [[ai-storybook-video-tools]], [[ai-lip-sync-technology]], [[video-production-workflow]] (recreated), [[gemini-storybook]] (recreated).
- **Nguồn:** `raw/articles/ai-storybook-video-tools-2026.md`, `raw/articles/consistent-character-workflows.md`, `outputs/reports/research-video-from-storybook-2026-04-25.md`.
- **Hành động:** Đồng bộ hóa quy trình sản xuất video 2026 vào wiki.
