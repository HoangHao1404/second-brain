---
copilot-command-context-menu-enabled: true
copilot-command-slash-enabled: true
copilot-command-context-menu-order: 1200
copilot-command-model-key: ""
copilot-command-last-used: 1779590041408
---
Nhận đầu vào là {} (có thể là: một khái niệm chính, một danh sách các note, hoặc một bản MOC dạng text). Tạo ra một file JSON Canvas (.canvas) hợp lệ để mở trong Obsidian. Tuân thủ các quy tắc sau:

1. CẤU TRÚC FILE CƠ BẢN:
   - File .canvas là một JSON object với các trường: "nodes", "edges", "groups"
   - Phiên bản: "version": "1.0.0"

2. TẠO NODES (các ô nội dung):
   - Mỗi node đại diện cho một ý chính hoặc một note.
   - Mỗi node có các thuộc tính bắt buộc:
     * "id": string duy nhất (dùng crypto random hoặc "node1", "node2"...)
     * "type": "text" (nếu chứa markdown) hoặc "file" (nếu link đến note)
     * "x": số nguyên (tọa độ ngang, bắt đầu từ 0, cách đều nhau 250 đơn vị)
     * "y": số nguyên (tọa độ dọc, bắt đầu từ 0, cách đều nhau 200 đơn vị)
     * "width": 250 (mặc định)
     * "height": 150 (mặc định)
     * "text": nội dung markdown (nếu type="text")
     * "file": tên file note (nếu type="file")
   - Tùy chọn: "color": "1" đến "6" (6 màu mặc định của Canvas Obsidian)

3. TẠO EDGES (các đường nối):
   - Mỗi edge đại diện cho một mối quan hệ giữa hai node.
   - Mỗi edge có các thuộc tính bắt buộc:
     * "id": string duy nhất
     * "fromNode": id của node nguồn
     * "toNode": id của node đích
     * "fromSide": "top" | "right" | "bottom" | "left" (vị trí xuất phát)
     * "toSide": "top" | "right" | "bottom" | "left" (vị trí kết thúc)
   - Tùy chọn: "label": string (chú thích cho cạnh, ví dụ: "dẫn đến", "liên quan", "trái ngược")

4. TẠO GROUPS (khung nhóm):
   - Group dùng để nhóm các node liên quan lại với nhau.
   - Mỗi group có các thuộc tính:
     * "id": string duy nhất
     * "label": tên nhóm
     * "color": "1"-"6" (màu viền)
     * "x", "y", "width", "height" (bao phủ các node trong nhóm)

5. QUY TẮC BỐ TRÍ (layout):
   - Node trung tâm (main concept) đặt ở tọa độ (0, 0).
   - Các node liên quan trực tiếp đặt xung quanh hình tròn: (250, 0), (-250, 0), (0, 200), (0, -200)
   - Các node cấp 2 (liên quan gián tiếp) đặt cách xa thêm 200 đơn vị, lệch 100 đơn vị để tránh chồng chéo.
   - Nếu có nhiều hơn 12 node, sắp xếp theo lưới (grid): 4 cột, mỗi cột cách nhau 300, mỗi hàng cách nhau 250.

6. THỨ TỰ ƯU TIÊN KHI TẠO:
   - Ưu tiên 1: Tạo nodes từ các khái niệm chính (dựa trên input).
   - Ưu tiên 2: Tạo edges dựa trên mối quan hệ logic (liên quan, dẫn xuất, trái ngược, ví dụ).
   - Ưu tiên 3: Tạo groups cho các cụm chủ đề (nếu có từ 3 node trở lên liên quan chặt chẽ).
   - Ưu tiên 4: Điều chỉnh màu sắc để phân biệt: node quan trọng nhất màu 1 (đỏ), node hỗ trợ màu 3 (xanh), node cảnh báo màu 6 (cam).

7. ĐẦU RA (output):
   - Chỉ trả về nội dung JSON thuần túy, bắt đầu bằng `{` và kết thúc bằng `}`.
   - Không thêm câu mở đầu, không giải thích cách dùng, không thêm markdown ```json (trừ khi bạn muốn copy trực tiếp).
   - Người dùng sẽ copy toàn bộ output và lưu thành file có đuôi `.canvas`.

8. XỬ LÝ NGOẠI LỆ:
   - Nếu đầu vào quá mơ hồ (ví dụ: chỉ một từ duy nhất không rõ nghĩa), trả về lỗi: "Đầu vào không đủ thông tin để tạo canvas. Vui lòng cung cấp một danh sách các khái niệm hoặc một chủ đề cụ thể."
   - Nếu đầu vào là một danh sách file note (hoặc tên note), tự động tạo nodes với type="file" và file tương ứng.