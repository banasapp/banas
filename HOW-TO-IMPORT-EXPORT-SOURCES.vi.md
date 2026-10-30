# Cách xuất và nhập nguồn nội dung & nguồn tải xuống

**Ngôn ngữ:** [English](HOW-TO-IMPORT-EXPORT-SOURCES.md) · [简体中文](HOW-TO-IMPORT-EXPORT-SOURCES.zh-CN.md) · [繁體中文](HOW-TO-IMPORT-EXPORT-SOURCES.zh-TW.md) · [日本語](HOW-TO-IMPORT-EXPORT-SOURCES.ja.md) · [한국어](HOW-TO-IMPORT-EXPORT-SOURCES.ko.md) · [ภาษาไทย](HOW-TO-IMPORT-EXPORT-SOURCES.th.md) · [Tiếng Việt](HOW-TO-IMPORT-EXPORT-SOURCES.vi.md)

Đóng gói **nguồn nội dung** hoặc **nguồn tải xuống** đã cấu hình thành gói mã hóa (`.banas`) để đổi máy, sao lưu hoặc đồng bộ sang thiết bị khác của bạn. Gói nội dung và gói tải xuống tách biệt—không trộn.

Thêm nguồn mới: [Cách thêm nguồn nội dung và nguồn tải xuống](HOW-TO-ADD-SOURCES.vi.md). Quay lại [README](README.vi.md) chính.

---

## Mở ở đâu

| Cần xuất / nhập | Lối vào |
| --- | --- |
| Nguồn nội dung | Thanh biểu tượng trái → **Nguồn nội dung** → **Nhập / Xuất** cạnh tiêu đề thanh bên (mũi tên hai chiều) |
| Nguồn tải xuống | Thanh biểu tượng trái → **Nguồn tải xuống** → **Nhập / Xuất** cạnh tiêu đề thanh bên |

Hộp thoại có hai tab: **Xuất** và **Nhập**. Gợi ý cho biết tệp được lưu mã hóa; khi nhập có thể chỉ chọn mục cần thiết.

---

## Xuất

1. Mở **Nhập / Xuất** của mô-đun tương ứng, đảm bảo đang ở tab **Xuất**.
2. Danh sách hiện các nguồn trên máy (tên + URL). Mặc định chọn hết; bỏ chọn phần không muốn.
3. Bấm **Xuất đã chọn** → chọn đường dẫn và tên tệp trong hộp lưu.
4. Tên mặc định dạng:
   - Nguồn nội dung: `banas-custom-sources-YYYY-MM-DD.banas`
   - Nguồn tải xuống: `banas-download-sources-YYYY-MM-DD.banas`
5. Thành công sẽ hiện kiểu 「Đã xuất N mục」.

**Trong gói có gì**

| Loại | Bao gồm |
| --- | --- |
| Nguồn nội dung | Tên, URL danh sách, trường bìa/chi tiết, cấu hình đầy đủ (bộ chọn, mục, công tắc theo dõi…); tên nhóm nếu có |
| Nguồn tải xuống | Tên, URL tìm kiếm, cấu hình đầy đủ (bộ chọn danh sách / magnet…) |

Tệp mã hóa chỉ ứng dụng này giải được—nhập trong Banas, không sửa như JSON thuần.

Nếu thanh bên chưa có nguồn nào, hiện 「Không có nguồn để xuất」—hãy thêm trước hoặc nhập từ nơi khác.

---

## Nhập

1. Mở **Nhập / Xuất** trong mô-đun **cùng loại** (gói nội dung → nguồn nội dung; gói tải xuống → nguồn tải xuống), chuyển tab **Nhập**.
2. Bấm **Chọn tệp nhập…**, chọn tệp `.banas` đã xuất trước đó.
3. Sau khi giải mã, liệt kê các mục trong gói; mặc định chọn hết—bỏ chọn phần không cần.
4. Bấm **Nhập đã chọn**. Kết quả dạng: 「Nhập xong: thêm X, bỏ qua Y, lỗi Z」.

**Ý nghĩa kết quả**

| Kết quả | Ý nghĩa |
| --- | --- |
| **Thêm** | Máy chưa có mục tương ứng, đã ghi |
| **Bỏ qua** | Đã có nguồn 「cùng tên + cùng URL」; không ghi đè, không đổi cấu hình local |
| **Lỗi** | Mục không hợp lệ, hoặc chạm hạn mức / cần Pro; khi hết hạn mức có thể dừng các mục sau |

**Ghi chú thêm cho nguồn nội dung**

- Nếu gói có tên nhóm và giấy phép cho phép nhóm nguồn nội dung: tái sử dụng nhóm cùng tên hoặc tạo mới.
- Hạn mức miễn phí có giới hạn; vượt sẽ lỗi hoặc gợi ý dùng thử/Pro.
- Nguồn bật 「Theo dõi mục mới」 sẽ khởi tạo lại trạng thái theo dõi theo ID mới sau khi nhập.

**Lưu ý**

- Chỉ nhập đúng mô-đun: trang nội dung không mở được gói tải xuống (và ngược lại)—báo không hợp lệ / hỏng.
- Sai phần mở rộng, tệp hỏng, hoặc không phải gói từ ứng dụng này → 「Tệp nhập không hợp lệ hoặc bị hỏng」.
- Chọn tệp rồi để lâu chưa nhập, bản xem trước có thể hết hạn → 「Bản xem trước nhập đã hết hạn; hãy chọn lại tệp」.

---

## Cách dùng gợi ý

| Tình huống | Cách làm |
| --- | --- |
| Đổi máy / đồng bộ nhiều máy | Xuất `.banas` trên máy cũ → chép → nhập ở mô-đun đúng loại và chọn nguồn cần |
| Chỉ sao lưu vài nguồn | Bỏ chọn phần còn lại khi xuất |
| Gói từ người khác | Kiểm tra URL danh sách rồi mới chọn; mục cùng tên+URL sẽ bị bỏ qua |
| Sao lưu toàn bộ (cài đặt, lối tắt…) | Dùng **Cài đặt → Sao lưu** xuất/nhập gói dữ liệu (JSON)—khác gói `.banas` thanh bên |

Gói thanh bên dành cho chỉ chuyển nguồn nội dung hoặc tải xuống; gói dữ liệu trong Cài đặt bao phủ cấu hình và thư viện rộng hơn. Hai loại không thay thế nhau.

---

## Lỗi thường gặp

1. **Nhập gói tải xuống trong nguồn nội dung (hoặc ngược lại)** → loại không khớp, không nhập được.
2. **Nghĩ nhập sẽ ghi đè nguồn cùng tên** → thực tế khử trùng bằng 「tên + URL」; đã có thì bỏ qua. Muốn cập nhật hãy sửa/xóa local rồi nhập lại.
3. **Sửa `.banas` như văn bản** → gói mã hóa; chỉ xuất/nhập trong ứng dụng.
4. **Hết slot nguồn nội dung miễn phí** → xóa nguồn không dùng hoặc nâng cấp rồi nhập.
5. **Không tìm thấy tệp đã xuất** → xem đường dẫn lúc lưu; tên mặc định có ngày và `custom` / `download`.
6. **Muốn mang theo nhóm và cấu hình theo dõi** → xuất nguồn nội dung từ thanh bên đã ghi trong gói; chỉ chép CSDL là đường khác.
