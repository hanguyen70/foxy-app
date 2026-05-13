# FOXY — Asset Manager

Web app quản lý tài sản cá nhân: bất động sản, tàu/máy móc, tiền mặt/ngân hàng, vàng SJC, cổ phần, công nợ.

🌐 **Live**: https://hanguyen70.github.io/foxy-app/

## Tính năng

- 6 loại tài sản, hệ thống giao dịch + theo dõi sở hữu nhiều giai đoạn (vessel/BĐS).
- Khóa PIN + mã hóa AES-GCM (PBKDF2 100k iterations).
- Sync GitHub: dữ liệu lưu ở repo riêng (private), app chỉ là code thuần.
- PWA — cài như app trên iPhone/Android.
- Dark/light theme, xuất JSON + CSV, lịch khấu hao, chế độ view-only trên iOS.
- Cảnh báo bảo mật qua Telegram bot (tùy chọn).

## Setup

App là **single-file HTML** — không build, không server. Chỉ cần mở `index.html` hoặc truy cập GitHub Pages.

### Cấu hình sync (lần đầu)

1. Tạo repo private tên `FOXY` (không phải repo này) để chứa dữ liệu.
2. Tạo Personal Access Token (PAT):
   - GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token
   - Resource owner: chính bạn
   - Repository access: chỉ chọn repo `FOXY` (data)
   - Permissions → Repository → **Contents: Read and write**
3. Mở app → Settings → dán token → Lưu.
4. Bấm **⬆ Lưu cloud** lần đầu để khởi tạo `felix-data.json`.

### iPhone (view sync)

1. Mở app trên iPhone qua link GitHub Pages.
2. Nhập cùng token + cùng PIN.
3. Bấm **⬇ Tải cloud** hoặc để auto-load.

## Kiến trúc

- Frontend: vanilla JS + Chart.js (CDN).
- Storage: `localStorage` (local) + GitHub Contents API (cloud).
- Mã hóa: Web Crypto API.

## License

Personal use — không có warranty.
