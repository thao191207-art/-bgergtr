# Nhật Ký Thay Đổi (CHANGELOG)

Tất cả các thay đổi đáng chú ý của dự án SaoViet CRM được ghi lại trong tài liệu này theo chuẩn [Semantic Versioning (SemVer)](https://semver.org/).

---

## [1.0.0] - 2026-11-18
### Đã thêm (Added)
- **Kiến trúc Next.js App Router (TypeScript):** Tương thích 100% môi trường Serverless trên Vercel với cấu hình khu vực Singapore (`sin1`).
- **Cơ sở dữ liệu PostgreSQL Cloud (Prisma ORM):** Kết nối pooling an toàn, hỗ trợ Supabase & Neon.
- **Xác thực phiên bảo mật (NextAuth / Auth.js):** Mật khẩu mã hóa Bcrypt 10 vòng, bảo vệ phiên qua cookie HttpOnly.
- **Trợ lý khởi tạo ban đầu (First-run Setup Wizard):** Tự động chuyển hướng đến `/cai-dat-ban-dau` gồm 4 bước thiết lập khi cơ sở dữ liệu trống.
- **Phân hệ Thẩm định Đối tác AI 6 Whys:** Chấm điểm 100 điểm, phát hiện Bẫy Cam Kết Ảo (-25đ + Cảnh báo đỏ), đối chiếu Geofencing 3.5km và SLA 48h kỹ thuật.
- **Phân hệ Kanban Công việc:** Cập nhật lạc quan (Optimistic UI), phản hồi tức thì và tự động hoàn tác khi có sự cố mạng.
- **Quản lý Đại lý & Khách tiềm năng:** Tìm kiếm, lọc theo vùng miền, kiểm soát trần công nợ tín chấp 500 triệu và xuất báo cáo Excel (.xlsx).
- **Trang Giám sát Sức khỏe Hệ thống (`/api/health`):** Báo đèn xanh/đỏ cho PostgreSQL, Storage và Email kèm hướng dẫn xử lý bằng Tiếng Việt.
- **Tác vụ định kỳ (Vercel Cron Jobs):** Quét hạn chót công việc và hợp đồng qua endpoint bảo mật với `CRON_SECRET`.
- **Hỗ trợ người dùng:** Thanh tìm kiếm toàn cục `Ctrl+K`, phím tắt `N`, bảng tra cứu `?` và Tour hướng dẫn 5 bước lần đầu đăng nhập.
