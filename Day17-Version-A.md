# Day 17 — Version A (End of session)

**Nộp:** trước **13:00** cùng ngày — **LMS** (snapshot, **không sửa sau khi nộp**).

**Student:** Nguyễn Thành Nam  
**Date:** 23/04/2026  
**Product idea (1 câu):** Web app giúp SME theo dõi công nợ, dùng AI viết tin Zalo nhắc khách, và sau này có thể gửi Zalo tự động.

**Day 16:** Cùng ý công nợ B2B + Zalo — `Day16-Submission-Nguyen-Thanh-Nam.md`.

---

## 1. MVP Boundary Sheet

**Riskiest Assumption:**

> Người dùng sẽ thích dùng AI vì AI “thông minh”.

### In-Scope (nháp — chưa map rõ từng dòng về Need Day 16)

1. **Upload file công nợ** — test nhanh: xem có upload được không.  
2. **AI viết tin nhắn nhắc nợ** — test: người ta có copy dùng không.  
3. **Chart dòng tiền 30 ngày** — test: trông “chuyên nghiệp”.  
4. *(Ghi thêm)* **Tích hợp Zalo OA gửi tin tự động** — nếu kịp trong tuần *(scope lỏng — dễ trở thành scope creep)*.

**Out-of-Scope**

- Chưa nghĩ kỹ.  
- Không làm bank.  

**Non-Goals**

- (để trống / chưa điền)

---

## 2. PRD Skeleton

**Problem:** Kế toán mệt vì công nợ.

**Target user:** SMB B2B như Day 16.

**User stories**

1. As a kế toán, I want upload data, so that I see list.  
2. As a kế toán, I want AI message, so that save time.

**AI — Model**

- **Model:** GPT-4 / model tốt nhất.  
- **Lý do:** AI mạnh.  
- **Trade-off:** (chưa ghi).  

**Data**

- Dữ liệu từ user.

**Fallback khi AI sai**

- Hiện **thông báo lỗi**; user thử lại.

**Success metrics**

- **Primary:** người dùng cảm thấy **dễ hơn ~50%** so với trước *(metric cảm giác — khó falsifiable)*.  
- **Timeframe:** 2 tuần.

**Dependencies:** cần OpenAI API.

---

## 3. Hypothesis / PMF (draft)

**H1:** Thêm AI sẽ làm user hài lòng.  
**Cách biết đúng:** survey 4–5 sao.

**H2:** Chart 30 ngày giúp chủ hiểu tiền.  
**Cách biết:** họ nói hiểu.

**Riskiest assumption:** (chưa tách riêng khỏi trên).

**PMF**

- **Aha moment:** User cảm thấy “wow” với app. *(cảm xúc, không phải hành vi cụ thể)*  
- **Metric:** số lượt bấm nút. *(gần vanity)*  
- **Method:** chưa chọn rõ Sean Ellis hay Aha tracking.

**Vanity:** sẽ tránh — (chưa liệt kê).

---

## 4. AI Critique / stress-test (draft)

- Chưa xong phần reflect.  
- *Ghi chú cho bản B: cần stress-test PRD và quyết định accept/reject từng góp ý.*

---

## 5. Self-assessment (ngắn)

Mắt xích yếu: chưa rõ.

Open questions: nhiều.

---

*Bản A — snapshot suy nghĩ cuối buổi sáng. **Không chỉnh file này sau khi đã nộp LMS**; bản hoàn chỉnh nằm ở `Day17-Version-B.md` / `submission.md`.*
