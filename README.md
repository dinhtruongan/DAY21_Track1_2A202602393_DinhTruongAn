# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- **Họ và tên:** Đinh Trường An
- **MSSV / mã học viên:** 2A202602393
- **Lớp:** AI20K Build Phase — Cohort 4, Track 1
- **Ngành đã chọn:** HR / tuyển dụng
- **Phạm vi:** AI hỗ trợ sàng lọc và xếp hạng CV.

Hai case dưới đây là hai nghiên cứu thực nghiệm khác nhau, sử dụng AI thật. Kết quả đo trong nghiên cứu được tách khỏi nguy cơ khi triển khai tuyển dụng. Nhãn rủi ro trong bài là đánh giá định tính của tôi, không phải phân loại pháp lý.

## 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | Ứng viên bị mất cơ hội phỏng vấn khi AI xếp hạng dựa trên dấu hiệu nhân khẩu học thay vì năng lực. Lý do đánh giá thiếu căn cứ có thể làm tổn hại phẩm giá. CV còn có nguy cơ bị sử dụng hoặc chia sẻ ngoài mục đích tuyển dụng. Doanh nghiệp có thể bỏ sót ứng viên phù hợp. |
| Mức độ high-stakes | **Cao.** Sàng lọc là cửa vào cơ hội việc làm và thu nhập. Người bị loại có thể không biết quyết định dựa trên AI hoặc không có cách yêu cầu xem xét lại. |
| Dữ liệu nhạy cảm có thể được sử dụng | Thông tin liên hệ, lịch sử làm việc, học vấn; dấu hiệu về tuổi, giới, sức khỏe/khuyết tật, chủng tộc hoặc tổ chức cộng đồng. Tôi chỉ phân tích nhóm dữ liệu, không đưa CV hay thông tin ứng viên thật vào repo. |
| Nhu cầu human review | **Cao.** Người tuyển dụng phải kiểm tra căn cứ gắn với yêu cầu công việc trước quyết định loại; người phụ trách chất lượng kiểm tra mẫu hồ sơ bị AI đánh giá thấp và chênh lệch giữa nhóm. Cần quyền sửa/ghi đè và kênh yêu cầu xem xét lại. Việc có người duyệt chỉ hữu ích khi họ kiểm tra độc lập. |

## 2. Case study 1 — GPT-4 xếp hạng CV có dấu hiệu khuyết tật

### Brief Case

