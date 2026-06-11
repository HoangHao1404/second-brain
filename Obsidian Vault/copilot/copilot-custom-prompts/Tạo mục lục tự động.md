---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1080
copilot-command-model-key: ""
copilot-command-last-used: 1779591628424
---
Tạo một bảng mục lục phân cấp cho {}. Thực hiện đúng các quy tắc sau:

1. Sử dụng các cấp độ heading phù hợp: H1 cho phần/chương chính, H2 cho mục con, H3 cho tiểu mục (nếu có). Không dùng H4 trở lên trừ khi thực sự cần thiết.

2. Nếu tài liệu gốc có số trang, hiển thị số trang tương ứng bên cạnh mỗi mục (định dạng: "Tên mục ............. trang X").

3. Nếu tài liệu gốc không có số trang, bỏ qua yêu cầu về số trang. Chỉ hiển thị cấu trúc heading.

4. Giữ nguyên thứ tự xuất hiện của các mục trong tài liệu gốc. Không sắp xếp lại, không lược bỏ mục con trừ khi mục đó là phần phụ lục hoặc chú thích cuối trang.

5. Với mỗi heading, chỉ lấy chính xác văn bản tiêu đề từ tài liệu gốc. Không viết lại, không tóm tắt, không thêm từ mô tả.

6. Thụt lề để thể hiện cấp độ: H1 không thụt lề, H2 thụt 2 khoảng trắng, H3 thụt 4 khoảng trắng.

7. Không thêm bất kỳ câu mở đầu (ví dụ: "Đây là mục lục của tài liệu") hay câu kết luận. Không thêm chú thích, không thêm giải thích.

8. Nếu tài liệu không có cấu trúc heading rõ ràng, hãy tự xác định cấu trúc dựa trên nội dung: mỗi lần chuyển chủ đề lớn là một H1, mỗi ý phụ trong chủ đề đó là H2.

Yêu cầu đặc biệt: Chỉ trả về bảng mục lục dưới dạng văn bản thuần túy, không dùng bảng (table) trong markdown trừ khi tài liệu gốc yêu cầu.