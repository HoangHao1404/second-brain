---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1020
copilot-command-model-key: ""
copilot-command-last-used: 1779893151162
---
Tạo bản tóm tắt dạng gạch đầu dòng cho {}. Thực hiện đúng các quy tắc sau:

1. Mỗi gạch đầu dòng chỉ chứa duy nhất MỘT ý chính. Không gộp hai ý vào cùng một bullet.

2. Mỗi bullet tối đa 12 từ. Cắt bỏ tính từ thừa, trạng từ vô dụng, và các cụm như "điều này cho thấy rằng".

3. Giữ nguyên thứ tự logic của văn bản gốc (theo thời gian, nguyên nhân-kết quả, hoặc từ tổng quát đến chi tiết).

4. Nếu văn bản gốc có số liệu, ngày tháng, hoặc tên riêng quan trọng → bắt buộc giữ lại.

5. Không thêm bất kỳ câu mở đầu (ví dụ: "Dưới đây là tóm tắt") hay câu kết luận. Chỉ trả về danh sách các gạch đầu dòng.

6. Nếu nội dung cần nhiều hơn 7 bullet để bao phủ các ý chính, hãy ưu tiên 7 ý quan trọng nhất và lược bỏ phần còn lại.

Yêu cầu đặc biệt: Tuyệt đối không viết đoạn văn. Chỉ dùng định dạng bullet với dấu `-` ở đầu mỗi dòng.