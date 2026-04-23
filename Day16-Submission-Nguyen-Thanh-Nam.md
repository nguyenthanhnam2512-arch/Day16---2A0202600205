# Day 16 Submission — Nguyễn Thành Nam (cá nhân)

## Author
- **Nguyễn Thành Nam** — tác giả duy nhất, hoàn thành toàn bộ nội dung bài nộp.

---

## 1. Idea reframed

**Original idea:**

> Công cụ AI nhắc nợ và theo dõi công nợ cho các SMB B2B ở Việt Nam, giảm thời gian “điện thoại hỏi tiền” mỗi tháng.

**Reframed as a product opportunity:**

> Cơ hội sản phẩm nằm ở **khoảng trống vận hành tài chính**: hầu hết doanh nghiệp siêu nhỏ/ nhỏ vẫn theo công nợ bằng **Excel + Zalo/điện thoại**, dẫn đến trễ thu, sai hạn, và mất 5–10 giờ/tuần cho công tác dunning lặp lại. **Observed gap:** không thiếu kế toán MISA/Fast, nhưng thiếu lớp “công cụ theo từng hóa đơn + nhắc theo hạn hợp đồng” ở mức vận hành (không cần ERP). **Founding belief:** nếu xây sản phẩm tập trung **1 workflow—đối soát công nợ gần hạn/ quá hạn** với cách nhắc phù hợp tập quán giao tiếp VN (Zalo, SMS), giá trị tính theo thời gian tiết kiệm sẽ đủ để bán ở mô hình SaaS mức thấp.

---

## 2. Customer / Segment Card

- **Segment name:** SMB B2B “Net 7–30” (phân phối nhỏ, sản xuất OEM nhỏ, dịch vụ B2B)  
- **Operational context:** Ra hóa đơn/ biên bản bàn giao, ghi nhận công nợ trên sổ kế toán hoặc file; công tác theo dõi hạn thanh toán nằm ở **Kế toán trưởng/ Kế toán tổng hợp** hoặc **chủ DN**; giao tiếp khách chủ yếu qua Zalo.  
- **Recurring workflow:** (1) Xuất hóa đơn → (2) ghi nhận hạn thu → (3) hàng tuần rà công nợ cận hạn/ quá hạn → (4) nhắc khách theo mốc hợp đồng → (5) cập nhật trạng thái/ đối soát.  
- **Pain moment:** Danh sách công nợ phân tán, dễ **trễ nhắc đúng ngày**; nhắc bằng cảm tính; khó ước lượng mức rủi ro dòng tiền 2–4 tuần tới.  
- **Why now:** Cạnh tranh dòng vốn tăng; nhiều nhà cung ứng **siết tín dụng nội bộ**; công nghệ gửi thông báo tự động (Zalo OA / SMS gateway) dễ tiếp cận hơn 3–5 năm trước.  
- **Access path:** Chợ đầu mối/ hiệp hội ngành địa phương, nhóm Facebook/Zalo nghề, giới thiệu từ dịch vụ kế toán thuê ngoài, hội doanh nghiệp trẻ.  

**One-sentence description:**

> *Khách hàng sớm là kế toán/ chủ DN B2B ~10–80 tỷ doanh thu/năm, đang “săn” từng hóa đơn cận hạn bằng bảng Excel và tin nhắn tay, cần bớt 5–10 giờ/tuần cho việc nhắc nợ lặp lại mà vẫn theo sát từng khách hàng.*

---

## 3. Need Map (2–3 needs)

### Need #1 (priority)

- **Statement (JTBD):** When **có nhiều hóa đơn cận hạn/ quá hạn cùng lúc**, I want **một bảng ưu tiên rõ theo số ngày quá hạn + số tiền** và **bộ mẫu nhắc theo từng bậc lịch sự**, so I can **thu về dòng tiền sớm hơn mà không làm tổn thương quan hệ B2B**.  
- **Current workaround:** Lọc Excel, note tay trên sổ, gọi điện từng người theo cảm giác, nhắc Zalo thủ công.  
- **Pain signal:** Công nợ quá hạn kéo dài; khách “im lặng” sau 2 lần nhắc; mất 1–2 ngày công/ tháng chỉ cho việc đôn đốc.  
- **Evidence / proxy evidence:** (Proxy) câu hỏi kế toán SME trên cộng đồng thường xoay quanh quản công nợ + Zalo; dự kiến bổ sung 3 hội thoại sâu hoặc khảo sát nhanh nếu triển khai pilot.  
- **Why underserved:** ERP/ phần mềm lớn quá; app kế toán tập trung **ghi sổ** hơn là **dunning theo từng mốc hạn**; công cụ nước ngoài không tối ưu tập quán giao tiếp VN.

