Bước 1: Đề xuất 2 Prompt mẫu
Giải pháp 1: Prompt Đơn giản, Ngắn gọn (Zero-shot CoT cơ bản)
Tập trung vào tốc độ triển khai, sử dụng câu lệnh kích hoạt suy luận từng bước ngắn gọn mà không có nhiều ràng buộc phức tạp.
Bạn là nhân viên chăm sóc khách hàng. Hãy đọc phản hồi của khách hàng dưới đây và suy nghĩ từng bước (step-by-step) để quyết định xem đơn hàng này có đủ điều kiện hoàn tiền theo chính sách (đổi trả trong 7 ngày nếu lỗi do nhà sản xuất) hay không.

Dữ liệu đầu vào:
"{{raw_feedback}}"

Hãy trả về kết quả gồm: Các bước phân tích, Quyết định (Hoàn tiền / Từ chối / Cần thêm thông tin) và Câu trả lời gửi khách.
Giải pháp 2: Prompt Chi tiết, Ràng buộc chặt chẽ (Structured CoT + Error Handling + JSON Schema)
### Bước 2: Lập bảng so sánh Trade-off

| Tiêu chí đánh giá | Giải pháp 1 (Đơn giản) | Giải pháp 2 (Chi tiết, nhiều ràng buộc) |
| :--- | :--- | :--- |
| **Độ dễ hiểu / Viết prompt** | **Cao** (Viết nhanh trong 30 giây, dễ đọc). | **Trung bình** (Cần tư duy thiết kế cấu trúc và lường trước các kịch bản lỗi). |
| **Chi phí Token (Input)** | **Ít** (~80 - 100 tokens/lượt gọi). | **Nhiều hơn** (~280 - 350 tokens/lượt gọi). |
| **Chặn lỗi biên (Edge Cases)** | **Trung bình** (Dễ bị AI suy diễn bừa nếu khách quên ghi mã đơn hoặc nhập ký tự rác). | **Cực tốt** (Bắt trọn các trường hợp thiếu dữ liệu, nhập sai, chống ảo giác triệt để). |
| **Tính nhất quán đầu ra** | **Thấp** (Mỗi lần chạy AI có thể trình bày một kiểu văn bản khác nhau, khó tích hợp code). | **Rất cao** (Cố định 100% cấu trúc JSON Schema, dễ dàng đưa vào hệ thống tự động hóa/API). |
| **Khả năng gỡ lỗi (Debug)** | **Khó** (Không phân tách rõ trạng thái lỗi hệ thống với nội dung trả lời). | **Dễ dàng** (Có trường `status` và mảng `reasoning_steps` minh bạch từng bước). |
Bước 3: Lựa chọn phương án tối ưu và Chạy thử
1. Lựa chọn phương án & Giải thích lý do
Phương án được chọn: Giải pháp 2 (Chi tiết, có nhiều ràng buộc).

Lý do lựa chọn: Mặc dù Giải pháp 2 tiêu tốn lượng token đầu vào cao hơn khoảng 3 lần so với Giải pháp 1, nhưng trong môi trường vận hành doanh nghiệp thực tế (Production), tính ổn định, khả năng chặn lỗi dữ liệu đứt gãy và định dạng JSON đồng nhất là yếu tố sống còn. Giải pháp 1 tuy rẻ và ngắn nhưng nếu gặp dữ liệu bẫy (khách hàng chửi bới mà không đưa mã đơn), AI rất dễ "ảo giác" hoặc trả về đoạn văn tự do khiến hệ thống Backend bị sập (crash) khi đọc dữ liệu. Chi phí token tăng thêm ở Giải pháp 2 là hoàn toàn xứng đáng để đổi lấy độ tin cậy tự động hóa 100%.

2. Chạy thử thực tế với dữ liệu bẫy (Dữ liệu bị thiếu thông tin quan trọng)
Dữ liệu đầu vào (Input thử nghiệm):

"Shop làm ăn chán thế, cái tai nghe Bluetooth mới mua hôm qua về sạc không vào điện, bật không lên nguồn. Cho tôi hoàn tiền ngay lập tức!" (Cố tình bỏ trống Mã đơn hàng để kiểm tra khả năng xử lý đứt gãy dữ liệu).