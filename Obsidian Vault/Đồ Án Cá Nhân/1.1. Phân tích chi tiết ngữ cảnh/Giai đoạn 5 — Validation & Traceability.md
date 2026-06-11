---
aliases:
  - Requirements Traceability Matrix
tags:
date: 2026-06-01
---

# Giai đoạn 5 — Requirements Traceability Matrix (RTM)

## Mục đích

- Đảm bảo mỗi **Functional Requirement (Must-have)** đều được phủ bởi ít nhất một Use Case.
- Đảm bảo mỗi Use Case đều giải quyết một Pain Point thực tế của sinh viên.
- Liên kết với Success Metrics để đo lường hiệu quả.

## Traceability Matrix

| Req ID | Mô tả Requirement (Must-have) | Use Case | Edge Case / Error | Pain Point | Success Metric |
|--------|-------------------------------|----------|-------------------|------------|----------------|
| FR01 | Đăng ký tài khoản (email + mật khẩu) | UC01 | E01, E02, E03 | Không có tài khoản → không lưu được dữ liệu cá nhân | - (điều kiện tiên quyết) |
| FR02 | Đăng nhập (email + mật khẩu) | UC02 | E04, E05, E06 | Cần xác thực để truy cập tài liệu riêng | - (điều kiện tiên quyết) |
| FR03 | Upload file (PDF, Word, ảnh, ≤10MB) | UC03 | E07, E08, E09, E10 | Có đống tài liệu rải rác, cần tập trung vào một nơi | - |
| FR04 | Xem danh sách tài liệu đã upload | UC04 | E11, E12 | Không biết đã có những tài liệu gì, khó quản lý | Tìm thông tin trong 30 giây (cần biết có gì trước) |
| FR05 | Chọn 1 hoặc nhiều tài liệu làm ngữ cảnh chat | UC05 | E13, E14 | Cần hỏi chỉ trong phạm vi tài liệu ôn tập, không phải cả thế giới | 70% user đánh giá câu trả lời hữu ích (nhờ đúng ngữ cảnh) |
| FR06 | Chat với AI (câu hỏi + trả lời có trích dẫn từ tài liệu) | UC06, UC08 | E15, E16, E17, E18 | Tìm lại thông tin từ đống tài liệu mất công; cần trả lời nhanh, chính xác kèm nguồn | Tìm thông tin trong 30 giây; 70% user đánh giá hữu ích |
| FR07 | Tự động lưu lịch sử chat (phiên, câu hỏi, câu trả lời) | UC07 | E20, E21 | Ôn thi: tắt tab mất hết, hỏi lại từ đầu mất thời gian | Tìm lại thông tin nhanh qua lịch sử (góp phần vào metric 30 giây) |

## Kiểm tra tính toàn vẹn

| Yêu cầu | Kết quả |
|---------|---------|
| Mỗi Must-have requirement có ít nhất 1 use case | ✅ (FR01→UC01, FR02→UC02, FR03→UC03, FR04→UC04, FR05→UC05, FR06→UC06+UC08, FR07→UC07) |
| Mỗi use case có ít nhất 1 requirement | ✅ (UC01→FR01, UC02→FR02, UC03→FR03, UC04→FR04, UC05→FR05, UC06+UC08→FR06, UC07→FR07) |
| Mỗi requirement trace về pain point thật | ✅ (cột Pain Point) |
| Mỗi requirement có success metric (nếu áp dụng) | ✅ (FR04, FR05, FR06, FR07 có metric; FR01,FR02,FR03 là nền tảng) |

## Trace ngược từ Pain Point

| Pain Point gốc | Requirement liên quan | Use Case |
|----------------|----------------------|----------|
| Có đống tài liệu (Word, PDF, ảnh ghi chú tay) nhưng ôn thi hoặc tìm lại thông tin rất mất công | FR03, FR04, FR05, FR06 | UC03, UC04, UC05, UC06 |
| Không có công cụ nào cho phép tra cứu nhanh trong đống tài liệu đó | FR06 | UC06 |
| Dẫn đến mất thời gian và học không hiệu quả | FR06, FR07 | UC06, UC07 |

## Success Metrics – Cách đo

| Metric | Cách đo | Yêu cầu liên quan |
|--------|---------|-------------------|
| User tìm được thông tin trong vòng 30 giây | A/B test hoặc theo dõi thời gian từ lúc nhập câu hỏi đến khi user tìm thấy câu trả lời (có thể ước lượng qua log: thời gian nhập câu hỏi → nhận câu trả lời + thời gian user đọc) | FR04, FR06, FR07 |
| 70% user đánh giá câu trả lời của AI là "hữu ích" | Sau mỗi câu trả lời, hiển thị nút 👍 / 👎 (thu thập phản hồi) | FR05, FR06 |

## Kết luận

Toàn bộ Must-have Functional Requirements đều được trace đến Use Case, Edge Case, Pain Point và Success Metric. RTM sẵn sàng để làm cơ sở cho phát triển và kiểm thử.