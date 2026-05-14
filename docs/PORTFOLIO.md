# Ghi chú portfolio

Repo này nên được nhìn như một sản phẩm kỹ thuật nhỏ: có vấn đề thật, có công cụ, có quy trình, có tài liệu và có bản phát hành.

## Cách repo tự giới thiệu

| Thành phần | Mục tiêu |
| --- | --- |
| README | Giải thích nhanh repo làm gì, dùng cho ai, có gì đáng xem |
| `automation/` | Phần “engine” thật: macro, include, DLL, config |
| `examples/` | Bằng chứng có workflow hiệu ứng thật, không chỉ gom file |
| `docs/` | Giải thích tư duy kỹ thuật để reviewer hiểu quyết định |
| `assets/` | Visual giúp repo không khô, có cảm giác sản phẩm |
| Release/tag | Tạo mốc phiên bản rõ để HR hoặc reviewer mở nhanh |

## Tín hiệu tốt cho HR

- Có mô tả repo rõ, không để tên repo trống nghĩa.
- Có topic đúng: `aegisub`, `lua`, `moonscript`, `ass-subtitles`, `typesetting`, `karaoke-effects`.
- Có release ổn định, changelog và asset preview.
- Có link về GitHub profile và danh sách repo portfolio.
- Có tài liệu tiếng Việt sạch, không lỗi mã hóa.

## Tín hiệu tốt cho engineering reviewer

- Có cấu trúc thư mục rõ.
- Có phân biệt code, config, docs, examples, assets.
- Có hướng dẫn cài đặt và kiểm tra.
- Có lệnh render cụ thể để tái tạo preview.
- Có ghi chú dependency và tác quyền để tránh phân phối bừa media hoặc script bên thứ ba.

## Việc nên làm tiếp

| Ưu tiên | Việc |
| --- | --- |
| Cao | Thêm ảnh crop preview tự tạo từ snippet không dùng media bản quyền |
| Cao | Viết script kiểm tra macro load được bằng `aegisub-cli` nếu môi trường có sẵn |
| Trung bình | Thêm danh sách macro theo nguồn/tác giả nếu xác định được header license |
| Trung bình | Tách config cá nhân quá riêng tư khỏi config dùng chung |
| Thấp | Làm demo GIF riêng bằng sample ASS tự tạo |
