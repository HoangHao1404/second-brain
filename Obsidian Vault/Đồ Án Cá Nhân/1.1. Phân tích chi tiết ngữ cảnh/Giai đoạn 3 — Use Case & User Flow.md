---
aliases:
  - Danh sách Use Case
  - UC Specifications
tags:
date: 2026-05-29
---

## Danh sách Usercase Must-have

> [!important] Use Case bắt buộc
> 1. User — Đăng ký tài khoản — vào hệ thống
> 2. User — Đăng nhập — vào hệ thống
> 3. User — Upload file — vào hệ thống
> 4. User — Xem danh sách tài liệu — với hệ thống
> 5. User — Chọn tài liệu làm ngữ cảnh — với hệ thống
> 6. User — Chat với AI — với hệ thống
> 7. User — Xem lịch sử chat — với hệ thống
> 8. AI System — Xử lý câu hỏi và trả lời — cho User

---

## 1. Use Case Specification

### UC01: Đăng ký tài khoản

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC01 |
| **Tên** | Đăng ký tài khoản |
| **Actor** | User |
| **Mô tả** | User tạo tài khoản mới bằng email và mật khẩu |
| **Điều kiện trước** | User chưa có tài khoản, đang ở màn hình đăng ký |
| **Điều kiện sau** | Tài khoản được tạo, user được chuyển vào app |

**Luồng chính:**
1. User nhập email và mật khẩu
2. Hệ thống kiểm tra email chưa tồn tại
3. Hệ thống tạo tài khoản
4. Hệ thống chuyển user vào trang chính

> [!warning] Luồng ngoại lệ
> - Email đã tồn tại → hiển thị lỗi "Email đã được đăng ký"
> - Mật khẩu không đủ mạnh → hiển thị yêu cầu mật khẩu

---

### UC02: Đăng nhập

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC02 |
| **Tên** | Đăng nhập |
| **Actor** | User |
| **Mô tả** | User đăng nhập vào hệ thống bằng email và mật khẩu |
| **Điều kiện trước** | User đã có tài khoản, đang ở màn hình đăng nhập |
| **Điều kiện sau** | User được vào trang chính của app |

**Luồng chính:**
1. User nhập email và mật khẩu
2. Hệ thống kiểm tra email tồn tại và mật khẩu đúng
3. Hệ thống tạo phiên đăng nhập (session/token)
4. Hệ thống chuyển user vào trang chính (danh sách tài liệu)

> [!warning] Luồng ngoại lệ
> - Email không tồn tại → hiển thị lỗi "Email không tồn tại"
> - Sai mật khẩu → hiển thị lỗi "Sai mật khẩu"
> - Quá 5 lần sai liên tiếp → khóa tạm thời 5 phút

---

### UC03: Upload file

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC03 |
| **Tên** | Upload file |
| **Actor** | User |
| **Mô tả** | User tải file lên hệ thống để làm tài liệu học tập |
| **Điều kiện trước** | User đã đăng nhập |
| **Điều kiện sau** | File được lưu vào hệ thống, hiển thị trong danh sách tài liệu |

**Luồng chính:**
1. User kéo/thả hoặc chọn file từ máy tính
2. Hệ thống kiểm tra định dạng file hợp lệ
3. Hệ thống kiểm tra dung lượng file
4. Hệ thống lưu file và gắn với user hiện tại
	4.1. Hệ thống xử lý và trích xuất nội dung từ file (parse text, OCR nếu là ảnh)
5. Hệ thống hiển thị file mới trong danh sách

> [!warning] Luồng ngoại lệ
> - Định dạng không hỗ trợ (không phải PDF/Word/ảnh) → hiển thị lỗi
> - Dung lượng vượt quá giới hạn → hiển thị lỗi "File quá lớn"
> - Upload thất bại do mạng → hiển thị lỗi và cho phép thử lại

---

