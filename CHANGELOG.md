# Changelog

## v1.1.0 - Portfolio hóa workflow hiệu ứng ASS

Ngày phát hành: 2026-05-14

### Thêm mới

- Viết lại README tiếng Việt bằng UTF-8 sạch để tránh lỗi chữ `????` hoặc mojibake trên GitHub.
- Thêm tài liệu case study cho workflow Kyoukai no Kanata OP theo phong cách glow/blur tham khảo từ Tamako Market ED.
- Thêm snippet ASS cho hiệu ứng glow 2 layer, phase màu theo scene và line lyric cuối giảm chói.
- Thêm sơ đồ pipeline SVG trong `assets/ass-effect-pipeline.svg`.
- Thêm tài liệu portfolio để repo rõ hơn với HR và engineering reviewer.

### Cải thiện

- README có bảng cấu trúc repo, macro nổi bật, quy trình cài đặt, quy trình render preview và phần tác quyền.
- Tài liệu phân biệt rõ phần code/snippet tự viết với media hoặc subtitle nguồn không được đưa vào repo.
- Metadata repo được định hướng lại theo hướng Aegisub automation, ASS typesetting, Lua/MoonScript, motion và karaoke effects.

## v1.0.0 - Aegisub Automation Pack

Ngày phát hành: 2026-05-14

### Thêm mới

- Chuẩn hóa README tiếng Việt với phần tóm tắt, bảng tín hiệu kỹ thuật, cấu trúc repo, hướng dẫn cài đặt và ghi chú dependency.
- Thêm visual motion cho repo: banner SVG tự host và GIF minh họa workflow automation.
- Đóng gói các nhóm macro Aegisub: timing, color, shape, motion, import/export và thư viện dùng chung.
- Ghi nhận các file/thư mục không đưa vào repo để tránh lẫn backup, autosave, log, crash dump và cấu hình local.

### Ghi chú

- Giữ nguyên cấu trúc `automation/autoload/` và `automation/include/` để macro có thể nạp dependency đúng đường dẫn.
- Repo này là bộ automation/config cá nhân; khi tái phân phối từng macro hoặc thư viện riêng lẻ, cần kiểm tra license upstream của module đó.
