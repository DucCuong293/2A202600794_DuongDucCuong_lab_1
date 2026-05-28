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
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít thay đổi giữa các lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời bắt đầu đa dạng hơn về cách diễn đạt nhưng vẫn còn khá hợp lý. Ở mức 1.5, phản hồi có xu hướng sáng tạo hơn nhưng cũng dễ lan man hoặc kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2 đến 0.4 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời nhất quán, ít bịa đặt và dễ kiểm soát hơn, trong khi vẫn đủ tự nhiên để hội thoại không quá cứng nhắc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o có giá output $0.010/1K token, còn GPT-4o-mini là $0.0006/1K token, nên GPT-4o đắt hơn khoảng 0.010 / 0.0006 = 16.7 lần. Với 10.000 người dùng mỗi ngày, mỗi người 3 lần gọi API, tổng số lần gọi là 30.000; nếu mỗi lần khoảng 350 output token thì tổng là 10,5 triệu output token/ngày. Chi phí ước tính là khoảng $105/ngày cho GPT-4o và $6.30/ngày cho GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng hơn trong các tác vụ cần chất lượng suy luận cao, ví dụ phân tích tài liệu pháp lý, xử lý yêu cầu khách hàng phức tạp, hoặc tạo nội dung quan trọng cần ít lỗi. GPT-4o-mini phù hợp hơn cho các tác vụ khối lượng lớn và rủi ro thấp như phân loại tin nhắn, tóm tắt ngắn, trả lời FAQ cơ bản hoặc chatbot nội bộ có ngân sách hạn chế.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi có thể dài hoặc mất nhiều thời gian, ví dụ chatbot tư vấn, trợ lý viết nội dung, giải thích từng bước hoặc tạo báo cáo, vì người dùng thấy kết quả xuất hiện ngay và cảm giác chờ đợi giảm đi rõ rệt. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý toàn bộ kết quả trước khi hiển thị, hoặc khi ứng dụng cần kiểm duyệt/định dạng JSON hoàn chỉnh trước khi gửi cho người dùng. Với các API backend hoặc tác vụ tự động, non-streaming cũng đơn giản hơn để log, kiểm tra lỗi và lưu kết quả.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
