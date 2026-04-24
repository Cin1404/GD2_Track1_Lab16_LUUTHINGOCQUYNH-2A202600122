# Day 16 Submission
- Lưu Thị Ngọc Quỳnh - 2A202600122

---

## 1. Idea reframed

Original idea:  
> Xây dựng một công cụ AI hỗ trợ đội vận hành chuỗi bán lẻ điều phối tồn kho giữa nhiều cửa hàng, nhằm giảm thiếu hàng và tồn dư.

Reframed as a product opportunity:  

> Đội vận hành chuỗi bán lẻ đang phải ra quyết định điều chuyển tồn kho trong bối cảnh quy mô bán lẻ đa kênh tăng nhanh, số lượng SKU lớn và nhu cầu biến động liên tục theo thời gian. Trong khi đó, dữ liệu bán hàng, tồn kho và nhu cầu vẫn phân tán giữa nhiều cửa hàng và hệ thống khác nhau, khiến việc tổng hợp và phân tích trở nên chậm trễ.
>
> Riêng tại Việt Nam, GMV ecommerce được Google, Temasek và Bain ước tính đạt 19 tỷ USD năm 2023 và dự kiến 25 tỷ USD năm 2025, phản ánh tốc độ mở rộng nhanh của hệ thống bán lẻ đa điểm. Điều này kéo theo áp lực rất lớn lên hoạt động vận hành tồn kho giữa các cửa hàng.
>
> Tuy nhiên, vấn đề cốt lõi không chỉ nằm ở việc thiếu dữ liệu, mà là **độ trễ trong ra quyết định (decision latency)** và **chất lượng quyết định (decision quality)**. Các dashboard hiện tại chủ yếu dừng ở việc cung cấp thông tin, nhưng không hỗ trợ người dùng chuyển từ insight sang hành động cụ thể.
>
> Trong khi đó, bài toán tồn kho gây ra tổn thất kinh tế đáng kể: IHL Group ước tính ngành bán lẻ toàn cầu mất khoảng 1.73 nghìn tỷ USD mỗi năm do out-of-stocks và overstocks.
>
> Cơ hội sản phẩm nằm ở việc xây dựng một **AI Decision Copilot for Inventory Operations**, có khả năng:
> - phát hiện sớm tín hiệu rủi ro thiếu hoặc dư hàng
> - dự báo nhu cầu ngắn hạn theo từng cửa hàng và SKU
> - đề xuất phương án điều chuyển cụ thể (từ đâu → đến đâu → bao nhiêu)
> - ước lượng tác động của từng quyết định (expected impact)
>
> McKinsey cho biết khi áp dụng AI vào forecasting cho supply chain, doanh nghiệp có thể giảm sai số dự báo 20 - 50%, giảm lost sales tới 65%, đồng thời giảm 5 - 10% chi phí kho và 25 - 40% chi phí hành chính.
>
> Founding belief của nhóm là: với một workflow mang tính vận hành cao và phụ thuộc nhiều vào con người như điều phối tồn kho, AI tạo giá trị mạnh nhất khi đóng vai trò **decision-support trực tiếp trong workflow**, giúp người dùng ra quyết định nhanh hơn, tự tin hơn và nhất quán hơn, trước khi tiến tới tự động hóa sâu hơn trong tương lai.

---

## 2. Customer/Segment Card

- **Segment name:** Nhân viên vận hành chuỗi bán lẻ dùng AI hỗ trợ điều phối tồn kho
- **Operational context:** Quản lý dữ liệu bán hàng, tồn kho và nhu cầu tại nhiều cửa hàng, nhưng thông tin phân tán, cập nhật liên tục và không đồng nhất giữa các hệ thống.
- **Recurring workflow:** Theo dõi bán hàng, phát hiện nơi thiếu hoặc dư hàng, so sánh giữa các cửa hàng và ra quyết định điều chuyển tồn kho.
- **Pain moment:** Cửa hàng hết hàng đúng lúc nhu cầu tăng, trong khi nơi khác vẫn còn dư mà không được phát hiện và xử lý kịp thời.
- **Why now:** AI đã đủ tốt để không chỉ dự báo nhu cầu mà còn phát hiện pattern bất thường, đưa ra gợi ý điều phối và hỗ trợ ra quyết định theo thời gian gần thực.
- **Access path:** Triển khai dưới dạng AI copilot tích hợp vào dashboard nội bộ hoặc phần mềm quản lý bán hàng.

One-sentence description:  
> Đây là người mỗi ngày phải ra nhiều quyết định điều chuyển tồn kho trong điều kiện thông tin không đầy đủ, và AI giúp họ ra quyết định nhanh hơn, chính xác hơn và tự tin hơn.

---

## 3. Need Map

### Need #1 (priority)
- **Statement (JTBD):** Khi tôi quản lý tồn kho cho nhiều cửa hàng, tôi muốn nhìn thấy sớm tín hiệu thiếu hàng hoặc dư hàng và biết nên làm gì ngay lập tức, để tôi có thể xử lý trước khi mất doanh thu.
- **Current workaround:** Kiểm tra báo cáo bán hàng và tồn kho thủ công mỗi ngày qua nhiều file hoặc dashboard.
- **Pain signal:** Chỉ phát hiện khi cửa hàng đã gần hết hàng hoặc đã dư hàng rõ rệt.
- **Evidence/proxy evidence:** Dữ liệu nằm rời rạc; phải kiểm tra nhiều nguồn mới thấy vấn đề.
- **Why underserved:** Dashboard hiện tại chỉ hiển thị dữ liệu mà chưa hỗ trợ chuyển từ insight sang action.

