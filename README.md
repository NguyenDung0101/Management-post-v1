# 📝 VSM Blog Platform

Dự án nền tảng Blog đơn giản sử dụng **NestJS + Prisma + MySQL** cho backend và **HTML/CSS/JS** thuần cho frontend.

## 📋 Mục Lục
- [Demo](#-demo)
- [Công Nghệ Sử Dụng](#-công-nghệ-sử-dụng)
- [Yêu Cầu Hệ Thống](#-yêu-cầu-hệ-thống)
- [Cấu Trúc Backend](#-cấu-trúc-backend)
- [Cài Đặt Backend với Prisma + MySQL](#-cài-đặt-backend-với-prisma--mysql)
- [API Endpoints](#-api-endpoints)
- [Frontend: GitHub Pages](#-frontend-github-pages)
- [Gợi Ý Mở Rộng](#-gợi-ý-mở-rộng)
- [Tác Giả](#-tác-giả)
- [Giấy Phép](#-giấy-phép)

## 🚀 Demo
- 🔗 Frontend: [https://<your-username>.github.io/vsm-blog-frontend](https://<your-username>.github.io/vsm-blog-frontend)
- 🔗 Backend: [https://vsm-blog-api.onrender.com](https://vsm-blog-api.onrender.com)

> 🛠️ Thay `<your-username>` bằng tên GitHub của bạn và `vsm-blog-api` bằng domain Render nếu khác.

## 📦 Công Nghệ Sử Dụng

### Backend (NestJS + Prisma)
- **NestJS** - Framework Node.js mạnh mẽ, hỗ trợ mô-đun hóa.
- **Prisma ORM** - Quản lý MySQL hiệu quả.
- **JWT Auth** - Đăng nhập và phân quyền.
- **Render.com** - Nền tảng deploy backend miễn phí.

### Frontend (HTML/CSS/JS)
- **HTML/CSS thuần** với hiệu ứng đẹp.
- **Fetch API** - Gọi API backend.
- **GitHub Pages** - Host trang tĩnh miễn phí.

## 🖥️ Yêu Cầu Hệ Thống
- Node.js (phiên bản 16 hoặc cao hơn)
- MySQL server (đã cài đặt và chạy, ví dụ: XAMPP)
- npm (Node Package Manager)
- Git (để clone và push code)
- phpMyAdmin (tùy chọn, để quản lý cơ sở dữ liệu)

## 🧩 Cấu Trúc Backend
```
src/
├── auth/                # Xử lý đăng ký, đăng nhập, bảo vệ route
├── users/               # Quản lý thông tin người dùng
├── posts/               # CRUD bài viết
├── common/              # Decorator, guard, helper tái sử dụng
├── main.ts              # Điểm khởi chạy
└── app.module.ts        # Nơi khai báo các module
```

## 🛠️ Cài Đặt Backend với Prisma + MySQL

### 1. Clone & Cài Đặt
```bash
git clone https://github.com/<your-username>/vsm-blog-backend.git
cd vsm-blog-backend
npm install
```

### 2. Cấu Hình Database
Tạo file `.env`:
```plaintext
DATABASE_URL="mysql://<user>:<pass>@<host>:<port>/<db>?schema=public"
JWT_SECRET="vsm-secret"
```
Ví dụ với XAMPP:
```plaintext
DATABASE_URL="mysql://root:@localhost:3306/vsm_blog"
```
📌 Đảm bảo bạn đã tạo cơ sở dữ liệu `vsm_blog` trong phpMyAdmin và thay `<user>`, `<pass>`, `<host>`, `<port>`, `<db>` bằng thông tin thực tế.

### 3. Khởi Tạo Prisma
```bash
npx prisma init        # Nếu chưa có thư mục Prisma
npx prisma migrate dev --name init
npx prisma generate
```

### 4. Seed Data Người Dùng
```bash
npx ts-node prisma/seed.ts
```

### 5. Chạy Server
```bash
npm run start:dev
```
API sẽ chạy tại: `http://localhost:3000`

## 🧪 API Endpoints

### Auth
| Method | Endpoint       | Chức năng       |
|--------|----------------|-----------------|
| POST   | /auth/register | Đăng ký         |
| POST   | /auth/login    | Đăng nhập       |

### Users
| Method | Endpoint    | Chức năng             |
|--------|-------------|-----------------------|
| GET    | /users/me   | Thông tin cá nhân (Bearer Token) |

### Posts
| Method | Endpoint     | Chức năng             |
|--------|--------------|-----------------------|
| GET    | /posts       | Lấy tất cả bài viết  |
| POST   | /posts       | Tạo bài viết mới     |
| PUT    | /posts/:id   | Chỉnh sửa bài viết   |
| DELETE | /posts/:id   | Xóa bài viết         |

🌐 Các API yêu cầu xác thực cần header: `Authorization: Bearer <token>`.

## 🌐 Frontend: GitHub Pages

### 1. Tạo Repo GitHub
Ví dụ: `vsm-blog-frontend`

### 2. Cấu Trúc Frontend
```
/
├── index.html    # Trang chính
└── assets/       # (nếu có) chứa ảnh, script, css bổ sung
```

### 3. Push Lên GitHub
```bash
git init
git add .
git commit -m "Deploy frontend"
git branch -M main
git remote add origin https://github.com/<your-username>/vsm-blog-frontend.git
git push -u origin main
```

### 4. Kích Hoạt GitHub Pages
- Vào repo → **Settings** → **Pages**
- **Source**: Chọn `main branch` → `/root`
- Link sẽ hiển thị sau vài phút tại:
  ```
  https://<your-username>.github.io/vsm-blog-frontend
  ```

## 🧠 Gợi Ý Mở Rộng
- Thêm avatar người dùng.
- Upload ảnh bài viết (sử dụng Cloudinary).
- Tìm kiếm, phân trang bài viết.
- Dashboard admin.

## 🧑‍💻 Tác Giả
- 📛 Nguyen Dung
- 💼 Dự án học tập: NestJS + Prisma + MySQL + GitHub Pages

## 📜 Giấy Phép
Dự án này được cấp phép theo Giấy phép MIT. Xem chi tiết trong file [LICENSE](LICENSE).