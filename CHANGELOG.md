# Changelog

## v1.0.0 - Aegisub Automation Pack

Ngày phát hành: 2026-05-14

### Thêm mới

- Chuẩn hóa README tiếng Việt với phần tóm tắt, bảng tín hiệu kỹ thuật, cấu trúc repo, hướng dẫn cài đặt và ghi chú dependency.
- Thêm visual motion cho repo: banner SVG tự host và GIF minh họa workflow automation.
- Đóng gói rõ các nhóm macro Aegisub: timing, color, shape, motion, import/export và thư viện dùng chung.
- Ghi nhận các file/thư mục không đưa vào repo để tránh lẫn backup, autosave, log, crash dump và cấu hình local.

### Ghi chú

- Giữ nguyên cấu trúc `automation/autoload/` và `automation/include/` để macro có thể nạp dependency đúng đường dẫn.
- Repo này là bộ automation/config cá nhân; khi tái phân phối từng macro hoặc thư viện riêng lẻ, cần kiểm tra license upstream của module đó.
