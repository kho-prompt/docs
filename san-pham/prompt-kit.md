# Prompt Kit

Prompt Kit là bộ sưu tập prompt do bạn tự tạo để gom nội dung theo chủ đề, bán trọn gói hoặc chia sẻ nội bộ. Một kit có thể chứa prompt của bạn hoặc prompt công khai của người khác (nếu được phép chia sẻ).

## Khi nào nên dùng Prompt Kit?

- Muốn bán combo nhiều prompt với một mức giá.
- Cần phân quyền cho đồng đội xem/chỉnh sửa prompt trong dự án riêng.
- Muốn tổ chức prompt theo quy trình (ví dụ bộ 5 bước viết email marketing).

## Trường dữ liệu nổi bật

- **Tên, mô tả, slug**: phục vụ SEO và hiển thị trên marketplace.
- **Ảnh & danh mục**: giúp kit xuất hiện ở đúng chuyên mục.
- **Giá**: dạng `decimal`, hỗ trợ cả gói miễn phí và trả phí.
- **Tag**: kế thừa hệ thống tag chung để người dùng lọc nhanh.
- **Chia sẻ**: `sharing_mode` quyết định phạm vi truy cập.

## Chế độ chia sẻ

| Chế độ | Mô tả | Khi dùng |
| --- | --- | --- |
| `private` | Chỉ chủ sở hữu xem | Kit nháp, nội bộ |
| `public` | Ai cũng thấy, hiển thị trên trang cá nhân | Dùng cho kit public/mua bán |
| `link` | Ai có link chứa `share_token` mới xem được | Chia sẻ kín cho khách hàng |
| `users` | Chỉ user trong `kit_shares` được xem/chỉnh | Làm việc nhóm, giao quyền tạm thời |

## Quản lý quyền chi tiết

- Mỗi bản ghi trong `kit_shares` lưu `can_view`, `can_edit` và `expires_at`.
- Có thể thu hồi quyền bất cứ lúc nào bằng tính năng "Revoke".
- Token chia sẻ sinh tự động, bạn có thể reset nếu link bị lộ.

## Lưu ý triển khai

- Trật tự prompt trong kit lưu tại bảng `kit_prompt` (`order`), nên hãy sắp xếp để người dùng dễ theo dõi.
- Nếu bán kit trả phí, nội dung bên trong sẽ được khóa cho đến khi đơn hàng hoàn tất tương tự prompt đơn lẻ.
