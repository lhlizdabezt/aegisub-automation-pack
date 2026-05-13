# Aegisub Automation Pack

<p align="center">
  <img src="assets/aegisub-hero.svg" alt="Banner chuyển động của bộ automation Aegisub" />
</p>

<h2 align="center">🎬 Bộ automation Aegisub cho fansub, typesetting và workflow phụ đề ASS</h2>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Inter&weight=800&size=24&pause=900&color=2563EB&center=true&vCenter=true&width=940&lines=Aegisub+Automation+%7C+Lua+%2B+MoonScript;Typesetting+%7C+Motion+%7C+Shape+Tools;Hotkeys+%7C+Configs+%7C+Reusable+Workflow" alt="Dòng chữ chuyển động mô tả automation Aegisub" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Aegisub-Automation%20Pack-0f172a?style=for-the-badge" alt="Aegisub automation pack" />
  <img src="https://img.shields.io/badge/Lua%20%2B%20MoonScript-Macros-2563eb?style=for-the-badge" alt="Lua và MoonScript macros" />
  <img src="https://img.shields.io/badge/Subtitle-ASS%20Typesetting-0f766e?style=for-the-badge" alt="ASS typesetting" />
  <img src="https://img.shields.io/badge/Release-v1.0.0-D95319?style=for-the-badge" alt="Release v1.0.0" />
</p>

<p align="center">
  <img width="760" src="assets/aegisub-workflow.gif" alt="GIF minh họa luồng automation từ subtitle đến macro, motion và export" />
</p>

---

## 🧭 Tóm tắt

Đây là bộ cấu hình Aegisub cá nhân được đóng gói lại theo hướng sạch, dễ xem và dễ tái sử dụng. Repo tập trung vào các phần có giá trị kỹ thuật: macro Lua/MoonScript, thư viện `include`, hotkey, cấu hình plugin, công cụ shape/motion/color và các thiết lập phục vụ fansub hoặc typesetting phụ đề `.ass`.

Mục tiêu của repo là biến một thư mục automation rời rạc thành một artifact GitHub có cấu trúc rõ ràng: người dùng Aegisub có thể clone về dùng thử, còn người review kỹ thuật có thể nhìn thấy cách tổ chức công cụ, dependency, cấu hình và workflow làm phụ đề.

---

## 🚦 Tín hiệu kỹ thuật

| Hạng mục | Nội dung trong repo | Giá trị khi review |
| --- | --- | --- |
| Automation Aegisub | Macro tự động trong `automation/autoload/` | Cho thấy workflow có thể mở rộng bằng Lua/MoonScript |
| Thư viện dùng chung | Module trong `automation/include/` và native DLL đi kèm | Giữ dependency đúng vị trí, giảm lỗi khi macro gọi module |
| Typesetting ASS | Công cụ shape, gradient, clip, motion, fade, color | Phù hợp xử lý hiệu ứng phụ đề có nhiều tag và vector |
| Cấu hình thao tác | `hotkey.json`, `config/`, `zeref-cfg/` | Có thể dựng lại môi trường làm việc nhanh hơn |
| Tổ chức repo | Loại bỏ autosave, backup, log, crash dump và file local | Sạch hơn cho GitHub, HR và engineering review |

---

## 📦 Có gì bên trong

| Đường dẫn | Vai trò |
| --- | --- |
| `automation/autoload/` | Macro Lua/MoonScript được Aegisub nạp tự động khi khởi động |
| `automation/include/` | Thư viện phụ trợ, module xử lý ASS, hình học, JSON, timing và native binary |
| `config/` | Cấu hình riêng cho từng macro hoặc plugin |
| `zeref-cfg/` | Cấu hình liên quan đến nhóm macro Zeref |
| `hotkey.json` | Bộ phím tắt Aegisub đã được gom lại để dễ phục hồi |
| `colourise.conf`, `masquerade.conf`, `recalculator.conf` | Cấu hình công cụ phụ trợ thường dùng trong workflow |

---

## ✨ Macro nổi bật

