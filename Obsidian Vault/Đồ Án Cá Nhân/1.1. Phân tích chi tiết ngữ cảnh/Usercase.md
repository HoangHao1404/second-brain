### UC02-đăng nhập

```mermaid
flowchart TD

A[Vào app] --> B[Màn hình chào]

B --> C[Chọn Đăng nhập]

C --> D[Nhập email]

D --> E[Nhập mật khẩu]

E --> F[Nhấn Đăng nhập]

F --> G{Email tồn tại?}

G -->|Không| H[Hiển thị lỗi: Email không tồn tại]

H --> D

G -->|Có| I{Mật khẩu đúng?}

I -->|Sai| J{Tăng biến đếm sai}

J --> K{Đủ 5 lần sai?}

K -->|Chưa| L[Hiển thị lỗi: Sai mật khẩu]

L --> E

K -->|Đủ 5 lần| M[Khóa tài khoản 5 phút]

M --> N[Hiển thị: Sai quá nhiều lần, thử lại sau 5 phút]

N --> O[Chờ 5 phút]

O --> C

I -->|Đúng| P[Tạo phiên đăng nhập]

P --> Q[Vào trang chính - danh sách tài liệu]

Q --> R[Kết thúc]
```

### UC01: Đăng ký
```mermaid
flowchart LR
    A[Vào app] --> B[Màn hình chào]
    B --> C[Chọn Đăng ký]
    C --> D[Nhập email]
    D --> E[Nhập mật khẩu ≥6 ký tự]
    E --> F[Nhập lại mật khẩu]
    F --> G[Nhấn Đăng ký]

    G --> H{Email đã tồn tại?}
    H -->|Có| I[Hiển thị lỗi: Email đã được đăng ký]
    I --> D

    H -->|Không| J{Mật khẩu khớp?}
    J -->|Không| K[Hiển thị lỗi: Mật khẩu xác nhận không khớp]
    K --> F

    J -->|Có| L{Mật khẩu đủ dài?}
    L -->|Không| M[Hiển thị lỗi: Mật khẩu phải ≥6 ký tự]
    M --> E

    L -->|Có| N[Tạo tài khoản]
    N --> O[Tự động đăng nhập]
    O --> P[Vào trang chính - danh sách tài liệu]
```
## UF-03: Upload file (UC03)
```mermaid
flowchart LR
    A[Đã đăng nhập - trang chính] --> B[Nhấn nút Upload]
    B --> C[Chọn file từ máy tính]

    C --> D{Định dạng hợp lệ?}
    D -->|Không PDF/Word/ảnh| E[Hiển thị lỗi: Chỉ hỗ trợ PDF, Word và ảnh]
    E --> C

    D -->|Có| F{Dung lượng ≤ 10MB?}
    F -->|Không| G[Hiển thị lỗi: File vượt quá 10MB]
    G --> C

    F -->|Có| H[Hiển thị thanh tiến trình upload]
    H --> I{Có mất kết nối?}
    I -->|Có| J[Hiển thị lỗi: Mất kết nối, thử lại]
    J --> K[Nhấn Thử lại]
    K --> H

    I -->|Không| L[Lưu file vào hệ thống]
    L --> M[Hiển thị: Upload thành công]
    M --> N[Refresh danh sách]
    N --> O[File mới xuất hiện trong danh sách]
```
## UF-04: Xem danh sách tài liệu (UC04)
```mermaid
flowchart LR
    A[Đã đăng nhập - vào trang chính] --> B[Hệ thống lấy danh sách tài liệu]

    B --> C{Lỗi tải danh sách?}
    C -->|Có| D[Hiển thị: Không thể tải danh sách]
    D --> E[Hiển thị nút Tải lại]
    E --> F[Nhấn Tải lại]
    F --> B

    C -->|Không| G{Có tài liệu?}
    G -->|Không| H[Hiển thị: Bạn chưa có tài liệu nào]
    H --> I[Hiển thị nút Upload ngay]
    I --> J[Nhấn Upload ngay]
    J --> K[Chuyển sang UF-03]

    G -->|Có| L[Hiển thị danh sách: tên file, loại, ngày, dung lượng]
    L --> M[Sắp xếp mặc định: mới nhất lên đầu]
    M --> N[User có thể sắp xếp theo tên/ngày]
```
## UF-05: Chọn tài liệu làm ngữ cảnh (UC05)
```mermaid
flowchart LR
    A[Đã đăng nhập - trang chính] --> B[Hiển thị danh sách tài liệu + checkbox]
    B --> C[User tick chọn 1 hoặc nhiều tài liệu]
    C --> D[Nhấn nút: Chat với tài liệu đã chọn]

    D --> E{Đã chọn ít nhất 1 tài liệu?}
    E -->|Không| F[Hiển thị cảnh báo: Vui lòng chọn ít nhất 1 tài liệu]
    F --> C

    E -->|Có| G[Chuyển sang giao diện chat]
    G --> H[Hệ thống ghi nhớ danh sách tài liệu được chọn]
    H --> I[Kết thúc - sẵn sàng chat]
```
## UF-06: Chat với AI (UC06)
```mermaid
flowchart LR
    A[Đã chọn tài liệu - ở giao diện chat] --> B[Nhập câu hỏi vào ô chat]
    B --> C[Nhấn Enter hoặc nút Gửi]
    C --> D[Hiển thị: Đang xử lý...]

    D --> E[Gửi câu hỏi + nội dung tài liệu đến AI API]

    E --> F{Gọi API thành công?}
    F -->|Không timeout/mất mạng| G[Hiển thị lỗi: AI đang bận hoặc mất kết nối]
    G --> H[Hiển thị nút Thử lại]
    H --> I[Nhấn Thử lại]
    I --> C

    F -->|Có| J{AI tìm thấy thông tin?}
    J -->|Không| K[Hiển thị: Không tìm thấy thông tin trong tài liệu]
    K --> L[Không lưu vào lịch sử]
    L --> B

    J -->|Có| M[Hiển thị câu trả lời + trích dẫn]
    M --> N[Lưu cặp câu hỏi - trả lời vào lịch sử]
    N --> B
```
## UF-07: Xem lịch sử chat (UC07)
```mermaid
flowchart LR
    A[Đã đăng nhập] --> B[Nhấn nút Lịch sử chat]
    B --> C[Chuyển sang màn hình Lịch sử chat]

    C --> D{Lỗi tải lịch sử?}
    D -->|Có| E[Hiển thị: Không thể tải lịch sử]
    E --> F[Hiển thị nút Tải lại]
    F --> G[Nhấn Tải lại]
    G --> C

    D -->|Không| H{Có phiên chat?}
    H -->|Không| I[Hiển thị: Chưa có lịch sử chat]
    I --> J[Hiển thị nút Bắt đầu chat ngay]
    J --> K[Nhấn Bắt đầu chat ngay]
    K --> L[Chuyển sang màn hình chọn tài liệu]

    H -->|Có| M[Hiển thị danh sách phiên chat]
    M --> N[User click vào một phiên]
    N --> O[Hiển thị toàn bộ câu hỏi và câu trả lời]
    O --> P[User có thể hỏi tiếp trong phiên cũ]
```
## UF-08: Xử lý câu hỏi và trả lời (UC08 - AI System)
```mermaid
flowchart LR
    A[AI System nhận request] --> B[Nhận đầu vào: câu hỏi + nội dung tài liệu]
    B --> C[Phân tích câu hỏi]
    C --> D[Tìm kiếm thông tin trong tài liệu]

    D --> E{Nội dung tài liệu quá dài?}
    E -->|Có| F[Trả về lỗi: Tài liệu quá dài, chọn ít hơn]
    F --> G[Kết thúc - lỗi]

    E -->|Không| H{Tìm thấy thông tin?}
    H -->|Không| I[Trả về: Không tìm thấy thông tin liên quan]
    I --> J[status: no_info]

    H -->|Có| K[Sinh câu trả lời bằng ngôn ngữ tự nhiên]
    K --> L[Xác định đoạn trích dẫn tên file + đoạn văn]
    L --> M[Trả về: answer + citations + status: success]

    J --> N[Kết thúc]
    M --> N
```
