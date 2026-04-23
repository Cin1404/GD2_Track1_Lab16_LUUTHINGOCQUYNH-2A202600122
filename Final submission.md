# Day 16 Submission
- Lưu Thị Ngọc Quỳnh - 2A202600122

---

## 1. Idea reframed

Original idea:  
> Xây dựng một công cụ AI hỗ trợ đội vận hành chuỗi bán lẻ điều phối tồn kho giữa nhiều cửa hàng, nhằm giảm thiếu hàng và tồn dư.

Reframed as a product opportunity:  

> Đội vận hành chuỗi bán lẻ đang phải ra quyết định điều chuyển tồn kho trong bối cảnh quy mô bán lẻ số tăng nhanh, trong khi dữ liệu bán hàng, tồn kho và nhu cầu vẫn phân tán giữa nhiều cửa hàng và hệ thống. Riêng tại Việt Nam, GMV ecommerce được Google, Temasek và Bain ước tính ở mức 19 tỷ USD năm 2023 và 25 tỷ USD năm 2025, cho thấy áp lực vận hành đa điểm bán ngày càng lớn.
> Trong khi đó, bài toán tồn kho không chỉ là bất tiện vận hành mà là tổn thất kinh tế thật: IHL Group ước tính ngành bán lẻ toàn cầu vẫn đang mất khoảng 1,73 nghìn tỷ USD mỗi năm do out-of-stocks và overstocks.
> Cơ hội sản phẩm nằm ở việc xây một AI copilot for inventory operations có thể phát hiện sớm rủi ro thiếu hàng hoặc dư hàng, dự báo nhu cầu ngắn hạn và gợi ý phương án phân bổ giữa các cửa hàng trước khi doanh thu bị mất. McKinsey cho biết khi áp dụng AI vào forecasting cho supply chain, doanh nghiệp có thể giảm sai số dự báo 20 - 50%, giảm lost sales/product unavailability tới 65%, đồng thời giảm 5 - 10% chi phí kho và 25 - 40% chi phí hành chính.
> Founding belief của nhóm là: với một workflow đang còn nặng thủ công và phản ứng muộn như điều phối tồn kho, AI tạo giá trị mạnh nhất khi đóng vai trò decision-support trước, rồi mới tiến tới tự động hóa sâu hơn sau này.
---

## 2. Customer/Segment Card

- **Segment name:** Nhân viên vận hành chuỗi bán lẻ dùng AI hỗ trợ điều phối tồn kho
- **Operational context:** Quản lý dữ liệu bán hàng, tồn kho và nhu cầu tại nhiều cửa hàng, nhưng thông tin phân tán và thay đổi liên tục.
- **Recurring workflow:** Theo dõi bán hàng, phát hiện nơi thiếu hoặc dư hàng, rồi quyết định điều chuyển giữa các điểm bán.
- **Pain moment:** Cửa hàng hết hàng đúng lúc nhu cầu tăng, trong khi nơi khác vẫn còn dư mà không xử lý kịp.
- **Why now:** AI đã đủ tốt để dự báo nhu cầu, cảnh báo thiếu hàng sớm và gợi ý phân bổ hiệu quả hơn thủ công.
- **Access path:** Triển khai dưới dạng AI copilot tích hợp vào dashboard nội bộ hoặc phần mềm quản lý bán hàng.

One-sentence description:  
> Đây là người mỗi ngày phải quyết định chuyển hàng giữa các cửa hàng, và AI giúp họ làm nhanh, sớm và chính xác hơn.

---

## 3. Need Map

### Need #1 (priority)
- **Statement (JTBD):** Khi tôi quản lý tồn kho cho nhiều cửa hàng, tôi muốn nhìn thấy sớm tín hiệu thiếu hàng hoặc dư hàng, để tôi có thể xử lý trước khi mất doanh thu.
- **Current workaround:** Kiểm tra báo cáo bán hàng và tồn kho thủ công mỗi ngày qua nhiều file hoặc dashboard.
- **Pain signal:** Chỉ phát hiện khi cửa hàng đã gần hết hàng hoặc đã dư hàng rõ rệt.
- **Evidence/proxy evidence:** Dữ liệu nằm rời rạc; phải kiểm tra nhiều nguồn mới thấy vấn đề.
- **Why underserved:** Cách hiện tại chậm, phản ứng muộn và phụ thuộc nhiều vào con người.

