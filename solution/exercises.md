# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít thay đổi nếu gọi lại nhiều lần. Khi tăng lên 0.5, 1.0 và 1.5, câu trả lời có xu hướng đa dạng hơn về cách diễn đạt và chi tiết được chọn, nhưng temperature quá cao cũng dễ làm phản hồi kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2-0.4 cho chatbot hỗ trợ khách hàng, vì loại chatbot này cần trả lời nhất quán, đúng chính sách và ít sáng tạo quá mức. Mức này vẫn cho phép câu trả lời tự nhiên hơn temperature 0.0 nhưng giảm rủi ro đưa ra thông tin không ổn định.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Với giá output trong đề bài, GPT-4o là $0.010/1K token và GPT-4o-mini là $0.0006/1K token, nên GPT-4o đắt hơn khoảng 0.010 / 0.0006 = 16.67 lần. Workload mỗi ngày là 10.000 * 3 * 350 = 10.500.000 token; chi phí output ước tính là khoảng $105/ngày cho GPT-4o và $6.30/ngày cho GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng hơn khi tác vụ cần chất lượng suy luận cao, ví dụ phân tích tài liệu quan trọng, hỗ trợ quyết định phức tạp hoặc xử lý yêu cầu có nhiều ngữ cảnh. GPT-4o-mini phù hợp hơn cho các tác vụ số lượng lớn, rủi ro thấp như FAQ, tóm tắt ngắn, phân loại nội dung đơn giản hoặc chatbot nội bộ cần tốc độ và chi phí thấp.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang chờ tương tác trực tiếp, ví dụ chatbot, trợ lý viết nội dung, giải thích từng bước hoặc các tác vụ có độ trễ cao, vì người dùng thấy kết quả bắt đầu xuất hiện ngay và cảm giác hệ thống phản hồi nhanh hơn. Non-streaming phù hợp hơn khi cần nhận toàn bộ kết quả trước khi xử lý tiếp, ví dụ gọi API backend để phân tích JSON, chấm điểm, kiểm duyệt, lưu log hoặc hiển thị một kết quả ngắn mà việc stream từng phần không tạo thêm giá trị.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
