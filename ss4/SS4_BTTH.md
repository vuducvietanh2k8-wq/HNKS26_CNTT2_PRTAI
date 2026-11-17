# BÁO CÁO THIẾT KẾ GIẢI PHÁP PROMPTING NÂNG CAO

**Đề tài:** Xây dựng hệ thống lập kế hoạch đón tiếp 1.000 tân sinh viên năm học 2027.

## 1. Bối cảnh và mục tiêu

Nhà trường cần tổ chức chương trình đón tiếp 1.000 tân sinh viên năm học 2027. Công việc bao gồm lập kế hoạch, phân công nhân sự, dự toán kinh phí, xây dựng kịch bản và đánh giá rủi ro.

**Mục tiêu:**
- Tự động hóa quá trình lập kế hoạch bằng AI.
- Sử dụng Chain-of-Thought để phân tích nhiệm vụ.
- Sử dụng Prompt Chaining để chia nhỏ công việc.
- Sử dụng Data Handoff để chuyển giao dữ liệu giữa các bước.
- Có cơ chế xử lý lỗi và khôi phục khi AI bị ngắt giữa chừng.

## 2. Thiết kế hệ thống Prompt Chaining

Hệ thống gồm 5 bước thực hiện tuần tự:

**Bước 1: Phân tích yêu cầu**
- Xác định mục tiêu, quy mô, thời gian và địa điểm.
- Đầu ra: Kế hoạch tổng thể dạng JSON.

**Bước 2: Phân công nhân sự**
- Dựa trên kế hoạch bước 1 để chia nhân sự thành các ban.
- Đầu ra: Danh sách nhân sự và nhiệm vụ.

**Bước 3: Lập ngân sách**
- Dựa trên dữ liệu nhân sự và kế hoạch để dự toán chi phí.
- Đầu ra: Bảng ngân sách dự kiến.

**Bước 4: Xây dựng kịch bản**
- Xây dựng lịch trình check-in, khai mạc, giới thiệu trường và giao lưu.
- Đầu ra: Kịch bản chương trình chi tiết.

**Bước 5: Kiểm tra và hoàn thiện**
- Kiểm tra dữ liệu, phát hiện thiếu sót và đánh giá rủi ro.
- Đầu ra: Báo cáo kế hoạch hoàn chỉnh.

## 3. Prompt thực thi từng bước

### Prompt 1 – Phân tích yêu cầu

Bạn là chuyên gia tổ chức sự kiện. Hãy lập kế hoạch đón tiếp 1.000 tân sinh viên năm 2027. Xác định mục tiêu, thời gian, địa điểm, cơ sở vật chất và các công việc cần chuẩn bị. Trình bày kết quả dưới dạng JSON hợp lệ.

### Prompt 2 – Phân công nhân sự

Dựa trên dữ liệu kế hoạch từ bước 1, hãy phân chia nhân sự thành các ban: lễ tân, hậu cần, truyền thông, kỹ thuật, an ninh và y tế. Xác định nhiệm vụ cụ thể của từng ban. Không tự ý thay đổi dữ liệu đầu vào.

### Prompt 3 – Dự toán kinh phí

Dựa trên kế hoạch và danh sách nhân sự từ các bước trước, hãy lập bảng dự toán chi phí cho sân khấu, âm thanh, nước uống, tài liệu, quà tặng và hậu cần. Nếu thiếu đơn giá, hãy đánh dấu là cần báo giá thay vì tự tạo số liệu thực tế.

### Prompt 4 – Xây dựng kịch bản

Dựa trên kế hoạch và ngân sách đã có, hãy xây dựng lịch trình chương trình theo từng khung giờ. Bao gồm đón tiếp, check-in, khai mạc, giới thiệu nhà trường và giao lưu. Đảm bảo phù hợp với quy mô 1.000 sinh viên.

### Prompt 5 – Kiểm tra và hoàn thiện

Tổng hợp kết quả 4 bước trước. Kiểm tra dữ liệu thiếu, trùng lặp và sai định dạng. Đánh giá các rủi ro về thời tiết, quá tải check-in, sự cố kỹ thuật và y tế. Đưa ra phương án dự phòng và xuất báo cáo cuối cùng.

## 4. Cơ chế xử lý lỗi và đứt gãy

- **Chain-of-Thought:** Yêu cầu AI trình bày các bước phân tích ngắn gọn, kết luận và căn cứ, không yêu cầu xuất suy luận nội bộ.
- **Data Handoff:** Chuyển kết quả từng bước bằng JSON để tránh sai lệch dữ liệu.
- **Validation:** Kiểm tra trường dữ liệu bắt buộc, kiểu dữ liệu và định dạng JSON trước khi chuyển bước.
- **Continue Prompting:** Khi câu trả lời bị ngắt, yêu cầu AI tiếp tục từ vị trí cuối cùng, không viết lại phần đã hoàn thành.
- **Rolling Summary:** Tóm tắt tiến độ, dữ liệu quan trọng và nhiệm vụ còn lại khi phiên chat dài.
- **Session Reset:** Khi ngữ cảnh quá tải, lưu bản tóm tắt rồi mở phiên chat mới để tiếp tục.

## 5. Kết quả đầu ra dự kiến

| Hạng mục | Kết quả |
|---|---|
| Quy mô | 1.000 sinh viên |
| Nhân sự | 6 ban phụ trách |
| Ngân sách | Dự toán theo báo giá |
| Kịch bản | Lịch trình theo khung giờ |
| Rủi ro | Có phương án dự phòng |
| Báo cáo | Hoàn chỉnh 5 bước |

**Kết quả kiểm tra:** Dữ liệu được kiểm tra định dạng, các thông tin chưa xác định được đánh dấu chờ bổ sung, không tự tạo số liệu thực tế.

## 6. Kết luận

Việc kết hợp Chain-of-Thought, Prompt Chaining, Data Handoff và Continue Prompting giúp chia nhỏ bài toán, xử lý tuần tự và hạn chế lỗi trong quá trình thực hiện. Hệ thống giúp tiết kiệm thời gian, nâng cao độ chính xác và tạo ra kế hoạch đón tiếp 1.000 tân sinh viên năm 2027 có tính tổ chức và khả năng triển khai thực tế.
