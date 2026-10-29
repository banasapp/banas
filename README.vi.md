# Banas

**Ngôn ngữ:** [English](README.md) · [简体中文](README.zh-CN.md) · [繁體中文](README.zh-TW.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [ภาษาไทย](README.th.md) · [Tiếng Việt](README.vi.md)

Công cụ quản lý thư viện cục bộ và thu thập metadata: quét video trên máy, bổ sung ảnh bìa và tiêu đề theo mã sản phẩm, sắp xếp thư mục theo mẫu kiểu Emby hoặc tùy chỉnh.

Bạn tự thêm nguồn nội dung, nguồn tải xuống và cấu hình trang. Banas không lưu trữ hay vận hành bất kỳ trang web hoặc nội dung trực tuyến bên thứ ba nào.

Ngôn ngữ giao diện: English, 简体中文, 繁體中文, 日本語, 한국어, ภาษาไทย, Tiếng Việt.

Hỗ trợ sâu Jasna (giải mã video), Transub (phụ đề) và Transub Player. Đường dẫn đặt trong **Cài đặt → Công cụ** hoặc **Cài đặt → Trực tiếp**.

**Tài liệu:** [Cách thêm nguồn nội dung và nguồn tải xuống](HOW-TO-ADD-SOURCES.vi.md)

---

## Tóm tắt tính năng

| Mô-đun | Công dụng |
| --- | --- |
| **Thư viện** | Quét thư mục cục bộ; bổ sung ảnh bìa / tiêu đề / phụ đề; lưu trữ theo mẫu |
| **Ảnh bìa** | Tra cứu và lưu ảnh bìa theo mã (quy tắc có sẵn, chỉnh được) |
| **Lọc** | Danh mục diễn viên, nhãn, nhà sản xuất, thể loại; tìm kiếm và xem ngẫu nhiên |
| **Nguồn nội dung** | Danh sách trang tùy chỉnh; HTML / JSON / trình duyệt; chọn trường trực quan — [hướng dẫn](HOW-TO-ADD-SOURCES.vi.md) |
| **Nguồn tải xuống** | Tìm tài nguyên theo mã hoặc từ khóa; sao chép hoặc mở kết quả — [hướng dẫn](HOW-TO-ADD-SOURCES.vi.md) |
| **Theo dõi** | Quét nguồn nội dung có mục mới, hoặc quét mã đã có tài nguyên tải hay chưa |
| **Trực tiếp** | Duyệt streamer theo danh mục; yêu thích và gần đây; trang tích hợp hoặc Transub Player |
| **Lối tắt & Tác vụ** | Ghim nguồn thường dùng; xem và thử lại tác vụ nền |
| **Riêng tư** | Ẩn khay hệ thống, mật khẩu khởi động, phím sếp ẩn cửa sổ |

---

## Hướng dẫn dùng

Thanh biểu tượng trái chuyển mô-đun; thanh bên phụ liệt kê và quản lý; vùng chính hiển thị lưới ảnh bìa, bảng hoặc biểu mẫu cài đặt. Bánh răng cạnh tiêu đề thanh bên để quản lý (sắp xếp, sửa, xóa).

### Thư viện

1. Thanh bên **Thêm thư mục** → chọn thư mục, đặt tên, chọn nguồn ảnh bìa (quy tắc có sẵn / ảnh cục bộ cùng thư mục) → lưu.
2. Chọn thư mục hoặc **Tất cả thư mục** → **Quét**; dùng tìm kiếm và bộ lọc như thiếu ảnh bìa.
3. Thanh công cụ: chuyển **theo phim / theo diễn viên**, hàng loạt **điền ảnh bìa, tiêu đề, phụ đề**, cùng **lưu trữ** và **giải mã Jasna**.
4. Bấm ảnh bìa để xem chi tiết (phát, mở thư mục, sửa); chuột phải để tra tiêu đề / ảnh bìa, lưu trữ hoặc chuyển sang thư mục diễn viên.

Cài đặt liên quan: **Tiêu đề & diễn viên**, **Lưu trữ phim** (mẫu đường dẫn, `movie.nfo` / `poster.jpg`), **Công cụ** (Jasna, Transub).

### Ảnh bìa (tra mã)

1. Ở cuối **Lối tắt**, nhập một hoặc nhiều mã (hoặc kéo tệp vào vùng chính; tên tệp dùng làm mã) → **Tìm**.
2. Trong lưới kết quả, bấm để xem trước và đổi nguồn ảnh; chuột phải để lưu ảnh bìa.
3. Sửa và chẩn đoán quy tắc tại **Cài đặt → Ảnh bìa phim**.

### Lọc

1. Thanh bên **Diễn viên / Nhãn / Nhà sản xuất / Thể loại** → tìm và chọn mục trong cửa sổ danh mục.
2. Vùng chính hiện video liên quan; **Làm mới** trên thanh bên cập nhật gói danh mục.
3. **Quản lý** để thêm, sửa, xóa, nhập/xuất; dữ liệu nằm trong `catalog.banascat`.

### Nguồn nội dung

1. **Thêm** → nhập URL trang → **phân tích thông minh** hoặc **chọn trực quan** (mục, mã, ảnh bìa, phân trang…) → thử → lưu; có thể nhóm.
2. Mở nguồn: đổi cột, tìm trong trang, phân trang tường ảnh bìa.
3. Ảnh bìa có thể phát (ưu tiên cục bộ, không thì phân tích rồi Transub Player), tra tải xuống, hoặc theo dõi tài nguyên; menu nguồn bật theo dõi tổng hợp hoặc thêm lối tắt.
4. Thanh bên **Nhập / Xuất** gói mã hóa để đồng bộ nhiều máy.

Chi tiết: [Cách thêm nguồn nội dung và nguồn tải xuống](HOW-TO-ADD-SOURCES.vi.md).

### Nguồn tải xuống

1. **Thêm nguồn tải xuống** → cấu hình URL tìm (có chỗ dành từ khóa) và trường danh sách → lưu.
2. Mở nguồn, nhập mã → **Tìm tài nguyên** → mở chi tiết, sao chép magnet hoặc tải trong bảng.
3. Có thể ghim lối tắt; nhập/xuất tương tự. Nguồn tải mặc định cho theo dõi tài nguyên ở **Cài đặt → Theo dõi**.

Chi tiết: [Cách thêm nguồn nội dung và nguồn tải xuống](HOW-TO-ADD-SOURCES.vi.md).

### Theo dõi

1. **Thêm theo dõi**: **Tổng hợp** (chọn nguồn nội dung cho mã mới) hoặc **Tài nguyên** (nhập mã để xem có tải được không).
2. Xem kết quả trong **Theo dõi tổng hợp / Theo dõi tài nguyên**; thanh công cụ **quét ngay** hoặc xóa.
3. Chuông trên thanh nguồn nội dung hoặc ảnh bìa cũng bật/tắt. Khoảng thời gian ở **Cài đặt → Theo dõi**.

### Trực tiếp

1. Chọn danh mục, hoặc mở **Yêu thích / Gần đây**; tìm streamer.
2. Mở phòng: chọn **web tích hợp** (tương tác) hoặc **Transub Player** (ghi hình; phòng công khai) từ thanh trên hoặc **Cài đặt → Trực tiếp**.
3. Tim để yêu thích; hiện danh mục và gương trực tiếp ở **Cài đặt → Trực tiếp**.

### Lối tắt

1. Thanh bên **+** → chọn nguồn nội dung hoặc tải xuống thường dùng → lưu; một lần bấm mở duyệt hoặc tra cứu.
2. **Tra mã** ở dưới tìm ảnh bìa trực tiếp.
3. **Cài đặt → Chung → Trang khởi động** chọn mô-đun mở ở vùng chính (thanh trái vẫn có thể ở Lối tắt).

### Tác vụ

**Tác vụ** trên thanh trái mở hàng đợi nền (quét, tải ảnh bìa, quét theo dõi, lưu trữ, giải mã…). Xem tiến độ, **thử lại** hoặc **hủy**, và xóa mục đã xong.

### Riêng tư & công cụ

- **Cài đặt → Riêng tư & bảo mật**: ẩn khay khi đóng/thu nhỏ, mật khẩu khởi động, phím sếp.
- **Cài đặt → Công cụ**: đường dẫn Jasna, Transub, Transub Player; menu Công cụ trên thanh trái cũng mở được.
- **Cài đặt → Sao lưu**: sao lưu / khôi phục CSDL, hoặc xuất / nhập cấu hình và gói nguồn (không gồm mật khẩu và mã kích hoạt).

---

## Dữ liệu

Chỉ mục video, cài đặt và danh mục lọc lưu trên máy, không tải lên.

```
Thư viện & cài đặt: <thư mục Banas.exe>/data/javgt.sqlite
Danh mục lọc:       <thư mục Banas.exe>/data/catalog.banascat
```

Sao lưu hoặc chuyển máy: sao chép cả thư mục `data`.

---

## Giấy phép

Dùng thử đủ tính năng 3 ngày lần đầu. Hết dùng thử vẫn quét, duyệt và sắp xếp thư viện cục bộ được; điền online, sắp xếp hàng loạt, nguồn nội dung, nguồn tải và theo dõi cần Pro.

Mua trên UniFans, đợi mã kích hoạt rồi dán vào **Cài đặt → Giấy phép**. Mỗi mã gắn một máy; đổi gắn cách 30 ngày. Thời hạn: một năm, hai năm hoặc vĩnh viễn.

---

## Lưu ý

Cài đặt, thư viện và giấy phép chủ yếu lưu trên máy. Khi online có thể gửi thông tin kỹ thuật hạn chế (như ID thiết bị) để kiểm tra giấy phép.

Tính khả dụng và tuân thủ pháp luật của nguồn do người dùng tự thêm (gồm danh mục lọc, nguồn nội dung, nguồn tải), proxy và trang bên thứ ba do người dùng chịu trách nhiệm.
