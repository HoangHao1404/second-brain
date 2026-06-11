---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1190
copilot-command-model-key: ""
copilot-command-last-used: 1779594898604
---
Nhận đầu vào là {} (có thể là URL hoặc đoạn HTML thô). Trích xuất và làm sạch nội dung web thành Markdown thuần túy. Tuân thủ các quy tắc sau:

1. LOẠI BỎ CÁC THÀNH PHẦN:
   - Quảng cáo (banner, popup, in-article ads)
   - Điều hướng (menu, header, footer, sidebar)
   - Phần bình luận (comments)
   - Social media widgets (nút like, share, embed)
   - Form đăng ký, newsletter
   - Thông báo cookie, popup chấp nhận điều khoản
   - Phần "bài viết liên quan", "đọc thêm", "recommended"

2. GIỮ LẠI CÁC THÀNH PHẦN:
   - Tiêu đề chính (H1)
   - Tiêu đề phụ (H2, H3, H4)
   - Đoạn văn (paragraphs)
   - Danh sách (ul, ol, li) → giữ nguyên dạng bullet hoặc số
   - Bảng (table) → chuyển sang markdown đơn giản (dùng | và ---)
   - Trích dẫn (blockquote) → giữ nguyên, thêm > ở đầu mỗi dòng
   - Hình ảnh (img) → lấy thuộc tính alt và src, chuyển thành ![alt]
   - Code blocks (pre, code) → giữ nguyên và thêm ``` với ngôn ngữ nếu phát hiện
   - Số liệu, ngày tháng, tên riêng, trích dẫn tác giả

3. XỬ LÝ ĐẶC BIỆT:
   - Nếu đầu vào là URL, tự động lấy nội dung HTML từ URL đó.
   - Nếu không thể truy cập URL, báo lỗi: "Không thể truy cập URL: [lý do]".
   - Nếu đầu vào là HTML, xử lý trực tiếp.
   - Sau khi làm sạch, chuẩn hóa khoảng trắng (chỉ 1 dòng trống giữa các đoạn, không có dòng trống thừa).

4. ĐẦU RA (output):
   - Chỉ trả về nội dung đã làm sạch dưới dạng Markdown.
   - Ở đầu nội dung, thêm một dòng metadata: <!-- Nguồn: [URL gốc hoặc "HTML đầu vào"] -->
   - Không thêm bất kỳ lời giới thiệu, giải thích, hay nhận xét nào khác.
   - Mỗi ý chính viết tối đa 2-3 câu, không viết đoạn văn dài.
* Ưu tiên dùng bullet points thay vì đoạn văn xuôi.
* Với mỗi khái niệm/lý thuyết: 1-2 câu định nghĩa + 1-2 câu ứng dụng thực tế.
* Không viết dẫn dắt, không viết kết luận thừa.

5. XỬ LÝ NGOẠI LỆ:
   - Nếu sau khi làm sạch không còn nội dung gì (rỗng), trả về: "Không tìm thấy nội dung chính từ trang này."
   - Nếu trang yêu cầu đăng nhập hoặc chặn truy cập, trả về: "Trang web yêu cầu xác thực, không thể trích xuất."
   - 