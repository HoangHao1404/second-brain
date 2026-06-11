---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1180
copilot-command-model-key: ""
copilot-command-last-used: 1779593821972
---
Dựa trên nội dung của {} (có thể là một thư mục ghi chú, một tập hợp các note, hoặc một chủ đề). Tạo một Map of Content (MOC) – một bản đồ liên kết các ghi chú liên quan đến nhau. Tuân thủ các quy tắc sau:

1. Xác định chủ đề trung tâm của bộ ghi chú này. Đặt chủ đề đó làm tiêu đề H1 duy nhất của MOC.

2. Liệt kê tất cả các ghi chú (hoặc các khái niệm/quan trọng) có liên quan đến chủ đề trung tâm. Nhóm chúng thành các danh mục H2 (tối đa 7 danh mục, mỗi danh mục từ 3–10 ghi chú).

3. Với mỗi ghi chú, chỉ hiển thị tiêu đề của ghi chú đó (không phải nội dung). Dưới mỗi tiêu đề, thêm tối đa 3 từ khóa mô tả ngắn gọn, đặt trong ngoặc vuông [].

4. Thể hiện mối quan hệ giữa các ghi chú bằng cách sử dụng mũi tên hoặc ký hiệu liên kết: dùng "→" để chỉ "dẫn đến", dùng "↔" để chỉ "liên quan qua lại", dùng "⊂" để chỉ "là một phần của".

5. Nếu một ghi chú liên quan đến nhiều danh mục, hãy đưa nó vào danh mục phù hợp nhất, sau đó ở cuối MOC thêm một phần "Liên kết chéo" (H2) để ghi lại các liên kết phụ.

6. Không thêm bất kỳ nội dung giải thích, không thêm câu mở đầu hay kết luận. Chỉ trả về cấu trúc MOC với H1, H2, danh sách các ghi chú và các ký hiệu liên kết.

7. Định dạng cuối cùng phải là markdown thuần túy, có thể copy trực tiếp vào Obsidian hoặc bất kỳ công cụ ghi chú nào.