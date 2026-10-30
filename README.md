# Bài tập tổng hợp: Cloud Workspace – SmartCampus

**Bối cảnh:** Nhóm 5 sinh viên còn 2 ngày nộp báo cáo. Mục tiêu là tránh mất file, cấp sai quyền và trôi thông báo.

## Phần 1 – Thiết lập Hybrid Workflow

**1. Laptop hỏng, mất file báo cáo:** Nếu đã lưu trong thư mục đồng bộ và OneDrive báo đồng bộ thành công, nhóm vẫn lấy được bản trên Cloud bằng máy khác. Nếu chưa đồng bộ xong thì vẫn có nguy cơ mất phần sửa mới nhất. **Auto Sync không thay thế hoàn toàn sao lưu.**

**2. Ba bước bật Auto Sync:**

1. Đăng nhập OneDrive, tạo thư mục `OneDrive/SmartCampus/`.
2. Đưa báo cáo, slide và tài liệu cần làm chung vào thư mục này; chỉnh sửa trực tiếp trên máy (Local).
3. Nhấn **Ctrl+S** → OneDrive tự tải thay đổi lên Cloud → đợi **tích xanh** và kiểm tra file trên web trước khi tắt máy.

**Luồng dữ liệu:** `Ctrl+S → SSD Local → OneDrive Auto Sync → Cloud → các thành viên khác`.

**3. Lỡ xóa 2 trang báo cáo:** Mở `BaoCao_CuoiKy_SmartCampus.docx` trên OneDrive/Word → **Version History (Lịch sử phiên bản)** → chọn bản trước khi xóa → **Restore (Khôi phục)**. Kiểm tra lại để tránh ghi đè những sửa đổi hợp lệ sau đó.

**4. Bẫy đồng bộ:**

- `node_modules/`: hàng nghìn file nhỏ, tốn dung lượng và thời gian đồng bộ. **Để ngoài thư mục OneDrive**, thêm vào `.gitignore`; lưu `package.json`, `package-lock.json` trên Git để chạy `npm ci` khi cần.
- Phim 4K không phục vụ bài nộp: file quá lớn, tốn băng thông và dung lượng. Để ở thư mục Local **không đồng bộ**; chỉ đưa tài sản thực sự cần dùng lên Cloud.

## Phần 2 – Phân quyền chia sẻ an toàn

**1. Bảng phân quyền đề xuất** (quyền áp dụng cho người được mời; chủ sở hữu vẫn quản lý file):

| File | Mức quyền | Phạm vi chia sẻ |
|---|---|---|
| `BaoCao_CuoiKy_SmartCampus.docx` – cả nhóm cùng viết | **Editor** | **Restricted** – 5 thành viên |
| `Slide_BaoCao.pptx` – một người phụ trách sửa | **Commenter** | **Restricted** – thành viên góp ý; chủ file sửa |
| `GopY_KhaoSat.docx` – thu thập nhận xét | **Commenter** | **Restricted** – người được mời |
| `ThongTin_CaNhan_SinhVien.xlsx` – dữ liệu nhạy cảm | **Viewer** | **Restricted** – chỉ người thật sự cần xem |

**2. Quy tắc Cờ Đỏ:** Tuyệt đối không chọn **Anyone with the link + Editor** cho file thông tin cá nhân. Link lộ ra ngoài sẽ khiến người lạ có thể xem, sửa hoặc xóa dữ liệu. Nên dùng **Restricted**, giới hạn người được mời và tắt khả năng chia sẻ lại khi phù hợp.

**3. Nếu cả 5 người đều là Editor của slide:** Dễ xảy ra **ghi đè nội dung** và **sửa sai bố cục**. Giải pháp: một người phụ trách chỉnh sửa, những người còn lại dùng **Commenter** để góp ý.

## Phần 3 – Tổ chức giao tiếp nhóm chuyên nghiệp

**1. Kế hoạch họp 30 phút:**

- **0–10 phút:** Kiểm tra Auto Sync, tình trạng file và lịch sử phiên bản.
- **10–20 phút:** Chốt người phụ trách, quyền truy cập và xử lý dữ liệu nhạy cảm.
- **20–30 phút:** Thống nhất kênh trao đổi, đầu việc và hạn hoàn thành.

**2. Kênh/nhóm chat đề xuất:**

- `#thong-bao`: chỉ trưởng nhóm đăng deadline và quyết định quan trọng.
- `#bao-cao`: thảo luận nội dung báo cáo, trả lời trong Thread/Topic.
- `#slide`: góp ý slide, giao Task cho người phụ trách.
- `#ho-tro`: hỏi lỗi kỹ thuật và nhờ hỗ trợ.

**3. Mẫu tin nhắn bất đồng bộ (đủ ngữ cảnh):**

> **[Cần góp ý báo cáo – hạn 17:00 ngày mai]** Mình đã cập nhật phần 2 trong `BaoCao_CuoiKy_SmartCampus.docx` (thư mục `SmartCampus`). Nhờ các bạn xem mục 2.3, góp ý bằng Comment trước 17:00. Nếu không có ý kiến, mình sẽ chốt bản này để làm slide. Không cần trả lời ngay tối nay.

**4. Tin nhắn soạn lúc 22:47:** Dùng **Schedule Send** để gửi lúc **08:00 sáng hôm sau**, không dùng `@all` ngoài tình huống khẩn cấp.

> **[Nhắc việc – hạn 17:00 hôm nay]** Nhờ người phụ trách slide hoàn tất 5 trang cuối và phản hồi tại `#slide` trước 17:00. File nằm trong `SmartCampus/`. Cảm ơn!

## Phần 4 – Thông báo tổng hợp

**Tin nhắn đăng tại `#thong-bao`:**

> **[QUAN TRỌNG – Chuẩn bị nộp báo cáo SmartCampus]**
>
> 1. Mọi người bật **Auto Sync** cho thư mục tài liệu dự án và kiểm tra **tích xanh** trước khi tắt máy.
> 2. File báo cáo gửi giảng viên chỉ cấp **Viewer + Restricted** theo đúng email; không bật **Anyone with the link**.
> 3. **@Tên_người_phụ_trách_báo_cáo** vui lòng hoàn tất phần còn thiếu trước **17:00 ngày mai** và báo lại trong `#bao-cao` (thay bằng tài khoản thật khi đăng).
>
> Mọi thắc mắc trả lời trong Thread/Topic tương ứng; **không spam `@all`**.

**Kết luận:** Làm việc nhanh trên Local, đồng bộ tài liệu quan trọng lên Cloud, cấp quyền tối thiểu và trao đổi theo chủ đề để tránh mất dữ liệu, lộ thông tin và trôi việc.