### Need #2

- **Statement (JTBD):**  
  When **sếp/ chủ DN hỏi “tháng này thu bao nhiêu, rủi ro dòng tiền ra sao”**, I want **báo cáo 2–3 chỉ số dự báo 30 ngày tới** từ dữ liệu hóa đơn, so I can **lên kế hoạch chi trả cho nhà cung ứng và tồn kho an toàn hơn**.  
- **Current workaround:** Tự tổng hợp từ Excel, copy sang slide hoặc tin nhắn Zalo.  
- **Pain signal:** Số liệu **không cập nhật tức thời**; tranh cãi nội bộ vì nguồn số khác nhau.  
- **Evidence / proxy evidence:** (Proxy) tần suất câu hỏi dòng tiền trong họp hàng tuần; checklist KPI SME thường có DSO.  
- **Why underserved:** SME không có data team; dashboard BI quá nặng cho quy mô.  

### Need #3 (optional)

- **Statement (JTBD):**  
  When **khách hàng thanh toán từng phần hoặc chậm theo từng lần giao dịch**, I want **lịch sử đối soát 1-1 theo từng hóa đơn/ biên bản** để mọi người nhìn cùng một “bằng chứng”, so I can **tránh cãi nhau nội bộ** và rút kinh nghiệm tín dụng cho khách.  
- **Current workaround:** Screenshot, forward tin nhắn, file Excel riêng từng người.  
- **Pain signal:** Mất 30–60 phút/ case để tìm lại đối thoại khi xảy ra hiểu lầm.  
- **Evidence / proxy evidence:** 1–2 case study từ phỏng vấn nếu có.  
- **Why underserved:** CRM nặng, không tích hợp văn hóa hóa đơn VN ở mức gọn.  

---

## 4. Strategy Statement

> For **kế toán tổng hợp/ chủ doanh nghiệp B2B (10–200 nhân) vận hành công nợ chủ yếu trên Excel**  
> who struggle with **nhắc nợ lặp lại, thiếu ưu tiên theo hạn, và mất nhiều thời gian liên lạc tay**,  
> this product helps them **rút ngắn số ngày thu tiền (DSO) và giảm giờ làm dunning mỗi tuần**  
> through **nhập/đồng bộ dữ liệu hóa đơn (CSV) + tự động tạo lịch nhắc + mẫu Zalo/ SMS theo cấp độ**,  
> unlike **MISA/Fast ở lớp hạch toán, hay CRM/ERP, hay nhắc nợ thủ công bằng Zalo/điện thoại**,  
> because I can leverage **tập trung 1 use-case, hiểu tập quán thu hồi công nợ VN, và triển khai nhanh ở quy mô cá nhân (sau đó mở rộng) — dunning có kiểm soát theo từng mốc hạn**.

---

## 5. Moat Hypothesis

- **Moat mechanism:** *Composite moat* — dữ liệu vận hành công nợ theo **ngành/ khu vực** (mẫu tin nhắm hiệu quả, mức độ “nhây nợ” trung bình) + tích hợp sâu với kênh Zalo/ SMS phổ biến tại VN.  
- **If I deploy [N] lần trong [SMB B2B phân phối/ dịch vụ tại 1 tỉnh/ miền], the following improve:**  
  1. Thư viện **mẫu nhắc + tông điệu** theo ngành (mỡ màu, chính thức, cảnh báo)  
  2. **Score rủi ro khách hàng** dựa trên lịch sử (proxy DSO)  
  3. Tích hợp tối ưu với nguồn dữ liệu thực tế (định dạng xuất từ kế toán, sau này API)  
- **Why competitors cannot easily replicate this:**  
  > Sản phẩm tài chính toàn cầu hay ERP không ưu tiên mức “nhắc nợ vừa đủ + đúng văn hóa VN + triển khai trong 1 buổi” cho SMB; cạnh tranh từ phía “tool nhắc chung chung” thiếu mô-đun **đúng từng hóa đơn/ hạn hợp đồng** và cách bán qua cộng đồng ngành.  