### Need #2
- **Statement (JTBD):** Khi nhu cầu giữa các cửa hàng thay đổi, tôi muốn biết nên chuyển hàng từ đâu, sang đâu và bao nhiêu, cũng như tác động nếu không thực hiện điều chuyển, để tôi có thể giảm cả thiếu hàng lẫn tồn dư.
- **Current workaround:** Dựa vào kinh nghiệm cá nhân và so sánh số liệu thủ công để quyết định điều chuyển.
- **Pain signal:** Một nơi hết hàng nhưng nơi khác vẫn còn dư hàng.
- **Evidence/proxy evidence:** Cùng lúc xuất hiện cả stockout và overstock trong cùng mạng lưới cửa hàng.
- **Why underserved:** Chưa có công cụ hỗ trợ decision-level đủ nhanh, nhất quán và gắn với dữ liệu thời gian gần thực.

### Need #3 (optional)
- **Statement (JTBD):** Khi tôi chuẩn bị ra quyết định điều phối tồn kho, tôi muốn có một góc nhìn thống nhất về doanh số, tồn kho và nhu cầu trong cùng một nơi, để tôi có thể giảm thời gian tổng hợp dữ liệu và tập trung vào hành động.
- **Current workaround:** Ghép dữ liệu từ nhiều file Excel, dashboard hoặc hệ thống khác nhau.
- **Pain signal:** Mất nhiều thời gian tổng hợp trước khi xử lý được vấn đề thật.
- **Evidence/proxy evidence:** Quy trình lặp lại mỗi ngày, tốn công và dễ sai sót.
- **Why underserved:** Hệ thống hiện tại chưa được thiết kế xoay quanh workflow ra quyết định.

---

## 4. Strategy Statement

For **nhân viên vận hành chuỗi bán lẻ** who struggle with **ra quyết định điều phối tồn kho chậm và chưa tối ưu**, our product helps them **giảm độ trễ quyết định và nâng cao chất lượng quyết định thông qua dự báo nhu cầu và gợi ý điều phối tồn kho**, through **một AI decision copilot tích hợp trực tiếp vào workflow vận hành hằng ngày**, unlike **báo cáo thủ công, dashboard tĩnh hoặc quyết định dựa vào kinh nghiệm cá nhân**, because we can leverage **dữ liệu bán hàng theo điểm bán, tín hiệu tồn kho, và learning loop từ quyết định thực tế**.

---

## 5. Moat Hypothesis

**Moat mechanism:** domain-learning flywheel kết hợp với decision intelligence

If we deploy [N] times in retail chain operations, the following improve:
1. Chất lượng dự báo nhu cầu theo từng cửa hàng và SKU tốt hơn nhờ dữ liệu lịch sử tích lũy.
2. Chất lượng gợi ý điều chuyển tốt hơn nhờ học từ quyết định đã được chấp nhận hoặc bị từ chối.
3. Khả năng đánh giá tác động của quyết định (impact estimation) ngày càng chính xác hơn.
4. Workflow ngày càng bám sát thực tế vận hành của từng chuỗi, tạo lợi thế tích hợp và switching cost cao.

Why competitors cannot easily replicate this:  
> Giá trị không chỉ nằm ở mô hình AI chung, mà nằm ở dữ liệu vận hành đặc thù, decision history, outcome thực tế và mức độ tích hợp sâu vào quy trình điều phối tồn kho của từng chuỗi bán lẻ.

---

## 6. Initial TAM/SAM/SOM view

### Cách tiếp cận ước tính
Giả định chính:
- Sản phẩm được bán dưới dạng **AI decision copilot hỗ trợ forecasting + inventory allocation**
- Mức giá giả định ban đầu là **USD 600/store/năm**  
- Thị trường mục tiêu trước mắt tập trung vào các chuỗi có nhiều điểm bán và có dữ liệu số hóa ở mức cơ bản

### Bảng TAM/SAM/SOM

| Layer | Estimate | Cách tính | Ý nghĩa |
|---|---:|---|---|
| **TAM** | **~USD 6.6M ARR** | 11,053 stores × USD 600/store/năm | Toàn bộ thị trường điểm bán hiện đại phù hợp tại Việt Nam |
| **SAM** | **~USD 2.16M ARR** | 5,138 stores × 70% readiness × USD 600 | Phần thị trường có thể phục vụ trong giai đoạn đầu |
| **SOM** | **~USD 0.43M ARR** | 6 chuỗi × 120 stores × USD 600 | Phần thị trường có thể đạt được trong 12–24 tháng |

---

### Kết luận ngắn
Đây là một thị trường đủ lớn và có nhu cầu thực tế rõ ràng:
- **TAM ~ 6.6M USD ARR**
- **SAM ~ 2.16M USD ARR**
- **SOM ~ 0.43M USD ARR**

---

### Top 3 điều cần kiểm chứng thêm
1. Mức giá tối ưu theo store hay theo value tạo ra
2. Mức độ sẵn sàng triển khai thực tế của các chuỗi
3. Nhóm ngành nào là beachhead tốt nhất

---

**Judgment:**
- [x] Worth pursuing now

---

## 7. Positioning Note (2 sentences)

**What we are:**  
> Một AI decision copilot hỗ trợ đội vận hành chuỗi bán lẻ phát hiện sớm rủi ro tồn kho và đưa ra gợi ý điều phối có tính định lượng.

**What we are not/not yet:**  
> Chúng tôi chưa phải là hệ thống tự động điều phối hoàn toàn; giai đoạn đầu tập trung vào decision support để con người vẫn là người ra quyết định cuối cùng, nhưng với sự hỗ trợ tốt hơn về tốc độ và độ chính xác.