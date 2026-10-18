# Hành trình AI của Nathan

Trang web nhật ký học AI của Nathan: ghi lại từng bước đi từ **chưa biết code** đến **tự tạo công cụ bằng AI**, để nhìn lại mình đã đi tới đâu và để ai đang bắt đầu cũng thấy: bắt đầu từ số 0 vẫn được.

## Trang có gì?

- **Vì sao học AI**: các thẻ động lực.
- **Kỹ năng**: thanh tiến độ tự đánh giá.
- **Dòng thời gian**: các mốc đã xong / đang học / sắp tới.
- **Chế độ sáng/tối**: nút 🌙 / ☀️ ở góc phải menu, lưu lựa chọn cho lần sau.

## Cấu trúc

Toàn bộ trang nằm trong một file duy nhất: `index.html` (HTML + CSS + JavaScript, không cần cài thêm gì).

Cách xem: mở `index.html` bằng trình duyệt.

## Cách thêm mốc vào timeline

Mở `index.html`, tìm `<div class="timeline">`, rồi sao chép một khối `div.item` và sửa chữ:

```html
<div class="item next">
  <span class="dot"></span>
  <div class="card">
    <span class="date">📅 20/10/2026</span>   <!-- dòng ngày: không cần thì xoá -->
    <span class="badge">🎯 SẮP TỚI</span>
    <h3>Tên mốc</h3>
    <p>Mô tả ngắn.</p>
  </div>
</div>
```

Class thứ hai của `item` quyết định trạng thái:

| Trạng thái | class | `dot` | `badge` |
|---|---|---|---|
| Đã xong | `item done` | `✓` | `✅ ĐÃ XONG` |
| Đang học | `item doing` | `●` | `🔥 ĐANG HỌC` |
| Sắp tới | `item next` | để trống | `🎯 SẮP TỚI` |

Khi học xong một mốc: đổi class `doing` thành `done`, đổi `dot` và `badge` theo bảng trên.

Sau khi thêm mốc, nhớ cập nhật 3 ô số liệu ở đầu trang (tìm `<div class="stats">`) cho khớp số mốc.

## Cách thêm chức năng

1. **Thêm thẻ / kỹ năng**: sao chép khối `div.card` (mục "Vì sao") hoặc `div.skill` (mục "Kỹ năng"). Với kỹ năng, đổi số % ở cả `<small>` lẫn `style="width:..."`.
2. **Đổi màu cả trang**: sửa các biến màu ở `:root` trong thẻ `<style>`. Bộ màu chế độ tối nằm ở `:root[data-theme="dark"]`.
3. **Thêm một mục mới**: tạo `<section id="ten-muc">` mới trong `<main>`, rồi thêm liên kết `<a href="#ten-muc">` vào menu ở đầu trang.
4. **Thêm chức năng JavaScript**: viết trong thẻ `<script>` ở cuối `index.html`, cạnh đoạn code nút sáng/tối.

## Quy trình làm việc với Git

Thử chức năng mới trên nhánh riêng, không làm trực tiếp trên `main`:

```bash
git checkout -b ten_nhanh      # tạo nhánh để thử
# ... sửa code, mở index.html kiểm tra ...
git add . && git commit -m "Mo ta thay doi"
git push -u origin ten_nhanh   # đẩy lên GitHub, rồi tạo Pull Request để gộp vào main
```

Gộp xong, xoá nhánh phụ: `git branch -d ten_nhanh` và `git push origin --delete ten_nhanh`.
