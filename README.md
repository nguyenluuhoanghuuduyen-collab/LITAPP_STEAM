# LitApp – Văn học kỳ thú (LITQUEST)

Ứng dụng web tĩnh: HTML + CSS + JavaScript thuần. Không backend, không API, không đăng nhập, không phí.
Tiến trình lưu trong `localStorage` của trình duyệt từng học sinh.

## Cấu trúc thư mục

```
litapp/
├── index.html
├── style.css
├── app.js              ← dữ liệu 10 thẻ (mảng C) và toàn bộ logic
├── .nojekyll
├── README.md
└── assets/cards/
    ├── LTQ-001.webp … LTQ-010.webp
```

Mọi tài nguyên dùng đường dẫn tương đối nên có thể đặt ở thư mục con (ví dụ `https://ten.github.io/litapp/`).
Lưu ý duy nhất cần mạng: phông chữ Google Fonts. Nếu offline, ứng dụng dùng phông hệ thống thay thế.

## Triển khai lên GitHub Pages

1. Tạo tài khoản GitHub, chọn **New repository**, đặt tên (ví dụ `litapp`), chọn **Public**.
2. Chọn **uploading an existing file**, kéo **toàn bộ nội dung** thư mục `litapp` vào (giữ nguyên thư mục `assets/cards`; `index.html` phải nằm ở gốc repo), rồi **Commit changes**.
3. Vào **Settings → Pages**. Ở **Build and deployment**, chọn **Deploy from a branch**, nhánh `main`, thư mục `/ (root)`, bấm **Save**.
4. Đợi 1–3 phút. Địa chỉ web hiện ở đầu trang Pages, dạng `https://TEN-GITHUB.github.io/litapp/`.
5. Mở địa chỉ đó trên điện thoại và kiểm tra bộ sưu tập hiển thị đủ 10 ảnh.

Cách khác: Netlify (kéo thả thư mục tại app.netlify.com/drop), Cloudflare Pages hoặc bất kỳ hosting tĩnh nào, không cần cấu hình thêm.

## Tạo mã QR cho 10 thẻ

1. Mở ứng dụng ở địa chỉ thật → **Kết nối thẻ vật lý** (trên trang chủ). Địa chỉ trang hiện tại được dùng tự động; nếu cần, dán địa chỉ website vào ô rồi **Lưu địa chỉ**.
2. Với mỗi thẻ, bấm **Sao chép** (liên kết dạng `https://.../litapp/?card=LTQ-001`).
3. Dán liên kết vào một trang/ứng dụng tạo QR bất kỳ, tải ảnh QR, in ở mặt sau thẻ cùng mã.
4. **Quét thử bằng điện thoại cho từng thẻ trước khi in hàng loạt.**
5. Nếu sau này đổi địa chỉ website, các mã QR cũ sẽ không còn dùng được và phải tạo lại.

## Kiểm tra nhanh sau khi triển khai

- `?card=LTQ-001` … `?card=LTQ-010` mở đúng nhiệm vụ cùng mã (LTQ-010 mở trang thẻ quyền năng).
- Mã sai (ví dụ `?card=LTQ-099`) hiện thông báo “Mã thẻ không hợp lệ”.
- Nhập mã thủ công: nút **NHẬP MÃ THẺ** trên trang chủ.

## Mở rộng lên 120 thẻ

1. Thêm ảnh `assets/cards/LTQ-011.webp`… (tỷ lệ 63:88, nên rộng khoảng 360 px, dưới 60 KB mỗi ảnh).
2. Trong `app.js`, thêm một đối tượng vào mảng `C` (đủ `id`, `n`, `w`, `g`, `d`, `xp`, `t`, `task`, `h1`, `h2`, `ans`, `cr`, `q`, `ic`).
3. Cập nhật `MAXXP`, các mốc cấp độ `LV` và huy hiệu `BD` nếu tổng điểm thay đổi. Một số chỗ đang gắn cứng cho 9 nhiệm vụ, nên cần rà lại, đặc biệt `cnt()===9`, `/9` và `xp()/2`.

## Lưu ý

