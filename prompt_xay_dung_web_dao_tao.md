# Prompt: Xây dựng trang web đào tạo ĐTV từ dữ liệu phân tích cuộc gọi

Dùng prompt này khi bạn có một bảng dữ liệu phân tích cuộc gọi (Google Sheet/Excel) và muốn AI tự đánh giá nghiệp vụ ĐTV rồi dựng thành một trang web đào tạo hoàn chỉnh.

---

## Prompt gốc

```
Tôi có một bảng dữ liệu phân tích cuộc gọi của ĐTV [tên ĐTV / mã agent], nguồn từ hệ thống
chấm điểm AI (Emas). Link: [dán link Google Sheet hoặc đính kèm file Excel/CSV]

Bảng gồm các cột: Ưu tiên, ID cuộc gọi, Thời điểm, Số KH, Thời lượng, Nhóm thời gian, Chủ đề,
Cảm xúc KH, Cảm xúc ĐTV, Hài lòng dịch vụ, Hài lòng với ĐTV, Điểm quy trình, Điểm thái độ,
Điểm trách nhiệm, Điểm giao tiếp, Điểm TB, Lý do không hài lòng do ĐTV, Dấu hiệu tiêu cực,
Cảnh báo, Tóm tắt hội thoại, Đánh giá/khuyến nghị AI, URL ghi âm.

Hãy làm 2 việc:

PHẦN 1 — PHÂN TÍCH & ĐÁNH GIÁ
1. Đọc toàn bộ dữ liệu (đọc hết các dòng, không chỉ mẫu đầu).
2. Tính điểm trung bình theo 4 trục: quy trình, thái độ, trách nhiệm, giao tiếp.
3. Tìm các mẫu lặp lại nhiều nhất trong cột "Đánh giá/khuyến nghị AI" — đây chính là
   những lỗi nghiệp vụ phổ biến nhất, không phải lỗi ngẫu nhiên của từng cuộc gọi.
4. Liệt kê 5 cuộc gọi có Điểm TB thấp nhất kèm lý do cụ thể (dùng làm case study).
5. Nêu rõ điểm mạnh (không chỉ điểm yếu) để chương trình đào tạo cân bằng.
6. Đề xuất giáo án đào tạo, số buổi, trọng tâm mỗi buổi — bám sát đúng 4 trục điểm có
   sẵn trong dữ liệu để sau này dễ đo lường tiến bộ.

PHẦN 2 — XÂY DỰNG TRANG WEB ĐÀO TẠO
Dựng thành 1 file HTML độc lập (vanilla HTML/CSS/JS, không cần backend), có 2 phần
chuyển đổi bằng nút toggle ở đầu trang:

A. PHẦN GIẢNG VIÊN (dashboard huấn luyện)
   - Tổng quan điểm trung bình 4 trục dưới dạng scorecard
   - Danh sách "vấn đề nghiệp vụ trọng tâm": mỗi vấn đề có mô tả, trích dẫn thật từ
     dữ liệu (cột khuyến nghị AI), và cách khắc phục cụ thể
   - Bảng giáo án (buổi / trọng tâm / nội dung / hình thức)
   - Danh sách các cuộc gọi cần nghe lại, hiển thị dạng "ticket" (mã cuộc gọi, điểm,
     chủ đề, lý do, khuyến nghị)

B. PHẦN ĐTV THỰC HÀNH
   - Quy trình chuẩn từng bước cho một cuộc gọi (rút ra từ dữ liệu, không bịa)
   - Thư viện câu nói mẫu, chia theo giai đoạn cuộc gọi (mở đầu / xác thực thông tin /
     xử lý khách bức xúc / cam kết thời gian / kết thúc) — lấy cảm hứng trực tiếp từ
     các câu ví dụ có trong cột khuyến nghị AI
   - Mô phỏng tình huống có thể tương tác: hiển thị câu nói của khách hàng (dựa trên
     tình huống thật trong dữ liệu), cho 3 lựa chọn trả lời, chọn xong hiện phản hồi
     ngay (đúng/cần điều chỉnh + lý do)
   - Bảng tự chấm điểm sau cuộc gọi (checklist theo 4 trục, có đếm điểm tự động bằng JS)

YÊU CẦU KỸ THUẬT
- 1 file HTML duy nhất, CSS và JS nhúng trong cùng file
- Không dùng localStorage/sessionStorage
- Responsive, chạy được trên di động
- Thiết kế không dùng màu/kiểu mặc định kiểu AI (tránh nền cream + serif + cam đất,
   tránh nền đen + neon). Chọn bảng màu và kiểu chữ phù hợp bối cảnh tổng đài viễn thông
   (VD: xanh navy/teal, chữ kỹ thuật cho số liệu, chữ display cho tiêu đề)
- Toàn bộ nội dung câu chữ, số liệu, ví dụ phải lấy từ dữ liệu thật đã phân tích ở
   Phần 1, không dùng nội dung chung chung
```

---

## Cách tuỳ biến prompt này

| Muốn thay đổi | Chỉnh chỗ nào trong prompt |
|---|---|
| Số buổi đào tạo | Sửa "Đề xuất giáo án... số buổi" |
| Thêm phần cho quản lý (không chỉ GV/ĐTV) | Thêm "PHẦN 3 — QUẢN LÝ" với các yêu cầu riêng |
| Nhiều ĐTV cùng lúc (so sánh nhóm) | Thêm câu: "So sánh điểm giữa các ĐTV, xếp hạng theo từng trục" |
| Xuất file Word/PDF thay vì web | Thay "PHẦN 2" bằng yêu cầu xuất báo cáo .docx |
| Cần số liệu chính xác 100% | Ghi rõ: "Dùng công cụ đọc toàn bộ file, không được ước tính nếu chưa đọc hết dữ liệu" |

---

## Lưu ý khi dùng lại

- Nếu bảng dữ liệu quá dài (hàng trăm dòng), nên **tải file Excel/CSV lên trực tiếp** thay vì
  dán link Google Sheet — việc đọc link Google Sheet qua trình duyệt có thể bị cắt bớt nội dung.
- Nếu muốn AI tính số liệu chính xác (không phải ước tính), yêu cầu rõ: dùng công cụ đọc file
  (ví dụ pandas/Excel) để tính trung bình thay vì đọc bằng mắt.
