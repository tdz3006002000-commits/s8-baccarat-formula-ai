# Hướng dẫn lấy file APK (miễn phí, không cần cài gì trên máy)

Sandbox của Claude không có quyền truy cập mạng tới máy chủ Android SDK/Gradle
nên không tự build APK ngay tại chỗ được. Cách nhanh nhất và HOÀN TOÀN MIỄN PHÍ
là dùng GitHub Actions — máy chủ build của GitHub có sẵn Android SDK.

## Các bước

1. Tạo tài khoản GitHub miễn phí (nếu chưa có): https://github.com/signup
2. Tạo repository mới (Private hoặc Public đều được): nút "New" trên
   https://github.com/new
3. Upload toàn bộ nội dung thư mục này lên repo đó:
   - Cách dễ nhất: vào trang repo vừa tạo -> "uploading an existing file"
     -> kéo thả TOÀN BỘ các file/thư mục trong đây vào (bao gồm cả thư mục
     ẩn `.github`) -> Commit.
   - Hoặc dùng Git: `git init && git add . && git commit -m "init" &&
     git remote add origin <link repo> && git push -u origin main`
4. Vào tab "Actions" trên trang repo -> chờ workflow "Build Debug APK"
   chạy xong (khoảng 3-5 phút).
5. Bấm vào lần chạy vừa xong -> mục "Artifacts" -> tải file
   `app-debug-apk.zip` -> giải nén ra được file `app-debug.apk`.
6. Copy file `.apk` đó vào điện thoại Android -> bật "Cài đặt ứng dụng
   không rõ nguồn gốc" (Install unknown apps) -> mở file để cài.

File `debug.keystore` trong project này đã được tạo sẵn (dùng để ký app khi
build) — không cần làm gì thêm với nó.

## Lưu ý về iOS
Đây là app Android gốc (Kotlin), không chạy được trên iPhone. Muốn dùng
trên iOS miễn phí cần một bản Progressive Web App (PWA) riêng — đây là việc
làm thêm, không dùng chung được code Android này.