### UC04: Xem danh sách tài liệu

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC04 |
| **Tên** | Xem danh sách tài liệu |
| **Actor** | User |
| **Mô tả** | User xem tất cả tài liệu đã upload của mình |
| **Điều kiện trước** | User đã đăng nhập |
| **Điều kiện sau** | Danh sách tài liệu được hiển thị |

**Luồng chính:**
1. User vào trang chính
2. Hệ thống lấy danh sách tài liệu của user hiện tại
3. Hệ thống hiển thị danh sách (tên file, ngày upload, loại file)
4. User có thể sắp xếp theo tên/ngày

> [!warning] Luồng ngoại lệ
> - User chưa có tài liệu nào → hiển thị thông báo "Chưa có tài liệu" + nút upload
> - Lỗi kết nối database → hiển thị thông báo lỗi chung

---

### UC05: Chọn tài liệu làm ngữ cảnh

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC05 |
| **Tên** | Chọn tài liệu làm ngữ cảnh |
| **Actor** | User |
| **Mô tả** | User chọn 1 hoặc nhiều tài liệu để AI dựa vào đó trả lời câu hỏi |
| **Điều kiện trước** | User đã đăng nhập, đã có ít nhất 1 tài liệu |
| **Điều kiện sau** | Hệ thống ghi nhớ tài liệu được chọn cho phiên chat hiện tại |

**Luồng chính:**
1. User vào giao diện chat
2. Hệ thống hiển thị danh sách tài liệu có sẵn (kèm checkbox)
3. User chọn 1 hoặc nhiều tài liệu
4. User có thể chọn "Tất cả tài liệu"
5. Hệ thống lưu lựa chọn làm ngữ cảnh

> [!warning] Luồng ngoại lệ
> - User chưa có tài liệu nào → ẩn lựa chọn, hiển thị nút upload
> - User bỏ chọn hết tài liệu → hiển thị cảnh báo "Vui lòng chọn ít nhất 1 tài liệu"

---

### UC06: Chat với AI

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC06 |
| **Tên** | Chat với AI |
| **Actor** | User (primary), AI System (external) |
| **Mô tả** | User đặt câu hỏi, AI trả lời dựa trên nội dung tài liệu đã chọn |
| **Điều kiện trước** | User đã đăng nhập, đã chọn ít nhất 1 tài liệu làm ngữ cảnh |
| **Điều kiện sau** | Câu trả lời và câu hỏi được lưu vào lịch sử chat |

**Luồng chính:**
1. User nhập câu hỏi vào ô chat
2. User nhấn gửi (Enter hoặc nút)
3. Hệ thống lấy nội dung của (các) tài liệu đã chọn
4. Hệ thống gửi câu hỏi + nội dung tài liệu đến AI System
5. AI System xử lý và trả về câu trả lời (kèm trích dẫn)
6. Hệ thống hiển thị câu trả lời cho User
7. Hệ thống lưu câu hỏi + câu trả lời vào lịch sử

> [!warning] Luồng ngoại lệ
> - Chưa chọn tài liệu → hiển thị "Hãy chọn tài liệu trước khi hỏi"
> - AI System timeout → hiển thị "AI đang bận, thử lại sau"
> - Nội dung tài liệu quá dài → hệ thống cắt bớt hoặc báo lỗi
> - Câu trả lời không có nội dung từ tài liệu → AI trả lời "Không tìm thấy thông tin trong tài liệu của bạn"

---

### UC07: Xem lịch sử chat

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC07 |
| **Tên** | Xem lịch sử chat |
| **Actor** | User |
| **Mô tả** | User xem lại các câu hỏi và câu trả lời cũ |
| **Điều kiện trước** | User đã đăng nhập, đã có ít nhất 1 phiên chat |
| **Điều kiện sau** | Lịch sử chat được hiển thị |

