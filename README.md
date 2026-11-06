# DICHUAONLINE V2 CLOUD — Demo độc lập

Ứng dụng Node.js **không cần npm install**, gồm giao diện chùa giả 3D bằng Canvas 2D (không phải mô hình 3D Three.js), nhân vật hoạt ảnh, hiệu ứng, bảng điểm realtime, dashboard quản trị và sự kiện mô phỏng. Không tích hợp TikTok LIVE hoặc doanh thu/quà tặng thật.

## Chạy trên máy

Yêu cầu Node.js 18+.

```bash
ADMIN_PASSWORD='mat-khau-rieng-cua-ban' npm start
```

Mở `http://localhost:3000` để xem chùa và `http://localhost:3000/dashboard.html` để điều khiển. Trên Windows PowerShell: `$env:ADMIN_PASSWORD='mat-khau-rieng-cua-ban'; npm start`.

## Triển khai Railway (tùy chọn)

1. Tạo repo GitHub riêng và tải các file trong thư mục này lên.
2. Railway → New Project → Deploy from GitHub repo → chọn repo.
3. Variables → thêm `ADMIN_PASSWORD` với mật khẩu mạnh, không dùng mặc định.
4. Generate Domain để có URL. Dashboard nằm tại `/dashboard.html`.

**Quan trọng:** Dữ liệu nằm trong `data/state.json` và sẽ mất nếu môi trường cloud xóa ổ đĩa. Muốn giữ dữ liệu sau redeploy, cần gắn volume lưu trữ bền vững vào `/app/data` (nếu working directory là `/app`) hoặc nâng cấp sang DB. Railway có thể yêu cầu phương thức thanh toán hoặc tính phí; không đảm bảo 24/7 miễn phí. Đừng công khai mật khẩu quản trị.

## Bảo mật và phạm vi

- Chỉ dashboard gửi sự kiện mô phỏng; server xác thực mật khẩu cho các thao tác thay đổi.
- API đọc công khai phục vụ màn hình hiển thị; không đặt dữ liệu cá nhân trong tên hiển thị.
- Dùng mật khẩu riêng qua biến môi trường. Mật khẩu mặc định `change-me-now` chỉ dùng cho kiểm thử cục bộ; không được dùng khi public.
- Nếu triển khai public, cần thêm rate limiting, TLS (Railway cung cấp HTTPS), và xác thực phiên mạnh hơn.
- Dự án này được viết độc lập; chưa ghép mã nguồn repo gamedevgs/DICHUAONLINE.
