# Cách thêm nguồn nội dung và nguồn tải xuống

**Ngôn ngữ:** [English](HOW-TO-ADD-SOURCES.md) · [简体中文](HOW-TO-ADD-SOURCES.zh-CN.md) · [繁體中文](HOW-TO-ADD-SOURCES.zh-TW.md) · [日本語](HOW-TO-ADD-SOURCES.ja.md) · [한국어](HOW-TO-ADD-SOURCES.ko.md) · [ภาษาไทย](HOW-TO-ADD-SOURCES.th.md) · [Tiếng Việt](HOW-TO-ADD-SOURCES.vi.md)

**Nguồn nội dung** dùng để duyệt danh sách site và tường bìa. **Nguồn tải xuống** dùng để tìm magnet (v.v.) theo mã sản phẩm. Banas không lưu trữ site bên thứ ba — bạn tự cấu hình URL và bộ chọn.

Quay lại [README](README.vi.md) chính.

---

## Nguồn nội dung

Thanh trái → **Nguồn nội dung** → thanh bên **Thêm**.

### Bước 1 — URL đích

| Tùy chọn | Ý nghĩa |
| --- | --- |
| **URL đích** | Trang danh sách hoặc trang chủ, ví dụ `https://example.com/` |
| **Bật VPN** | Cần cấu hình node/đăng ký trong **Cài đặt → Mạng** trước |
| **Thêm trực quan**（khuyến nghị, mặc định bật） | Chọn trường trên trang; không cần viết CSS tay |
| **Phân tích tự động** | Khi tắt trực quan; ứng dụng đoán bộ chọn |
| **Bỏ qua chống bot** | Cho Cloudflare…; chế độ trực quan dùng trang nhúng |

Nhập URL → **Tiếp**.

### Chọn trực quan（khuyến nghị）

Làm theo bước trên bảng và bấm phần tử tương ứng:

1. **Danh sách mục** — một thẻ danh sách（cả hàng/thẻ）
2. **Mã/tiêu đề** — chữ mã hoặc tiêu đề trong mục
3. **Bìa**（tuỳ chọn）— ảnh bìa
4. **Studio / Diễn viên / Phân trang**（tuỳ chọn）
5. **Chuyên mục** — liên kết điều hướng

Chuyển **Chọn / Nhấp**: xác nhận tuổi hoặc đăng nhập dùng「Nhấp」; lấy bộ chọn dùng「Chọn」. Nếu Cloudflare không qua, dùng **Mở bằng Camoufox**. Xong rồi vào form xác nhận.

### Bước 2 — Xác nhận thông tin nguồn

#### Cơ bản

| Trường | Cách điền |
| --- | --- |
| **Tên** | Nhãn trên thanh bên（bắt buộc） |
| **Nhóm** | Pro; tạo nhóm trước nếu cần |
| **URL danh sách** | Mẫu danh sách; có thể dùng thẻ bên dưới |
| **Chế độ lấy** | `Trang HTML` / `JSON API` / `Render JS（trình duyệt）` |
| **Theo dõi mục mới** | Pro; dùng cho theo dõi tổng hợp |

**Thẻ URL danh sách**（sao chép từ「Trợ giúp thẻ」）:

| Thẻ | Ý nghĩa | Ví dụ |
| --- | --- | --- |
| `${page}` | Số trang; với `/page/${page}`, trang 1 bỏ `/page/1` | `https://xxx.com/page/${page}` |
| `${page*}` | Phân trang tuỳ chọn; trang 1 bỏ cả đoạn | `https://xxx.com/?page=${page*}` |
| `${keyword}` / `${wd}` / `${q}` | Từ khoá tìm kiếm | Dùng trong URL tìm kiếm |
| `${date}` | Hôm nay `YYYY-MM-DD` | `?dateFrom=${date}` |

#### Phân tích（HTML / trình duyệt）

| Trường | Cách điền |
| --- | --- |
| **Phân tích thông minh** | Bật: trích mã theo quy tắc. Tắt: phải điền bộ chọn |
| **Bộ chọn mục** | Mỗi hàng, ví dụ `.movie-box`, `article.item` |
| **Bộ chọn mã/tiêu đề** | Tương đối trong từng mục |
| **Studio / Diễn viên / Ngày** | Tuỳ chọn, tương đối mục |
| **Bỏ tiêu đề（chỉ giữ mã）** | Khi tiêu đề lẫn ngôn ngữ khác |
| **Regex mã** | Lấy mã từ tiêu đề |
| **Bộ chọn chờ** | Chế độ trình duyệt: chờ phần tử này rồi mới phân tích |

