# Automation Flow

Automation Flow là workflow tải lên (n8n, Make.com, Zapier hoặc JSON tùy chỉnh) cho phép người khác tải về và tái sử dụng trong dự án tự động hóa.

## Nội dung cần có

- **File workflow**: định dạng `.json` hoặc `.zip`, lưu tại trường `workflow_file`.
- **Platform**: chọn `n8n`, `make`, `zapier` hoặc `other` để người mua lọc.
- **Phiên bản**: `workflow_version` giúp thông báo khi bạn cập nhật.
- **Mô tả & metadata**: viết rõ mục đích, input, output, và các ứng dụng bên thứ ba đang kết nối.
- **SEO**: điền `meta_title`, `meta_description`, OG image để trang chi tiết dễ index.

## Quy trình phát hành

1. Tải file + nhập thông tin → hệ thống ghi nhận trạng thái `pending`.
2. Admin test workflow, kiểm tra nội dung nhạy cảm.
3. Khi duyệt, trạng thái chuyển `approved`, `published_at` được set và listing xuất hiện trên marketplace.

## Mua và tải xuống

- Workflow miễn phí: người dùng đăng nhập, nhấn tải xuống là nhận file, hệ thống cộng `downloads_count`.
- Workflow trả phí: người mua thêm vào giỏ, thanh toán. Sau khi order `paid`, bản ghi `user_automation_flow_purchases` tạo ra quyền tải không giới hạn.
- Mọi lượt tải (kể cả free) đều cập nhật `downloads_count` để bạn đo nhu cầu.

## Chỉ số & đánh giá

- `views`, `downloads_count`, `purchases_count` cho biết độ quan tâm.
- Người mua có thể vote `Helpful` / `Unhelpful`. Mỗi user chỉ vote 1 lần, dữ liệu lưu ở `automation_flow_ratings`.

## Cập nhật phiên bản

- Bảng `automation_flow_versions` lưu lịch sử (filename, changelog, semver).
- Khi đăng version mới bạn nên mô tả thay đổi để người đã mua biết lý do cập nhật.
