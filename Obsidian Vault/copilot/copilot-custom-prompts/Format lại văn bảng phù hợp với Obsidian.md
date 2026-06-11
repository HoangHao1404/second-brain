---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1160
copilot-command-model-key: ""
copilot-command-last-used: 1780929449868
---
Viết hoặc chỉnh sửa nội dung {} thành một note Obsidian hợp lệ, tuân thủ chính xác các quy tắc sau:

1. LIÊN KẾT:
   - Dùng wikilinks để liên kết đến note khác. Ví dụ: Cách ghi chú hiệu quả
   - Nếu muốn hiển thị tên khác, dùng: tên hiển thị
   - Để nhúng một note vào note hiện tại, dùng !note cần nhúng
     * KHÔNG tự động tạo wikilinks ... cho các từ khóa hay khái niệm trong nội dung. 
  Chỉ tạo wikilinks khi người dùng chỉ định rõ ràng. 
  Thay vào đó, dùng **in đậm** để nhấn mạnh các thuật ngữ quan trọng.

1. CALLOUTS – Bắt buộc dùng để làm nổi bật nội dung:
    * Tự động chọn loại callout phù hợp với nội dung: - [!info] → định nghĩa, giải thích, thông tin nền - [!tip] → mẹo, gợi ý, cách làm tốt hơn - [!important] → điểm cốt lõi, cần nhớ - [!warning] → lưu ý, cảnh báo, ngoại lệ - [!example] → ví dụ minh họa - [!success] → kết quả, lợi ích, điểm mạnh - [!danger] → sai lầm phổ biến, rủi ro - [!question] → câu hỏi gợi mở, kiểm tra hiểu biết * Mỗi phần nội dung quan trọng phải được đặt trong callout phù hợp. * Cú pháp: > [!type] Tiêu đề >Nội dung bên dưới
   - Ví dụ: 
     > [!warning] Cần kiểm tra lại
     > Số liệu này chưa được xác thực.

3. PROPERTIES (frontmatter):
   - Đặt ở đầu file, giữa hai dòng `---`
   - Hỗ trợ các kiểu: string, number, boolean, date, datetime, list, tags.
   - Ví dụ:
     ---
     aliases: [Ghi chú chính, Note A]
     tags: [học tập, lý thuyết]
     date: 2026-01-15
     ---

4. THẺ (TAGS):
   - Dùng #hashtag ở bất kỳ đâu trong note
   - Có thể đặt thẻ trong properties hoặc trong nội dung.
5. ĐỊNH DẠNG KHÁC:
   - Gạch ngang tạo đường kẻ ngang: --- (cả ba dấu trên một dòng riêng)
   - Checklist: - [ ] việc chưa làm, - [x] việc đã làm

6. YÊU CẦU ĐẶC BIỆT:
   - Không dùng link kiểu text(URL) trừ khi là link web ngoài. Luôn ưu tiên wikilinks cho link nội bộ.
   - Không dùng HTML trong note Obsidian trừ khi thực sự cần.
   - Giữ nguyên tất cả nội dung gốc, chỉ thay đổi định dạng để đúng cú pháp Obsidian.
   - TAGS – Bắt buộc tuân theo hệ thống 2 lớp sau, không dùng tag ngoài danh sách:
  Lớp 1 (loại nội dung): khái-niệm, phương-pháp, công-cụ, dự-án, tài-liệu
  Lớp 2 (chủ đề): học-tập, công-việc, sức-khỏe, tài-chính, công-nghệ
  Mỗi note gắn tối đa 1 tag Lớp 1 + 1 tag Lớp 2.

Chỉ trả về nội dung đã được định dạng đúng Obsidian. Không thêm lời giải thích.