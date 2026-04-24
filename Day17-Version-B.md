# Day 17 — Version B (BTVN / GitHub)

**Student:** Nguyễn Thành Nam  
**Date:** 23/04/2026  
**Product idea (1 câu):** Bản web giúp kế toán/ chủ DN B2B nhỏ ưu tiên công nợ, nhận 3 bản nháp tin Zalo cấp độ (kèm mức ưu tiên dựa trên hóa đơn CSV) và theo dõi 30 ngày tới, giảm thời gian dunning hàng tuần.

**Liên kết Day 16:** cùng phân khúc *SMB B2B “Net 7–30”*, cùng **Need #1** (bảng ưu tiên + mẫu nhắc), **Need #2** (chỉ số dòng tiền/30 ngày) trong `Day16-Submission-Nguyen-Thanh-Nam.md`.

---

## 1. MVP Boundary Sheet

**Riskiest Assumption:**

> Khách hàng sẵn sàng *đổi hành vi* (chuyển từ tin nhắn viết toàn bộ bằng tay sang: nhập CSV → sửa bản nháp AI) nếu họ tin bản nháp *đủ sát* ngữ cảnh VN (chứ không phải vì “có AI”).

### In-Scope (tối đa 3) — ánh xạ về nhu cầu Day 16

| # | Tính năng (MVP) | Ánh xạ Day 16 Need | Assumption cần test nhanh |
|---|-----------------|--------------------|---------------------------|
| **1** | **Công nợ theo từng dòng hóa đơn** (upload CSV: mã HĐ, ngày hết hạn, số tiền, tên KH) + bảng xếp hạng theo số ngày quá hạn & số tiền | **Need #1** (JTBD: ưu tiên khi nhiều hóa đơn) | Một bảng sort/filter đúng 3 trường dữ liệu đã *giúp* người dùng chọn *ai nhắc trước* trong dưới 5 phút. |
| **2** | **Sinh 3 bản nháp tin Zalo (cấp 1–2–3)** từ dữ liệu hóa đơn đã chọn, có khối sửa trước khi gửi (copy sang Zalo) | **Need #1** (bộ mẫu nhắc theo bậc) | Bản nháp cấp 2 (nhắc lần 2) có tỷ lệ *dùng nguyên hoặc sửa <20%* cao hơn mẫu tĩnh. |
| **3** | **Dải 30 ngày: tổng cần thu, % quá hạn, ước tính DSO 30d** từ dữ liệu snapshot CSV | **Need #2** (chỉ số dự báo cho chủ) | 2 chỉ số tối thiểu (tiền sắp đến hạn; tiền quá hạn) *đủ* để họ dùng trong họp 15 phút. |

**Out-of-Scope (và lý do)**

- **A — Gửi Zalo/ SMS tự động qua tích hợp chính thức (OA/gateway).** Cần hợp đồng, phí, review pháp lý/brand; làm hỏng tốc độ ship MVP.  
- **B — Tích hợp 2 chiều MISA/ Fast/ API bên thứ 3 ngay từ đầu.** Ảnh hưởng biên dự án; CSV đủ để học.  
- **C — Cơ chế dự báo mạch học/ ML phức tạp cho rủi ro khách hàng.** Chưa có dữ liệu lịch sử ổn định; để sau khi có pilot.  

**Non-Goals (lằn ranh đỏ)**

- Không thay thế sổ kế toán, không tự tạo hóa đơn, không tính thuế.  
- Không bán tính năng “thẩm định tín dụng”/ điểm tín dụng pháp lý.  
- Không lưu số tài khoản ngân hàng/ ảnh CCCD khách: chỉ tối thiểu phục vụ nhắc nợ.  

---

## 2. PRD Skeleton

### 2.1 Problem statement (1 câu)

