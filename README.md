# DT3Q Sinh Nhat 7 Tuoi

## 2 file

| File | Muc dich |
|------|----------|
| **`admin.html`** | Operation Tool — **3 tabs**: Config+Validation, Report, FE Preview |
| **`vng.html`** | Trang event nguoi choi (muc 1-4, scroll 1 luong) |

Mo **`admin.html`** de lam viec hang ngay. Tab 3 preview nhung `vng.html` trong iframe.

## Cau truc trang event (`vng.html`, scroll 1 luong)

| Muc | Section ID | Noi dung |
|-----|------------|----------|
| 1 | `#dt3q-ld-sinhnhat-header` | Thiep moi dai tiec |
| 2 | `#dt3q-ld-sinhnhat-vongquay` | Mo qua sinh nhat |
| 3 | `#dt3q-ld-sinhnhat-doiqua` | Tich banh mo qua VIP |
| 4 | `#dt3q-loichuc` | Ban tiec / binh chon / loi chuc (frame4 nhung truc tiep) |

Truoc day muc 4 dung `<iframe src="vote-sinh-nhat">` nen nhin nhu `1 2 3` roi lai mot layout moi.  
Hien tai da **bo iframe**, nhung truc tiep HTML + `frame4.css` vao muc 4.

## Lam duoc gi

- Scroll lien tuc tu muc 1 -> 4 tren cung 1 trang.
- Muc 4 co UI binh chon/loi chuc (mock 6 loi chuc mau).
- Nut The le / Nhiem vu / Gui loi chuc mo popup co san tren trang.
- Tat auto popup dang nhap cho demo local (`offAutoShowFormLogin`, `isRequireLogin = 0`).

## Cach chay

**Admin (3 tabs):** mo `admin.html`  
**Event FE:** mo `vng.html` hoac xem trong Tab 3 cua admin

1. Double-click `admin.html` hoac `vng.html`.
2. Admin Tab 1: config + validation → Save.
3. Admin Tab 2: report (mac dinh Today).
4. Admin Tab 3: preview `vng.html` (Reload Preview sau khi save).

## Chua lam duoc / gioi han

- Vote/gui loi chuc that can API `event-vn.vnggames.com` (chi demo UI + alert).
- Khong load `vote.js` / `frame4.js` day du de tranh redirect ve trang khac va popup login iframe.
- **Promotion 1 (moc Q1–Q7):** Admin Save → `localStorage` `dt3q_7y_config` → `vng.html` cap nhat **nguong moc** (`<span>`) + **active/off**. Mo ta qua / URL anh trong admin la **CMS only** (chua wire len tooltip anh).

## Nguon

- `libraryMainsite`, `DT3Q.css`, `frame4.css` tu CDN VNGGames.
- Mock loi chuc lay tu du lieu mau trang vote-sinh-nhat.
