Bước 1: Thiết kế giải pháp (I/O)
1. Định nghĩa Input (Dữ liệu đầu vào)
Hệ thống tiếp nhận một gói dữ liệu thô từ khách hàng gửi qua kênh hỗ trợ, bao gồm:

Nội dung phản hồi thô (raw_feedback): Văn bản khiếu nại của khách hàng (có thể dài, lộn xộn, chứa nhiều cảm xúc hoặc thiếu thông tin cốt lõi như mã đơn hàng, số điện thoại).

Chính sách đổi trả (store_policy_snippet): Quy định đổi trả của cửa hàng (ví dụ: đổi trả trong vòng 7 ngày, sản phẩm phải còn nguyên tem mác, lỗi do nhà sản xuất).

2. Định nghĩa Output (Cấu trúc kết quả mong muốn - JSON Schema)
Kết quả trả về bắt buộc phải ở định dạng JSON thuần túy để hệ thống backend tự động định tuyến (Routing) đến bộ phận phù hợp, kèm theo các bước suy luận logic (reasoning_steps) và cơ chế bắt lỗi (status):
{
  "ticket_id": "string or null",
  "customer_name": "string or null",
  "issue_category": "Product Error | Delivery Delay | Policy Dispute | Invalid",
  "sentiment": "Negative | Neutral | Positive",
  "reasoning_steps": [
    "Bước 1: Phân tích nội dung và xác định yêu cầu chính của khách hàng...",
    "Bước 2: Đối chiếu với chính sách đổi trả 7 ngày...",
    "Bước 3: Đánh giá tính hợp lệ của thông tin cung cấp..."
  ],
  "eligibility_for_refund": true,
  "action_required": "Approve Refund | Request More Info | Reject",
  "drafted_response": "Nội dung phản hồi dự kiến gửi khách hàng...",
  "status": "SUCCESS | MISSING_CRITICAL_DATA | INVALID_INPUT"
}
Bước 2: Thiết kế Prompt hoàn chỉnh (Ứng dụng CoT & Error Handling)