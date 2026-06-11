---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1170
copilot-command-model-key: ""
copilot-command-last-used: 1779589971479
---
Đọc toàn bộ nội dung của {}. Rút ra danh sách các việc cần làm (action items) từ những ghi chú đó. Tuân thủ các quy tắc sau:

1. Mỗi việc cần làm bắt đầu bằng một động từ hành động (ví dụ: viết, gọi, kiểm tra, phân tích, họp, gửi).

2. Việc cần làm phải cụ thể, có thể đo lường được, và có ranh giới rõ ràng. Tránh các cụm mơ hồ như "xem xét" hoặc "nghiên cứu thêm" trừ khi kèm theo tiêu chí hoàn thành.

3. Nếu ghi chú có ẩn ý về thời hạn (hạn chót, "càng sớm càng tốt", "tuần sau"), hãy thêm thời hạn đó vào cuối dòng, đặt trong ngoặc đơn.

4. Nếu ghi chú có tên người phụ trách hoặc bên liên quan, hãy thêm tên đó vào đầu dòng với định dạng [Tên người].

5. Trình bày dưới dạng gạch đầu dòng, mỗi dòng một việc. Không thêm câu mở đầu hay kết luận. Chỉ trả về danh sách.

6. Nếu ghi chú không chứa bất kỳ việc cần làm nào, trả về duy nhất một dòng: "Không có việc cần làm."