# DT3Q Sinh Nhat 7 Tuoi - Admin Operation Tool

## 1. Muc tieu

Tool nay phuc vu viec cau hinh va van hanh promotion sinh nhat DT3Q 7 tuoi. Admin cau hinh tai `index.html`, sau do preview ket qua tren FE `vng.html`.

Pham vi bai tap khong ket noi API that, nen cac so lieu thong ke, ton kho, claim va doanh thu dang la mock/estimate de minh hoa workflow van hanh.

## 2. Promotion gom bao nhieu module?

Promotion hien duoc hieu la 4 module chinh:

| Module | Mapping trong bai | Noi dung cau hinh |
|---|---|---|
| Thiep Moi Dai Tiec | Community Milestone | Start/end date, cac moc tich luy, anh tooltip, danh sach qua theo tung moc, the le HTML |
| Mo Qua Sinh Nhat | Vong quay + Nhiem vu + Tich luy nhan luot | Start/end date, danh sach phan thuong, rate (%), gioi han phat moi giai, enabled, nhiem vu nhan luot, direct URL, moc tich luy nhan luot, the le HTML |
| Tich Banh Mo Qua VIP | Doi qua | Start/end date, vat pham doi, so luong item nhan moi lan, so banh dieu kien doi, gioi han phat, enabled, anh tooltip, the le HTML |
| Ban Tiec Sinh Nhat | Loi chuc / binh chon / mission phu | Start/end date, the le HTML, danh sach nhiem vu nhan luot, direct URL |

## 3. Persona nguoi dung tool

### Primary persona: Event Operation Admin

Nguoi van hanh su kien hang ngay. Ho khong can code, nhung can sua nhanh cau hinh promotion va xem preview truoc khi publish.

Cong viec hang ngay:

- Cap nhat thoi gian bat dau/ket thuc tung module.
- Dieu chinh danh sach qua, rate, gioi han phat va dieu kien doi.
- Bat/tat nhiem vu, sua so luot thuong va link dieu huong.
- Sua noi dung the le HTML theo yeu cau campaign.
- Chay validation truoc khi save.
- Mo FE preview de dam bao cau hinh hien thi dung.
- Xem dashboard mock de theo doi tinh trang event.

### Secondary persona: Campaign Owner / PO

Nguoi review tinh dung cua campaign:

- Kiem tra module co dung scope promotion khong.
- Kiem tra copywriting, the le, moc thuong.
- Kiem tra rui ro cau hinh sai: rate khong du 100%, end date nho hon start date, gioi han phat/quantity khong hop le.

## 4. Cac tinh nang da co

### Configuration

- Cau hinh start/end date theo module.
- Cau hinh Thiep Moi Dai Tiec nhu Community Milestone.
- Cau hinh Mo Qua Sinh Nhat: phan thuong, rate, gioi han phat, enabled, nhiem vu, direct URL, tich luy nhan luot.
- Cau hinh Tich Banh Mo Qua VIP nhu Doi Qua.
- Cau hinh Ban Tiec Sinh Nhat: the le va nhiem vu.
- Cau hinh the le HTML cho cac module chinh.
- FE preview doc config tu `localStorage` va reflect len `vng.html`.

### Validation

- Tong rate vong quay phai bang 100%.
- Start/end date: end date phai lon hon start date.
- Cac field so tu nhien lon hon 0 duoc chan ngay luc nhap voi cac field quan trong.
- Gioi han phat, moc tich luy, luot quay, quantity item khong duoc la so thap phan/chu/<= 0 khi cau hinh dang enabled.
- Canh bao/loi khi reward/item dang enabled nhung gioi han phat <= 0.

### Dashboard / Report

- KPI tong participants, conversion, doanh thu uoc tinh, tong luot quay da dung.
- Chart participants theo ngay.
- Chart top rewards claimed dang dung mock data.
- Widget milestone progress.
- Bang trang thai vat pham doi qua gom gioi han phat, da phat mock va con lai mock.
- Conversion funnel mock.

## 5. Gioi han hien tai

Do bai tap khong ket noi API, cac muc sau chi la mock/estimate:

- Ton kho thuc te cua vat pham.
- So luot quay da dung/con lai theo tung giai.
- Claim rate thuc te so voi cau hinh.
- Top 10 phan thuong nhan nhieu nhat.
- Conversion that theo chuoi visit -> login -> mission done.
- Doanh thu that tu goi nap.

## 6. Ghi chu nghiep vu ve Stock / Ton kho

Trong bai tap nay nen tach ro 2 khai niem:

- `quantity`: so luong item nguoi choi nhan duoc moi lan claim/doi.
- `stock` hoac `limit`: tong so luong toi da co the phat trong su kien. Trong UI nen hieu la "Gioi han phat".

Khong co API thi khong the biet ton kho realtime. Tuy nhien admin tool van cho cau hinh `stock/limit` ban dau de validation va dashboard mock co co so tinh:

- remaining = configured stock - mock claimed count
- warning khi stock = 0 nhung reward/item van enabled
- warning khi claimed count mock > configured stock

Trong ban demo, `remaining` la mock. Ban production can claim API/log de tinh remaining that.

## 7. Cach chay

1. Mo `index.html` de cau hinh admin.
2. Chay validation.
3. Save Config hoac Save & Preview.
4. FE preview mo `vng.html` va doc config tu `localStorage`.
