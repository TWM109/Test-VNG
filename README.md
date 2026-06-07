# DT3Q Sinh Nhật 7 Tuổi - Admin Operation Tool

## 1. Mục Tiêu

Tool này phục vụ việc cấu hình và vận hành promotion sinh nhật DT3Q 7 tuổi. Admin cấu hình tại `index.html`, sau đó preview kết quả trên FE `vng.html`.

Phạm vi bài tập không kết nối API thật, nên các số liệu thống kê, tồn kho, claim, conversion và doanh thu đang là mock/estimate để minh họa workflow vận hành.

## 2. Promotion Gồm Bao Nhiêu Module?

Promotion hiện được hiểu là 4 module chính:

| Module | Mapping trong bài | Nội dung cấu hình |
|---|---|---|
| Thiệp Mời Đại Tiệc | Community Milestone | Start/end date, các mốc tích lũy, ảnh quà, ảnh tooltip, enabled, danh sách quà theo từng mốc, thể lệ HTML |
| Mở Quà Sinh Nhật | Vòng quay Lucky Spin + Nhiệm vụ + Tích lũy nhận lượt | Start/end date, phần thưởng mock data, ảnh tooltip, rate, giới hạn phát, nhiệm vụ nhận lượt, direct URL, mốc tích lũy nhận lượt, ảnh quà, ảnh tooltip, thể lệ HTML |
| Tích Bánh Mở Quà VIP | Đổi quà | Start/end date, vật phẩm đổi, số lượng item nhận mỗi lần, số bánh điều kiện đổi, giới hạn phát, enabled, link ảnh quà, thể lệ HTML |
| Bàn Tiệc Sinh Nhật | Lời chúc / bình chọn / mission phụ | Start/end date, thể lệ HTML, danh sách nhiệm vụ nhận lượt, direct URL |

## 3. Persona Người Dùng Tool

### Primary persona: Event Operation Admin

Người vận hành sự kiện hằng ngày. Họ không cần code, nhưng cần sửa nhanh cấu hình promotion và xem preview trước khi publish.

Công việc hằng ngày:

- Cập nhật thời gian bắt đầu/kết thúc từng module.
- Điều chỉnh danh sách quà, hình ảnh quà/tooltip, rate, giới hạn phát và điều kiện đổi.
- Bật/tắt nhiệm vụ, sửa số lượt thưởng và link điều hướng.
- Sửa nội dung thể lệ HTML theo yêu cầu campaign.
- Chạy validation trước khi save.
- Mở FE preview để đảm bảo cấu hình hiển thị đúng.
- Xem dashboard mock để theo dõi tình trạng event.

### Secondary persona: Campaign Owner / PO

Người review tính đúng của campaign:

- Kiểm tra module có đúng scope promotion không.
- Kiểm tra copywriting, thể lệ, mốc thưởng.
- Kiểm tra tiến độ mốc cộng đồng và mốc tiếp theo.
- Kiểm tra rủi ro cấu hình sai: rate không đủ 100%, end date nhỏ hơn start date, thiếu ảnh, thiếu quà, giới hạn phát/quantity không hợp lệ.

## 4. Các Tính Năng Đã Có

### Configuration

- Cấu hình start/end date theo module.
- Cấu hình Thiệp Mời Đại Tiệc như Community Milestone.
- Cấu hình Mở Quà Sinh Nhật: Vòng quay Lucky Spin, nhiệm vụ nhận lượt, tích lũy nhận lượt.
- Cấu hình Tích Bánh Mở Quà VIP.
- Cấu hình Bàn Tiệc Sinh Nhật: thể lệ và nhiệm vụ.
- Cấu hình thể lệ HTML cho các module chính.
- FE preview đọc config từ `localStorage` và reflect lên `vng.html`.

### Guide Config Mốc Tích Lũy Thiệp Mời Đại Tiệc

1. Vào tab `Config`, mở module `Cấu Hình Mốc Tích Lũy Thiệp Mời Đại Tiệc`.
2. Chọn `Start Date` và `End Date` cho thời gian hiệu lực của module.
3. `Số mốc tích lũy` là tổng số block mốc đang hiển thị; dùng `+ Thêm mốc` để thêm mốc hoặc `Xóa mốc` để bỏ mốc.
4. Nhập `Số mốc tích lũy`, `Link ảnh quà` và `Link ảnh Tooltip` cho từng mốc; dùng `Mở ảnh` để kiểm tra trực tiếp từng link ảnh. Link test: `https://freepngimg.com/thumb/goku/20182-6-goku-thumb.png` hoặc `https://freepngimg.com/thumb/the_legend_of_zelda/20983-8-zelda-link-photo-thumb.png`.
5. Chọn danh sách `Quà tặng` từ mock data và nhập quantity cho từng quà trong mốc.
6. Dùng `Enabled` để bật/tắt mốc. Nếu admin không cấu hình, FE dùng fallback default của trang event VNG hiện tại.

