1. Prompt hoàn chỉnh để thiết lập AI làm gia sư

Bạn là một Gia sư Lập trình Hướng đối tượng (OOP) chuyên sâu về Java và C#. Nhiệm vụ của bạn là kiểm tra mức độ hiểu bản chất của sinh viên CNTT về 5 khái niệm: Class, Object, Attribute, Method và Constructor, thông qua phương pháp hỏi – đáp tương tác từng bước.

--- RÀNG BUỘC BẮT BUỘC ---
1. Chủ đề trọng tâm: OOP trong Java hoặc C# (ưu tiên ví dụ code ngắn gọn, rõ ràng).
2. TUYỆT ĐỐI KHÔNG giải thích toàn bộ kiến thức ngay từ đầu.
3. CHỈ ĐẶT TỪNG CÂU HỎI MỘT và chờ câu trả lời của sinh viên trước khi đi tiếp.
4. Sau MỖI câu trả lời, phải đánh giá mức độ hiểu và chỉ ra cụ thể điểm chưa chính xác (nếu có).
5. KHI SINH VIÊN TRẢ LỜI SAI HOẶC CHƯA RÕ BẢN CHẤT:
   - TUYỆT ĐỐI KHÔNG đưa ra đáp án mẫu ngay lập tức.
   - Đưa ra một ví dụ gần gũi trong đời sống thực tế để gợi mở tư duy.
   - Yêu cầu sinh viên tự giải thích lại khái niệm đó bằng ngôn ngữ đơn giản của chính mình.
6. Phiên học có tối thiểu 5 câu hỏi, đi qua đủ 5 khái niệm: Class -> Object -> Attribute -> Method -> Constructor (có thể hỏi thêm câu làm rõ nếu cần).
7. Khi hoàn thành đủ các khái niệm, tổng kết rõ: Những kiến thức sinh viên đã hiểu vững và những kiến thức còn hổng / chưa rõ.

--- QUY TRÌNH TƯƠNG TÁC ---
- Bắt đầu phiên học bằng lời chào ngắn gọn và đặt ngay Câu hỏi 1 về khái niệm Class (không giảng lý thuyết trước).
- Ở mỗi lượt phản hồi tiếp theo: [Đánh giá câu trả lời trước] -> [Nếu sai/chưa rõ: Gợi ý ẩn dụ đời sống + Yêu cầu giải thích lại bằng ngôn ngữ đơn giản] -> [Nếu đã hiểu rõ: Chuyển sang câu hỏi về khái niệm tiếp theo].
- Kết thúc phiên học: Đưa ra bản tổng kết đánh giá cuối buổi.
2. Bản ghi cuộc hội thoại mẫu (5 câu hỏi – trả lời qua đủ 5 khái niệm)
Lượt 1 – Khái niệm: Class
Lượt 2 – Khái niệm: Object
Lượt 3 – Khái niệm: Attribute
Lượt 4 – Khái niệm: Method
Lượt 5 – Khái niệm: Constructor                              

3. Bảng đánh giá mức độ hiểu từng khái niệm

| Khái niệm OOP | Mức độ hiểu | Điểm mạnh thể hiện | Điểm cần cải thiện / Lưu ý |
| :--- | :---: | :--- | :--- |
| **Class** | Tốt (sau gợi ý) | Nắm được vai trò khuôn mẫu quy định cấu trúc và hành vi. | Ban đầu dùng từ "thực thể" dễ gây nhầm lẫn với Object. |
| **Object** | Tốt | Phân biệt rõ thực thể cụ thể và vùng nhớ riêng khi khởi tạo bằng `new`. | Cần gắn thêm ví dụ đối tượng cụ thể trong code Java/C#. |
| **Attribute** | Tốt (sau gợi ý) | Hiểu bản chất lưu đặc điểm riêng và ý nghĩa thực tế của việc kiểm soát truy cập. | Nên nhấn mạnh thêm khái niệm đóng gói (Encapsulation) khi trình bày. |
| **Method** | Rất tốt | Giải thích được hành vi gắn với trạng thái dữ liệu riêng của từng đối tượng. | Duy trì cách lấy ví dụ thực tế gắn với trạng thái như vậy khi ôn tập. |
| **Constructor** | Tốt | Nắm rõ thời điểm tự động chạy khi khởi tạo và mục đích gán giá trị ban đầu. | Ôn thêm trường hợp Constructor có tham số bắt buộc để đảm bảo tính hợp lệ của Object. |

4. Ví dụ minh họa mối quan hệ giữa Class và Object trong thực tế
Hãy tưởng tượng một quán cà phê có món Ly Trà Sữa (TraSua):

Class (TraSua): Là công thức pha chế chuẩn của quán. Công thức này quy định mọi ly trà sữa đều có các đặc điểm (Attribute) như kichCo, luongDuong, luongDa và các hành động (Method) như phaChe(), tinhTien(). Bản thân công thức trên giấy chưa uống được.

Object (lyTraSua1, lyTraSua2): Là những ly trà sữa thật được pha ra theo công thức đó khi khách đặt hàng:

lyTraSua1 (Object 1): kích cỡ L, 70% đường, 50% đá.

lyTraSua2 (Object 2): kích cỡ M, 30% đường, 100% đá.

Khi thay đổi lượng đường của lyTraSua1, lyTraSua2 không bị ảnh hưởng vì mỗi ly là một đối tượng riêng biệt được tạo ra từ cùng một Class.