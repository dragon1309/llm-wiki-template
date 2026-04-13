---
title: "Wiki Dashboard — Trung Tâm Điều Khiển"
date_added: 2026-04-13
status: canonical
summary: "Bảng điều khiển động sử dụng Dataview để quản lý toàn bộ Wiki."
---

# 📊 Wiki Dashboard — Trung Tâm Điều Khiển

> Đây là bảng điều khiển tự động cập nhật thông qua plugin **Dataview**. Giúp bạn quản lý tiến độ, phát hiện các lỗ hổng kiến thức và truy cập nhanh vào các tài nguyên quan trọng.

---

## 🚀 Trạng Thái Dự Án (Project Status)

| Loại Bài Viết | Số Lượng | Trạng Thái |
| :--- | :---: | :--- |
| **Concepts** | `$= dv.pages('"wiki/concepts"').length` | `$= dv.pages('"wiki/concepts"').where(p => p.status == "canonical").length` / `$= dv.pages('"wiki/concepts"').length` đã hoàn thiện |
| **Tools** | `$= dv.pages('"wiki/tools"').length` | `$= dv.pages('"wiki/tools"').where(p => p.status == "canonical").length` / `$= dv.pages('"wiki/tools"').length` đã hoàn thiện |
| **People** | `$= dv.pages('"wiki/people"').length` | `$= dv.pages('"wiki/people"').where(p => p.status == "canonical").length` / `$= dv.pages('"wiki/people"').length` đã hoàn thiện |
| **Comparisons** | `$= dv.pages('"wiki/comparisons"').length` | `$= dv.pages('"wiki/comparisons"').where(p => p.status == "canonical").length` / `$= dv.pages('"wiki/comparisons"').length` đã hoàn thiện |

---

## 🛠️ Việc Cần Làm Ngay (Action Items)

### 🔴 Bài viết sơ khai (Stubs - Cần bổ sung)
```dataview
TABLE summary as "Tóm tắt", date_added as "Ngày tạo"
FROM "wiki"
WHERE status = "stub"
SORT date_added ASC
```

### 🟠 Bài viết đang soạn thảo (Drafts - Cần kiểm tra)
```dataview
TABLE tags as "Chủ đề", date_added as "Ngày tạo"
FROM "wiki"
WHERE status = "draft"
SORT date_added DESC
```

---

## 🧬 Hệ Sinh Thái Nhân Vật (Character Ecosystem)

```dataview
TABLE summary as "Vai trò", status as "Trạng thái", related as "Liên kết"
FROM "wiki/people"
SORT file.name ASC
```

---

## 📘 Kiến Thức Hệ Thống (System Knowledge)

```dataview
TABLE summary as "Nội dung chính", tags as "Tags"
FROM "wiki/concepts" OR "wiki/tools" OR "wiki/comparisons"
WHERE file.name != "character-design-system"
SORT file.name ASC
```

---

## 📂 Dữ Liệu Thô Đã Ingest (Raw Sources)

```dataview
TABLE date_added as "Ngày Ingest", tags as "Loại"
FROM "raw"
WHERE file.name != ".gitkeep" AND file.name != "_ingest.py"
SORT date_added DESC
LIMIT 10
```

---

## 🕒 Hoạt Động Gần Đây (Recent Updates)

```dataview
LIST file.name + " (" + date_added + ")"
FROM "wiki"
WHERE date_added >= date(today) - dur(7 days)
SORT date_added DESC
LIMIT 10
```

---
**Ghi chú:** Nếu bảng không hiển thị, hãy đảm bảo bạn đã bật **Enable Inline Queries** và **Enable JavaScript Queries** trong cài đặt của Plugin Dataview.