---

## 6. Initial TAM / SAM / SOM view

| Layer | Estimate | Key assumptions | Confidence |
|--------|-----------|----------------|------------|
| TAM | ~ **80–200 triệu USD/năm** (giảm DSO/ chi phí dunning cho lớp SMB B2B ở VN — order of magnitude) | Ước số doanh nghiệp vừa/nhỏ B2B × chi trả sẵn sàng cho tool vận hành 10–30 USD/ user/ tháng; **nhiều quan trọng ở cách định nghĩa phạm vi** | low |
| SAM | **8–20 triệu USD/năm** (SMB ~10–200 nhân, chấp nhận SaaS, công nợ 50+ hóa đơn/ tháng) | 5–8% thị trường mục tiêu; bán trực tiếp + kênh kế toán dịch vụ/ giới thiệu; **TAM ở trên là cùng cấp, không cần chính xác tuyệt đối** | med |
| SOM (12–24 tháng) | **0,3–1,0 triệu USD ARR** (khoảng 300–1.200 khách trả phí) | **Góc cá nhân:** giai đoạn đầu tự làm sales + 1–2 kênh giới thiệu, 15–30 pilot/ năm (điều chỉnh theo thời gian thực tế); số này là **giả thuyết, cần thử ở pilot** | low |

- **Top 3 unknowns requiring further research:**  
  1. Tỷ lệ SMB chấp nhận trả phí theo mô hình **per-seat vs per-ticket**; ngưỡng “đau ví” thực tế.  
  2. Tính tương thích **xuất dữ liệu** từ MISA/Fast mà SME đang dùng (rào cản tích hợp thực tế).  
  3. Mức trần cạnh tranh từ **Zalo shop/ ngân hàng số** cung cấp tính năng nhắc thanh toán (đe dọa từ phía tài chính lớn).  

- **Judgment:**  
  - [x] **Worth pursuing now** (với cách **pilot 5–8 khách, scope CSV + bảng ưu tiên + mẫu Zalo 3 cấp** trước khi mở rộng)  
  - [ ] Worth pursuing but not now (need to validate […] first)  
  - [ ] Not worth pursuing as currently framed  

---

## 7. Positioning Note (2 sentences)

- **What we are:**  
  > Đây là công cụ vận hành công nợ cho SME B2B, giúp ưu tiên ai cần nhắc trước, nhắc đúng mốc, và giảm thời gian đôn đốc thủ công.  

- **What we are not / not yet:**  
  > Sản phẩm này không thay thế kế toán, không phải hệ thống ERP, và (giai đoạn sớm) cũng **chưa** là công cụ thẩm định tín dụng pháp lý cho ngân hàng.  

---

## 8. Self-assessment before Day 17

Trong 6 mắt xích **Idea, Customer, Need, Strategy, Moat, Market size**, mắt xích tôi cần tập trung nhất lúc này là: **Need + Evidence (đặc biệt SOM/ willingness to pay)** — tôi có câu chuyện thuyết phục ở mức logic, nhưng chưa khóa bằng **số liệu pilot đủ nặng** (trước/sau DSO, thời gian tiết kiệm). Mắt xích **rõ nhất** hiện tại: **Idea/ Strategy** (problem/solution hẹp, dễ mô tả với khách hàng sớm).

> [trả lời thật — đây là input quan trọng cho Day 17]

**Open questions tôi muốn khám phá thêm ở Day 17:**

1. **MVP 6 tuần** nên cắt tới mức nào: chỉ bảng ưu tiên + mẫu Zalo, hay cần thêm nhắc tự động qua 1 tích hợp?  
2. Cấu trúc **PRD** ưu tiên metric nào: giảm giờ dunning, giảm DSO, hay tỷ lệ công nợ quá hạn?  
3. Thí nghiệm 2 tuần đầu: nên thiết kế theo dạng **A/B mẫu nhắc** hay **đo thời gian trước-sau tại 1 doanh nghiệp thử nghiệm (pilot)?**  

---

*Bài nộp cá nhân — Nguyễn Thành Nam. Nên rà số TAM/SAM theo cách tính giảng viên yêu cầu (nếu có) và chuẩn bị bảo vệ bằng số từ phỏng vấn/pilot khi có.*