**Luồng chính:**
1. User vào màn hình lịch sử chat
2. Hệ thống lấy danh sách các phiên chat (theo thời gian giảm dần)
3. Hệ thống hiển thị danh sách (ví dụ: "Chat lúc 15/01 - 3 câu hỏi")
4. User chọn một phiên chat
5. Hệ thống hiển thị toàn bộ câu hỏi và câu trả lời trong phiên đó

> [!warning] Luồng ngoại lệ
> - User chưa có lịch sử chat → hiển thị "Chưa có lịch sử chat"
> - Lỗi tải dữ liệu → hiển thị thông báo lỗi

---

### UC08: Xử lý câu hỏi và trả lời (AI System)

| Trường | Nội dung |
|--------|----------|
| **Use Case ID** | UC08 |
| **Tên** | Xử lý câu hỏi và trả lời |
| **Actor** | AI System |
| **Mô tả** | AI System nhận câu hỏi và nội dung tài liệu, trả về câu trả lời có trích dẫn |
| **Điều kiện trước** | AI System sẵn sàng, nhận được request từ hệ thống chính |
| **Điều kiện sau** | Trả về phản hồi hợp lệ |

**Luồng chính:**
1. AI System nhận câu hỏi + nội dung tài liệu
2. AI System phân tích câu hỏi
3. AI System tìm kiếm thông tin trong nội dung tài liệu
4. AI System sinh câu trả lời kèm đoạn trích dẫn
5. AI System trả về phản hồi

> [!warning] Luồng ngoại lệ
> - Không tìm thấy thông tin liên quan → trả về "Không có thông tin trong tài liệu"
> - Nội dung tài liệu quá dài → tự động cắt hoặc báo lỗi
> - Câu hỏi không liên quan đến tài liệu → yêu cầu user hỏi lại trong phạm vi tài liệu
>   

## 2. User Flow

### UF-01: Đăng ký tài khoản (UC01)

```
Vào app
→ Màn hình chào
→ Chọn "Đăng ký"
→ Nhập email
→ Nhập mật khẩu (≥6 ký tự)
→ Nhập lại mật khẩu
→ Nhấn "Đăng ký"
    → Email chưa tồn tại, mật khẩu hợp lệ
        → Tạo tài khoản
        → Tự động đăng nhập
        → Vào trang chính (danh sách tài liệu)
    → Email đã tồn tại
        → Hiển thị lỗi "Email đã được đăng ký"
        → Quay lại nhập email khác
    → Mật khẩu không khớp
        → Hiển thị lỗi "Mật khẩu xác nhận không khớp"
        → Quay lại nhập lại mật khẩu
    → Mật khẩu quá ngắn
        → Hiển thị lỗi "Mật khẩu phải có ít nhất 6 ký tự"
        → Quay lại nhập mật khẩu mới
```

### UF-02: Đăng nhập (UC02)

```
Vào app
→ Màn hình chào
→ Chọn "Đăng nhập"
→ Nhập email
→ Nhập mật khẩu
→ Nhấn "Đăng nhập"
    → Email tồn tại và mật khẩu đúng
        → Tạo phiên đăng nhập
        → Vào trang chính (danh sách tài liệu)
    → Email không tồn tại
        → Hiển thị lỗi "Email không tồn tại"
        → Quay lại nhập email khác
    → Sai mật khẩu
        → Hiển thị lỗi "Sai mật khẩu"
        → Quay lại nhập lại mật khẩu
    → Sai mật khẩu 5 lần liên tiếp
        → Khóa tài khoản 5 phút
        → Hiển thị thông báo "Sai quá nhiều lần, vui lòng thử lại sau 5 phút"
```

### UF-03: Upload file (UC03)

