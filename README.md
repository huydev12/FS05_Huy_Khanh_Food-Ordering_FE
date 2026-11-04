# 🍔 Savour - Food Ordering System (Frontend)

Giao diện web (Frontend) cho nền tảng đặt đồ ăn trực tuyến **Savour**, kết nối liền mạch 4 đối tượng: **Khách hàng**, **Nhà hàng**, **Tài xế** và **Quản trị viên** với trải nghiệm theo thời gian thực (Real-time).

---

## 🌟 Tính năng nổi bật

### 👤 Khách hàng (Customer)
* **Khám phá ẩm thực:** Tìm kiếm món ăn, lọc theo danh mục, xem đánh giá và chi tiết thực đơn nhà hàng.
* **Đặt hàng thuận tiện:** Thêm món, ghi chú đơn hàng, giỏ hàng linh hoạt và quy trình thanh toán rõ ràng.
* **Theo dõi trực tiếp (Live Tracking):** Giám sát lộ trình đơn hàng và vị trí giao hàng theo thời gian thực trên bản đồ số.
* **Tương tác & Tiện ích:** Chat hỗ trợ trực tuyến, tham gia cộng đồng chia sẻ món ăn, lưu địa chỉ giao hàng và danh sách yêu thích.

### 🏪 Đối tác Nhà hàng (Restaurant)
* **Đăng ký mở quán:** Biểu mẫu đăng ký đối tác nhanh chóng.
* **Quản lý kinh doanh (Restaurant Dashboard):** Quản lý thực đơn, phân loại món ăn, theo dõi và cập nhật trạng thái đơn hàng.

### 🛵 Đối tác Tài xế (Driver)
* **Đăng ký tài xế:** Đăng ký hồ sơ giao nhận thuận tiện.
* **Bảng điều khiển tài xế (Driver Dashboard):** Tiếp nhận đơn hàng mới, cập nhật trạng thái giao hàng và đồng bộ vị trí di chuyển.

### 🛡️ Quản trị viên (Admin)
* **Trang quản trị (Admin Dashboard):** Giám sát tổng quan hệ thống, kiểm duyệt nhà hàng/tài xế, quản lý tài khoản và phân quyền truy cập (RBAC).

---

## 🛠️ Công nghệ sử dụng (Tech Stack)

| Thành phần | Công nghệ chính |
| :--- | :--- |
| **Nền tảng chính** | [React 19](https://react.dev/), [TypeScript](https://www.typescriptlang.org/), [Vite](https://vitejs.dev/) |
| **Giao diện & Styling** | [Tailwind CSS v4](https://tailwindcss.com/), Radix UI / Shadcn UI, Lucide Icons |
| **Quản lý trạng thái** | [Redux Toolkit](https://redux-toolkit.js.org/) & [Zustand](https://github.com/pmndrs/zustand) |
| **Điều hướng (Routing)** | [React Router DOM v7](https://reactrouter.com/) |
| **Bản đồ & Real-time** | [Leaflet](https://leafletjs.com/) / React-Leaflet, [Socket.IO Client](https://socket.io/) |
| **API Client** | [Axios](https://axios-http.com/) (xử lý interceptor & tự động refresh token) |
| **Đa ngôn ngữ (i18n)** | [i18next](https://www.i18next.com/) (Hỗ trợ Tiếng Việt & Tiếng Anh) |

---

## 📁 Cấu trúc thư mục chính

```text
src/
├── app/
│   ├── components/    # Component theo vai trò (admin, driver, restaurant, map, auth, ui)
│   ├── features/      # Redux Slices (auth, driver, map, order, restaurant)
│   ├── hooks/         # Custom Hooks (useAuth, useChat, useOrderTracking...)
│   ├── pages/         # Giao diện chính (Khách hàng, Nhà hàng, Tài xế, Admin)
│   ├── services/      # Tầng giao tiếp API Backend
│   ├── stores/        # Zustand Stores (cart, favorite, auth)
│   └── types/         # TypeScript Interfaces & Types
├── components/        # Component dùng chung toàn ứng dụng (ChatBox, ...)
├── i18n/              # Cấu hình đa ngôn ngữ (vi, en)
└── styles/            # Cấu hình Theme & CSS toàn cục
```

---

## 🚀 Hướng dẫn cài đặt & Khởi chạy

### Yêu cầu môi trường
* **Node.js**: >= 18.x (khuyên dùng Node 20 hoặc 22)
* **Trình quản lý gói**: `npm` hoặc `pnpm`

### 1. Cài đặt Dependencies
```bash
npm install
# hoặc nếu dùng pnpm:
pnpm install
```

### 2. Cấu hình biến môi trường
Tạo file `.env` ở thư mục gốc (nếu cần thay đổi API Backend):
```env
VITE_API_URL=https://your-api-domain.com
```
*(Nếu không khai báo, hệ thống sẽ sử dụng API mặc định đã cấu hình trong mã nguồn).*

### 3. Chạy môi trường phát triển (Dev)
```bash
npm run dev
# hoặc
pnpm dev
```
Mở trình duyệt và truy cập: `http://localhost:5173`

### 4. Build cho Production
```bash
npm run build
```

---

## 🐳 Triển khai với Docker

Dự án đã tích hợp sẵn `Dockerfile` nhiều giai đoạn (Multi-stage build) kết hợp Nginx:

```bash
# 1. Build image
docker build -t savour-frontend .

# 2. Khởi chạy container
docker run -d -p 80:80 --name savour-fe-app savour-frontend
```
Ứng dụng sẽ hoạt động tại cổng `http://localhost:80`.