Chế độ JSON: đường dẫn danh sách, trường tiêu đề/bìa/ID chi tiết, mẫu URL chi tiết（có preset MacCMS）.

#### Bìa

| Tuỳ chọn | Ý nghĩa |
| --- | --- |
| **Lai**（thường dùng） | Quy tắc HD có sẵn trước, rồi ảnh site |
| **Có sẵn** | Chỉ quy tắc có sẵn theo mã |
| **Từ site** | Chỉ bộ chọn ảnh trên trang danh sách |

Site / lai cần **Bộ chọn ảnh** và **Thuộc tính ảnh**（ví dụ `data-src, src`）.

#### Nâng cao（thường dùng）

| Trường | Cách điền |
| --- | --- |
| **URL trang công bố** | Nếu URL chính chết, lấy địa chỉ mới từ trang này rồi thử lại |
| **Tìm trên site** | Bật và điền URL tìm, ví dụ `/search?q=${keyword}` |
| **Phát trên site nguồn** | Pro; giải m3u8/liên kết trực tiếp từ bìa |

Bảng phải **Quản lý chuyên mục**: 「Lấy chuyên mục」 hoặc thêm tên + mẫu URL thủ công.

Bấm **Kiểm tra** đến khi có mục rồi **Lưu**.

---

## Nguồn tải xuống

Thanh trái → **Nguồn tải xuống** → **Thêm nguồn tải xuống**.

### Bước 1 — URL đích

Nhập trang chủ hoặc trang tìm, ví dụ `https://1cili.net/`. Tuỳ chọn:

- **Bật VPN**
- **Bỏ qua chống bot**（chậm hơn; dùng cho site challenge）

**Tiếp** — ứng dụng cố nhận URL tìm và trường danh sách.

### Bước 2 — Xác nhận quy tắc tìm

| Trường | Cách điền |
| --- | --- |
| **Tên** | Tên hiển thị |
| **Khớp host** | Thường tự điền hostname |
| **URL tìm** | **Phải có placeholder từ khoá**, ví dụ `https://xxx.com/search?q=${keyword}` |
| **Danh sách** | Bộ chọn mỗi hàng kết quả |
| **Tiêu đề / Kích thước / Ngày** | Tương đối từng mục |
| **Magnet** | Bộ chọn liên kết `magnet:` trên danh sách |
| **Trang chi tiết** | Bộ chọn liên kết chi tiết |
| **Magnet ở trang chi tiết** | Khi danh sách không có magnet; mở chi tiết để lấy |
| **Từ khoá thử** | Ví dụ `IPX-001` — **Kiểm tra** trước khi lưu |

URL tìm còn hỗ trợ `${wd}`, `${q}`, `${code}`, `${CODE}`（hoa）, `{0}`（từ khoá）, `{1}` / `${page}`（trang）.

Khi kiểm tra có hàng thì **Lưu**. Mở nguồn, nhập mã → **Tìm tài nguyên** → sao chép magnet hoặc mở chi tiết.

---

## Sau khi lưu

| Mục tiêu | Thao tác |
| --- | --- |
| Duyệt tường bìa | Mở nguồn nội dung → chuyên mục / tìm / phân trang |
| Tìm tải xuống | Nút tải trên bìa, hoặc tìm trong nguồn tải |
| Theo dõi phim mới | Bật「Theo dõi mục mới」hoặc theo dõi tổng hợp |
| Chờ magnet của một mã | Cần nguồn tải trước → chuông trên bìa / theo dõi tài nguyên |
| Đồng bộ nhiều máy | **Nhập/Xuất** trên thanh bên（gói mã hoá）— [Cách xuất và nhập nguồn](HOW-TO-IMPORT-EXPORT-SOURCES.vi.md) |

Nguồn tải mặc định cho theo dõi tài nguyên: **Cài đặt → Theo dõi**.

---

## Lỗi thường gặp

1. **URL tìm thiếu `${keyword}`** — tìm luôn sai.
2. **Chọn khối chi tiết thay vì thẻ danh sách** — trong thêm trực quan hãy chọn thẻ danh sách.
3. **Bộ chọn theo cả trang** — tiêu đề/magnet phải tương đối với **mục**.
4. **Site challenge mà không dùng Camoufox / trực quan** — rỗng hoặc lỗi.
5. **Bật VPN nhưng chưa cấu hình mạng** — đặt **Cài đặt → Mạng** trước.
6. **Giới hạn gói** — miễn phí giới hạn số nguồn nội dung; tải / theo dõi cần dùng thử hoặc Pro.
