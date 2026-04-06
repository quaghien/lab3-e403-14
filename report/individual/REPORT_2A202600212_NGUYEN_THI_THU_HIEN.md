# Individual Report: Lab 3 - Chatbot vs ReAct Agent

- **Student Name**: Nguyen Thi Thu Hien
- **Student ID**: 2A202600212
- **Date**: April 6, 2026
- **Reference:** `tests/test_cases.py`, `run_evaluation.py`, `SCORING.md`

---

## I. Technical Contribution (15 Points)

- **Modules:** `tests/test_cases.py`, `run_evaluation.py` (root project)  
- **Nội dung:**  
  - 5 case: simple, multi_step, **multi_turn** (T04/T05).  
  - **T04:** `turns` + **`per_turn`** chấm riêng lượt 1 (từ chối Toyota) và lượt 2 (VF3 + KM).  
  - **T05:** hai lượt; pass theo `expected_contains` trên **câu trả lời cuối** (`run_v1`/`run_v2`).  
  - **`_replies_per_turn`:** gọi graph từng lượt + `with_timestamped_run_name` khi có `per_turn`.  
  - Runner in v1/v2, latency, pass rate; `check_pass` dùng `any(...)` substring.

**Hạn chế:** T03 v1 có thể PASS matcher nhưng **sai giá cơ sở** (21,722… vs 21,204…) nếu chỉ khớp chuỗi lỏng — đã bổ sung biến thể `21.204` trong `expected_contains`.

---

## II. Debugging Case Study

- **Input:** Cả suite 5 case, một lệnh `python run_evaluation.py`.  
- **Kết quả (log `vinfast_20260406_090834.log`):** v1 **2/5**, v2 **5/5**.  
- **Đọc log:** T04 v1 — l1 vẫn có lần gọi tool Toyota; T05 v1 — đổi 48 tháng sớm, chuỗi cuối “16,76 triệu” vs `expected_contains` dạng `16.760.846`.  
- **Gợi ý:** Đính kèm path log trong báo cáo nhóm khi nộp bài.

---

## III. Personal Insights

1. Evaluation **cheap** (substring) phù hợp lab nhanh nhưng **không thay thế** kiểm thử số.  
2. Báo cáo nên nêu rõ **“PASS kỹ thuật ≠ PASS nghiệp vụ”** (T03).  
3. README standalone giúp chấm reproducible mà không cần repo lab gốc.

---

## IV. Future Improvements

- Thêm cột `expected_monthly_range` hoặc so sánh số với output tool.  
- Xuất CSV giống `report/evaluation_results.csv` của project lớn nếu cần merge điểm.