Kế toán tổng hợp/ chủ DN B2B nhỏ **mất 5–10 giờ/tuần** cho việc rà công nợ và soạn tin lặp lại, dẫn đến **DSO kéo dài** và dòng tiền **khó lường 30 ngày tới** — tổn thất trực tiếp theo số ngày trễ thu. *(Nguồn: Day 16 Need #1, #2.)*

### 2.2 Target user

**Persona (liên hệ *Customer / Segment Card* Day 16):** *Chị Lan — kế toán tổng hợp tại DN phân phối thực phẩm, quy mô 10–80 tỷ/năm, 40–200 hóa đơn/ tháng, đối soát công nợ trên Excel, nhắc KH chính qua Zalo.*

### 2.3 User stories

1. **As a** kế toán tổng hợp, **I want to** tải CSV và thấy ngay hàng công nợ xếp theo rủi ro (ngày + tiền), **so that** tôi quyết định ai cần nhắc trước mà không lọc tay 30 phút.  
2. **As a** kế toán, **I want to** tạo 3 bản nháp tin theo 3 cấp độ lịch sự cho 1 dòng công nợ đã chọn, **so that** tôi copy sang Zalo, chỉnh nhẹ, và gửi trong 2 phút.  
3. **As a** chủ DN, **I want to** thấy tổng sắp đến hạn vs quá hạn trong 30 ngày, **so that** tôi trả lời trong họp 15’ về tình hình dòng tiền.  

### 2.4 Success metrics (product)

| Loại | Metric | Ngưỡng thành công (pilot) | Timeframe |
|------|--------|----------------------------|------------|
| **Primary (hành động)** | Thời gian từ *upload → copy tin Zalo* (cấp bất kỳ) | Median **≤ 4 phút** (n=5–8 người) | 2 tuần |
| **Guardrail** | Tỷ lệ lỗi dữ liệu do định dạng CSV | **&lt; 5%** lần upload | 2 tuần |
| **Proxy outcome** | User báo cảm giác *“đỡ stress khi ưu tiên”* (1–5) | Trung bình **≥ 4.0** | 2 tuần |

**Owner sản phẩm/đo:** Nguyễn Thành Nam (cá nhân). **Cập nhật:** review sau mỗi vòng phỏng vấn/pilot (1–2 tuần).  

### 2.5 Dependencies & constraints

- **Dữ liệu:** Chỉ CSV từ xuất MISA/Excel; template cột cần tài liệu hóa.  
- **Kỹ thuật:** Cần API LLM; không lưu dữ liệu lâu dài ở pilot ngoài tùy chọn tự host.  
- **Rủi ro:** Tên KH/ số tiền là thông tin nhạy cảm — prompt không ghi log công khai; tùy chọn “chế độ cẩn mận” (ẩn tên, chỉ mã số) trong bản B.  
- **Pháp/ ngôn từ:** Cấp 3 cảnh báo phải có disclaimer “do người dùng duyệt trước khi gửi”.  

---

## 2.6 AI — Model Selection (lựa chọn thật, có trade-off)

| Trường | Nội dung |
|--------|----------|
| **Model gợi ý (MVP)** | `gpt-4.1-mini` **hoặc** `gpt-4o-mini` (OpenAI API) — chọn 1 theo sẵn có & giá. |
| **Lý do** | Tiếng Việt tốt ở mức bản thảo; độ trễ thấp; API ổn định; đủ context cho 1 hóa đơn + 3 cấp tonality. **Không** cần model “max” vì bài toán là sản xuất văn bản cấu trúc, không lý luận dài. |
| **Chấp nhận trade-off** | Thỉnh thoảng lệch tông nghiệp (B2B trang trọng vs thân) → sửa bằng **hướng dẫn hệ thống + 3 preset** trong prompt; chi phí ~ vài trăm VNĐ/gọi. |
| **Không chấp nhận** | Hallucination số tiền hoặc ngày: **bắt buộc** trích từ bảng JSON validate phía server; model chỉ viết câu, **không** tự tính toán. |
| **Data requirements** | **Nguồn:** CSV người dùng + cấu hình ngành 1 dòng (tuỳ chọn) để bảo đảm từ vựng. **Không** huấn luyện mô hình tùy biến trong MVP. **Không gửi** email/SĐT đăng ký tài chính — chủ đích giảm PII. |

### Fallback UX (1 kịch bản sâu, đủ trigger — Version B)

- **Chiến lược:** **Graceful handover** + chút *expectation management* (báo rõ: “bản thảo — bạn chịu trách nhiệm nội dung gửi đi”).  
- **Khi nào coi “AI không đủ tự tin” (trigger dùng tín hiệu kỹ thuật):**  
  - API lỗi/ timeout **hoặc**  
  - Nội dung trả về thiếu 1 trong 3 placeholder bắt buộc (mã HĐ, số ngày quá hạn, số tiền) **hoặc**  
  - Điểm **độ tự giám** từ API (logprobs) thấp hơn ngưỡng cấu hình.  
- **Hành động hệ thống:** Trả 3 mẫu **tĩnh** cùng cấp (từ thư viện biến thể), điền số/ ngày từ bảng **đã xác thực**; hiển thị banner: *“Bản tĩnh — không dùng AI lúc này”*; ghi sự kiện lỗi.  
- **User có thể:** (1) Sửa trực tiếp trong ô; (2) bấm “Thử tạo lại (AI)”; (3) bỏ qua, copy mẫu tĩnh.  

*Đây là phần đã siết mạnh so với Version A: trước đó chỉ ghi “báo lỗi chung chung” — thiếu trigger và tuyến mẫu tĩnh; engineer không thể build.*

---

## 3. Hypothesis Table

*(Mỗi tính năng In-Scope tối thiểu 1 giả thuyết — phải **có cách làm sai** / falsifiable.)*

| ID | Tính năng (In-Scope) | Công thức |
|----|------------------------|-----------|
| **H1** | Tính năng 1 (bảng ưu tiên) | Tôi tin rằng **bảng ưu tiên theo ngày+tiền từ CSV** sẽ giúp **kế toán** **giảm thời gian quyết định “ai cần nhắc trước” xuống ≤ 5’ so với Excel**. **Làm sai nếu:** 3/5 người nói vẫn mất &gt; 10’ hoặc vẫn xuất ra Excel phụ. |
| | Validation | Sẽ biết khi: **% phiên sử dụng** có **thời gian ưu tiên** (self-report+timer) **≤ 5’** ở **≥ 3/5** người trong **10 ngày**. |
| **H2** | Tính năng 2 (3 bản nháp + AI) | Tôi tin rằng **3 bản nháp từ AI + 1 bản tĩnh dự phòng** sẽ giúp **kế toán** **copy tin đầu tiên &lt; 4’** (median) sau khi chọn 1 công nợ. **Làm sai nếu:** median &gt; 6’ hoặc 3/5 gọi nội dung “sai tông mức không chấp nhận sửa nhanh”. |
| | Validation | Sẽ biết khi: **median thời gian** từ chọn dòng → copy **≤ 4’** với **n ≥ 5** trong **2 tuần** (bút giấy/ stopwatch tại pilot). |
| **H3** | Tính năng 3 (dải 30 ngày) | Tôi tin rằng **2 số: sắp đến hạn vs quá hạn 30d** sẽ giúp **chủ DN** **dùng trong 1 slide họp 15’** mà không hỏi thêm số. **Làm sai nếu:** 2/3 lần họ phải tự tính lại ở Excel. |
| | Validation | Sẽ biết khi: **2/2 buổi họp pilot** số từ màn hình trùng với tổng tự tính (±0,5% làm tròn). |

**Assumption rủi ro nhất (lặp lại ở kiểm chứng nhanh):**  
→ Khách sẵn sàng dùng bản thảo thay vì tự gõ. **Cách rẻ nhất để thử (cheapest test):** 1 buổi 45’ với 3 kế toán: đưa Google Form mock + màn hình thật, đo 2 vòng: (a) tự gõ, (b) bản thảo, so sánh thời gian và thái độ.  

**Riskiest assumption (bảng trên) — 1 câu tóm:**  
> Khách chấp nhận **hương vị câu chữ từ AI** trong ngữ cảnh nhắc nợ mà vẫn cảm thấy an toàn khi sửa & gửi.  

---

## 4. PMF Scorecard

- **Aha moment (hành vi, không phải cảm xúc):**  
  Trong **10 phút đầu** sau import CSV, user **mở 1 dòng công nợ quá hạn** và **copy ít nhất 1 bản tin** (bất cấp) từ sản phẩm sang clipboard — đủ để đối ta biết *workflow đóng*.

- **Actionable metric:**  
  **Tỷ lệ phiên có “import → copy 1 zalo block” (Yes/No)** theo từng user trong tuần 1; đo từ log (sự kiện) hoặc bút giấy pilot.

- **PMF method (chọn 1, có nguỡng):**  
  - **Aha moment tracking (cohort tuần 1)**: ngưỡng **≥ 60%** user pilot đạt Aha **trong 1 buổi sử dụng 45’**.  
  - **Bổ trợ (tuỳ chọn tại tuần 3–4):** *Sean Ellis* — câu “Bạn sẽ cảm thấy thế nào nếu không còn sản phẩm này?”; ngưỡng **&gt; 40%** trả lời “rất thất vọng” ở **N≥10** (hướng tới Day sau).  

**Vanity metrics tôi sẽ không dùng làm go/no-go:**  
- Số lượt gọi API/ user (không tương ứng giá trị).  
- Thời gian “ở lại màn hình” nếu không gắn hành động copy/ gửi.  
- Số tài khoản đăng ký nếu chưa có bằng chứng workflow Aha.  

---

## 5. AI Critique Log

*(Ghi lại cách tôi dùng góp ý từ AI: chấp nhận / từ chối / một phần — điểm chấm ở rubric *Iteration quality* + *Product judgment*.)*

1. **“Thêm tự động gửi Zalo OA từ MVP”** — **Từ chối** — *Lý do:* scope creep, phụ thuộc pháp/ kỹ thuật, không ánh xạ nhu cầu Day 16 ngoài cách “nhắc bằng Zalo thủ công vốn vẫn dùng”.  
2. **“Fallback: chỉ hiện toast lỗi”** — **Một phần → bổ sung** — *Lý do:* cần **mẫu tĩnh + khi nào bật**; giữ thông báo lỗi cho log hệ thống, user vẫn có cách lấy nội dung.  
3. **“Metric: Dễ hơn 50% theo cảm giác”** — **Từ chối** — *Lý do:* không falsifiable; đổi thành **thời gian median** và % phiên Aha.  
4. **(Thêm) “Gộp 3 tính năng còn 2: bỏ dải 30 ngày”** — **Một phần** — *Lý do:* tính năng 3 ánh xạ rõ **Need #2** — giữ; nhưng **làm thành 1 bảng tóm 2 số** (không chart phức tạp) để cắt công.  

**Thay đổi lớn nhất giữa Version A và Version B:**

> Version A ghi *Fallback* chung chung, metric mang tính cảm giác, và còn mở API “tự gửi Zalo” trong ý. Version B: **(1)** đóng phạm vi, **(2)** mô tả 1 chuỗi fallback với mẫu tĩnh + ngưỡng, **(3)** đổi sang metric hành động (time + Aha) để kỹ sư và giảng viên thấy rõ cách chấm đỗ/thất bại.  

---

## 6. Self-assessment

**Mắt xích tôi yếu nhất giữa [MVP Boundary / PRD / Hypothesis / PMF]:**  
> **PMF (đo lường dài hạn) & giả định trả phí** — tôi mới bám pilot 2 tuần; Sean Ellis/ retention sẽ cần dữ liệu lớn hơn.  

**Open questions muốn làm rõ thêm:**  
1. Có cần bắt buộc **Zalo Mini App** hay web/desktop CSV là đủ giai đoạn sớm?  
2. Khi tích hợp bên 3, nên ưu tiên **MISA** hay **Fast** theo tỷ lệ xuất file thực tế ở 10 pilot?  
3. Có cần bản “chỉ tĩnh, không API” tại trường hợc khách từ chối cloud không?  

---

## 7. References (core readings)

- Dan Olsen, *The Lean Product Playbook* — Problem vs Solution space, [leanproductplaybook.com](https://leanproductplaybook.com/) (đã dùng như tài liệu nền Day 16–17).  
- Ghi chú lớp: *Product–Market Fit pyramid*, cách tách *vanity vs actionable* metrics.  

---

*Phiên bản **B** — 23/04/2026. Nội dung **trùng** `submission.md` trên repo GitHub. **Version A** (`Day17-Version-A.md`) nộp snapshot sáng trên LMS — **không chỉnh A sau khi nộp**; file này thể hiện cải thiện so với A (stress-test, rubric A→B).*