```
Đã đăng nhập - đang ở trang chính
→ Nhấn nút "Upload"
→ Chọn file từ máy tính
→ Hệ thống kiểm tra file
    → Định dạng hợp lệ (PDF, Word, ảnh) và dung lượng ≤ 10MB
        → Hiển thị thanh tiến trình upload
        → Lưu file vào hệ thống
        → Hiển thị thông báo "Upload thành công"
        → Refresh danh sách tài liệu
        → File mới xuất hiện trong danh sách
    → Định dạng không hợp lệ
        → Hiển thị lỗi "Chỉ hỗ trợ PDF, Word và ảnh"
        → Quay lại chọn file khác
    → Dung lượng > 10MB
        → Hiển thị lỗi "File vượt quá 10MB"
        → Quay lại chọn file khác
    → Mất kết nối khi đang upload
        → Hiển thị lỗi "Mất kết nối, vui lòng thử lại"
        → Nhấn "Thử lại" để upload lại
```

### UF-04: Xem danh sách tài liệu (UC04)

```
Đã đăng nhập - vừa vào trang chính
→ Hệ thống lấy danh sách tài liệu của user
    → Có tài liệu
        → Hiển thị danh sách: tên file, loại file, ngày upload, dung lượng
        → Sắp xếp mặc định: mới nhất lên đầu
        → User có thể sắp xếp theo tên (A→Z) hoặc theo ngày (cũ trước)
    → Chưa có tài liệu
        → Hiển thị thông báo "Bạn chưa có tài liệu nào"
        → Hiển thị nút "Upload ngay"
        → Nhấn nút "Upload ngay" → chuyển sang UF-03
    → Lỗi tải danh sách
        → Hiển thị thông báo "Không thể tải danh sách, vui lòng thử lại"
        → Hiển thị nút "Tải lại"
        → Nhấn "Tải lại" → gọi lại API lấy danh sách
```

### UF-05: Chọn tài liệu làm ngữ cảnh (UC05)

```
Đã đăng nhập - đang ở trang chính (danh sách tài liệu)
→ User thấy danh sách tài liệu đã upload
→ Mỗi tài liệu có checkbox bên cạnh
→ User tick chọn 1 hoặc nhiều tài liệu
→ User nhấn nút "Chat với tài liệu đã chọn"
    → Đã chọn ít nhất 1 tài liệu
        → Hệ thống chuyển sang giao diện chat
        → Hệ thống ghi nhớ danh sách tài liệu được chọn
        → Kết thúc
    → Chưa chọn tài liệu nào
        → Hiển thị cảnh báo "Vui lòng chọn ít nhất 1 tài liệu"
        → Quay lại bước chọn tài liệu
```

### UF-06: Chat với AI (UC06)

```
Đã chọn tài liệu - đang ở giao diện chat
→ User nhập câu hỏi vào ô chat
→ User nhấn Enter hoặc nút "Gửi"
→ Hệ thống hiển thị "Đang xử lý..."
→ Hệ thống gửi câu hỏi + nội dung tài liệu đến AI API
    → Gọi AI API thành công
        → AI trả về câu trả lời + đoạn trích dẫn (tên file + đoạn văn)
        → Hệ thống hiển thị câu trả lời trong khung chat
        → Hệ thống lưu cặp (câu hỏi, câu trả lời, thời gian) vào lịch sử
        → User có thể hỏi tiếp câu mới
    → Gọi AI API thất bại (timeout / mất mạng)
        → Hiển thị lỗi "AI đang bận hoặc mất kết nối, vui lòng thử lại"
        → Hiển thị nút "Thử lại"
        → User nhấn "Thử lại" → quay lại bước gửi câu hỏi
    → AI trả về "không tìm thấy thông tin"
        → Hiển thị "Không tìm thấy thông tin liên quan trong tài liệu của bạn"
        → Không lưu vào lịch sử (hoặc vẫn lưu nhưng đánh dấu)
```

### UF-07: Xem lịch sử chat (UC07)

