# Prompt cơ bản

Prompt là nội dung AI do người dùng tạo và xuất bản trên Kho Prompt. Mỗi prompt lưu lại trạng thái duyệt, thông tin giá và số liệu tương tác để người mua đánh giá chất lượng.

## Thành phần chính

- **Tên & slug**: slug tạo tự động từ tên và luôn duy nhất để bạn có URL sạch.
- **Nội dung**: trường `content` nhận văn bản đầy đủ, hỗ trợ chế độ `prompt_type = text|json` và `prompt_output = text|image|video`.
- **Mô tả**: `description` (ngắn) và `full_description` (dài) giúp người xem hiểu lợi ích trước khi mua.
- **Giá**: `price` lưu tiền VNĐ. `0` = miễn phí, > 0 = trả phí.
- **Danh mục & thẻ**: `category_id` + nhiều `tags` để người mua tìm kiếm nhanh, đồng thời prompt có thể thuộc nhiều Prompt Kit.
- **Ảnh bìa**: khuyến nghị tải ảnh minh họa để nổi bật trên trang danh sách.

## Quy trình duyệt

1. Tác giả tạo prompt → trạng thái `pending`.
2. Admin kiểm tra nội dung. Có thể yêu cầu chỉnh sửa ngay trong phần ghi chú.
3. Khi đạt yêu cầu, trạng thái chuyển sang `approved` và prompt hiện công khai. Nếu vi phạm, prompt bị `rejected` và ẩn khỏi marketplace.

## Quyền truy cập nội dung

- Prompt miễn phí: ai đã đăng nhập cũng xem trọn nội dung.
- Prompt trả phí: khách chỉ thấy phần mô tả. Nội dung đầy đủ chỉ mở sau khi đơn hàng được đánh dấu `paid` và bản ghi `user_prompt_purchases` được tạo.
- Quyền xem luôn gắn với tài khoản đã mua, nên bạn có thể cập nhật nội dung mà không lo thất thoát.

## Chỉ số theo dõi

- `views`: tổng lượt xem trang chi tiết.
- `helpful_count` / `unhelpful_count`: số lượt đánh giá hữu ích để nổi bật prompt chất lượng.
- `saved_prompts`: số người lưu prompt này vào danh sách yêu thích.

## Mẹo viết nhanh

- Mô tả rõ bài toán, dữ liệu đầu vào và kỳ vọng đầu ra.
- Đưa ví dụ mẫu ngay trong nội dung để người dùng copy-paste.
- Sử dụng thẻ miêu tả ngành nghề (marketing, HR, tài chính...) để tối ưu tìm kiếm.
- Nếu bán trả phí, thêm FAQ ngắn giải thích vì sao nội dung đáng tiền.
