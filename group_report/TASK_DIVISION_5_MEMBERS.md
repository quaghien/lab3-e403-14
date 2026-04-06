# Mô tả công việc từng thành viên (không dùng bảng)

Tài liệu ngắn gọn: ai làm gì trong repo `vinfast_langgraph`, và **test** đang kiểm tra điều gì (một dòng / case).

---

## Test suite năm case (để mọi người cùng ngôn ngữ)

Chạy `python run_evaluation.py`: mỗi case gọi **v1** và **v2**, coi **PASS** khi câu trả lời cuối (hoặc từng lượt nếu có `per_turn`) chứa đủ chuỗi quy định.

- **T01** — Hỏi giá VF8 Plus một câu. Kỳ vọng: nhắc con số ~1,259 tỷ (tool trả giá niêm yết).
- **T02** — Hỏi VF9 giảm tháng 4 bao nhiêu. Kỳ vọng: **50 triệu** (chỉ đúng nếu prompt/bảng KM có trong context; v1 thường fail).
- **T03** — Một câu: VF8 + KM tháng 4 + trả trước 30% + vay 48 tháng, hỏi tiền góp. Kỳ vọng: số góp **sau khi trừ KM** (`~21,2…` triệu/tháng), không tính nhầm trên giá niêm yết.
- **T04** — **Hai lượt.** Lượt 1: hỏi Toyota Camry (hãng khác) → phải **từ chối**, nhắc chỉ VinFast. Lượt 2: VF3 có KM không + góp 24 tháng 25% → phải có **10 triệu** KM và tính đúng trên giá sau KM.
- **T05** — **Hai lượt.** Lượt 1: vay 50 tháng Lux (kỳ không hợp lệ với tool). Lượt 2: đổi sang 48 tháng + 20% trả trước → kỳ vọng tiền góp ~**16,76 triệu**/tháng.

---

