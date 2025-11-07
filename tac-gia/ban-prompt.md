# Bán Prompt của bạn

Tài liệu này giúp bạn xuất bản prompt lên Kho Prompt và nhận tiền về ví cá nhân.

## 1. Chuẩn bị

- Đảm bảo tài khoản đã xác minh email và hoàn thiện hồ sơ thanh toán (ngân hàng hoặc thông tin nhận payout).
- Soạn sẵn nội dung prompt, ví dụ đầu vào/đầu ra và ảnh đại diện.
- Xác định mô hình giá: miễn phí để lấy lượt xem hay trả phí để kiếm doanh thu.

## 2. Tạo prompt

1. Vào trang "Tạo prompt".
2. Nhập tên, mô tả ngắn, mô tả đầy đủ.
3. Chọn danh mục, tag và (nếu có) Prompt Kit muốn gắn.
4. Dán nội dung đầy đủ vào trường `content`, chọn `prompt_type` (text/json) và `prompt_output`.
5. Đặt giá VNĐ. Giá `0` khiến prompt hiển thị miễn phí, `>0` kích hoạt cơ chế khóa nội dung.
6. Kiểm tra lại ảnh bìa và FAQ.

## 3. Gửi duyệt

- Nhấn **Submit for review** để chuyển trạng thái `pending`.
- Admin sẽ xem xét: nội dung phải rõ ràng, không vi phạm bản quyền hoặc chính sách AI.
- Nếu cần sửa, bạn nhận thông báo qua email/notification và có thể cập nhật lại rồi gửi duyệt lần nữa.

## 4. Sau khi được phê duyệt

- Prompt chuyển sang `approved` và xuất hiện công khai. Từ đây bạn có thể chỉnh sửa mô tả nhỏ mà không cần duyệt lại (trừ khi thay đổi lớn).
- Theo dõi số liệu `views`, `helpful_count`, `saved_prompts` để tối ưu nội dung.
- Kết hợp nhiều prompt thành Prompt Kit để tạo gói giá trị cao hơn.

## 5. Nhận tiền

- Mỗi đơn hàng tạo `order_items` chứa `seller_amount` và `platform_fee`.
- Khi hệ thống đánh dấu order `paid`, listener sẽ **credit** ví của bạn (`wallets.balance`).
- Bạn có thể yêu cầu payout khi số dư ≥ 100.000 VNĐ. Yêu cầu chuyển sang trạng thái `pending` để admin xử lý.
- Lịch sử giao dịch thể hiện trong `wallet_transactions`, giúp đối chiếu doanh thu từng đơn.

### Mẹo tăng doanh thu

- Luôn trả lời câu hỏi của người mua trong phần FAQ hoặc bình luận.
- Cập nhật prompt định kỳ để giữ thứ hạng.
- Chạy thử bằng tài khoản phụ để kiểm tra trải nghiệm content gating trước khi public.