- **Tổ chức / sản phẩm AI:** Nghiên cứu của University of Washington về ChatGPT sử dụng GPT-4.
- **Thời gian, địa điểm / bối cảnh:** Công bố tại FAccT tháng 6/2024; thí nghiệm với vị trí student researcher tại Mỹ.
- **AI được dùng để làm gì:** So sánh CV gốc với bản bổ sung thành tích liên quan đến khuyết tật.
- **Vấn đề:** AI có thể đánh giá bất lợi khi CV có thêm dấu hiệu về khuyết tật.
- **Số liệu:** Sáu biến thể, mỗi biến thể so sánh 10 lần: CV bổ sung đứng đầu **15/60 lần (25%)**; sau thêm hướng dẫn chống thiên lệch, **37/60 lần**. Đây là lượt so sánh, không phải số ứng viên bị từ chối.
- **Nguồn:** Stefan Milne, UW News, 21/06/2024, [ChatGPT is biased against resumes with credentials that imply a disability — but it can improve](https://www.washington.edu/news/2024/06/21/chatgpt-ai-bias-ableism-disability-resume-cv/), các đoạn mô tả thiết kế và kết quả thí nghiệm.
- **Bằng chứng và nhận định:** Nguồn xác nhận kết quả xếp hạng; chưa chứng minh thiệt hại tuyển dụng thực tế. Tôi xem đây là tín hiệu cần kiểm tra trước triển khai.

### Harm Map Worksheet

Các nhãn mức độ và biện pháp trong bảng là phân tích của tôi.

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Người tuyển dụng dùng thứ hạng CV để chọn shortlist hoặc loại hồ sơ mà không xem căn cứ độc lập. |
| Stakeholder bị ảnh hưởng | Ứng viên có dấu hiệu khuyết tật trong hồ sơ; người tuyển dụng; doanh nghiệp; bộ phận giám sát chất lượng tuyển dụng. |
| Failure mode | **Bias / fairness.** Nguy cơ bổ sung: over-reliance nếu người duyệt xem thứ hạng như đánh giá khách quan. |
| Layer bắt đầu lỗi | **Model** là giả thuyết phù hợp từ hành vi đầu ra. **Grounding** liên quan tới hướng dẫn đánh giá, nhưng chưa đủ bằng chứng xác định nguyên nhân bên trong mô hình. |
| Harm xảy ra là gì? | Đã quan sát bất lợi trong xếp hạng thí nghiệm. **Nguy cơ:** ứng viên mất cơ hội khi shortlist phụ thuộc kết quả đó; chưa có số liệu về người mất việc hoặc thiệt hại thu nhập thực tế. |
| Harm lens | **Opportunity loss** là nguy cơ chính; **dignity loss** nếu đánh giá năng lực bị quy về thuộc tính cá nhân. |
| Severity | **High**, theo đánh giá của tôi, nếu quyết định loại ảnh hưởng đến cơ hội việc làm. Không xếp Critical vì case không chứng minh tổn hại thể chất nghiêm trọng. |
| Scale | Phạm vi được nguồn báo cáo là thí nghiệm ở Brief Case. Quy mô ứng viên bị ảnh hưởng ngoài thực tế **chưa đủ dữ liệu**. |
| Probability | Kết quả 25% là tỷ lệ CV bổ sung đứng đầu trong thiết kế đó; **không phải xác suất bị phân biệt đối xử ngoài thực tế**. Chưa đủ dữ liệu để ước lượng xác suất harm khi triển khai. |
| Frequency | Có lặp lại việc đánh giá trong thí nghiệm. Tần suất sự cố trong quy trình tuyển dụng thật chưa được nguồn xác định. |
| Vì sao? | Tôi đánh giá severity theo hậu quả tiềm tàng của quyết định loại. Scale, probability và frequency cần kiểm tra trên dữ liệu triển khai; không suy rộng từ số lượt gọi mô hình sang số nạn nhân. |

**Biện pháp đề xuất:** Dùng rubric năng lực gắn với vị trí, yêu cầu người duyệt kiểm tra chứng cứ trong CV; kiểm tra kết quả khi thêm/bỏ dấu hiệu nhân khẩu học trên hồ sơ thử nghiệm tương đương. Không coi thêm một câu hướng dẫn chống thiên lệch là chứng nhận an toàn. Cho phép ứng viên yêu cầu xem xét lại quyết định.

## 3. Case study 2 — Thiên lệch tên trong sàng lọc CV bằng embedding

### Brief Case

- **Tổ chức / sản phẩm AI:** Kyra Wilson và Aylin Caliskan, University of Washington; e5, GritLM và SFR.
- **Thời gian, địa điểm / bối cảnh:** Bản nghiên cứu 29/07/2024; sàng lọc CV tiếng Anh theo mô tả việc làm.
- **AI được dùng để làm gì:** Xếp hạng độ phù hợp CV bằng độ tương đồng embedding.
- **Vấn đề:** Đổi tên biểu thị nhóm nhân khẩu học có thể làm thay đổi kết quả chọn CV.
- **Số liệu:** **554 CV, 571 mô tả công việc, chín nhóm nghề, ba mô hình.** Mục Results báo cáo **85,1%** ưu tiên tên gắn với người da trắng trong bộ kiểm tra thiên lệch chủng tộc. Đây là tỷ lệ kiểm tra, không phải tỷ lệ ứng viên được tuyển.
- **Nguồn:** Wilson & Caliskan, [Gender, Race, and Intersectional Bias in Resume Screening via Language Model Retrieval](https://arxiv.org/html/2407.20371v1), 29/07/2024, mục Data và Results, Figure 4.
- **Bằng chứng và nhận định:** Nghiên cứu đo đầu ra trong mô phỏng sàng lọc; tôi phân tích nguy cơ triển khai, không coi đây là số nạn nhân thực tế.

### Harm Map Worksheet

Các nhãn mức độ và biện pháp trong bảng là phân tích của tôi.

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Hệ thống chọn top-k CV để chuyển sang phỏng vấn; người tuyển dụng chỉ đọc danh sách được hệ thống đưa lên. |
| Stakeholder bị ảnh hưởng | Ứng viên thuộc nhóm bị xếp hạng bất lợi; người tuyển dụng; nhà cung cấp mô hình; doanh nghiệp dùng dịch vụ. |
| Failure mode | **Bias / fairness.** Over-reliance là nguy cơ của bước sử dụng điểm số, chưa phải hành vi recruiter được nghiên cứu này đo. |
| Layer bắt đầu lỗi | **Model**, xét biểu diễn embedding và hành vi xếp hạng; chưa đủ căn cứ quy lỗi cho một tập dữ liệu huấn luyện cụ thể. Cách dùng điểm để loại hồ sơ là rủi ro thiết kế **UX/Safety** cần kiểm soát thêm. |
| Harm xảy ra là gì? | Đã đo chênh lệch lựa chọn trong thí nghiệm. **Nguy cơ:** ứng viên phù hợp không vào shortlist chỉ vì tín hiệu từ tên. Chưa chứng minh số người mất cơ hội việc làm khi doanh nghiệp triển khai. |
| Harm lens | **Opportunity loss**; **dignity loss** nếu giá trị của ứng viên bị thay thế bằng tín hiệu nhóm xã hội. |
| Severity | **High**, theo đánh giá của tôi, khi thứ hạng quyết định cơ hội phỏng vấn. Nếu chỉ dùng để tổ chức hồ sơ và mọi CV vẫn được đánh giá độc lập, tác động có thể thấp hơn. |
| Scale | Phạm vi khảo sát được nêu trong Brief Case. Không coi số CV mẫu là số người chịu thiệt hại hoặc đại diện toàn thị trường tuyển dụng. |
| Probability | Tỷ lệ kiểm tra ưu tiên một nhóm phản ánh thiết kế nghiên cứu; **không phải xác suất một cá nhân bị loại**. Chưa đủ dữ liệu định lượng probability của harm ngoài thực tế. |
| Frequency | Chênh lệch xuất hiện qua nhiều điều kiện khảo sát; chưa có tần suất sự cố theo ngày/tháng trong một hệ thống đang vận hành. |
| Vì sao? | Top-k là điểm có thể biến một chênh lệch điểm nhỏ thành mất cơ hội. Cần kiểm tra cấu hình, ngưỡng và dữ liệu cụ thể; kết quả trên tiếng Anh không tự xác nhận mức thiên lệch đối với CV/tên tiếng Việt. |

**Biện pháp đề xuất:** So sánh hồ sơ tương đương khi đổi tín hiệu tên; thử che tên và kiểm tra cả các dấu hiệu thay thế còn lại. Người tuyển dụng phải kiểm tra mẫu hồ sơ ngoài top-k. Ghi lại phiên bản mô hình, rubric, ngưỡng và lý do loại để có thể xem xét lại; không dùng cosine similarity như xác suất ứng viên phù hợp.

## 4. Tổng hợp và ưu tiên kiểm soát

| Điểm so sánh | Case 1 | Case 2 |
| --- | --- | --- |
| Cơ chế | LLM sinh thứ hạng và giải thích | Embedding phục vụ truy hồi/xếp hạng |
| Dấu hiệu cần kiểm tra | Thông tin liên quan khuyết tật | Tên gợi nhóm nhân khẩu học |
| Điểm chuyển từ lỗi sang harm | Recruiter dùng thứ hạng để loại | Shortlist chỉ lấy top-k |
| Điều chưa chứng minh | Thiệt hại tuyển dụng thực tế | Tác động trong hệ thống doanh nghiệp và bối cảnh Việt Nam |

**Ưu tiên của tôi:** trước khi để AI ảnh hưởng quyết định loại, kiểm tra hồ sơ tương đương, kiểm tra mẫu ngoài shortlist và yêu cầu người duyệt ghi căn cứ gắn với công việc. Nếu phát hiện chênh lệch chưa giải thích được, dừng dùng điểm AI để loại hồ sơ cho tới khi điều tra và đánh giá lại.

## 5. AI Support Log

Tôi sử dụng Codex để hỗ trợ tìm nguồn, tổng hợp theo mẫu README và kiểm tra đủ 11 trường Harm Map. Điểm được chỉnh khi tổng hợp là tách số liệu kiểm tra khỏi xác suất tuyển dụng và phân biệt kết quả nghiên cứu với harm ngoài thực tế. Các đánh giá định tính là phần phân tích trong báo cáo; không bổ sung dữ liệu ứng viên hoặc kết quả không có nguồn.

