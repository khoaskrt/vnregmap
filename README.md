# Khung pháp lý Ngân hàng và Fintech — Sơ đồ tư duy

Sơ đồ tư duy tra cứu khung pháp lý Việt Nam cho lĩnh vực ngân hàng và fintech, tổ chức theo 4 nhánh:

| Nhánh | Nội dung |
|---|---|
| Sandbox công nghệ số | Cơ chế thử nghiệm có kiểm soát cho sản phẩm, dịch vụ ứng dụng công nghệ số nói chung |
| Sandbox ngân hàng – fintech | Cơ chế thử nghiệm riêng cho hoạt động ngân hàng |
| Tài sản mã hóa | Khung pháp lý cho tài sản số, tài sản mã hóa |
| Trung tâm tài chính quốc tế | Khung pháp lý cho trung tâm tài chính quốc tế tại Việt Nam |

## Miễn trừ trách nhiệm

Thông tin tham khảo phục vụ tra cứu, **không phải tư vấn pháp lý chính thức**. Trước khi viện dẫn trong tài liệu chính thức, đối chiếu bản gốc tại [vbpl.vn](https://vbpl.vn), [vanban.chinhphu.vn](https://vanban.chinhphu.vn) hoặc [congbao.chinhphu.vn](https://congbao.chinhphu.vn).

Node gắn nhãn *cần đối chiếu* hoặc *dự thảo* là phần chưa xác minh đủ — không dùng trực tiếp.

Nội dung cập nhật đến 25/08/2026.

## Cấu trúc kỹ thuật

Toàn bộ ứng dụng nằm trong một file `index.html` tự chứa — CSS inline, dữ liệu và logic render SVG trong hai khối `<script>`. Không dependency, không build step, không CDN.

## Cách cập nhật nội dung

Chỉ chỉnh khối `const DATA = {...}` trong `<script>` đầu tiên của `index.html`. Phần render bên dưới không cần chạm tới.

Mỗi node văn bản pháp luật dùng các trường:

| Trường | Ý nghĩa |
|---|---|
| `code` | Số hiệu ngắn, ví dụ `Luật 71/2025/QH15` |
| `name` / `title` | Tên ngắn / tên đầy đủ của văn bản |
| `role` | `Luật nền` \| `Nghị định hướng dẫn` \| `Nghị quyết thí điểm` \| … |
| `status` | `ok` — số hiệu, ngày ban hành, ngày hiệu lực đã xác minh<br>`check` — còn điểm cần đối chiếu bản gốc (ghi rõ ở `note`)<br>`draft` — chưa ban hành / mới là dự thảo |
| `banHanh` / `hieuLuc` | Ngày ban hành / ngày có hiệu lực |
| `dieuKhoan` | Mảng các điều khoản đáng chú ý |
| `nguon` | `{ url, label }` — link bản gốc để đối chiếu |
| `note` | Ghi chú về phần chưa xác minh |
| `shared` | `true` nếu văn bản xuất hiện ở nhiều nhánh |

**Quy tắc:** mọi số hiệu văn bản phải được xác nhận tồn tại và đúng nội dung tại nguồn chính thức trước khi đặt `status: 'ok'`.

## Phát triển cục bộ

Mở trực tiếp `index.html` bằng trình duyệt, hoặc:

```bash
python3 -m http.server 8000
```

## Deploy

Static site trên Vercel. Mỗi lần push lên `main` sẽ tự động deploy production.
