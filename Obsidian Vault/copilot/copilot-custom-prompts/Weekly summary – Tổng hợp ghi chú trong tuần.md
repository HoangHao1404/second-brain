---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1210
copilot-command-model-key: ""
copilot-command-last-used: 1779616783773
---
Tổng hợp tất cả ghi chú của tôi trong tuần này (từ Thứ Hai đến Chủ Nhật). Đầu vào {} có thể là: một thư mục chứa ghi chú, một danh sách các file, hoặc nội dung các ghi chú được dán trực tiếp.

TUÂN THỦ CÁC QUY TẮC SAU:

1. XÁC ĐỊNH PHẠM VI THỜI GIAN:
   - Chỉ lấy ghi chú được tạo hoặc sửa trong 7 ngày qua
   - Nếu ghi chú không có ngày tháng, dựa vào ngữ cảnh hoặc bỏ qua
   - Nếu không có ghi chú nào trong tuần, trả về: "Không có ghi chú mới trong tuần này."

2. PHÂN LOẠI GHI CHÚ THEO 3 NHÓM:
   A. KIẾN THỨC MỚI: lý thuyết, khái niệm, bài học, sách đã đọc
   B. VIỆC CẦN LÀM: task, hành động, dự án đang tiến hành
   C. Ý TƯỞNG: suy nghĩ, câu hỏi, phát hiện, liên kết giữa các khái niệm

3. TỔNG HỢP MỖI NHÓM THEO CẤU TRÚC:
   
   ## KIẾN THỨC MỚI
   - Mỗi ghi chú kiến thức: tóm tắt trong 1 câu (tối đa 20 từ)
   - Chỉ giữ lại 3 ý quan trọng nhất của tuần
   - Kèm theo 1 câu "Tại sao điều này đáng nhớ?"
   ## Ý TƯỞNG
   - Liệt kê dạng gạch đầu dòng, mỗi ý tưởng 1 dòng
   - Với mỗi ý tưởng, thêm 1 câu: "Có thể kết hợp với: [ghi chú liên quan]" (nếu có)

4. THỐNG KÊ NHANH CUỐI TUẦN:
   - Tổng số ghi chú mới: X
   - Tổng số task đã hoàn thành: X
   - Tổng số task tồn đọng: X
   - Chủ đề nổi bật nhất tuần: [một cụm từ ngắn]

5. ĐẦU RA (output):
   - Trình bày dưới dạng markdown, có tiêu đề # Tổng kết tuần [dd/mm - dd/mm]
   - Mỗi nhóm cách nhau bởi dòng trống
   - Không thêm câu mở đầu như "Dưới đây là..."
   - Không thêm lời khuyên, nhận xét cá nhân, hay đề xuất hành động (trừ khi có trong ghi chú gốc)

6. XỬ LÝ NGOẠI LỆ:
   - Nếu ghi chú quá dài (>500 từ): tóm tắt thành 2-3 câu trước khi đưa vào báo cáo
   - Nếu ghi chú trùng lặp nội dung: chỉ giữ một bản, thêm "[ĐÃ TRÙNG]" cuối dòng
   - Nếu ghi chú là hình ảnh hoặc file không đọc được: báo "Không thể đọc: [tên file]"

7. TỰ KIỂM TRA TRƯỚC KHI TRẢ VỀ:
   - Đã đủ 3 nhóm chưa? (nếu nhóm nào trống, ghi "Không có")
   - Mỗi câu tóm tắt có dưới 20 từ không?
   - Đã đánh dấu đúng các task khẩn cấp chưa?