### Need #2
- **Statement (JTBD):** Khi nhu cầu giữa các cửa hàng thay đổi, tôi muốn biết nên chuyển hàng từ đâu, sang đâu và bao nhiêu, để tôi có thể giảm cả thiếu hàng lẫn tồn dư.
- **Current workaround:** Dựa vào kinh nghiệm cá nhân và so sánh số liệu thủ công để quyết định điều chuyển.
- **Pain signal:** Một nơi hết hàng nhưng nơi khác vẫn còn dư hàng.
- **Evidence/proxy evidence:** Cùng lúc xuất hiện cả stockout và overstock trong cùng mạng lưới cửa hàng.
- **Why underserved:** Chưa có công cụ hỗ trợ quyết định đủ nhanh, nhất quán và gắn với dữ liệu thời gian gần thực.

### Need #3 (optional)
- **Statement (JTBD):** Khi tôi chuẩn bị ra quyết định điều phối tồn kho, tôi muốn có một góc nhìn thống nhất về doanh số, tồn kho và nhu cầu, để tôi có thể dành ít thời gian tổng hợp dữ liệu hơn và nhiều thời gian hành động hơn.
- **Current workaround:** Ghép dữ liệu từ nhiều file Excel, dashboard hoặc hệ thống khác nhau.
- **Pain signal:** Mất nhiều thời gian tổng hợp trước khi xử lý được vấn đề thật.
- **Evidence/proxy evidence:** Quy trình lặp lại mỗi ngày, tốn công và dễ sai sót.
- **Why underserved:** Hệ thống hiện tại chưa được thiết kế xoay quanh workflow điều phối vận hành.

---

## 4. Strategy Statement

For **nhân viên vận hành chuỗi bán lẻ** who struggle with **phát hiện rủi ro tồn kho muộn và ra quyết định điều chuyển chưa tối ưu**, our product helps them **dự báo nhu cầu ngắn hạn và gợi ý điều phối tồn kho tốt hơn**, through **một AI copilot tích hợp vào workflow vận hành hằng ngày**, unlike **báo cáo thủ công, dashboard tĩnh hoặc quyết định dựa vào kinh nghiệm cá nhân**, because we can leverage **dữ liệu bán hàng theo điểm bán, tín hiệu tồn kho và learning loop từ quyết định thực tế**.

---

## 5. Moat Hypothesis

**Moat mechanism:** domain-learning flywheel

If we deploy [N] times in retail chain operations, the following improve:
1. Chất lượng dự báo nhu cầu theo từng cửa hàng và SKU tốt hơn nhờ dữ liệu lịch sử tích lũy.
2. Chất lượng gợi ý điều chuyển tốt hơn nhờ học từ quyết định đã được chấp nhận hoặc bị từ chối.
3. Workflow ngày càng bám sát thực tế vận hành của từng chuỗi, tạo lợi thế tích hợp và switching cost.

Why competitors cannot easily replicate this:  
> Giá trị không chỉ nằm ở mô hình AI chung, mà nằm ở dữ liệu vận hành đặc thù, feedback loop từ quyết định thật và mức độ tích hợp sâu vào quy trình điều phối tồn kho của từng chuỗi bán lẻ.

---

## 6. Initial TAM/SAM/SOM view

### Cách tiếp cận ước tính
Giả định chính:
- Sản phẩm được bán dưới dạng **AI copilot hỗ trợ forecasting + inventory allocation**
- Mức giá giả định ban đầu là **USD 600/store/năm**  
- Thị trường mục tiêu trước mắt tập trung vào các chuỗi có nhiều điểm bán và có dữ liệu số hóa ở mức cơ bản

### Bảng TAM/SAM/SOM

| Layer | Estimate | Cách tính | Ý nghĩa |
|---|---:|---|---|
| **TAM** | **~USD 6.6M ARR** | 11,053 stores × USD 600/store/năm | Toàn bộ thị trường điểm bán hiện đại phù hợp tại Việt Nam |
| **SAM** | **~USD 2.16M ARR** | 5,138 stores (HCM + HN) × 70% readiness × USD 600 | Phần thị trường nhóm có thể phục vụ trong giai đoạn đầu |
| **SOM** | **~USD 0.43M ARR** | 6 chuỗi × 120 stores/chuỗi × USD 600 | Phần thị trường nhóm có thể thực sự giành được trong 12–24 tháng đầu |

### 6.1. TAM - Total Addressable Market
TAM là **toàn bộ thị trường khả dụng** nếu sản phẩm có thể bán cho tất cả các chuỗi phù hợp với bài toán này tại Việt Nam.