```
Đã đăng nhập - đang ở giao diện chat hoặc menu chính
→ User nhấn vào nút "Lịch sử chat"
→ Hệ thống chuyển sang màn hình Lịch sử chat
→ Hệ thống lấy danh sách các phiên chat của user
    → Có phiên chat
        → Hiển thị danh sách phiên: tiêu đề, thời gian, số câu hỏi
        → Sắp xếp: mới nhất lên đầu
        → User click vào một phiên
            → Hệ thống hiển thị toàn bộ câu hỏi và câu trả lời trong phiên đó
            → User có thể tiếp tục hỏi thêm trong phiên cũ
    → Chưa có lịch sử chat
        → Hiển thị thông báo "Chưa có lịch sử chat"
        → Hiển thị nút "Bắt đầu chat ngay"
        → Nhấn nút → chuyển sang màn hình chọn tài liệu
    → Lỗi tải lịch sử
        → Hiển thị "Không thể tải lịch sử, vui lòng thử lại"
        → Hiển thị nút "Tải lại"
        → Nhấn "Tải lại" → gọi lại API
```

### UF-08: Xử lý câu hỏi và trả lời (UC08 - AI System)

```
AI System nhận request từ hệ thống chính
→ Nhận đầu vào: câu hỏi + nội dung tài liệu
→ Phân tích câu hỏi
→ Tìm kiếm thông tin trong nội dung tài liệu
    → Tìm thấy thông tin
        → Sinh câu trả lời bằng ngôn ngữ tự nhiên
        → Xác định đoạn trích dẫn (tên file + đoạn văn)
        → Trả về: {answer, citations, status: "success"}
    → Không tìm thấy thông tin
        → Trả về: {answer: "Không tìm thấy thông tin...", citations: [], status: "no_info"}
→ [Ngoại lệ]
    → Nội dung tài liệu quá dài
        → Trả về lỗi: "Tài liệu quá dài, vui lòng chọn ít tài liệu hơn"
    → Lỗi hệ thống AI (quota, crash)
        → Trả về lỗi: "Hệ thống AI đang gặp sự cố, vui lòng thử lại sau"
```

