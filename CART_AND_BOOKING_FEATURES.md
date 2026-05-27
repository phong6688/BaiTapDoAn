# Tính Năng Giỏ Hàng Và Đặt Lịch Hẹn

## Tổng Quan

Đã thêm hai tính năng chính vào website:
1. **Hệ thống giỏ hàng** - Người dùng có thể thêm sản phẩm vào giỏ, quản lý số lượng và thanh toán
2. **Đặt lịch hẹn** - Người dùng có thể đặt lịch hẹn cho các dịch vụ

---

## 1. Hệ Thống Giỏ Hàng

### Cấu Trúc
- **CartContext** (`src/context/CartContext.jsx`): Quản lý trạng thái giỏ hàng toàn cục
- **ProductCard** (`src/components/ProductCard.jsx`): Nút "Thêm vào giỏ hàng"
- **Cart Page** (`src/pages/Cart.jsx`): Trang giỏ hàng đầy đủ
- **Header**: Hiển thị số lượng sản phẩm trong giỏ

### Tính Năng

#### Thêm Sản Phẩm Vào Giỏ
- Click nút "Thêm Vào Giỏ Hàng" trên ProductCard
- Hiển thị thông báo xác nhận
- Số lượng trong header tự động cập nhật

#### Quản Lý Giỏ Hàng
- **Xem giỏ hàng**: `/cart`
- **Tăng/giảm số lượng**: Nút + và - cho mỗi sản phẩm
- **Xóa sản phẩm**: Click icon thùng rác
- **Xóa tất cả**: Nút "Xóa Tất Cả"
- **Tổng tiền**: Tự động tính toán
- **Thanh toán**: Nút "Tiến Hành Thanh Toán"

#### Lưu Trữ
- Dữ liệu giỏ hàng được lưu trong `localStorage`
- Giữ nguyên giỏ hàng khi tải lại trang

### API Sử Dụng

```javascript
import { useCart } from './context/CartContext';

const { 
  cartItems,        // Mảng sản phẩm trong giỏ
  addToCart,        // Thêm sản phẩm
  removeFromCart,   // Xóa sản phẩm
  updateQuantity,   // Cập nhật số lượng
  clearCart,        // Xóa tất cả
  getCartTotal,     // Tính tổng tiền
  getCartCount      // Tổng số lượng sản phẩm
} = useCart();
```

---

## 2. Hệ Thống Đặt Lịch Hẹn

### Cấu Trúc
- **Booking Page** (`src/pages/Booking.jsx`): Form đặt lịch
- **Success Page** (`src/pages/Success.jsx`): Trang xác nhận
- **Header**: Link "Đặt Lịch Hẹn" trong menu

### Tính Năng

#### Form Đặt Lịch
- **Đường dẫn**: `/booking`
- **Trường thông tin**:
  - Họ và tên (bắt buộc)
  - Email (bắt buộc, có validate)
  - Số điện thoại (bắt buộc, 10-11 số)
  - Dịch vụ (dropdown, bắt buộc)
  - Ngày hẹn (date picker, bắt buộc, không chọn ngày quá khứ)
  - Giờ hẹn (dropdown, bắt buộc, từ 9:00 - 20:30)

#### Xác Thực
- Tất cả trường đều được validate
- Hiển thị lỗi cụ thể cho từng trường
- Chỉ cho phép submit khi form hợp lệ

#### Xác Nhận
- Lưu dữ liệu vào `localStorage`
- Tự động chuyển hướng đến `/success`
- Hiển thị thông báo với đầy đủ thông tin:
  - Tên khách hàng
  - Dịch vụ đã đặt
  - Ngày và giờ hẹn
  - Thông tin liên hệ

### Dịch Vụ Có Sẵn
1. Tư Vấn Thời Trang
2. Thiết Kế Riêng
3. Đo Riêng Cao Cấp
4. Sửa Chữa Trang Phục
5. Tư Vấn Phong Cách Cá Nhân

