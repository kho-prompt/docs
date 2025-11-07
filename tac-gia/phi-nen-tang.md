# Phí nền tảng & doanh thu

Kho Prompt chia đơn hàng thành 2 phần: tiền trả cho tác giả (`seller_amount`) và phí nền tảng (`platform_fee`). Cơ chế này áp dụng cho Prompt, Prompt Kit và Automation Flow.

## Công thức cơ bản

```
price = seller_amount + platform_fee
```

- `price`: giá người mua trả ở trang thanh toán.
- `seller_amount`: tiền ghi có vào ví tác giả sau khi đơn hàng `paid`.
- `platform_fee`: phí vận hành nền tảng (hiện mặc định bằng 0 theo tài liệu MVP, nhưng có thể cập nhật khi mở beta công khai).

| Ví dụ | Giá bán | Platform fee | Seller amount |
| --- | --- | --- | --- |
| Prompt miễn phí | 0 ₫ | 0 ₫ | 0 ₫ |
| Prompt trả phí | 99.000 ₫ | 0 ₫ | 99.000 ₫ |
| Kit trong tương lai* | 199.000 ₫ | 19.900 ₫ (10%) | 179.100 ₫ |

`*` Ví dụ dự phòng để minh họa khi nền tảng bật phí. Tỷ lệ thực tế sẽ được thông báo trước khi áp dụng.

## Ghi nhận trong hệ thống

- Mỗi dòng `order_items` lưu `unit_price`, `seller_amount`, `platform_fee`.
- Sau khi đơn hàng thanh toán thành công, worker `CreditWalletListener` cộng `seller_amount` vào `wallets.balance` của tác giả và tạo bản ghi `wallet_transactions`.
- Nếu đơn bị hủy trước khi thanh toán, không có giao dịch ví.

## Payout & báo cáo

1. Khi số dư ≥ 100.000 ₫, bạn có thể gửi yêu cầu payout (`payouts` table) với trạng thái `pending`.
2. Admin kiểm tra và chuyển sang `processing` → `paid`, đồng thời tạo bút toán `debit` trong ví.
3. Bạn có thể xem báo cáo tại trang Doanh thu: tổng bán ra, nền tảng phí đã thu và các yêu cầu payout trước đây.

## Câu hỏi thường gặp

- **Bao giờ áp dụng phí?**: Giai đoạn MVP ghi rõ `platform_fee = 0`. Tương lai khi bật phí sẽ thông báo qua email và cập nhật bảng tính ngay tại đây.
- **Có mất phí khi rút tiền?**: Kho Prompt không trừ thêm phí. Nếu ngân hàng thu phí chuyển khoản, khoản này nằm ngoài hệ thống.
- **Automation Flow có bị khác?**: Không. Tất cả sản phẩm số dùng chung cơ chế order + ví.
