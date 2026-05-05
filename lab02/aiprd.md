# 6. Dependencies & Constraints — Ràng buộc cần biết

## 🛠️ Kỹ thuật & Công nghệ
- **STT Engine**  
  Cần API nhận diện giọng nói tiếng Trung độ trễ thấp, nhận tốt giọng Việt  
  *(Whisper, Google STT, iFlytek)*

- **TTS Engine**  
  Giọng đọc AI tự nhiên, phù hợp hội thoại  
  *(Azure, ElevenLabs)*

- **LLM**  
  Phản hồi giữ ngữ cảnh, sử dụng từ vựng *Business Chinese*

- **Độ trễ toàn hệ thống**  
  (STT → LLM → TTS) không vượt quá **2 giây**

---

## 📚 Dữ liệu & Nội dung
- Bộ kịch bản hội thoại thực tế trong môi trường công việc tại Việt Nam  
- Cơ sở dữ liệu âm thanh phát âm chuẩn  
  *(Pinyin, Tones)*

---

## 👤 Người dùng & Môi trường
- AI cần khả năng lọc nhiễu tốt, nhận diện chính xác trong môi trường ồn  
- Hỗ trợ lưu trạng thái hội thoại, phù hợp với lịch học ngắt quãng  
- Ưu tiên tối ưu cho thiết bị di động (*mobile-first*)

---

## 🔒 Quy định & Bảo mật
- Tuân thủ bảo mật dữ liệu cá nhân  
  *(GDPR, quy định Việt Nam)*

- Guardrails kiểm soát nội dung LLM  
  → Tránh các chủ đề nhạy cảm về văn hóa / chính trị