---

## 3. Hướng Dẫn Sử Dụng

### Giỏ Hàng

1. **Thêm sản phẩm**:
   - Vào trang Shop
   - Click "Thêm Vào Giỏ Hàng" trên sản phẩm
   - Xem thông báo xác nhận

2. **Xem giỏ hàng**:
   - Click icon giỏ hàng trên header (có hiển thị số lượng)
   - Hoặc vào `/cart`

3. **Quản lý giỏ**:
   - Tăng/giảm số lượng bằng nút + và -
   - Xóa sản phẩm bằng icon thùng rác
   - Xóa tất cả bằng nút "Xóa Tất Cả"

4. **Thanh toán**:
   - Click "Tiến Hành Thanh Toán"
   - Chuyển đến trang checkout

### Đặt Lịch Hẹn

1. **Mở form đặt lịch**:
   - Vào menu "Trang" > "Đặt Lịch Hẹn"
   - Hoặc vào `/booking`

2. **Điền thông tin**:
   - Nhập đầy đủ các trường bắt buộc
   - Chọn dịch vụ mong muốn
   - Chọn ngày và giờ phù hợp

3. **Gửi đặt lịch**:
   - Click "Đặt Lịch Ngay"
   - Hệ thống tự động validate
   - Chuyển đến trang thành công

4. **Xem xác nhận**:
   - Trang `/success` hiển thị thông tin chi tiết
   - Có thể về trang chủ hoặc đặt lịch mới

---

## 4. Cấu Trúc Dữ Liệu

### Giỏ Hàng (localStorage: 'cart')
```javascript
[
  {
    id: 1,
    name: "Áo thun nam",
    price: 299000,
    image: "path/to/image.jpg",
    category: "Nam",
    slug: "ao-thun-nam",
    quantity: 2
  },
  // ...
]
```

### Đặt Lịch (localStorage: 'bookingData')
```javascript
{
  name: "Nguyễn Văn A",
  email: "a@example.com",
  phone: "0901234567",
  service: "Tư Vấn Thời Trang",
  date: "2026-06-01",
  time: "14:00"
}
```

---

## 5. Các File Đã Tạo/Sửa

### File Mới
- `src/context/CartContext.jsx` - Context cho giỏ hàng
- `src/pages/Cart.jsx` - Trang giỏ hàng
- `src/pages/Booking.jsx` - Form đặt lịch
- `src/pages/Success.jsx` - Trang xác nhận (đã sửa hoàn toàn)

### File Đã Sửa
- `src/components/ProductCard.jsx` - Thêm nút và chức năng thêm vào giỏ
- `src/components/Header.jsx` - Thêm cart count badge và link booking
- `src/App.jsx` - Thêm routes mới
- `src/main.jsx` - Wrap CartProvider
- `src/App.css` - Thêm style cho button outline

---

## 6. Demo

### Giỏ Hàng
1. Truy cập: `http://localhost:5174/shop`
2. Thêm sản phẩm vào giỏ
3. Click icon giỏ hàng trên header
4. Quản lý giỏ hàng

### Đặt Lịch
1. Truy cập: `http://localhost:5174/booking`
2. Điền form và submit
3. Xem trang xác nhận

---

## 7. Tính Năng Mở Rộng (Gợi Ý)

### Giỏ Hàng
- [ ] Tích hợp cổng thanh toán
- [ ] Mã giảm giá
- [ ] Phí vận chuyển theo khu vực
- [ ] Lưu giỏ hàng cho user đã đăng nhập

### Đặt Lịch
- [ ] Gửi email xác nhận
- [ ] SMS notification
- [ ] Calendar integration
- [ ] Admin dashboard quản lý lịch hẹn
- [ ] Cancel/Reschedule appointment

---

**Phát triển bởi: AI Assistant**  
**Ngày: 27/05/2026**