## Functional Requirements

**Danh sách tính năng đầy đủ:**

1. **Quản lý tài liệu**
    
    - Upload tài liệu (PDF, Word, ảnh ghi chú tay) — kéo/thả hoặc chọn file, nhiều file cùng lúc
    - Xem danh sách tài liệu đã upload (tên file, ngày upload, loại file, dung lượng)
    - Xóa tài liệu (xóa vĩnh viễn)
    - Xem chi tiết tài liệu (nội dung thô hoặc ảnh xem trước)
2. **Chat với AI**
    
    - Chọn 1 hoặc nhiều tài liệu làm ngữ cảnh
    - Đặt câu hỏi bằng ngôn ngữ tự nhiên
    - AI trả lời có trích dẫn nguồn (tên file, đoạn trích)
    - Lưu lịch sử chat tự động theo session
    - Xóa lịch sử chat
3. **Tóm tắt & Ôn tập**
    
    - Tóm tắt tài liệu (ngắn / trung bình / dài)
    - Gợi ý câu hỏi ôn tập (trắc nghiệm / tự luận)
    - Highlight nội dung quan trọng
4. **Tìm kiếm**
    
    - Tìm kiếm trong nội dung tài liệu đã upload
    - Tìm kiếm trong lịch sử chat
5. **Quản lý người dùng**
    
    - Đăng ký / Đăng nhập (email + password)
    - Đăng nhập Google
    - Xem hồ sơ cá nhân
    - Xóa tài khoản

---

## MoSCoW Classification

| Mức độ          | Tính năng                                                                                                                                |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Must-have**   | ==Upload file, Chat với AI (có trích dẫn), Chọn tài liệu làm ngữ cảnh, Xem danh sách tài liệu, Đăng ký/Đăng nhập, Lịch sử chat tự động== |
| **Should-have** | Tóm tắt tài liệu, Tìm kiếm trong tài liệu, Xóa tài liệu, Đăng nhập Google                                                                |
| **Could-have**  | Gợi ý câu hỏi ôn tập, Highlight, Xóa lịch sử chat                                                                                        |

---

## Non-functional Requirements

|Mức độ|NFR|
|---|---|
|**Must-have**|Bảo mật (cách ly dữ liệu giữa các user), Usability cơ bản (không cần hướng dẫn), Privacy policy (không dùng dữ liệu user)|
|**Should-have**|Hiệu năng (AI phản hồi ≤ 15s), Lưu lịch sử không mất, 99% uptime|
|**Could-have**|Hỗ trợ 50 người dùng đồng thời|