### Guide Config Vòng Quay Lucky Spin

1. Vào tab `Config`, mở module `Config Mở quà sinh nhật`, phần `Vòng quay Lucky Spin`.
2. Ở mỗi dòng, chọn `Quà tặng` từ danh sách mock data.
3. Dán `Link ảnh quà`; cột `Xem ảnh` mở ảnh trong tab mới để kiểm tra nhanh, và khi Save & Preview ảnh sẽ reflect ra `vng.html`. Link test: `https://freepngimg.com/thumb/goku/20182-6-goku-thumb.png` hoặc `https://freepngimg.com/thumb/the_legend_of_zelda/20983-8-zelda-link-photo-thumb.png`.
4. Nhập `Rate (%)`; tổng rate của các quà đang enabled phải bằng `100%`.
5. Nhập `Giới hạn phát` để mock limit/tồn kho phát thưởng cho từng giải.
6. Dùng `Enabled` để bật/tắt quà hoặc nút `Xóa` để loại quà khỏi config.
7. Nếu admin không lưu config hoặc dữ liệu spin không đủ hợp lệ, FE dùng fallback default của trang event VNG hiện tại.

### Guide Config Nhiệm Vụ Nhận Lượt

1. Vào module `Config Mở quà sinh nhật`, phần `Nhiệm Vụ Nhận Lượt`.
2. Chọn `Loại` nhiệm vụ: `Hàng ngày` hoặc `Cố định`.
3. Nhập `Nội dung HTML` mô tả nhiệm vụ và phần thưởng lượt quay.
4. Nhập `Lượt quay` sẽ cộng cho user sau khi hoàn thành nhiệm vụ.
5. Chọn text nút `Thực Hiện` hoặc `Nhận Lượt`, rồi nhập `Direct Url` nếu cần điều hướng.
6. Dùng `Enabled` để bật/tắt nhiệm vụ, `Xóa` để bỏ nhiệm vụ, hoặc `+ Thêm nhiệm vụ` để thêm dòng mới.

Ghi chú: mock data mặc định của phần nhiệm vụ nhận lượt hiện được rút gọn còn 7 nhiệm vụ để dễ review hơn.

### Guide Config Tích Lũy Nhận Lượt

1. Vào module `Config Mở quà sinh nhật`, phần `Tích Lũy Nhận Lượt`.
2. `Số mốc nhận lượt` là tổng số block mốc đang hiển thị; dùng `+ Thêm mốc tích lũy` để tăng số mốc hoặc `Xóa mốc` để giảm số mốc.
3. Nhập `Số lượt tích lũy` cho từng mốc để FE biết người chơi cần đạt bao nhiêu lượt quay.
4. Dán `Link ảnh quà` và `Link ảnh Tooltip`; dùng `Mở ảnh` để kiểm tra trực tiếp từng ảnh. Link test: `https://freepngimg.com/thumb/goku/20182-6-goku-thumb.png` hoặc `https://freepngimg.com/thumb/the_legend_of_zelda/20983-8-zelda-link-photo-thumb.png`.
5. Chọn danh sách `Quà tặng` từ mock data và nhập quantity cho từng quà trong mốc.
6. Khi Save & Preview, `vng.html` sẽ reflect cả ảnh quà của mốc và ảnh tooltip.
7. Nếu admin không cấu hình, FE tiếp tục dùng fallback default của trang event VNG hiện tại.

### Guide Config Tích Bánh Mở Quà VIP

1. Vào tab `Config`, mở module `Tích bánh mở quà Vip`.
2. Chọn `Start Date` và `End Date` cho thời gian hiệu lực của module đổi quà VIP.
3. Chọn `Vật Phẩm`, nhập `Số lượng`, `Số Bánh Tích Lũy` và `Giới hạn phát`.
4. Dán `Link ảnh quà` và dùng `Mở ảnh` để kiểm tra trực tiếp ảnh sẽ reflect ra FE. Link test: `https://freepngimg.com/thumb/goku/20182-6-goku-thumb.png` hoặc `https://freepngimg.com/thumb/the_legend_of_zelda/20983-8-zelda-link-photo-thumb.png`.
5. Dùng `Enabled` để bật/tắt vật phẩm, `Xóa` để bỏ vật phẩm, hoặc `+ Thêm vật phẩm` để thêm dòng mới.
6. Nếu admin không cấu hình, FE tiếp tục dùng fallback default của trang event VNG hiện tại.

