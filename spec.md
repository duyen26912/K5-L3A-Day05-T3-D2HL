# Bài nộp LAB5 — [Track] · Nhóm [tên]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]

## §1. Lát cắt & phạm vi
# Bài nộp LAB5 — T3 Du lịch · Nhóm <TenNhom>

**Lớp:** L3_ · **Bàn / zone:** __ · **Track:** T3

> Nhóm 4 thành viên — đã được giảng viên cho phép.

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
|Vũ Gia Linh|2A202603677||

| (A) | | §1 Lát cắt & phạm vi, §2 Kịch bản rủi ro, kịch bản demo |
| (B) | | §3 Khi AI sai, câu chữ prototype |
| (C) | | §4 Mức tự chủ, §6 Tốt là gì |
| (D) | | §5 Prototype, ảnh đánh số, repo |

---

## §1. Lát cắt & phạm vi

### 1.1 Lát cắt

> Trong **Đặt chỗ của tôi**, khi **hành khách** vừa nhận tin chuyến bay bị huỷ và nhắn hỏi, **AI đề xuất và giữ chỗ chuyến thay thế, hỏi lại cho rõ, đổi vé, hay chuyển nhân viên**, để khách tới nơi kịp mà không mất vé hay tiền vì một thao tác không đảo lại được.

| Sản phẩm | Một người dùng | Một việc | Một quyết định của AI | Một kết quả |
|---|---|---|---|---|
| Đặt chỗ của tôi (giống Traveloka) | Hành khách | Vừa nhận tin chuyến bị huỷ, nhắn hỏi | Giữ chỗ, hỏi lại, đổi vé, hay chuyển nhân viên | Khách tới nơi kịp, không mất vé hay tiền vì một thao tác không đảo được |

### 1.2 AI được thêm quyền gì so với hôm nay

- **Hôm nay** (mục "Sản phẩm thật hôm nay"): khách **tự bấm** khoảng 8 bước Đổi lịch (mở vé → Hoàn tiền & Đổi lịch → Đổi lịch → chọn chuyến, hành khách → tìm chuyến → xem phí → thanh toán). Hoàn tiền cũng do khách tự gửi. Trang trợ giúp không mô tả trợ lý AI làm thay bước nào.
- **Khi tích hợp AI:** trợ lý được gọi 5 tool thay khách. Ba tool **thay đổi trạng thái vé**:

| Tool | Thay đổi gì | Đảo lại được? | Nhóm đánh giá |
|---|---|---|---|
| `tra_cuu_dat_cho` | Không — chỉ đọc | — | An toàn, nhưng là **nguồn sự thật duy nhất**: AI nói gì về giờ, chỗ, quyền lợi đều phải lấy từ đây |
| `giu_cho_chuyen_moi` | Giữ chỗ 20 phút | Được, tự nhả | Rẻ khi sai |
| `doi_chuyen_bay` | Đổi vé, **dùng lần đổi miễn phí duy nhất** | **Khó** | Nguy hiểm — sai là mất quyền đổi, chuyến đúng có thể đã hết chỗ |
| `gui_yeu_cau_hoan_ve` | Gửi yêu cầu hoàn | **Không** | Nguy hiểm nhất — gửi rồi không rút được, mất chỗ mọi chuyến, tiền về tới 90 ngày |
| `chuyen_nhan_vien` | Chuyển chat | Được | Rẻ khi thừa, đắt khi thiếu |

- **Việc khách sẽ đòi mà không có tool nào làm:** bồi thường tiền mặt, đổi tên người bay, tách trẻ đi riêng, đổi lần hai miễn phí. AI phải **nói rõ không làm được** và chỉ đường (nhân viên / chính sách), không được hứa.

### 1.3 AI sai thì ai chịu gì — hướng nào đắt hơn

| Hướng sai | Ai chịu | Chịu gì | Đảo được? |
|---|---|---|---|
| **Làm quá tay:** đổi vé khi khách chưa nói rõ chuyến / hành khách | Hành khách | Mất lần đổi miễn phí duy nhất; chuyến đúng (BM 205 chỉ còn 4 chỗ) có thể hết | Khó |
| **Làm quá tay:** gửi hoàn khi khách chỉ đang bực | Hành khách | Mất chỗ trên mọi chuyến thay thế; tiền về tới 90 ngày | **Không** |
| **Nói sai:** hứa bồi thường cho chuyến huỷ do thời tiết | Hãng + nhân viên | Khách mất niềm tin, nhân viên phải gỡ lời hứa | Sửa được, tốn công |
| **Làm quá ít:** bắt chờ nhân viên cho mọi việc | Hành khách | Chuyến tốt hết chỗ trong lúc chờ; khách đi cùng trẻ nhỏ phải chờ thêm | Không — chỗ đã mất thì mất |

**Kết luận:** sai theo hướng **làm quá tay với tool không đảo được** là đắt nhất, vì cái giá rơi hết vào hành khách và không lấy lại được. Nhưng **làm quá ít** cũng có giá thật (hết chỗ), nên thiết kế không thể "chuyển nhân viên hết cho an toàn".

### 1.4 Ba việc tính năng KHÔNG làm

| # | Không làm | Vì sao |
|---|---|---|
| 1 | **Không hứa, không xử lý bồi thường tiền mặt** | Dữ liệu ghi rõ "huỷ do thời tiết thì không bồi thường tiền mặt"; không có tool bồi thường. Hứa sai thì mất niềm tin và nhân viên phải gỡ. AI chỉ nói quyền lợi thật: đổi miễn phí một lần trong 48 giờ hoặc hoàn toàn bộ. |
| 2 | **Không đổi tên người bay, không xử lý trẻ em bay một mình hoặc tách trẻ khỏi người lớn trong đặt chỗ** | Không có tool cho các việc này; đây là việc có rủi ro an toàn và giấy tờ, rubric riêng của track yêu cầu chuyển nhân viên. Đặt chỗ có bé Nguyễn Gia Bình 5 tuổi nên khả năng gặp ca này là thật. |
| 3 | **Không xin, không nhận số thẻ, OTP; không xử lý thanh toán phí chênh lệch** | Ngoài lát cắt (chuyến bị huỷ được đổi miễn phí, không có phí chênh); mục An toàn & đạo đức của track cấm xin số thẻ, OTP. |

*Đã cân nhắc nhưng không đưa vào 3 việc chính:* không đặt khách sạn / xe đưa đón khi chuyến huỷ (ngoài lát cắt, nhưng ít rủi ro nên không cần nhấn); không xử lý chuyến **không** bị huỷ (đúng nhưng hiển nhiên theo lát cắt).

---

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

## §3. Khi AI sai  (chặng 3)
Với mỗi kịch bản đắt nhất:
- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype  (chặng 5)
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
