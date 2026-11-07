# BTVN Session 21 - Troubleshooting & Bug Reporting

## Phần 1: Googling Đúng Cách

* **Lý do Bad Query thất bại:** Chứa từ cảm thán/văn nói, thiếu từ khóa kỹ thuật cốt lõi làm loãng kết quả tìm kiếm.
* **Bóc tách thông báo lỗi:**

| Thành phần | Nội dung |
| :--- | :--- |
| **HĐH / Software** | Windows 11 / Node.js (npm) |
| **Raw Error** | `'npm' is not recognized as an internal or external command, operable program or batch file.` |
| **Thao tác** | Gõ `npm -v` trong Terminal (VS Code) |

* **3 Cú pháp tìm kiếm Google:**
  * `site:` ➔ `site:stackoverflow.com npm is not recognized windows 11`
  * `" "` ➔ `"npm is not recognized as an internal or external command"`
  * `-` ➔ `npm is not recognized windows 11 -xp -windows7`

---

## Phần 2: Thẩm Định StackOverflow

* **Bảng so sánh uy tín:**

| Tiêu chí | Câu trả lời A | Câu trả lời B |
| :--- | :--- | :--- |
| **Vote & Tích xanh** | Accepted Answer (✓), +186 upvotes | Không tích xanh, +2 upvotes |
| **Thời gian** | 2 năm trước (mới) | 9 năm trước (cũ) |
| **Tags** | `[node.js]` `[windows]` `[npm]` | `[node.js]` `[windows-xp]` (lệch HĐH) |

* **Áp dụng:** Chọn **A**. Không chọn B vì yêu cầu cài lại driver mạng cho Windows XP — không liên quan đến lỗi PATH, nguy cơ hỏng hệ thống.
* **Quy trình 30s đọc lướt:**
  1. Xem ngay **Accepted Answer (✓)**.
  2. Kiểm tra **Upvotes** và **Tags** môi trường.
  3. Đọc lướt khung chứa code/giải pháp chính.

---

## Phần 3: Hỏi AI & Nhận Diện Rủi Ro

* **Prompt 3 Thành phần:**
  > **Context:** Vừa cài Node.js trên Windows 11, gõ `npm -v` trong VS Code báo lỗi không nhận diện. Đã thêm `C:\Program Files\nodejs\` vào PATH và mở lại Terminal nhưng không hết lỗi.  
  > **Raw Error:** `'npm' is not recognized as an internal or external command, operable program or batch file.`  
  > **Instruction:** Giải thích nguyên nhân PATH chưa ăn và đưa ra các bước kiểm tra tiếp theo an toàn trên Windows 11.

* **Thẩm định an toàn (Mục 3e):** **KHÔNG AN TOÀN**. Lệnh `del /f /s /q C:\Windows\System32\*` sẽ xóa sạch file hệ thống Windows (AI ảo giác/phá hoại).
* **Phản hồi lại AI:** Cảnh báo AI rằng lệnh xóa System32 sẽ làm sập máy, yêu cầu phân tích lại lỗi PATH mà không dùng lệnh xóa file hệ thống.

---

## Phần 4: Bug Report Chuẩn

* **Tin nhắn kém:** *"Thầy ơi máy em bị lỗi npm không chạy được, sửa sao vậy thầy?"*
* **Bug Report chuẩn 4 bước:**

| Mảnh ghép | Nội dung |
| :--- | :--- |
| **Context** | Cài Node.js trên Windows 11, đã thêm PATH nhưng gõ `npm -v` trong VS Code vẫn lỗi. |
| **Expected** | Hiển thị phiên bản npm (ví dụ: `10.x.x`). |
| **Actual** | Báo lỗi `'npm' is not recognized...` |
| **Log & Screenshot** | `'npm' is not recognized as an internal or external command, operable program or batch file.` *(Kèm ảnh chụp)* |

* **Chụp màn hình & Bảo mật:**
  * Phím tắt: `Windows + Shift + S`.
  * Bảo mật: Che mờ email, token, mật khẩu hoặc thông tin cá nhân riêng tư trước khi gửi ảnh.