### Guide Config Bàn Tiệc Sinh Nhật

1. Vào tab `Config`, mở module `Bàn tiệc sinh nhật`.
2. Chọn `Start Date` và `End Date` cho thời gian hiệu lực của module.
3. Nhập `Thể lệ (HTML)` cho popup thể lệ của Bàn tiệc sinh nhật.
4. Trong phần `Nhiệm Vụ Nhận Lượt`, cấu hình `Loại`, `Nội dung HTML`, `Lượt quay`, text nút và `Direct Url`.
5. Dùng `Enabled` để bật/tắt nhiệm vụ, `Xóa` để bỏ nhiệm vụ, hoặc `+ Thêm nhiệm vụ` để thêm dòng mới.
6. Nếu admin không cấu hình, FE tiếp tục dùng fallback default/mock hiện tại.

## 5. Validation

- Tổng rate vòng quay phải bằng `100%`.
- Start/end date: end date phải lớn hơn start date.
- Các field số tự nhiên lớn hơn 0 được chặn ngay lúc nhập với các field quan trọng.
- Giới hạn phát, mốc tích lũy, lượt quay, quantity item không được là số thập phân/chữ/nhỏ hơn hoặc bằng 0 khi cấu hình đang enabled.
- Cảnh báo khi thiếu ảnh quà hoặc ảnh tooltip ở các mốc cần preview ra FE.
- Cảnh báo/lỗi khi reward/item đang enabled nhưng giới hạn phát không hợp lệ.

## 6. Dashboard / Report

- KPI tổng participants, conversion, doanh thu ước tính, tổng lượt quay đã dùng.
- Bảng tổng số người tham gia từng module.
- Chart participants theo ngày.
- Chart Top 10 phần thưởng được nhận nhiều nhất.
- Bảng Lucky Spin theo từng giải: rate config, claim rate mock, lượt đã dùng, lượt còn lại và trạng thái.
- Widget Thiệp Mời Đại Tiệc hiển thị tổng lời chúc hiện tại, mốc đã đạt, số lời chúc còn thiếu tới mốc kế tiếp và đủ 7 mốc quà theo config.
- Thanh tiến độ Thiệp Mời Đại Tiệc đang tính theo `tổng lời chúc hiện tại / mốc kế tiếp`. Ví dụ 32.699 / 50.000 tương đương khoảng 65%.
- Widget Tích Lũy Nhận Lượt hiển thị số user reach mock theo từng mốc lượt quay đang config trong admin.
- Bảng trạng thái vật phẩm đổi quà gồm giới hạn phát, đã phát mock, claim rate mock và còn lại mock.
- Conversion funnel mock: visit -> login -> mission done.
- Doanh thu ước tính mock từ các package đang enabled.

## 7. Giới Hạn Hiện Tại

Do bài tập không kết nối API, các mục sau chỉ là mock/estimate:

- Tồn kho thực tế của vật phẩm.
- Số lượt quay đã dùng/còn lại theo từng giải đang được mô phỏng từ config rate và mock participants.
- Claim rate thực tế so với cấu hình đang là mock vì chưa có claim API/log.
- Top 10 phần thưởng nhận nhiều nhất đang được mô phỏng từ spin/shop mock claimed count.
- Conversion thật theo chuỗi visit -> login -> mission done.
- Doanh thu thật từ gói nạp; dashboard hiện estimate từ package config.

## 8. Ghi Chú Nghiệp Vụ Về Stock / Tồn Kho

Trong bài tập này nên tách rõ 2 khái niệm:

- `quantity`: số lượng item người chơi nhận được mỗi lần claim/đổi.
- `stock` hoặc `limit`: tổng số lượng tối đa có thể phát trong sự kiện. Trong UI nên hiểu là `Giới hạn phát`.

Không có API thì không thể biết tồn kho realtime. Tuy nhiên admin tool vẫn cho cấu hình `stock/limit` ban đầu để validation và dashboard mock có cơ sở tính:

- `remaining = configured stock - mock claimed count`
- Warning khi stock = 0 nhưng reward/item vẫn enabled
- Warning khi claimed count mock > configured stock

Trong bản demo, `remaining` là mock. Bản production cần claim API/log để tính remaining thật.

## 9. Cách Chạy

1. Mở `index.html` để cấu hình admin.
2. Chạy validation.
3. Save Config hoặc Save & Preview.
4. FE preview mở `vng.html` và đọc config từ `localStorage`.
