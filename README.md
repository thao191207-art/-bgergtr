# SAOVIET CRM - HỆ THỐNG QUẢN TRỊ & ĐIỀU HÀNH DOANH NGHIỆP
> **Giải pháp SaaS Cloud hiện đại: Triển khai 1-Click trên Vercel + Supabase/Neon PostgreSQL**

![SaoViet CRM Banner](https://images.unsplash.com/photo-1551836022-d5d88e9218df?auto=format&fit=crop&w=1200&q=80)

---

## 1. GIỚI THIỆU
**SaoViet CRM** là hệ thống quản trị và điều hành doanh nghiệp chuyên sâu cho các ngành sản xuất, thương mại và phân phối hàng hóa (Gia dụng, FMCG, Bán lẻ công nghệ). 

Hệ thống được thiết kế theo kiến trúc **Next.js App Router (TypeScript) Serverless**, tương thích 100% với **Vercel** và cơ sở dữ liệu **PostgreSQL đám mây (Supabase / Neon)**.
- **Không cần thuê máy chủ riêng (VPS)**, không cần Docker, không cần chạy lệnh Linux phức tạp.
- Người dùng không rành kỹ thuật chỉ cần đẩy mã nguồn lên GitHub, kết nối Vercel, điền biến môi trường là chạy được ngay.
- Toàn bộ giao diện và hướng dẫn hoàn toàn bằng **Tiếng Việt**, múi giờ chuẩn **Asia/Ho_Chi_Minh**, tiền tệ **VNĐ**.

---

## 2. YÊU CẦU CHUẨN BỊ (MIỄN PHÍ)
Trước khi bắt đầu, bạn chỉ cần chuẩn bị 4 tài khoản miễn phí sau:
1. **GitHub** ([github.com](https://github.com)): Nơi lưu trữ mã nguồn.
2. **Vercel** ([vercel.com](https://vercel.com)): Nền tảng máy chủ đám mây Serverless miễn phí.
3. **Supabase** ([supabase.com](https://supabase.com)) hoặc **Neon** ([neon.tech](https://neon.tech)): Nơi lưu trữ cơ sở dữ liệu PostgreSQL đám mây miễn phí.
4. **Resend** ([resend.com](https://resend.com)) *(Tùy chọn)*: Dịch vụ gửi email thông báo tự động (3.000 mail/tháng miễn phí).

---

## 3. HƯỚNG DẪN TRIỂN KHAI TỪNG BƯỚC (DÀNH CHO NGƯỜI MỚI BẮT ĐẦU)

### Bước 1: Tạo cơ sở dữ liệu trên Supabase hoặc Neon
1. Đăng nhập [Supabase.com](https://supabase.com), bấm **New Project**, đặt tên dự án (ví dụ `saoviet-crm`), chọn khu vực **Singapore (`ap-southeast-1`)** và đặt mật khẩu database.
2. Vào **Project Settings** -> **Database** -> mục **Connection string**:
   - Chọn thẻ **Transaction Pooler** (cổng 6543) -> Sao chép URL này làm `DATABASE_URL`.
   - Chọn thẻ **Direct Connection** (cổng 5432) -> Sao chép URL này làm `DIRECT_URL`.

### Bước 2: Tải mã nguồn lên GitHub
- **Cách 1 (Dùng giao diện Web):** Tạo repo mới trên GitHub, chọn **Upload files**, kéo thả toàn bộ thư mục dự án lên rồi bấm **Commit**.
- **Cách 2 (Dùng lệnh Git):**
  ```bash
  git init
  git add .
  git commit -m "Khoi tao SaoViet CRM"
  git branch -M main
  git remote add origin https://github.com/tai-khoan-cua-ban/saoviet-crm.git
  git push -u origin main
  ```

### Bước 3: Kết nối dự án trên Vercel
1. Đăng nhập [Vercel.com](https://vercel.com) bằng tài khoản GitHub.
2. Bấm nút **Add New...** -> **Project** -> Chọn kho mã `saoviet-crm` bạn vừa tải lên.

### Bước 4: Điền các Biến Môi Trường (Environment Variables)
Tại mục **Environment Variables** trên Vercel, sao chép và điền các khóa sau:

| Tên biến môi trường | Ý nghĩa & Cách lấy | Ví dụ mẫu |
|---|---|---|
| `DATABASE_URL` | Chuỗi kết nối PostgreSQL Pooled (Cổng 6543) | `postgresql://postgres:[PASS]@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres?pgbouncer=true` |
| `DIRECT_URL` | Chuỗi kết nối trực tiếp PostgreSQL (Cổng 5432) | `postgresql://postgres:[PASS]@aws-0-ap-southeast-1.pooler.supabase.com:5432/postgres` |
| `AUTH_SECRET` | Chuỗi khóa bí mật mã hóa phiên đăng nhập | `saoviet_crm_super_secret_key_random_32_characters_123` |
| `NEXTAUTH_URL` | Tên miền ứng dụng (hoặc để trống trên Vercel) | `https://saoviet-crm.vercel.app` |
| `CRON_SECRET` | Khóa bí mật bảo vệ tác vụ định kỳ Vercel Cron | `saoviet_cron_secret_key_888` |
| `RESEND_API_KEY` | *(Tùy chọn)* Khóa gửi email từ Resend | `re_123456789abcdef` |

### Bước 5: Bấm Deploy
- Bấm nút **Deploy**. Vercel sẽ tự động build ứng dụng và hoàn tất trong khoảng 2 phút.
- Khi màn hình hiện pháo hoa chúc mừng, bạn đã có ngay đường link website hoạt động 24/7!

### Bước 6: Khởi tạo bảng dữ liệu (Database Migration)
- Chạy lệnh migration từ máy tính của bạn chỉ với 1 câu lệnh:
  ```bash
  npm run db:push
  ```
  *(Lệnh này tự động tạo toàn bộ bảng dữ liệu vào cơ sở dữ liệu Supabase/Neon của bạn mà không làm mất dữ liệu cũ).*

### Bước 7: Mở trang web và làm theo Trợ lý Cài Đặt Ban Đầu (Setup Wizard)
1. Truy cập đường dẫn Vercel của bạn (ví dụ: `https://saoviet-crm.vercel.app`).
2. Hệ thống nhận diện cơ sở dữ liệu mới và tự động mở trang `/cai-dat-ban-dau`:
   - **Bước 1:** Đặt tài khoản Admin (`admin@saoviet.vn` / `Admin@123456`).
   - **Bước 2:** Nhập tên công ty, mã số thuế và chọn màu thương hiệu.
   - **Bước 3:** Chọn ngành nghề (Gia dụng, FMCG, Bán lẻ...).
   - **Bước 4:** Chọn **Nạp sẵn Bộ Dữ liệu Mẫu** để trải nghiệm ngay.

---

## 4. TÀI KHOẢN TRẢI NGHIỆM MẪU (DEMO)
- **Tài khoản Quản trị (Admin):**
  - Email: `admin@saoviet.vn`
  - Mật khẩu: `Admin@123456`
- **Tài khoản Nhân viên Kinh doanh:**
  - Email: `kinhdoanh@saoviet.vn`
  - Mật khẩu: `Nhanvien@123`

---

## 5. BẢNG KHẮC PHỤC SỰ CỐ THƯỜNG GẶP (TROUBLESHOOTING)

| Hiện tượng lỗi | Nguyên nhân | Cách khắc phục |
|---|---|---|
| **Build Vercel báo lỗi TypeScript / Prisma** | Chưa chạy `prisma generate` | Đã được cấu hình tự động trong lệnh build `prisma generate && next build`. |
| **Không đăng nhập được, báo sai mật khẩu** | Chưa khởi tạo tài khoản hoặc chưa nạp dữ liệu mẫu | Mở trang `/cai-dat-ban-dau` để khởi tạo lại tài khoản quản trị. |
| **Trang web báo lỗi "Thiếu biến DATABASE_URL"** | Chưa điền biến môi trường trên Vercel | Vào Vercel -> Project Settings -> Environment Variables, điền đầy đủ `DATABASE_URL` và `DIRECT_URL`. |
| **Tác vụ Cron không kích hoạt** | Chưa cấu hình `CRON_SECRET` | Thêm biến `CRON_SECRET` trên Vercel để đồng bộ với file `vercel.json`. |

---

## 6. DANH MỤC PHÍM TẮT HỆ THỐNG
- `Ctrl + K` (hoặc `Cmd + K` trên macOS): Mở thanh tìm kiếm và điều hướng toàn cục.
- `N`: Mở cửa sổ tiếp nhận nhanh Khách hàng / Lead / Hợp đồng mới.
- `?`: Xem danh sách toàn bộ phím tắt.
- `Esc`: Đóng nhanh cửa sổ pop-up đang mở.

---

## 7. GIẤY PHÉP & PHIÊN BẢN
- Phiên bản: `v1.0.0` (Semantic Versioning)
- Giấy phép: MIT License - Toàn quyền sử dụng và tùy biến cho doanh nghiệp.