| Nhóm | Macro / module | Gợi ý tác vụ |
| --- | --- | --- |
| Timing và line tool | `ua.Recalculator.lua`, `ua.Relocator.lua`, `ua.NecrosCopy.lua` | Căn chỉnh, di chuyển, copy và xử lý line nhanh |
| Hiệu ứng và màu | `ua.FadeWorks.lua`, `ua.Colorize.lua`, `phos.AutoFade.moon`, `zah.aegi-color-track.lua` | Fade, color track, tự động hóa tag màu |
| Shape và vector | `ILL.Shapery.moon`, `lyger.GradientEverything.moon`, `lyger.ClipGrad.lua` | Xử lý shape, gradient, clip và vector typesetting |
| Motion | `a-mo.Aegisub-Motion.moon`, `l0.MoveAlongPath.moon`, `phos.wobble.moon` | Motion path, wobble, transform theo khung hình |
| Tiện ích import/export | `petzku.EncodeClip.lua`, `lyger.Image2ASS.lua`, `l0.PasteAiLines.moon` | Encode clip, chuyển ảnh sang ASS, paste line từ nguồn ngoài |

---

## ⚙️ Cài đặt nhanh

Clone repo vào thư mục cấu hình roaming của Aegisub trên Windows:

```powershell
cd "$env:APPDATA"
git clone https://github.com/lhlizdabezt/aegisub-automation-pack.git Aegisub
```

Nếu đã có thư mục Aegisub sẵn, hãy sao lưu thư mục cũ rồi copy các thư mục quan trọng từ repo này vào:

```powershell
Copy-Item .\automation "$env:APPDATA\Aegisub" -Recurse -Force
Copy-Item .\config "$env:APPDATA\Aegisub" -Recurse -Force
Copy-Item .\zeref-cfg "$env:APPDATA\Aegisub" -Recurse -Force
Copy-Item .\hotkey.json "$env:APPDATA\Aegisub\hotkey.json" -Force
```

Sau khi copy, đóng Aegisub hoàn toàn rồi mở lại để chương trình nạp lại macro trong `automation/autoload/`.

---

## 🧪 Quy trình dùng gợi ý

1. Mở Aegisub và kiểm tra menu `Automation`.
2. Xác nhận các macro quan trọng đã xuất hiện trong danh sách.
3. Mở một file `.ass` thử nghiệm trước khi áp dụng lên project thật.
4. Chạy từng nhóm macro theo nhu cầu: timing, color, shape, motion hoặc export.
5. Giữ nguyên cấu trúc `automation/include/` vì nhiều macro phụ thuộc đường dẫn tương đối.

---

## 🧹 Những gì không đưa vào repo

Các thư mục và file dưới đây được loại khỏi Git vì thường chứa dữ liệu riêng tư, trạng thái runtime, log, backup hoặc đường dẫn theo máy:

| Nhóm | Ví dụ |
| --- | --- |
| Backup và autosave | `autoback/`, `autosave/`, `recovered/` |
| Log và crash dump | `log/`, `crashdumps/`, `feedDump/` |
| Cache và lịch sử local | `catalog/`, `mru.json`, `shift_history.json` |
| Cấu hình máy cá nhân | `config.json`, `aegisub-motion.json`, `aegisub-motion.stats.json` |

---

## 🧩 Ghi chú về dependency và tác quyền

Một số macro trong repo dùng thư viện bên thứ ba và native binary đi kèm, ví dụ module xử lý shape, JSON, timing, clipping hoặc image. Repo này giữ nguyên cấu trúc thư mục để các macro có thể resolve dependency đúng cách trong Aegisub.

Về tác quyền, đây là bộ automation/config cá nhân được đóng gói phục vụ workflow học tập và làm phụ đề. Nếu dùng lại từng macro hoặc thư viện riêng lẻ, hãy kiểm tra header/license upstream của chính module đó trước khi phân phối lại.

---

## 🏷️ Release

| Phiên bản | Nội dung | Trạng thái |
| --- | --- | --- |
| `v1.0.0` | Đóng gói bộ automation Aegisub đầu tiên với macro, include library, config, hotkey, README tiếng Việt và visual motion | Stable |

---

## 👤 Tác giả

**Lương Hải Long**

Sinh viên ngành **Điện tử Viễn thông**; quan tâm đến **Verilog, C/C++, Python, AI, Kaggle, IPYNB**, hệ thống nhúng và các workflow automation có thể tái sử dụng.

Repo này nằm trong portfolio GitHub cá nhân, được trình bày theo hướng gọn, rõ và đủ tín hiệu để HR lẫn kỹ sư đều review được.