## 3.  Edge Case & Error Flow
| ID  | Mô tả                                       | Loại       | UC liên quan | Điều kiện xảy ra                                      | Cách xử lý                                                                     | Hành động của user sau đó                   |
| --- | ------------------------------------------- | ---------- | ------------ | ----------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------- |
| E01 | Email đã tồn tại                            | Validation | UC01         | User nhập email đã có trong database                  | Hiển thị lỗi: "Email đã được đăng ký"                                          | Nhập email khác                             |
| E02 | Mật khẩu xác nhận không khớp                | Validation | UC01         | User nhập mật khẩu và xác nhận khác nhau              | Hiển thị lỗi: "Mật khẩu xác nhận không khớp"                                   | Nhập lại mật khẩu xác nhận                  |
| E03 | Mật khẩu quá ngắn                           | Validation | UC01         | Mật khẩu < 6 ký tự                                    | Hiển thị lỗi: "Mật khẩu phải có ít nhất 6 ký tự"                               | Nhập mật khẩu mới dài hơn                   |
| E04 | Email không tồn tại khi đăng nhập           | Validation | UC02         | User nhập email chưa đăng ký                          | Hiển thị lỗi: "Email không tồn tại"                                            | Đăng ký hoặc nhập email khác                |
| E05 | Sai mật khẩu                                | Validation | UC02         | User nhập đúng email nhưng sai mật khẩu               | Hiển thị lỗi: "Sai mật khẩu"                                                   | Nhập lại mật khẩu                           |
| E06 | Sai mật khẩu quá nhiều lần                  | Security   | UC02         | Sai mật khẩu 5 lần liên tiếp                          | Khóa tài khoản 5 phút, hiển thị thông báo                                      | Chờ 5 phút hoặc dùng "Quên mật khẩu"        |
| E07 | Định dạng file không hỗ trợ                 | Validation | UC03         | User upload file không phải PDF/Word/ảnh              | Hiển thị lỗi: "Chỉ hỗ trợ PDF, Word và ảnh"                                    | Chọn file khác                              |
| E08 | Dung lượng file vượt quá giới hạn           | Validation | UC03         | File > 10MB                                           | Hiển thị lỗi: "File vượt quá 10MB"                                             | Chọn file nhỏ hơn hoặc nén file             |
| E09 | Mất kết nối khi upload                      | Network    | UC03         | Mạng ngắt giữa lúc upload                             | Hiển thị lỗi: "Mất kết nối, vui lòng thử lại" + nút "Thử lại"                  | Nhấn "Thử lại"                              |
| E10 | Upload thất bại do lỗi server               | System     | UC03         | Server lỗi hoặc hết dung lượng                        | Hiển thị lỗi: "Upload thất bại, thử lại sau"                                   | Thử lại sau                                 |
| E11 | User chưa có tài liệu nào                   | Business   | UC04         | User mới, chưa upload file nào                        | Hiển thị thông báo: "Bạn chưa có tài liệu nào" + nút "Upload ngay"             | Nhấn "Upload ngay"                          |
| E12 | Lỗi tải danh sách tài liệu                  | System     | UC04         | Database lỗi, API timeout, mất mạng                   | Hiển thị thông báo: "Không thể tải danh sách" + nút "Tải lại"                  | Nhấn "Tải lại"                              |
| E13 | User chưa có tài liệu khi vào chọn ngữ cảnh | Business   | UC05         | User chưa upload file nào                             | Ẩn checkbox chọn tài liệu, hiển thị nút "Upload ngay"                          | Nhấn "Upload ngay"                          |
| E14 | User bỏ chọn hết tài liệu                   | Validation | UC05         | User bỏ tick khỏi tất cả tài liệu                     | Hiển thị cảnh báo: "Vui lòng chọn ít nhất 1 tài liệu"                          | Chọn lại ít nhất 1 tài liệu                 |
| E15 | Chưa chọn tài liệu khi bắt đầu chat         | Validation | UC06         | User vào giao diện chat nhưng chưa chọn tài liệu nào  | Hiển thị cảnh báo: "Hãy chọn tài liệu trước khi hỏi"                           | Quay lại màn hình chọn tài liệu             |
| E16 | AI API timeout                              | System     | UC06, UC08   | AI API không phản hồi trong thời gian giới hạn        | Hiển thị lỗi: "AI đang bận hoặc mất kết nối, vui lòng thử lại" + nút "Thử lại" | Nhấn "Thử lại"                              |
| E17 | Nội dung tài liệu quá dài                   | Technical  | UC06, UC08   | Tổng nội dung tài liệu vượt quá context window của AI | Hiển thị lỗi: "Tài liệu quá dài, vui lòng chọn ít tài liệu hơn"                | Chọn ít tài liệu hơn hoặc tài liệu ngắn hơn |
| E18 | AI không tìm thấy thông tin trong tài liệu  | Business   | UC06, UC08   | Câu hỏi không liên quan hoặc nội dung không có        | AI trả lời: "Không tìm thấy thông tin liên quan trong tài liệu của bạn"        | Hỏi câu khác hoặc chọn tài liệu khác        |
| E19 | Lỗi hệ thống AI (quota, crash)              | System     | UC08         | Hết quota API, AI model crash                         | Hiển thị lỗi: "Hệ thống AI đang gặp sự cố, vui lòng thử lại sau"               | Thử lại sau                                 |
| E20 | User chưa có lịch sử chat                   | Business   | UC07         | User chưa từng chat lần nào                           | Hiển thị thông báo: "Chưa có lịch sử chat" + nút "Bắt đầu chat ngay"           | Nhấn "Bắt đầu chat ngay"                    |
| E21 | Lỗi tải lịch sử chat                        | System     | UC07         | Database lỗi, API timeout                             | Hiển thị thông báo: "Không thể tải lịch sử" + nút "Tải lại"                    | Nhấn "Tải lại"                              |
## 4. Usercase
[[Usercase]]
