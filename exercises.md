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
> Khi temperature tăng, phản hồi trở nên sáng tạo và đa dạng hơn về cách diễn đạt, nhưng có thể trở nên lan man hoặc kém chính xác ở mức cực cao. Ở temperature thấp, phản hồi mang tính ổn định, súc tích và gần như giống hệt nhau qua các lần thử.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2 - 0.5. Lý do là chatbot hỗ trợ khách hàng cần sự chính xác, nhất quán và tuân thủ đúng các thông tin/quy trình đã thiết lập, tránh việc AI tự ý "sáng tạo" thêm thông tin sai lệch.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload mỗi ngày: 10.000 users × 3 calls/user × 350 tokens/call = 10.500.000 tokens/day ,Tổng cộng khoảng 10.5 triệu token/ngày. Nếu tính theo input token:GPT-4o:      10.5 × $2.50 = $26.25/ngày ,GPT-4o-mini: 10.5 × $0.15 = $1.575/ngày ,Tỉ lệ chênh lệch: 2.50 / 0.15 ≈ 16.7 lần . Nếu tính theo output token: 10.00 / 0.60 ≈ 16.7 lần .Vì vậy, có thể ước tính GPT-4o đắt hơn GPT-4o-mini khoảng 16–17 lần cho workload tương tự, tùy tỉ lệ input/output thực tế.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o-mini phù hợp hơn cho các tác vụ đơn giản, lặp lại nhiều và cần tối ưu chi phí, ví dụ: chatbot FAQ, phân loại email, tóm tắt ngắn, gắn nhãn dữ liệu hoặc xử lý request số lượng lớn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng chatbot tương tác trực tiếp với người dùng (như ChatGPT), nơi tốc độ phản hồi cảm nhận (perceived latency) là then chốt; nó giúp người dùng bắt đầu đọc ngay khi AI đang tạo văn bản. Ngược lại, non-streaming phù hợp hơn cho các tác vụ xử lý hàng loạt (batch processing), trích xuất dữ liệu có cấu trúc (như JSON) để hệ thống khác xử lý tiếp, hoặc khi nội dung phản hồi rất ngắn khiến việc streaming không mang lại sự khác biệt đáng kể.


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
