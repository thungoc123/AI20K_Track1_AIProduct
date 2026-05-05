
## 1. Problem Statement — Bài toán cần giải quyết là gì?
Người đi làm (22–40 tuổi) học tiếng Trung tại Việt Nam, có nền tảng ngữ pháp/từ vựng nhưng "câm" khi giao tiếp thực tế, do thiếu môi trường luyện nói không áp lực. Điều này khiến họ không đạt hiệu quả sử dụng tiếng Trung trong công việc hoặc giao thương.

## 2. Target User — Ai là người dùng ưu tiên?
Người đi làm (22–40 tuổi) học tiếng Trung tại Việt Nam, tranh thủ thời gian rảnh (giờ nghỉ trưa, sau khi con cái đi ngủ), mong muốn phản xạ tự nhiên, không cần dịch nhẩm, phát âm chuẩn hơn.

## 3. User Stories — Hành vi người dùng trông như thế nào?
- As a busy office worker learning Chinese, I want to practice speaking with an always-available, non-judgmental partner, so that I can improve my pronunciation and fluency without feeling embarrassed.
- As a Vietnamese professional, I want to fit short speaking practice sessions into my fragmented schedule, so that I can gradually build natural reflexes for real-life conversations.


## 4. MVP Scope — Ranh giới build

**In-Scope:**
- Có thể nghe được người dùng nói và bắt đầu được cuộc trò chuyện trôi chảy theo một chủ đề cụ thể.

**Out-of-Scope:**
- AI sàng lọc ra những lỗi của người dùng khi nói chuyện và recommend họ theo hướng tốt hơn.

**Non-Goals:**
- Dạy kiến thức về tiếng Trung.
- Phổ cập nội dung hay đa dạng các nội dung như đọc/viết.

## 5. Success Metrics — Thế nào là thành công?
- Tỷ lệ người dùng trả lời tiếng Trung dưới 3 giây mà không cần dịch nhẩm trong đầu.
- Số lần luyện nói/ngày.
- Mức độ tự tin khi giao tiếp thực tế (qua khảo sát hoặc phản hồi).

## 6. Dependencies & Constraints — Ràng buộc cần biết

**Kỹ thuật & Công nghệ:**
- STT Engine: Cần API nhận diện giọng nói tiếng Trung độ trễ thấp, nhận tốt giọng Việt (Whisper, Google STT, iFlytek).
- TTS Engine: Giọng đọc AI tự nhiên, phù hợp hội thoại (Azure, ElevenLabs).
- LLM: Phản hồi giữ ngữ cảnh, dùng từ vựng business Chinese.
- Độ trễ toàn hệ thống (STT→LLM→TTS) không vượt 2 giây.

**Dữ liệu & Nội dung:**
- Bộ kịch bản hội thoại thực tế công việc tại Việt Nam.
- Cơ sở dữ liệu âm thanh phát âm chuẩn (Pinyin, Tones).

**Người dùng & Môi trường:**
- AI cần lọc nhiễu tốt, nhận diện đúng trong môi trường ồn.
- Hỗ trợ lưu trạng thái hội thoại, phù hợp lịch học ngắt quãng.
- Ưu tiên tối ưu cho thiết bị di động (mobile-first).

**Quy định & Bảo mật:**
- Tuân thủ bảo mật dữ liệu cá nhân (GDPR, quy định VN).
- Guardrails kiểm soát nội dung LLM, tránh chủ đề nhạy cảm văn hóa/chính trị.