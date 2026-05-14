# Ghi chú hiệu ứng ASS

Tài liệu này gom các mẫu hiệu ứng đã dùng trong workflow typesetting thực tế. Mục tiêu là giữ lại tư duy kỹ thuật: ít layer, sạch tag, dễ debug bằng Aegisub và FFmpeg/libass.

## Nguyên tắc đang dùng

| Nguyên tắc | Lý do |
| --- | --- |
| Một line lyric thường chỉ cần 2 layer | Layer dưới làm glow/blur màu, layer trên là chữ trắng sạch |
| Không nhét `\blur` và `\bord` vào `\t` nếu không cần | Transform blur/bord dễ tạo cảm giác “dị” và khó kiểm soát |
| Không dùng shadow cho lyric chính | Shadow làm bẩn viền, đặc biệt trên nền sáng hoặc cảnh nhiều glow |
| Màu glow phải theo background | Màu đẹp trên một frame có thể lệch hẳn khi đổi scene |
| Frame gần nhau cùng context thì hạn chế fade đầu/cuối | Tránh lỗi subtitle nhấp nháy khi các phase nối sát nhau |

## Mẫu glow 2 layer

Layer dưới chỉ làm viền màu mờ:

```ass
Dialogue: 1,0:00:00.00,0:00:03.00,OP,,0,0,0,,{\an2\q2\fad(120,150)\blur7.5\bord6.5\1a&HFF&\3a&H3A&\c&H7E5D31&\3c&H7E5D31&}Nội dung lyric
```

Layer trên là chữ trắng đọc chính:

```ass
Dialogue: 2,0:00:00.00,0:00:03.00,OP,,0,0,0,,{\an2\q2\fad(120,150)\blur0.7\bord0\1a&H00&\c&HFFFFFF&}Nội dung lyric
```

## Bảng màu tham khảo

Lưu ý: màu ASS dùng định dạng `&HBBGGRR&`, không phải RGB.

| Cảnh | Màu ASS | RGB gần đúng | Ghi chú |
| --- | --- | --- | --- |
| Nền xanh đêm, trăng, mặt nước | `&H7E5D31&` | `#315D7E` | Đậm hơn xanh trắng, bớt chói |
| Cảnh Mirai, tóc nâu ấm | `&H86A7D5&` | `#D5A786` | Hợp tóc và áo khoác hơn xanh ngọc |
| Cảnh xanh lá/cầu thang | `&H61733F&` | `#3F7361` | Tông lạnh dịu, hợp lan can/cây |
| Cảnh phase xanh/tím | `&H29448C&` | `#8C4429` | Dùng khi muốn glow nâu đỏ trầm |
| Cảnh trời/tím gradient | `&HE22565&` -> `&H35A8D8&` | `#6525E2` -> `#D8A835` | Dùng cho gradient dọc dạng đặc biệt |

## Kiểm tra preview bằng FFmpeg

Render full frame:

```powershell
ffmpeg -i input.mkv -ss 00:01:24.60 -vf "ass='subtitle.ass'" -frames:v 1 preview.png
```

Render crop vùng subtitle:

```powershell
ffmpeg -i input.mkv -ss 00:01:24.60 -vf "ass='subtitle.ass',crop=1500:230:210:820" -frames:v 1 preview-crop.png
```

## Khi nào dùng gradient nhiều line?

Chỉ dùng gradient line-by-line khi hiệu ứng thật sự cần loang màu theo chiều dọc hoặc theo frame. Với lyric thường, 2 layer đủ sạch hơn và dễ sửa hơn. Nếu cần gradient, nên dùng script như `lyger.GradientEverything.moon` để tự động hóa thay vì gõ tay hàng trăm `\clip`.