Nhóm chọn 3 nhóm điểm bán hiện đại có khả năng cao phát sinh nhu cầu điều phối tồn kho:
- **449 siêu thị**
- **7,362 cửa hàng convenience/mini-super**
- **3,242 nhà thuốc chuỗi**

Tổng cộng là **11,053 điểm bán**.

Với giả định giá trung bình là **USD 600/store/năm**, ta có:

**TAM = 11,053 × 600 = USD 6,631,800/năm**

Điều này có nghĩa là nếu sản phẩm được thương mại hóa rộng trên toàn bộ nhóm cửa hàng mục tiêu, quy mô doanh thu phần mềm hằng năm có thể vào khoảng **6.6 triệu USD ARR**.

### 6.2. SAM - Serviceable Available Market
SAM là **phần thị trường mà nhóm thực sự có khả năng phục vụ trong giai đoạn đầu**, xét theo địa lý và mức độ sẵn sàng triển khai.

Nhóm chọn **TP.HCM và Hà Nội** làm thị trường khởi đầu vì đây là hai khu vực tập trung nhiều chuỗi bán lẻ nhất, đồng thời có mức độ số hóa cao hơn mặt bằng chung.

Số điểm bán tại 2 thành phố này gồm:
- **228 siêu thị**
- **3,639 cửa hàng convenience/mini-super**
- **1,271 nhà thuốc chuỗi**

Tổng cộng: **5,138 điểm bán**

Tuy nhiên, không phải tất cả đều sẵn sàng triển khai ngay. Nhóm giả định chỉ khoảng **70% số điểm bán** thuộc các chuỗi có đủ điều kiện ban đầu như:
- có hệ thống POS/ERP hoặc dữ liệu bán hàng số hóa
- có đội vận hành theo dõi tồn kho liên cửa hàng
- có pain rõ về stockout/overstock
- sẵn sàng thử nghiệm công cụ decision-support

Do đó:

**SAM stores = 5,138 × 70% = 3,597 stores**  
**SAM = 3,597 × 600 = USD 2,158,200/năm**

Nói cách khác, quy mô thị trường khả dụng thực tế trong giai đoạn đầu vào khoảng **2.16 triệu USD ARR**.

### 6.3. SOM - Serviceable Obtainable Market
SOM là **phần thị trường nhóm có thể thực sự đạt được trong 12–24 tháng đầu**, nếu đi theo hướng pilot rồi mở rộng dần.

Nhóm đưa ra kịch bản thực tế hơn:
- chốt được **6 chuỗi đầu tiên**
- trung bình mỗi chuỗi có **120 điểm bán**
- tổng quy mô triển khai là **720 stores**

Khi đó:

**SOM = 720 × 600 = USD 432,000 ARR**

Đây là mục tiêu tương đối hợp lý cho giai đoạn đầu vì:
- chưa cần phủ rộng toàn thị trường
- có thể bắt đầu từ pilot nhỏ
- sau khi chứng minh được hiệu quả giảm stockout/overstock thì mới mở rộng theo chuỗi


### Kết luận ngắn
Từ góc nhìn ban đầu, đây là một thị trường đủ lớn để đáng theo đuổi:
- **TAM ~ 6.6M USD ARR**
- **SAM ~ 2.16M USD ARR**
- **SOM ~ 0.43M USD ARR trong 12 - 24 tháng đầu**

Điều này cho thấy sản phẩm không chỉ giải quyết một pain thực tế trong vận hành chuỗi bán lẻ, mà còn có quy mô đủ rõ để xem như một cơ hội sản phẩm khả thi.

### Top 3 điều cần kiểm chứng thêm
1. Mức giá phù hợp nhất nên là **theo store**, **theo chain**, hay **theo số lần sử dụng/giá trị tạo ra**
2. Tỷ lệ readiness thực tế của các chuỗi bán lẻ có đúng gần mức 70% hay không
3. Nhóm ngành nào là beachhead tốt nhất: **convenience**, **pharmacy**, hay **supermarket**


**Judgment:**
- [x] Worth pursuing now
- [ ] Worth pursuing but not now (need to validate [...] first)
- [ ] Not worth pursuing as currently framed

---

## 7. Positioning Note (2 sentences)

**What we are:**  
> Một AI copilot hỗ trợ đội vận hành chuỗi bán lẻ phát hiện sớm rủi ro tồn kho và đưa ra gợi ý điều phối giữa các cửa hàng.

**What we are not/not yet:**  
> Chúng tôi chưa phải là hệ thống tự động điều phối hoàn toàn; giai đoạn đầu tập trung vào decision support để con người vẫn là người ra quyết định cuối cùng.