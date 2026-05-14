# Case study: chỉnh lyric Kyoukai no Kanata OP theo hướng Tamako-style glow

Case study này ghi lại phần tư duy và snippet hiệu ứng từ một project typesetting thực tế. Repo không kèm video/anime gốc hoặc phụ đề nguồn đầy đủ; chỉ lưu lại cách xử lý kỹ thuật để review workflow.

## Mục tiêu

| Vấn đề ban đầu | Cách xử lý |
| --- | --- |
| Màu từng line không thống nhất | Chọn màu theo context scene, tách phase khi scene đổi rõ |
| Border/blur quá gắt hoặc quá chói | Học theo Tamako Market ED: glow mềm, trắng đọc chính, màu nằm ở layer dưới |
| Quá nhiều `\t`, clip và line rác | Đưa lyric thường về 2 layer sạch |
| Shadow làm chữ bẩn | Xóa shadow khỏi lyric chính |
| Một số line đặc biệt cần giữ style cũ | `Xanh ước mơ` giữ lại block gradient cũ từ bản Fix-Beta1 |

## Công thức layer chính

| Layer | Vai trò | Tag chính |
| --- | --- | --- |
| 1 | Glow màu mờ | `\blur`, `\bord`, `\1a&HFF&`, `\3a` và màu `\3c` |
| 2 | Chữ trắng đọc chính | `\blur0.7`, `\bord0`, `\c&HFFFFFF&` |

Ví dụ đoạn cuối đã giảm chói:

```ass
Dialogue: 1,0:01:22.35,0:01:28.19,OP,,0,0,0,,{\an2\q2\fad(0,180)\blur7.5\bord6.5\1a&HFF&\3a&H3A&\c&H7E5D31&\3c&H7E5D31&}Giờ sang trang, là do anh soi sáng
Dialogue: 2,0:01:22.35,0:01:28.19,OP,,0,0,0,,{\an2\q2\fad(0,180)\blur0.7\bord0\1a&H00&\c&HFFFFFF&}Giờ sang trang, là do anh soi sáng
```

## Các quyết định màu đáng chú ý

| Line | Scene | Màu glow |
| --- | --- | --- |
| `Chính anh đã níu em lại mà` | Cầu thang, cây xanh, nền dịu | `&H61733F&` |
| `Cùng nhau che chở...` phase sau | Cảnh sáng/lửa và chuyển sắc | `&H29448C&` |
| `Giờ sang trang...` phase Mirai | Gần mặt Mirai, tóc nâu ấm | `&H86A7D5&` |
| `Giờ sang trang...` đoạn cuối | Nền trăng/xanh đêm | `&H7E5D31&` |

## Bài học kỹ thuật

- Đẹp nhất không phải là nhiều tag nhất; đẹp là tag ít nhưng đúng cảnh.
- Dùng `\fad` cho chuyển vào/ra, tránh lạm dụng `\t` cho blur/bord.
- Render crop vùng subtitle để đánh giá glow nhanh hơn full frame.
- Với scene đổi gắt, tách phase theo thời gian thay vì ép một màu chạy suốt.
- Với line đặc biệt như gradient dọc, có thể giữ block riêng nếu đó là “chất” của câu.

## Lệnh render kiểm tra

```powershell
ffmpeg -i NCOP.mkv -ss 00:01:24.60 -vf "ass='[Hopeful] Kyoukai no Kanata - NCOP1.ass'" -frames:v 1 preview.png
```

```powershell
ffmpeg -i NCOP.mkv -ss 00:01:24.60 -vf "ass='[Hopeful] Kyoukai no Kanata - NCOP1.ass',crop=1500:230:210:820" -frames:v 1 preview-crop.png
```
