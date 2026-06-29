# Blog — Nguyễn Thanh Vũ

Trang blog cá nhân: *"Tôi từng mất tất cả vì một cú khóa kênh — và đó là lý do hôm nay tôi dạy người khác làm sạch."*

Câu chuyện của **Nguyễn Thanh Vũ** — Coach xây kênh online cho chuyên gia y tế & người khởi nghiệp.

## Nội dung

- `index.html` — toàn bộ blog (1 file tĩnh, self-contained, chỉ phụ thuộc Google Fonts).
- `DESIGN-SYSTEM.md` — tài liệu hệ thống thiết kế (tông đỏ rượu vang / đen / trắng, Playfair Display).

## Chạy thử

Mở trực tiếp `index.html` bằng trình duyệt, hoặc chạy server tĩnh:

```bash
python3 -m http.server 8000
# rồi mở http://localhost:8000
```

## Thiết kế

- Màu chủ đạo: đỏ rượu vang `#7b1e2b` trên nền đen `#0d0b0c` và kem/trắng `#f7f4ef`.
- Typography: Playfair Display (tiêu đề) + Inter (body).
- Bố cục tạp chí longform: mục lục sticky có scroll-spy, drop-cap, pull-quote, các khối "interlude" nền đen, CTA "Lời mời".