- Dữ liệu tiến trình nằm trên từng thiết bị/trình duyệt, xóa dữ liệu trình duyệt sẽ mất tiến trình.
- Chế độ riêng tư của một số trình duyệt có thể không cho lưu `localStorage`.
- Ứng dụng không thu thập thông tin cá nhân; biệt danh chỉ lưu trên máy.
- Nút tải xuống trong LitStudio hoạt động trên website độc lập; nút Sao chép là phương án dự phòng.


---

# Bộ sưu tập mới: ĐĂM SĂN ĐI BẮT NỮ THẦN MẶT TRỜI (Giai đoạn 1)

Ngữ văn 10 · Kết nối tri thức với cuộc sống · Bài 4: Sức sống của sử thi · SGK tập một, tr. 105–111.

## Tệp mới và tệp đã chỉnh sửa

Mới:
- `assets/css/damsan.css`, `assets/js/damsan.js`
- `data/damsan-cards.json` (nội dung 12 thẻ, giáo viên sửa trực tiếp)
- `assets/cards/NV01 … TC02` và `card-back` (mỗi ảnh có bản `.png` dự phòng và bản `.webp` nhẹ hơn)

Chỉnh sửa tối thiểu (10 thẻ LTQ, đường dẫn `?card=LTQ-…` và các chức năng cũ giữ nguyên):
- `index.html`: thêm 1 dòng CSS và 1 dòng script
- `app.js`: 3 chỗ nhỏ để nhận mã thẻ Đăm Săn (NV01…) và chờ tải xong script mới trước khi đọc URL

## 12 đường dẫn truy cập trực tiếp

- NV01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=NV01
- NV02: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=NV02
- NV03: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=NV03
- BT01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=BT01
- SK01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=SK01
- SK02: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=SK02
- NT01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=NT01
- NT02: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=NT02
- VH01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=VH01
- VH02: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=VH02
- TC01: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=TC01
- TC02: https://nguyenluuhoanghuuduyen-collab.github.io/LitApp/?card=TC02

Mã không tồn tại (ví dụ `?card=NV09`) hiện thông báo kèm nút “Về thư viện thẻ”. Cũng nhận chữ thường (`?card=nv01`).

## Đưa lên GitHub (cập nhật kho LitApp hiện có)

1. Sao lưu: tải bản sao lưu `LitApp_backup_truoc_nang_cap.zip` (đã kèm) hoặc dùng **Code → Download ZIP** của kho.
2. Giải nén gói nâng cấp. Mở kho GitHub → **Add file → Upload files**.
3. Kéo **toàn bộ nội dung** thư mục `litapp` vào (gồm `index.html`, `app.js`, `assets`, `data`…). Khi GitHub hỏi ghi đè, đồng ý; thư mục `assets/cards` sẽ được thêm ảnh mới, ảnh LTQ cũ giữ nguyên.
4. Bấm **Commit changes**. Đợi 1–3 phút để GitHub Pages cập nhật.
5. Mở các đường dẫn ở trên để kiểm tra (nên mở bằng điện thoại và tải lại trang bằng Ctrl+F5 nếu thấy bản cũ).

Lưu ý: tệp trong kho của bạn đang tên `_nojekyll`. Tên đúng là `.nojekyll` (có dấu chấm); thiếu tệp này vẫn chạy bình thường vì dự án không dùng Jekyll.

## Việc đã làm / chưa làm

Đã làm (Giai đoạn 1): 12 ảnh thẻ, thư viện có tìm kiếm và lọc 6 nhóm, thẻ lật 3D có mặt sau từ `card-back`, câu hỏi/gợi ý/đáp án/nhiệm vụ nâng cao/nguồn, ô nhập câu trả lời lưu trên thiết bị, đường dẫn riêng cho từng thẻ, trang chủ chuyên đề, chế độ giảm hiệu ứng.

Chưa làm: công cụ tạo mã QR, 5 trò chơi và 30 câu trắc nghiệm (Giai đoạn 2); board game 18 ô, góc sáng tạo STEAM, hệ thống danh hiệu (Giai đoạn 3).
