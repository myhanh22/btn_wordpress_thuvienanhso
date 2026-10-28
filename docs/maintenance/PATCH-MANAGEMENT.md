# Quy trình quản lý bản vá — Lăng Kính



## 1. Mục đích



Quy định cách theo dõi, đánh giá, kiểm thử và triển khai bản vá cho website thư viện ảnh số Lăng Kính, hạn chế lỗi giao diện, mất dữ liệu và rủi ro bảo mật.



## 2. Phạm vi



Áp dụng cho:

- WordPress core.

- Theme Astra và theme con `astra-child`.

- Plugin đang sử dụng, đặc biệt các plugin liên quan đến watermark, tối ưu ảnh WebP và bảo mật.

- Cấu hình máy chủ web Nginx và các thành phần phụ trợ của môi trường LocalWP.



## 3. Nguyên tắc



1. Xác định phiên bản hiện tại trước khi cập nhật.

2. Đọc changelog và thông tin bảo mật từ nhà phát triển hoặc nguồn chính thức.

3. Sao lưu database, media và cấu hình liên quan trước khi cập nhật.

4. Thử nghiệm trên môi trường kiểm thử trước khi triển khai lên website chính.

5. Không sửa trực tiếp mã nguồn bên trong thư mục plugin của bên thứ ba nếu có phương án cấu hình hoặc hook được hỗ trợ.

6. Không đưa mật khẩu, API token, `wp-config.php` hoặc thông tin đăng nhập vào Git.

7. Nếu bản vá gây lỗi, ưu tiên khôi phục bản sao lưu hoặc quay lại phiên bản đã kiểm thử.



## 4. Quy trình xử lý bản vá



### Bước 1 — Ghi nhận



Ghi lại thành phần cần cập nhật, phiên bản hiện tại, phiên bản dự kiến, lý do cập nhật, nguồn thông tin và mức độ ảnh hưởng.



### Bước 2 — Đánh giá rủi ro



Xác định bản cập nhật có liên quan đến lỗ hổng bảo mật, thay đổi cơ sở dữ liệu, xử lý ảnh, quyền người dùng, giao diện hoặc cấu hình Nginx hay không.



Ưu tiên xử lý lỗ hổng nghiêm trọng theo hướng dẫn của nhà phát triển. Không bỏ qua bước sao lưu và kiểm thử.



### Bước 3 — Sao lưu



Sao lưu database, thư mục media và cấu hình máy chủ cần thiết. Kiểm tra khả năng khôi phục trước khi triển khai.



Không lưu bản sao chứa dữ liệu nhạy cảm vào repository công khai.



### Bước 4 — Kiểm thử



Thực hiện cập nhật trên môi trường thử nghiệm. Kiểm tra tối thiểu:



- Trang chủ, bộ lọc, tìm kiếm và lightbox.

- Đăng nhập, phân quyền và gửi ảnh.

- Trạng thái chờ duyệt và quy trình duyệt tác phẩm.

- Watermark đối với ảnh mới và ảnh cần xử lý lại.

- Ảnh JPG/PNG, đầu ra WebP và khả năng fallback khi trình duyệt không hỗ trợ WebP.

- Nhật ký lỗi PHP, phản hồi HTTP và các chức năng bảo mật liên quan.



Chỉ đánh dấu kiểm thử đạt khi có kết quả thực tế hoặc bằng chứng phù hợp.



### Bước 5 — Triển khai



Ghi nhận người thực hiện, thời điểm, phiên bản trước và sau cập nhật, thay đổi cấu hình cùng kết quả kiểm thử. Triển khai vào thời điểm phù hợp và kiểm tra lại website sau cập nhật.



### Bước 6 — Khôi phục khi có lỗi



Nếu website phát sinh lỗi nghiêm trọng, dừng triển khai tiếp theo, ghi nhận lỗi và khôi phục phiên bản hoặc bản sao lưu đã xác minh. Kiểm tra lại các chức năng chính sau khi khôi phục.



### Bước 7 — Đóng bản vá



Lưu bằng chứng kiểm thử, kết quả triển khai, lỗi còn tồn tại và biện pháp xử lý. Không ghi trạng thái hoàn thành nếu chưa kiểm chứng.



## 5. Theo dõi lịch sử bản vá



Duy trì bảng ghi nhận với các trường:



| Ngày | Thành phần | Phiên bản trước/sau | Lý do | Kiểm thử | Kết quả | Người thực hiện |

|---|---|---|---|---|---|---|

| Chưa ghi nhận | Chưa ghi nhận | Chưa ghi nhận | Chưa ghi nhận | Chưa thực hiện | Chưa xác minh | Chưa ghi nhận |



Cập nhật bảng khi có một lần vá thực tế. Không điền dữ liệu giả để làm đầy lịch sử.



## 6. Quản lý mã nguồn



- Thực hiện thay đổi trên nhánh riêng.

- Kiểm tra `git diff` và `git status` trước khi commit.

- Đặt thông điệp commit mô tả rõ nội dung thay đổi.

- Mở Pull Request để thành viên nhóm xem xét trước khi hợp nhất.

- Không đưa file cấu hình môi trường, bản sao lưu database hoặc bí mật vào commit.

- Giữ nguyên các thay đổi của thành viên khác nếu chưa thống nhất.



## 7. Trạng thái áp dụng



Tài liệu này quy định quy trình đề xuất. Việc đã tạo tài liệu không đồng nghĩa các bản vá đã được triển khai, kiểm thử hoặc khôi phục thành công. Các lần cập nhật thực tế phải được ghi nhận riêng.
