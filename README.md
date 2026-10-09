# Rubik 3×3 Guide — uni-app Vue 3 + Three.js (offline)

## Yêu cầu
- HBuilderX bản hỗ trợ uni-app Vue 3 (khuyến nghị bản App Development)
- Node.js 20+ và npm (để bundle Three.js vào HTML offline)
- Internet **chỉ trong bước npm install**; APK sau đó không cần Internet.

## Chuẩn bị mô hình 3D (làm một lần và mỗi khi sửa viewer-src)
Mở CMD trong thư mục dự án:

```cmd
npm install
npm run build:viewer
```

Lệnh tạo `hybrid/html/rubik/index.html` và `hybrid/html/rubik/assets/*` chứa JS Three.js đã đóng gói. KHÔNG dùng CDN. Trước khi build cần đảm bảo các file đó tồn tại.

## HBuilderX
1. Mở HBuilderX → File → Open Directory → chọn thư mục này.
2. Trong `manifest.json`, mở giao diện cấu hình và **lấy AppID hợp lệ của DCloud** (giá trị `__UNI__RUBIK3X3` chỉ là placeholder).
3. Chạy: Run → Run to Phone or Emulator → Android.
4. Đóng gói: Publish → Native App – Cloud Packaging → Android. Cấu hình chữ ký/keystore theo yêu cầu của HBuilderX.
5. Cài APK lên điện thoại.

**Không chạy `npx cap ...`** vì dự án này là uni-app, không phải Capacitor.

## Offline
- JSON gốc: `static/data/algorithms.json` (10 mục từ mirror2.docx).
- Ghi chú và yêu thích: `uni.setStorageSync` trên thiết bị.
- Rubik 3D: `hybrid/html/rubik` được đóng gói nội bộ; không gọi mạng.

## Lưu ý kỹ thuật
- Viewer hoạt động trong WebView của **App Android**; không kỳ vọng chạy trong mini-program.
- Công thức được mô phỏng trên khối ban đầu đã giải; không tự nhận dạng Rubik bằng camera và không tự giải từ trạng thái ngẫu nhiên.
- Chữ `R'2` từ Word được diễn giải là `R2` để mô phỏng, cần kiểm chứng. Hai công thức tầng 2 được giữ theo cách ghi gốc, không tự suy luận trường hợp sử dụng.
- Đối với các công thức tầng 3 có yêu cầu lật khối, người học phải tự xác định lại hướng cầm thực tế; mô phỏng không tự lật định hướng mặt.
- HBuilderX/Android SDK không có sẵn trong môi trường tạo mã nguồn, nên chưa xác nhận build APK thực tế.
