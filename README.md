# Web demo quản trị KDNT (bản demo tĩnh)

Bản trình bày giao diện và logic phân quyền cho cổng quản trị kinh doanh ngoại tệ. Toàn bộ số liệu là **giả lập**.

## Nội dung

- `index.html`: toàn bộ ứng dụng (HTML, CSS, JavaScript trong một file, không cần cài thêm gì).
- `.gitignore`: chặn các file dữ liệu và bí mật không được đưa lên repo.

## Tài khoản demo

Mật khẩu chung: `demo123`

| Tài khoản | Vai trò | Phạm vi nhìn thấy |
|---|---|---|
| `admin` | Phòng KDNH, quản trị | Toàn hàng, có upload và nhật ký |
| `ld` | Ban Lãnh đạo | Toàn hàng, chỉ xem |
| `kh_dn` | Ban Khách hàng Doanh nghiệp | Phân khúc KHDN |
| `kh_cn` | Ban Khách hàng Cá nhân | Phân khúc KHCN |
| `cn001` | Chi nhánh CN 001 | CN 001 và số liệu chung khu vực |

## Đưa lên GitHub Pages

1. Tạo repo mới trên GitHub (có thể để **Private**), ví dụ `web-demo-kdnt`.
2. Upload `index.html`, `README.md`, `.gitignore` vào nhánh `main`.
3. Vào **Settings → Pages**. Ở mục **Build and deployment**, chọn **Source: Deploy from a branch**, nhánh `main`, thư mục `/ (root)`, rồi bấm **Save**.
4. Sau vài phút, trang có địa chỉ dạng `https://<tên-tài-khoản>.github.io/web-demo-kdnt/`.

Lưu ý: với gói GitHub Free, trang Pages có thể công khai dù repo là Private. Chỉ đưa lên khi chấp nhận điều đó, vì bản demo này không chứa dữ liệu thật.

## Giới hạn của bản demo

- Phân quyền và mật khẩu kiểm tra trên trình duyệt, ai đọc mã nguồn cũng thấy. Đây chỉ là minh họa.
- Upload chỉ xem trước file CSV, không ghi vào đâu.
- Tỷ giá là số ngẫu nhiên mô phỏng, không phải tỷ giá thật.
- Khuyến nghị và bản tin được tạo theo quy tắc đơn giản, chưa qua kiểm định nghiệp vụ.

## Kiến trúc đề xuất cho triển khai thật

| Thành phần | Nội dung | Ghi chú |
|---|---|---|
| Giao diện | Giữ như bản demo | Có thể đặt trên hạ tầng nội bộ |
| Xác thực | Tài khoản nội bộ (AD hoặc SSO) | Không lưu mật khẩu trong mã nguồn |
| Phân quyền | Kiểm tra ở máy chủ theo phân khúc và chi nhánh | Bắt buộc, không làm trên trình duyệt |
| Dữ liệu | Cơ sở dữ liệu nội bộ, upload có kiểm tra định dạng và phê duyệt | Không đưa dữ liệu khách hàng ra ngoài |
| Tỷ giá | Lấy từ nguồn được phê duyệt, cập nhật theo lịch hoặc liên tục | Ghi rõ nguồn và thời điểm |
| Bản tin | Tác vụ chạy theo lịch trên máy chủ | Gửi qua kênh nội bộ |
| Nhật ký | Ghi trên máy chủ: ai xem, ai upload, khi nào | Phục vụ kiểm toán |

Không đưa số liệu thật, thông tin khách hàng hay số liệu chi nhánh lên bất kỳ nền tảng nào ngoài hạ tầng đã được Khối CNTT/ATTT phê duyệt, kể cả repo Private.
