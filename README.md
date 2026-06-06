# PAKENDU RUNNER — Xuất file APK cho Android

Có 2 cách lấy file APK để cài lên điện thoại Android.
Cách 1 KHÔNG cần cài Android Studio (build trên GitHub, miễn phí) — khuyên dùng.

============================================================
CÁCH 1 — BUILD TRÊN GITHUB (không cần cài gì trên máy)  ★ DỄ NHẤT
============================================================

Bước 1. Tạo tài khoản GitHub miễn phí: https://github.com (nếu chưa có).

Bước 2. Tạo một repository mới:
  - Bấm dấu "+" góc trên phải -> "New repository".
  - Đặt tên ví dụ: pakendu-runner
  - Để "Public" hoặc "Private" đều được. Bấm "Create repository".

Bước 3. Tải toàn bộ thư mục project này lên repo:
  - Trong repo vừa tạo, bấm "uploading an existing file"
    (hoặc Add file -> Upload files).
  - Kéo-thả TẤT CẢ file & thư mục trong project này vào
    (gồm: www/, resources/, .github/, package.json, capacitor.config.json).
    Lưu ý: phải giữ nguyên cấu trúc thư mục, đặc biệt là thư mục .github
  - Bấm "Commit changes".

Bước 4. Chạy build:
  - Vào tab "Actions" của repo.
  - Nếu được hỏi, bấm "I understand my workflows, enable them".
  - Chọn workflow "Build Android APK" ở cột trái -> bấm "Run workflow" -> "Run workflow".
    (Hoặc nó tự chạy ngay sau khi anh upload file ở Bước 3.)

Bước 5. Tải APK về:
  - Chờ khoảng 3-6 phút cho tới khi có dấu ✓ xanh.
  - Bấm vào lần chạy đó -> kéo xuống phần "Artifacts" -> tải "PakenduRunner-APK".
  - Giải nén file zip vừa tải -> được file app-debug.apk

Bước 6. Cài lên điện thoại:
  - Chép app-debug.apk sang điện thoại (qua Zalo/Drive/cáp USB...).
  - Mở file ra, khi máy hỏi thì bật "Cho phép cài từ nguồn này" rồi cài.

============================================================
CÁCH 2 — BUILD BẰNG ANDROID STUDIO (trên máy của anh)
============================================================

Bước 1. Cài Node.js (LTS): https://nodejs.org
Bước 2. Cài Android Studio: https://developer.android.com/studio
        (chọn cài "Standard" để có sẵn Android SDK + JDK).
Bước 3. Mở Terminal/CMD tại thư mục project, chạy lần lượt:

        npm install
        npx cap add android
        npx cap sync android
        npx cap open android

Bước 4. Android Studio mở lên, chờ "Gradle sync" xong, rồi:
        Build -> Build Bundle(s) / APK(s) -> Build APK(s)
        File APK nằm tại:
        android/app/build/outputs/apk/debug/app-debug.apk

Bước 5. Chép APK sang điện thoại và cài như Cách 1, Bước 6.

(Tùy chọn) Tạo icon đẹp từ ảnh trong resources/:
        npm install @capacitor/assets --save-dev
        npx capacitor-assets generate --android

============================================================
GHI CHÚ
============================================================
- File APK ở trên là bản "debug": cài trực tiếp lên điện thoại được ngay,
  không cần Google Play. Đây đúng thứ anh cần để chơi/chia sẻ.
- Muốn đưa lên Google Play (bản chính thức) thì cần tạo bản .aab đã ký
  và tài khoản Google Play Console (25 USD, đóng 1 lần). Khi cần mình hướng dẫn tiếp.
- Sửa game về sau: chỉ sửa file www/index.html rồi build lại.

Thông tin app:
  Tên:    Pakendu Runner
  App ID: com.pakendu.runner
  Game:   www/index.html (chơi được độc lập trong mọi trình duyệt)
